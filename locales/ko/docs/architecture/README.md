# Cline 확장 아키텍처

이 디렉토리에는 Cline VSCode 확장 프로그램의 아키텍처 문서가 포함되어 있습니다.

## 확장 아키텍처 다이어그램

[extension-architecture.mmd](./extension-architecture.mmd) 파일에는 Cline 확장의 고수준 아키텍처를 보여주는 Mermaid 다이어그램이 포함되어 있습니다. 다이어그램은 다음을 설명합니다:

1. **코어 확장**
   - 확장 진입점 및 주요 클래스
   - VSCode의 글로벌 상태 및 비밀 저장소를 통한 상태 관리
   - Cline 클래스 내의 핵심 비즈니스 로직

2. **웹뷰 UI**
   - React 기반 사용자 인터페이스
   - ExtensionStateContext를 통한 상태 관리
   - 구성 요소 계층 구조

3. **저장소**
   - 이력 및 상태에 대한 작업별 저장소
   - 파일 변경에 대한 Git 기반 체크포인트 시스템

4. **데이터 흐름**
   - 구성 요소 간의 코어 확장 데이터 흐름
   - 웹뷰 UI 데이터 흐름
   - 코어와 웹뷰 간의 양방향 통신

## 다이어그램 보기

다이어그램을 보려면:
1. VSCode에 Mermaid 다이어그램 뷰어 확장을 설치하세요
2. extension-architecture.mmd 파일을 엽니다
3. 확장의 미리보기 기능을 사용하여 다이어그램을 렌더링하세요

또한 GitHub에서 다이어그램을 볼 수 있으며, GitHub에는 내장된 Mermaid 렌더링 지원이 있습니다.

## 색상 구성표

다이어그램은 더 나은 가시성을 위해 고대비 색상 구성표를 사용합니다:
- 분홍색 (#ff0066): 글로벌 상태 및 비밀 저장소 구성 요소
- 파란색 (#0066ff): 확장 상태 컨텍스트
- 녹색 (#00cc66): Cline 제공자
- 모든 구성 요소는 최대 가독성을 위해 흰색 텍스트를 사용합니다