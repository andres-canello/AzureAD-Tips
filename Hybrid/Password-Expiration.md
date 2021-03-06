# パスワードの有効期限に関する考慮点

## 考慮点：パスワードハッシュ同期利用時、オンプレミスADアカウントのパスワード有効期限が切れているにもかかわらず、失効したパスワードを利用してAzure ADにログインできる

ユーザーがパスワード同期のスコープ内にいる場合、クラウド アカウントのパスワードは "期限なし" に設定される仕様となっています。
つまり、オンプレミス環境でユーザーのパスワードが期限切れになった場合でも当該ユーザーは同期されたパスワード値を利用し、引き続きクラウドサービスにサインインできます。 クラウド上に格納されているハッシュ化されたパスワードは、次にオンプレミス環境でパスワードを変更したときに更新されます。

オンプレミスADがパスワード有効期限の計算をユーザーログイン時にリアルタイムで計算しているため、ユーザー属性値として有効期限を保持していないという技術的制約が背景となっています。
  
Azure AD 開発部門では、CY18中に解決できるようソリューションを検討しています。