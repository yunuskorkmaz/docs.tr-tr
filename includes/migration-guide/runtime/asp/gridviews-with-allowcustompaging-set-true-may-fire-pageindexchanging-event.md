---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496845"
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
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
