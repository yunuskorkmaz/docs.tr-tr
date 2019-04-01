---
ms.openlocfilehash: 63a38f33fef09577c5ed621727b8c38e4c7e1bdf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760937"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>WPF'nin biçimlendirme derleyici için varsayılan karma algoritması SHA256 sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|WPF MarkupCompiler XAML işaretleme dosyaları için derleme hizmetleri sağlar.  .NET Framework 4.7.1 ve önceki sürümlerinde sağlaması için kullanılan varsayılan karma algoritma SHA1 oluştu. SHA1 ile en son güvenlik kaygıları nedeniyle, bu varsayılan için SHA256 değiştirildi .NET Framework ile 4.7.2 başlatılıyor.  Bu değişiklik tüm sağlama toplamı oluşturulması işaretleme dosyaları için derleme sırasında etkiler.|
|Öneri|.NET Framework 4.7.2 hedefleyen bir geliştirici ya da daha büyük ve SHA1 karma davranışa dönmek istediği aşağıdaki AppContext bayrak ayarlamanız gerekir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bir aşağıda 4.7.2 .NET framework sürümünü hedefleme kümesi SHA256 karma yararlanmak isteyen bir geliştirici AppContext bayrağı altında.  .NET Framework'ün yüklü sürümü 4.7.2 olmasına dikkat edin veya daha büyük.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|

