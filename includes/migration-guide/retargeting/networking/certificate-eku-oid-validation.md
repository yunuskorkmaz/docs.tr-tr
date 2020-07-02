---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615757"
---
### <a name="certificate-eku-oid-validation"></a>Sertifika EKU OID doğrulaması

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Net.Security.SslStream> veya <xref:System.Net.ServicePointManager> sınıfları gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulaması gerçekleştirir. Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları belirten bir nesne tanımlayıcıları (OID) koleksiyonudur. EKU OID doğrulaması, uzak sertifikanın amaçlanan amaç için doğru OID 'ler olduğundan emin olmak için uzak sertifika geri çağırmaları kullanır.

#### <a name="suggestion"></a>Öneri

Bu değişiklik istenmeyen ise, [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) uygulama yapılandırma dosyanızdaki öğesine aşağıdaki anahtarı ekleyerek SERTIFIKA EKU OID doğrulamasını devre dışı bırakabilirsiniz [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde kullanılması önerilmez.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
