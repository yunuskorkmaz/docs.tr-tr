---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804429"
---
### <a name="certificate-eku-oid-validation"></a>Sertifika EKU OID doğrulama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile <xref:System.Net.Security.SslStream> <xref:System.Net.ServicePointManager> başlayarak, veya sınıflar gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulaması gerçekleştirir. Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları gösteren nesne tanımlayıcıları (OSB) koleksiyonudur. EKU OID doğrulama, uzak sertifikanın amaçlanan amaç için doğru OSB'lere sahip olduğundan emin olmak için uzaktan sertifika geri aramalarını kullanır.|
|Öneri|Bu değişiklik istenmiyorsa, uygulama yapılandırma dosyanızın>[ \<AppContextSwitchOverrides'e](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) aşağıdaki anahtarı ekleyerek sertifika EKU OID doğrulaması'nı devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Kullanımı aksi takdirde tavsiye edilmez.</blockquote> |
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
