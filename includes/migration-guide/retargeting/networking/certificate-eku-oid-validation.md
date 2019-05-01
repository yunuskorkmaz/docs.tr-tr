---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640098"
---
### <a name="certificate-eku-oid-validation"></a>Sertifika EKU OID doğrulama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Net.Security.SslStream> veya <xref:System.Net.ServicePointManager> sınıfları, Gelişmiş anahtar kullanımı (EKU) nesnenin tanımlayıcısını (OID) doğrulama gerçekleştirin. Bir anahtarı kullanan uygulamaları gösteren, nesne tanımlayıcıları (OID) koleksiyonunu bir Gelişmiş anahtar kullanımı (EKU) uzantısıdır. EKU OID'sini doğrulama Uzak sertifika geri çağırmaları uzak sertifika hedeflenen amaç için doğru OID'ler olduğundan emin olmak için kullanır.|
|Öneri|Bu değişiklik, istenmeyen ise, sertifika doğrulama EKU OID aşağıdaki geçin ekleyerek devre dışı bırakabilirsiniz [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) içinde [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) biri, Uygulama yapılandırma dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde, kullanımı önerilmez.</blockquote> |
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
