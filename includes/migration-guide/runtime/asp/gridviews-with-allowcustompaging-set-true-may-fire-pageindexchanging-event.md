---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858397"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging'in gerçeğe ayarlı GridViews,görünümün son sayfasından ayrılırken PageIndexChanging olayını ateşleyebilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5'teki <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> bir hata, <xref:System.Web.UI.WebControls.GridView?displayProperty=name>etkinleştirilen <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>ler için bazen yangın yapmamaya neden olur.|
|Öneri|Bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir. Bir geçici çözüm olarak, uygulama bu koşulları vuracak <code>Page_Load</code> herhangi bir açık BindGrid yapabilirsiniz <xref:System.Web.UI.WebControls.GridView?displayProperty=name> (son<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> sayfada <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>ve Son farklıdır). Alternatif olarak, bu senaryo sorunu göstermediğinden, uygulama sayfalama (özel sayfalama yerine) izin verecek şekilde değiştirilebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
