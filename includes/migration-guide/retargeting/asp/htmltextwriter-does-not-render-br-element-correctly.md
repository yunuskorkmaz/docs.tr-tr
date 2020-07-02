---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615742"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter `<br/>` öğeyi doğru işlemiyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> içeren bir `<BR />` öğe çağırmak doğru bir şekilde yalnızca bir tane eklenir `<BR />` (iki yerine)

#### <a name="suggestion"></a>Öneri

Bir uygulama ekstra etikete bağımlılarsa `<BR />` <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci kez çağrılmalıdır. Bu davranış değişikliğinin yalnızca .NET Framework 4,6 veya üstünü hedefleyen uygulamaları etkilediğini unutmayın. bu nedenle, eski davranışı almak için başka bir seçenek .NET Framework önceki bir sürümünü hedeflemelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
