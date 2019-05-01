---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649602"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews AllowPaging özelliği true olarak ayarlanmış son sayfa görünümün ayrılırken PageIndexChanging olayını ateşle

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatanın neden <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> bazen için değil ateşlenmesine <xref:System.Web.UI.WebControls.GridView?displayProperty=name>etkinleştirdiyseniz s <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir. Geçici çözüm, uygulama, herhangi bir açık BindGrid gerçekleştirebilir <code>Page_Load</code> Bu koşullar isabet ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> olan son sayfasında ve son<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> farklıdır <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatif olarak, bu senaryo, sorun gösterilmemiştir gibi uygulama disk belleği (yerine özel sayfalamayı) izin verecek şekilde değiştirilebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
