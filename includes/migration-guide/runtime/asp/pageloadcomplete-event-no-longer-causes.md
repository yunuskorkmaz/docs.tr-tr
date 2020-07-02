---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620539"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="8afb4-101">Page. Loadtamamlanma olayı artık System. Web. UI. WebControls. EntityDataSource denetimine veri bağlamayı çağırmaya neden olmaz</span><span class="sxs-lookup"><span data-stu-id="8afb4-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="8afb4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8afb4-102">Details</span></span>

<span data-ttu-id="8afb4-103"><xref:System.Web.UI.Page.LoadComplete>Olay artık <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> denetim oluşturma/güncelleştirme/silme parametrelerine yapılan değişiklikler için denetimin veri bağlamayı çağırmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="8afb4-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="8afb4-104">Bu değişiklik veritabanına yönelik gereksiz bir seyahati ortadan kaldırır, denetim değerlerinin sıfırlanmasını önler ve ve gibi diğer veri denetimleriyle tutarlı bir davranış üretir <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8afb4-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="8afb4-105">Bu değişiklik, uygulamaların olayda veri bağlamayı çağırmaya bağlı olması olası olmayan olayda farklı davranışlar üretir <xref:System.Web.UI.Page.LoadComplete> .</span><span class="sxs-lookup"><span data-stu-id="8afb4-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8afb4-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="8afb4-106">Suggestion</span></span>

<span data-ttu-id="8afb4-107">Veri bağlama için bir gereksinim varsa, geri gönderinin önceki kısımlarında bulunan bir olayda el ile DataBind komutunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="8afb4-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="8afb4-108">Name</span><span class="sxs-lookup"><span data-stu-id="8afb4-108">Name</span></span>    | <span data-ttu-id="8afb4-109">Değer</span><span class="sxs-lookup"><span data-stu-id="8afb4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8afb4-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8afb4-110">Scope</span></span>   |<span data-ttu-id="8afb4-111">Edge</span><span class="sxs-lookup"><span data-stu-id="8afb4-111">Edge</span></span>|
|<span data-ttu-id="8afb4-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8afb4-112">Version</span></span>|<span data-ttu-id="8afb4-113">4,5</span><span class="sxs-lookup"><span data-stu-id="8afb4-113">4.5</span></span>|
|<span data-ttu-id="8afb4-114">Tür</span><span class="sxs-lookup"><span data-stu-id="8afb4-114">Type</span></span>|<span data-ttu-id="8afb4-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="8afb4-115">Runtime</span></span>|
