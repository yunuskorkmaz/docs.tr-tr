---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858929"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>WPF PackageDigitalSignatureManager için varsayılan karma algoritması şimdi SHA256 olduğunu

|   |   |
|---|---|
|Ayrıntılar|WPF <code>System.IO.Packaging.PackageDigitalSignatureManager</code> paketleriile ilgili olarak dijital imzalar için işlevsellik sağlar.  .NET Framework 4.7 ve önceki sürümlerde,<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>bir paketin bölümlerini imzalamak için kullanılan varsayılan algoritma SHA1'dir.  SHA1 ile ilgili son güvenlik endişeleri nedeniyle, bu varsayılan değer .NET Framework 4.7.1 ile başlayarak SHA256 olarak değiştirilmiştir.  Bu değişiklik, XPS belgeleri de dahil olmak üzere tüm paket imzalamayı etkiler.|
|Öneri|.NET Framework 4.7.1'in altındaki bir çerçeve sürümünü hedefleyerek bu değişikliği kullanmak isteyen bir geliştirici veya .NET Framework 4.7.1 veya daha büyük bir alanı hedefleyerek önceki işlevselliği gerektiren bir geliştirici aşağıdaki AppContext bayrağını uygun şekilde ayarlayabilir.  True değeri SHA1'in varsayılan algoritma olarak kullanılmasına neden olur; SHA256 yanlış sonuçlar.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
