### .clineignoreのサポート

Clineがアクセスできるファイルをより制御できるように、`.clineignore`機能を実装しました。これは`.gitignore`に似ており、Clineがアクセスまたは処理すべきでないファイルやディレクトリを指定できます。これは以下の点で役立ちます：

*   **プライバシー：** ワークスペース内の機密性の高いまたはプライベートなファイルへのClineのアクセスを防ぐ。
*   **パフォーマンス：** タスクに関連しない大きなディレクトリやファイルを除外し、Clineの効率を向上させる。
*   **コンテキスト管理：** プロジェクトの関連部分にClineの注意を集中させる。

**`.clineignore`の使用方法**

1.  **`.clineignore`ファイルを作成する：** ワークスペースのルートディレクトリ（`.vscode`フォルダと同じレベル、またはVS Codeで開いたトップレベルのフォルダ）に、`.clineignore`という名前の新しいファイルを作成します。

2.  **無視パターンを定義する：** `.clineignore`ファイルを開き、Clineが無視すべきファイルやディレクトリのパターンを指定します。構文は`.gitignore`と同じです：

    *   ファイルの各行がパターンを表します。
    *   **標準のグロブパターンがサポートされています：**
        *   `*`はゼロ以上の文字にマッチします
        *   `?`は一文字にマッチします
        *   `[]`は文字範囲にマッチします
        *   `**`は任意の数のディレクトリとサブディレクトリにマッチします。

    *   **ディレクトリパターン：** パターンの末尾に`/`を付けてディレクトリを指定します。
    *   **否定パターン：** パターンの先頭に`!`を付けて、以前に無視されたパターンを否定（無視しない）します。
    *   **コメント：** 行の先頭に`#`を付けてコメントを追加します。

    **`.clineignore`ファイルの例：**

    ```
    # ログファイルを無視
    *.log

    # 'node_modules'ディレクトリ全体を無視
    node_modules/

    # 'temp'ディレクトリとそのサブディレクトリ内のすべてのファイルを無視
    temp/**

    # ただし、ルートにある'important.log'は無視しない
    !important.log

    # 任意のサブディレクトリにある'secret.txt'という名前のファイルを無視
    **/secret.txt
    ```

3.  **Clineはあなたの`.clineignore`を尊重します：** `.clineignore`ファイルを保存すると、Clineは自動的にこれらのルールを認識し適用します。

    *   **ファイルアクセス制御：** Clineは`read_file`などのツールを使用して無視されたファイルの内容を読み取ることができません。無視されたファイルに対してツールを使用しようとすると、Clineは`.clineignore`設定によりアクセスがブロックされていることを通知します。
    *   **ファイルリスト：** ディレクトリ内のファイルをリストアップするようClineに依頼した場合（例：`list_files`を使用）、無視されたファイルやディレクトリは依然としてリストされますが、名前の横に**🔒**シンボルが付いて無視されていることを示します。これにより、Clineがどのファイルと対話できるかがわかります。

4.  **動的更新：** Clineは`.clineignore`ファイルの変更を監視します。`.clineignore`ファイルを変更、作成、または削除すると、ClineはVS Codeや拡張機能を再起動せずに自動的に無視ルールを更新します。

**まとめ**

`.clineignore`ファイルは、ワークスペースのファイルに対するClineのアクセスを制御するための強力で柔軟な方法を提供し、プライバシー、パフォーマンス、コンテキスト管理を向上させます。馴染みのある`.gitignore`構文を活用することで、プロジェクトの最も関連性の高い部分にClineの焦点を簡単に合わせることができます。