---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805229"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>WPF PackageDigitalSignatureManager için varsayılan karma algoritması SHA256 sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> WPF paketleri ile ilgili dijital imzalar için işlevsellik sağlar.  .NET Framework 4.7 ve önceki sürümlerinde, varsayılan algoritma (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) bölümleri paketi imzalamak için kullanılan SHA1 oluştu.  SHA1 ile en son güvenlik kaygıları nedeniyle, bu varsayılan için SHA256 değiştirildi .NET Framework 4.7.1 ile başlatılıyor.  Bu değişiklik tüm paket imzalama, XPS belgeleri de dahil olmak üzere etkiler.|
|Öneri|Bu değişiklik sırasında bir .NET Framework 4.7.1 veya büyük olabilir ya da .NET Framework 4.7.1'i hedefleyen aşağıdaki AppContext bayrak ayarlanırken önceki işlevselliği gerektiren bir geliştirici aşağıda framework sürümünü hedefleme uygun şekilde kullanmak isteyen bir geliştirici.  Doğru değeri, SHA1 neden olur; varsayılan algoritma kullanılan SHA256 sonuçlanır.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
