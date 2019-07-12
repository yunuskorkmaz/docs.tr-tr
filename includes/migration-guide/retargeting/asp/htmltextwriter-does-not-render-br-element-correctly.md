---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804484"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter işleme değil `<br/>` öğesi doğru

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6, çağırma başlayarak <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> ile bir <code>&lt;BR /&gt;</code> öğesi doğru ekler tek <code>&lt;BR /&gt;</code> (yerine iki)|
|Öneri|Bir uygulama üzerinde fazladan bağlıysa <code>&lt;BR /&gt;</code> etiketi <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci bir kez çağrılmalıdır. Bu davranışı değiştirmek yalnızca unutmayın .NET Framework 4.6 veya üzeri, eski davranışı sağlamak için .NET Framework'ün önceki bir sürümü hedeflemek için başka bir seçenek, bu nedenle hedefleyen uygulamaları etkiler.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

