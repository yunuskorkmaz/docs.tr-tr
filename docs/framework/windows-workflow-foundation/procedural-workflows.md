---
title: Yordam İş Akışları
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 15ff155fb057c4c10663d383a8942108c6e4375c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348363"
---
# <a name="procedural-workflows"></a><span data-ttu-id="69656-102">Yordam İş Akışları</span><span class="sxs-lookup"><span data-stu-id="69656-102">Procedural Workflows</span></span>
<span data-ttu-id="69656-103">Yordam iş akışları, akış denetimi yöntemleri yordam dillerinde bulunan benzer kullanın.</span><span class="sxs-lookup"><span data-stu-id="69656-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="69656-104">Bu yapılar dahil `While` ve `If`.</span><span class="sxs-lookup"><span data-stu-id="69656-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="69656-105">Bu iş akışları gibi diğer akış denetimi etkinlikleri kullanarak serbestçe oluşturulabildikleri <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="69656-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="69656-106">Yürütme akışı denetimi</span><span class="sxs-lookup"><span data-stu-id="69656-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="69656-107">İş akışı etkinlik kitaplığı yordam dilde kullanılan çoğu akış denetimi yöntemleri modelleme için etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="69656-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="69656-108">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="69656-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="69656-109">Akış denetimi etkinlikleri kullanmak için sürükleyip bunları **etkinlik** Tasarımcı penceresinin içinde bileşik bir etkinlik araç.</span><span class="sxs-lookup"><span data-stu-id="69656-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69656-110">Windows Server AppFabric barındırma özellikleri ana iş akışları için bir Web grubunda kullanıyorsanız, AppFabric örnekleri farklı AppFabric sunucular arasında taşıyın.</span><span class="sxs-lookup"><span data-stu-id="69656-110">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="69656-111">Bu, kaynakları tüm düğümler arasında paylaşılacak mümkün olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69656-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="69656-112">Varsayılan ağ 4 iş akışı etkinlikleri hiçbiri yerel kaynaklara erişen herhangi bir işlem içerir.</span><span class="sxs-lookup"><span data-stu-id="69656-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="69656-113">İş akışı immovable olarak işaretlemek için herhangi bir mekanizma AppFabric sunmaz olduğundan, bir geliştirici iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="69656-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69656-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69656-114">See also</span></span>

- [<span data-ttu-id="69656-115">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="69656-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
