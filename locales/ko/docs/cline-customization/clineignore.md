### .clineignore 지원

Cline이 접근할 수 있는 파일을 더 많이 제어할 수 있도록 `.clineignore` 기능을 구현했습니다. 이는 `.gitignore`와 유사하며, Cline이 접근하거나 처리하지 말아야 할 파일과 디렉터리를 지정할 수 있습니다. 이는 다음과 같은 경우에 유용합니다:

*   **개인정보 보호:** 작업 공간에서 민감하거나 개인적인 파일에 Cline이 접근하지 못하도록 방지합니다.
*   **성능:** 작업과 무관한 큰 디렉터리나 파일을 제외하여 Cline의 효율성을 potentially 향상시킵니다.
*   **컨텍스트 관리:** 프로젝트의 관련 부분에 Cline의 주의를 집중시킵니다.

**`.clineignore` 사용 방법**

1.  **`.clineignore` 파일 생성:** 작업 공간의 루트 디렉터리(`.vscode` 폴더와 동일한 레벨이거나 VS Code에서 열린 최상위 폴더)에 `.clineignore`라는 새 파일을 만듭니다.

2.  **무시 패턴 정의:** `.clineignore` 파일을 열고 Cline이 무시해야 할 파일과 디렉터리의 패턴을 지정합니다. 구문은 `.gitignore`와 동일합니다:

    *   파일의 각 줄은 패턴을 나타냅니다.
    *   **표준 glob 패턴이 지원됩니다:**
        *   `*`는 0개 이상의 문자와 일치합니다.
        *   `?`는 한 문자와 일치합니다.
        *   `[]`는 문자 범위와 일치합니다.
        *   `**`는 모든 수의 디렉터리 및 하위 디렉터리와 일치합니다.

    *   **디렉터리 패턴:** 패턴 끝에 `/`를 추가하여 디렉터리를 지정합니다.
    *   **부정 패턴:** 패턴 앞에 `!`를 추가하여 이전에 무시된 패턴을 취소합니다.
    *   **주석:** 줄의 시작에 `#`를 추가하여 주석을 추가합니다.

    **`.clineignore` 파일 예시:**

    ```
    # 로그 파일 무시
    *.log

    # 'node_modules' 디렉터리 전체 무시
    node_modules/

    # 'temp' 디렉터리와 그 하위 디렉터리의 모든 파일 무시
    temp/**

    # 하지만 'important.log'는 루트에 있어도 무시하지 않음
    !important.log

    # 모든 하위 디렉터리의 'secret.txt' 파일 무시
    **/secret.txt
    ```

3.  **Cline은 `.clineignore`를 존중합니다:** `.clineignore` 파일을 저장하면 Cline은 자동으로 이 규칙을 인식하고 적용합니다.

    *   **파일 접근 제어:** Cline은 `read_file` 같은 도구를 사용하여 무시된 파일의 내용을 읽을 수 없습니다. 무시된 파일에 도구를 사용하려고 하면 Cline은 `.clineignore` 설정으로 인해 접근이 차단되었다고 알립니다.
    *   **파일 목록:** 디렉터리의 파일을 나열하도록 Cline에게 요청할 때(예: `list_files` 사용), 무시된 파일과 디렉터리는 여전히 나열되지만 이름 옆에 **🔒** 기호가 표시되어 무시된 파일임을 나타냅니다. 이를 통해 Cline이 어떤 파일과 상호작용할 수 있는지 알 수 있습니다.

4.  **동적 업데이트:** Cline은 `.clineignore` 파일의 변경 사항을 모니터링합니다. `.clineignore` 파일을 수정, 생성 또는 삭제하면 Cline은 VS Code나 확장 프로그램을 다시 시작할 필요 없이 자동으로 무시 규칙을 업데이트합니다.

**요약**

`.clineignore` 파일은 Cline이 작업 공간 파일에 접근하는 것을 제어하는 강력하고 유연한 방법을 제공하여 개인정보 보호, 성능 및 컨텍스트 관리를 향상시킵니다. 익숙한 `.gitignore` 구문을 활용하여 프로젝트의 가장 관련 있는 부분에 Cline의 초점을 쉽게 맞출 수 있습니다.