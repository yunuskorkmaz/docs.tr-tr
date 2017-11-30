---
title: "Yordam iş akışları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8f517b68695457c2819612bbd092b5ea03c5f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="d6714-102">Yordam iş akışları</span><span class="sxs-lookup"><span data-stu-id="d6714-102">Procedural Workflows</span></span>
<span data-ttu-id="d6714-103">Yordam iş akışları yordam dillerinde bulunan benzer akış denetimi yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6714-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="d6714-104">Bu yapıları içermek `While` ve `If`.</span><span class="sxs-lookup"><span data-stu-id="d6714-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="d6714-105">Bu iş akışları gibi diğer akış denetimi etkinlikleri kullanarak serbestçe birleştirilebilen <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="d6714-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="d6714-106">Yürütme akışı denetimi</span><span class="sxs-lookup"><span data-stu-id="d6714-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="d6714-107">İş akışı etkinlik kütüphanesini yordam dillerde kullanılan çoğu akış denetimi yöntemleri modelleme için etkinlikler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d6714-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="d6714-108">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d6714-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="d6714-109">Akış denetimi etkinlikleri kullanmak için sürükleyip onlardan **etkinlik** bileşik etkinliği Tasarımcı penceresinin içinde içine araç.</span><span class="sxs-lookup"><span data-stu-id="d6714-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6714-110">Kullanıyorsanız [!INCLUDE[dublin](../../../includes/dublin-md.md)] ana iş akışları bir Web grubunda AppFabric örnekleri farklı AppFabric sunucular arasında taşınır.</span><span class="sxs-lookup"><span data-stu-id="d6714-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="d6714-111">Bu kaynaklar tüm düğümler arasında paylaşılan mümkün olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d6714-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="d6714-112">Varsayılan NET 4 iş akışı etkinlikleri hiçbiri yerel kaynaklara erişmek herhangi bir işlem içerir.</span><span class="sxs-lookup"><span data-stu-id="d6714-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="d6714-113">Bir geliştirici AppFabric iş akışı immovable olarak işaretlemek için herhangi bir mekanizma sunmaz olduğundan, bir iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6714-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6714-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6714-114">See Also</span></span>  
 [<span data-ttu-id="d6714-115">Akış Çizelgesi iş akışları</span><span class="sxs-lookup"><span data-stu-id="d6714-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
