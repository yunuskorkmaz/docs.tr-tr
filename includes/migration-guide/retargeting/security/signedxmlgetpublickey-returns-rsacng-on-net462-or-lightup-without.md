---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859028"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey, değişikliği yeniden hedeflemeden net462 (veya lightup) üzerinde RSACng döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> yöntemle döndürülen nesnenin somut türü CryptoServiceProvider uygulamasından Cng uygulamasına (tuhaflık olmadan) değiştirildi. Bunun nedeni, uygulamanın <code>certificate.PublicKey.Key</code> iç tenene <code>certificate.GetAnyPublicKey</code> iletilmesine göre <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>değiştirilmesidir.|
|Öneri|.NET Framework 4.7.1'de çalışan uygulamalardan başlayarak, .NET Framework 4.6.1 ve önceki sürümlerde varsayılan olarak kullanılan CryptoServiceProvider uygulamasını, uygulama config dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek kullanabilirsiniz:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
