---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804484"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter öğeyi `<br/>` doğru işlemez

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6'dan <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> başlayarak, arama ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> bir <code>&lt;BR /&gt;</code> öğeyle yalnızca bir <code>&lt;BR /&gt;</code> tane (iki yerine) doğru bir şekilde ekler|
|Öneri|Bir uygulama ek <code>&lt;BR /&gt;</code> etikete bağlıysa, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci kez çağrılmalıdır. Bu davranış değişikliğinin yalnızca .NET Framework 4.6 veya sonraki leri hedefleyen uygulamaları etkilediğini unutmayın, bu nedenle başka bir seçenek de eski davranışı elde etmek için .NET Framework'ün önceki bir sürümünü hedeflemektir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
