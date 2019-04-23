---
title: Yordam İş Akışları
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 05942418038ca4349e32973aeefdfc4a50e49f46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164755"
---
# <a name="procedural-workflows"></a><span data-ttu-id="d3f48-102">Yordam İş Akışları</span><span class="sxs-lookup"><span data-stu-id="d3f48-102">Procedural Workflows</span></span>
<span data-ttu-id="d3f48-103">Yordam iş akışları, akış denetimi yöntemleri yordam dillerinde bulunan benzer kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3f48-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="d3f48-104">Bu yapılar dahil `While` ve `If`.</span><span class="sxs-lookup"><span data-stu-id="d3f48-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="d3f48-105">Bu iş akışları gibi diğer akış denetimi etkinlikleri kullanarak serbestçe oluşturulabildikleri <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="d3f48-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="d3f48-106">Yürütme akışı denetimi</span><span class="sxs-lookup"><span data-stu-id="d3f48-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="d3f48-107">İş akışı etkinlik kitaplığı yordam dilde kullanılan çoğu akış denetimi yöntemleri modelleme için etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d3f48-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="d3f48-108">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d3f48-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="d3f48-109">Akış denetimi etkinlikleri kullanmak için sürükleyip bunları **etkinlik** Tasarımcı penceresinin içinde bileşik bir etkinlik araç.</span><span class="sxs-lookup"><span data-stu-id="d3f48-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3f48-110">Kullanıyorsanız [!INCLUDE[dublin](../../../includes/dublin-md.md)] bir Web grubundaki konak iş akışlarına AppFabric örnekleri farklı AppFabric sunucular arasında taşınır.</span><span class="sxs-lookup"><span data-stu-id="d3f48-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="d3f48-111">Bu, kaynakları tüm düğümler arasında paylaşılacak mümkün olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d3f48-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="d3f48-112">Varsayılan ağ 4 iş akışı etkinlikleri hiçbiri yerel kaynaklara erişen herhangi bir işlem içerir.</span><span class="sxs-lookup"><span data-stu-id="d3f48-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="d3f48-113">İş akışı immovable olarak işaretlemek için herhangi bir mekanizma AppFabric sunmaz olduğundan, bir geliştirici iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3f48-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f48-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3f48-114">See also</span></span>

- [<span data-ttu-id="d3f48-115">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="d3f48-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
