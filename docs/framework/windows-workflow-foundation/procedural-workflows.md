---
title: Yordam İş Akışları
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956111"
---
# <a name="procedural-workflows"></a><span data-ttu-id="e755a-102">Yordam İş Akışları</span><span class="sxs-lookup"><span data-stu-id="e755a-102">Procedural Workflows</span></span>
<span data-ttu-id="e755a-103">Yordamsal iş akışları, yordamsal dillerde bulunanlara benzer akış denetimi yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e755a-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="e755a-104">Bu yapılar ve `While` `If`içerir.</span><span class="sxs-lookup"><span data-stu-id="e755a-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="e755a-105">Bu iş akışları <xref:System.Activities.Statements.Flowchart> , ve <xref:System.Activities.Statements.Sequence>gibi diğer akış denetimi etkinlikleri kullanılarak serbestçe oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e755a-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="e755a-106">Yürütme akışını denetleme</span><span class="sxs-lookup"><span data-stu-id="e755a-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="e755a-107">İş akışı etkinlik kitaplığı, yordamsal dillerde kullanılan akış denetimi yöntemlerinin çoğunu modellemeye yönelik etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e755a-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="e755a-108">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e755a-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="e755a-109">Flow denetim etkinliklerini kullanmak için, onları **etkinlik** araç kutusundan Tasarımcı penceresinin içindeki bir bileşik etkinliğe sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="e755a-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e755a-110">Web çiftliğinde iş akışlarını barındırmak için Windows Server AppFabric barındırma özelliklerini kullanıyorsanız, AppFabric örnekleri farklı bir AppFabric sunucuları arasında taşıyacaktır.</span><span class="sxs-lookup"><span data-stu-id="e755a-110">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="e755a-111">Bu, kaynakların tüm düğümler arasında paylaşılabilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e755a-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="e755a-112">Varsayılan NET 4 iş akışı etkinliklerinin hiçbiri, yerel kaynaklara erişen işlemler içermez.</span><span class="sxs-lookup"><span data-stu-id="e755a-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="e755a-113">AppFabric bir iş akışını taşınabilir olarak işaretlemek için herhangi bir mekanizma sunmadığından, bir geliştirici bir iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e755a-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e755a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e755a-114">See also</span></span>

- [<span data-ttu-id="e755a-115">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="e755a-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
