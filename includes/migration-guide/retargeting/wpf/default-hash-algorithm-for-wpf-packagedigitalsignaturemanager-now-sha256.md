---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614913"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>WPF PackageDigitalSignatureManager için varsayılan karma algoritması artık SHA256

#### <a name="details"></a>Ayrıntılar

, `System.IO.Packaging.PackageDigitalSignatureManager` WPF paketleriyle ilgili olarak dijital imzalar için işlevsellik sağlar.  .NET Framework 4,7 ve önceki sürümlerde, <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> bir paketin parçalarını imzalamak için kullanılan varsayılan algoritma () SHA1 ' dir.  SHA1 ile ilgili en son güvenlik sorunları nedeniyle, bu varsayılan değer .NET Framework 4.7.1 ile başlayarak SHA256 olarak değiştirilmiştir.  Bu değişiklik, XPS belgeleri dahil olmak üzere tüm paket imzasını etkiler.

#### <a name="suggestion"></a>Öneri

Bu değişikliği kullanmak isteyen bir geliştirici .NET Framework 4.7.1 veya önceki işlevselliği gerektiren bir geliştirici, .NET Framework 4.7.1 ya da daha fazlasını hedeflemek için aşağıdaki AppContext bayrağını uygun şekilde ayarlayabilir.  True değeri, varsayılan algoritma olarak SHA1 kullanılmasına neden olur; SHA256 içinde yanlış sonuçlar.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
