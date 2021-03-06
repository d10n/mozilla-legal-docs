## プリインストール条件

2013年12月3日

［この文書は、日本のFirefox Marketplaceコンテンツの開発者の便宜を図るために掲載している、Preload Prerequisitesの参考訳です。］

アプリケーションがプリインストールの対象となるためには、開発者は、第1に記載される方法に従って、迅速にバグを特定し修正することに同意しなければならず、かつ、アプリは、第2において定義される技術要件を満たさなければなりません。

## 第1　サービスレベル条件

Mozilla、通信事業者または端末製造業者が不具合や欠陥を発見した場合、Bugzillaを通じて、開発者に報告されます。開発者は、以下に定義される方法に従って、これらのバグを迅速に修正することに同意するものとします。

<table>
  <thead>
    <tr>
      <th>
        優先度
      </th>
      <th>
        内容
      </th>
      <th>
        修正期限
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        P1 = 致命的
      </td>
      <td>
        致命的なバグとは、直ちに修正しなければならないバグであり、修正がなされなければ、アプリは、いずれの通信事業者によってもプリインストールされません。そのままの状態で公開された場合、アプリの基本的な機能を妨げるバグです。
      </td>
      <td>
        Bugzillaを通じて、サードパーティである開発者が担当者として設定されてから3営業日以内に、修正をMarketplaceに提出しなければなりません。
      </td>
    </tr>
    <tr>
      <td>
        P2 = 重大
      </td>
      <td>
      　重大なバグとは、バグではあるものの、アプリの基本的な機能には影響を及ぼさないものをいいます。重大なバグがあることを理由として、アプリはプリインストール対象から除外されませんが、速やかに修正されなければなりません。通常、エンドユーザによる回避策またはリリース後に適用できる応急措置があります。
      </td>
      <td>
        Bugzillaを通じて、サードパーティである開発者が担当者として設定されてから 5 営業日以内に、修正をMarketplaceに提出しなければなりません。
      </td>
    </tr>
    <tr>
      <td>
        P3 = 軽微
      </td>
      <td>
        ボタンのサイズやスペルミスなどの外観にかかる軽度な問題をいいます。
      </td>
      <td>
        Bugzillaを通じて、サードパーティである開発者が担当者として設定されてから10営業日以内に、修正をMarketplaceに提出しなければなりません。
      </td>
    </tr>
    <tr>
      <td>
        P4 = 要向上
      </td>
      <td>
        機能の向上または「あればより望ましい」事項を対象とします。
      </td>
      <td>
        開発者は、当該事項がロードマップにおいて承認された場合、アプリの新しいバージョンのリリース日を提示しなければなりません。
      </td>
    </tr>
  </tbody>
</table>

サードパーティアプリのバグ重要度レベルについては、Bugzillaにおけるプライオリティフィールドを使用して指定されます。

サードパーティアプリであることを理由に端末の出荷が停止されることはありませんが、最終的な判断は、製造受託企業（OEM）／通信事業者が行います。端末適合認証を拒絶しない代わりに、当該アプリをプリインストール対象から除外する場合があります。

## 第2　プリインストールアプリの技術要件

<table>
  <thead>
    <tr>
      <th>
        項目
      </th>
      <th>
        技術要件
      </th>
      <th>
        ユーザに取ってのメリット
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        起動時
      </td>
      <td>
        動作に数秒以上かかる場合、進捗状況を表示するインジケーターを使用しなければなりません。

        <p><a href="https://developer.mozilla.org/docs/Mozilla/Firefox_OS/Performance">
        　パフォーマンス
        </a></p>
      </td>
      <td>
        進捗状況を表示するインジケーターは、「現在、起動中です。ここまで起動済みであり、残り時間は表示のとおりです。」といった想定される会話プロトコルの側面を維持した対話的なシステムです。
      </td>
    </tr>
    <tr>
      <td>
        完全なオフラインアプリ
      </td>
      <td>
        インターネットへの接続を必要としないアプリは、完全にパッケージ化され、100％オフラインで利用可能でなければなりません（すなわち、使用に際してインターネットへの接続が要求されません）。これには、通常、ゲームやユーティリティなどのアプリが該当します。
      </td>
      <td>
        インターネットへの接続を必要としないアプリが、ユーザの想定どおりに起動し、かつその他のプラットフォーム上のものと同様に動作することを保証します。
      </td>
    </tr>
    <tr>
      <td>
        オフライン動作
      </td>
      <td>
        静的な構成要素の一切（ロゴ、メニューテキストなど）は、ライブデータをもたないアプリ（例：ゲーム、ユーティリティ）が100%オフラインで動作するように、ローカルに保存されなければなりません。
      </td>
      <td>
