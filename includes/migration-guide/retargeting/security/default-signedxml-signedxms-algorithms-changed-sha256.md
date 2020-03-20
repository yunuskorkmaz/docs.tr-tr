---
ms.openlocfilehash: db076d6799e4de5b8610cf9c1aac79b5386a7229
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858994"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Varsayılan İmzaXML ve İmzaXMS algoritmaları SHA256 olarak değiştirildi

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ve daha önceki nde, Bazı işlemler için SignedXML ve SignedCMS varsayılan SHA1'dir. .NET Framework 4.7.1 ile başlayarak, SHA256 varsayılan olarak bu işlemler için etkinleştirilir. SHA1 artık güvenli olarak kabul edilir, çünkü bu değişiklik gereklidir.|
|Öneri|SHA1 (güvensiz) veya SHA256'nın varsayılan olarak kullanılıp kullanılmadığını denetlemek için iki yeni bağlam anahtarı değeri vardır:<ul><li>Switch.System.Security.Cryptography.Xml.UseSecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>.NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamalariçin, SHA256 kullanımı istenmeyen ise, uygulama config dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek varsayılanı SHA1'e geri yükleyebilirsiniz:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>.NET Framework 4.7 ve önceki sürümleri hedefleyen uygulamalar için, uygulama config dosyanızın [çalışma süresi](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek bu değişikliği tercih edebilirsiniz:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|
