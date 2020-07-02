---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620532"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>Allowcustompeskime ile true olarak ayarlanan GridViews, görünümün son sayfasından çıkılırken PageIndexChanging olayını tetiklebiliyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' deki bir hata <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> bazen <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> etkinleştirilmiş olan s için tetiklenmesine neden olur <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir. Geçici bir çözüm olarak, uygulama, bu koşullara ulaşmaları için açık bir BindGrid gerçekleştirebilir <code>Page_Load</code> ( <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> son sayfada ve son <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> olarak ' den farklıdır <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ). Alternatif olarak, bu senaryo sorunu göstermediğinden, uygulama, sayfalama (özel disk belleği yerine) için de değiştirilebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