ユーザは、インターネットへの接続を求められることなく、かつライブデータの構成要素がプリロードされる間に、アプリケーションフレームワークを閲覧することができます。またユーザは、インターネットに接続することなく、ボックス化解除されているアプリケーションフレームワークを閲覧することができます。キャッシュ機能に加えて、インターネット接続ができない場合でも、アプリの全てを閲覧することができます。
      </td>
    </tr>
    <tr>
      <td>
        キャッシュ
      </td>
      <td>
        アプリは、少なくとも、過去に閲覧されたページがキャッシュされるように、<strong>appcache</strong> をサポートしていなければなりません。インデックス付きデータベース（IndexedDB）（ローカル保存）を利用して、情報が保存されていることが理想的です。インターネットに接続されていない場合かつ以下に該当する場合に、アプリのセッション履歴に関するデータがキャッシュされ表示されなければなりません。

        <ul>
          <li>
            アプリがバックグラウンドに移行し、再開された場合
          </li>
          <li>
          	アプリが終了され、再起動された場合
          </li>
          <li>
            端末の電源が切られ、再起動された場合
          </li>
        </ul>

インターネットに接続できないとき（端末がオンラインになっているかどうかを確認することにより検知することができます）は、アプリはキャッシュされたコンテンツをロードしなければならず（これは、アプリケーションキャッシュ（appcache）が搭載されている場合には自動的に実施されます）、ユーザに対して、アプリ内においてインターネット接続を要求するメッセージを表示します。アプリを初めて起動する場合（データが全くキャッシュされていない場合）は、ブラウザ上でのエラーとしてではなく、Firefox OSに、例えば「このアプリを使用するにはインターネットへの接続が必要です」というような「ユーザフレンドリー」なメッセージを表示しなければなりません。

        <p><a href="https://developer.mozilla.org/docs/HTML/Using_the_application_cache">
          アプリケーションキャッシュ
        </a></p>
      </td>
      <td>
        ユーザは、インターネットに接続されていない場合または更新データのロードが遅い場合に、最後に保存されたデータを閲覧することができます。
      </td>
    </tr>
    <tr>
      <td>
        言語
      </td>
      <td>
        アプリは、アプリの全ての静的な要素（例：メニューアイテム、利用規約、説明書等）において、アプリがプリインストールされている国の言語をサポートしていなければなりません。アプリは、端末の設定に基づき、言語を検出しなければなりません。
      </td>
      <td>
        ユーザは、対象となる国の言語でアプリを利用することができます。
      </td>
    </tr>
    <tr>
      <td>
        サウンド
      </td>
      <td>
        アプリは、該当する場合（例：ゲーム）、サウンドをサポートしていなければなりません。
      </td>
      <td>
      </td>
    </tr>
    <tr>
      <td>
        ユーザインターフェース（UI）
      </td>
      <td>
        アプリは、フルタッチスクリーンのユーザ・インターフェース環境をサポートしていなければならず、かつ十分な品質（例：正しいサイズのメニュー、ボタン、構成要素）を備えていなければなりません。

        <p><a href="https://developer.mozilla.org/docs/Mozilla/Firefox_OS/UX">
          ユーザインタフェースガイドライン
        </a></p>
      </td>
      <td>
      </td>
    </tr>
  <tbody>
</table>
