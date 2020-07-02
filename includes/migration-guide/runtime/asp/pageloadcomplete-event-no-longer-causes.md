---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620539"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Page. Loadtamamlanma olayı artık System. Web. UI. WebControls. EntityDataSource denetimine veri bağlamayı çağırmaya neden olmaz

#### <a name="details"></a>Ayrıntılar

<xref:System.Web.UI.Page.LoadComplete>Olay artık <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> denetim oluşturma/güncelleştirme/silme parametrelerine yapılan değişiklikler için denetimin veri bağlamayı çağırmasına neden olmaz. Bu değişiklik veritabanına yönelik gereksiz bir seyahati ortadan kaldırır, denetim değerlerinin sıfırlanmasını önler ve ve gibi diğer veri denetimleriyle tutarlı bir davranış üretir <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> . Bu değişiklik, uygulamaların olayda veri bağlamayı çağırmaya bağlı olması olası olmayan olayda farklı davranışlar üretir <xref:System.Web.UI.Page.LoadComplete> .

#### <a name="suggestion"></a>Öneri

Veri bağlama için bir gereksinim varsa, geri gönderinin önceki kısımlarında bulunan bir olayda el ile DataBind komutunu çağırın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
