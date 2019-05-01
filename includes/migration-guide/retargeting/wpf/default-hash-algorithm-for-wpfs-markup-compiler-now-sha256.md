---
ms.openlocfilehash: 14b8930044381d1d86ec7984d36a5c3588eebd81
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762630"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>WPF'nin biçimlendirme derleyici için varsayılan karma algoritması SHA256 sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|WPF MarkupCompiler XAML işaretleme dosyaları için derleme hizmetleri sağlar.  .NET Framework 4.7.1 ve önceki sürümlerinde sağlaması için kullanılan varsayılan karma algoritma SHA1 oluştu. SHA1 ile en son güvenlik kaygıları nedeniyle, bu varsayılan için SHA256 değiştirildi .NET Framework ile 4.7.2 başlatılıyor.  Bu değişiklik tüm sağlama toplamı oluşturulması işaretleme dosyaları için derleme sırasında etkiler.|
|Öneri|.NET Framework 4.7.2 hedefleyen bir geliştirici ya da daha büyük ve SHA1 karma davranışa dönmek istediği aşağıdaki AppContext bayrak ayarlamanız gerekir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bir aşağıda 4.7.2 .NET framework sürümünü hedefleme kümesi SHA256 karma yararlanmak isteyen bir geliştirici AppContext bayrağı altında.  .NET Framework'ün yüklü sürümü 4.7.2 olmasına dikkat edin veya daha büyük.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
