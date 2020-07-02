---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616098"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml. GetPublicKey yeniden hedefleme değişikliği olmadan net462 (veya açıklamadan) üzerinde RSACng döndürüyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ile başlayarak, yöntem tarafından döndürülen nesnenin somut türü <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> (bir olağandışı bir şekilde), bir CryptoServiceProvider uygulamasından CNG uygulamasına değişti. Bunun nedeni, uygulamanın ' i `certificate.PublicKey.Key` ileten iç öğesini kullanmaya değiştiği `certificate.GetAnyPublicKey` anlamına gelir <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.1 üzerinde çalışan uygulamalardan başlayarak, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek .NET Framework 4.6.1 ve önceki sürümlerde varsayılan olarak kullanılan CryptoServiceProvider kullanabilirsiniz:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
