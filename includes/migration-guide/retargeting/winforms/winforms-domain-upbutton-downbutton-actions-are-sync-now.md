---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614912"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm 'ın etki alanı UpButton ve DownButton eylemleri şimdi eşitlendi

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerde denetim <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> metni mevcut olduğunda denetim eylemi yok sayılır ve geliştirici, <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylem kullanılmadan önce denetimde eylemi kullanmak için gereklidir <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . .NET Framework başlayarak, hem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> hem de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemleri bu senaryoda bağımsız olarak çalışır ve eşitlenmiş olarak kalır.

#### <a name="suggestion"></a>Öneri

Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.2 hedeflemek için yeniden derlenir. Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.
- Aşağıdaki [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` `false` örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve olarak ayarlayarak eski kaydırma davranışının yerine geçer.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
