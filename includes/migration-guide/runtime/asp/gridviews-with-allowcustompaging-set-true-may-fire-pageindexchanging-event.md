---
ms.openlocfilehash: a7a8bd1a9823a621f3a63c6877da9454489b48fd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858397"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews AllowPaging özelliği true olarak ayarlanmış son sayfa görünümün ayrılırken PageIndexChanging olayını ateşle

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatanın neden <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> bazen için değil ateşlenmesine <xref:System.Web.UI.WebControls.GridView?displayProperty=name>etkinleştirdiyseniz s <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir. Geçici çözüm, uygulama, herhangi bir açık BindGrid gerçekleştirebilir <code>Page_Load</code> Bu koşullar isabet ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> olan son sayfasında ve son<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> farklıdır <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatif olarak, bu senaryo, sorun gösterilmemiştir gibi uygulama disk belleği (yerine özel sayfalamayı) izin verecek şekilde değiştirilebilir.|
|`Scope`|Küçük|
|Version|4,5|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

