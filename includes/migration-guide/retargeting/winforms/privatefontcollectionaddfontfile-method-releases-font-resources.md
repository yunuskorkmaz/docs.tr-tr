---
ms.openlocfilehash: 6ee290f6722480778381376f588e16877894f232
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606574"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection. AddFontFile yöntemi, yazı tipi kaynaklarını yayınlar

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerde, <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> sınıfı, <xref:System.Drawing.Text.PrivateFontCollection> <xref:System.Drawing.Font> yöntemi kullanılarak bu koleksiyona eklenen nesneler için ATıLDıKTAN sonra GDI+ yazı tipi kaynaklarını serbest bırakmaz <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> . .NET Framework 4.7.2 ve üzeri, <xref:System.Drawing.Text.FontCollection.Dispose%2A> koleksiyona dosya olarak eklenmiş olan GDI+ yazı tiplerini yayınlar.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.2 hedeflemek için yeniden derlenir. Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.
- Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4.7.1 veya daha önceki bir sürümü hedefler ve eski erişilebilirlik davranışlarından yararlanarak, aşağıdaki [AppContext anahtarını](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` app.config dosyasının bölümüne ekleyerek ve öğesini olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

.NET Framework 4.7.2 veya üstünü hedefleyen ve eski davranışı korumak isteyen uygulamalar, bu AppContext anahtarını açıkça ayarlayarak yazı tipi kaynaklarını serbest bırakmaya izin verebilir `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
