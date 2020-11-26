---
title: Yordam İş Akışları
description: Workflow Foundation 'da, yordamsal iş akışları, yordamsal dillerde bulunanlara benzer akış denetimi yöntemlerini kullanır.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 13d1b5e55b84687e2a78db1a94317b8b1e33328c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246036"
---
# <a name="procedural-workflows"></a><span data-ttu-id="a3bdf-103">Yordam İş Akışları</span><span class="sxs-lookup"><span data-stu-id="a3bdf-103">Procedural Workflows</span></span>

<span data-ttu-id="a3bdf-104">Yordamsal iş akışları, yordamsal dillerde bulunanlara benzer akış denetimi yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-104">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="a3bdf-105">Bu yapılar `While` ve içerir `If` .</span><span class="sxs-lookup"><span data-stu-id="a3bdf-105">These constructs include `While` and `If`.</span></span> <span data-ttu-id="a3bdf-106">Bu iş akışları, ve gibi diğer akış denetimi etkinlikleri kullanılarak serbestçe oluşturulabilir <xref:System.Activities.Statements.Flowchart> <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="a3bdf-106">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="a3bdf-107">Yürütme akışını denetleme</span><span class="sxs-lookup"><span data-stu-id="a3bdf-107">Controlling Execution Flow</span></span>  

 <span data-ttu-id="a3bdf-108">İş akışı etkinlik kitaplığı, yordamsal dillerde kullanılan akış denetimi yöntemlerinin çoğunu modellemeye yönelik etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-108">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="a3bdf-109">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="a3bdf-109">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="a3bdf-110">Flow denetim etkinliklerini kullanmak için, onları **etkinlik** araç kutusundan Tasarımcı penceresinin içindeki bir bileşik etkinliğe sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-110">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3bdf-111">Web çiftliğinde iş akışlarını barındırmak için Windows Server AppFabric barındırma özelliklerini kullanıyorsanız, AppFabric örnekleri farklı bir AppFabric sunucuları arasında taşıyacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-111">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="a3bdf-112">Bu, kaynakların tüm düğümler arasında paylaşılabilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-112">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="a3bdf-113">Varsayılan NET 4 iş akışı etkinliklerinin hiçbiri, yerel kaynaklara erişen işlemler içermez.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-113">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="a3bdf-114">AppFabric bir iş akışını taşınabilir olarak işaretlemek için herhangi bir mekanizma sunmadığından, bir geliştirici bir iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-114">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3bdf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3bdf-115">See also</span></span>

- [<span data-ttu-id="a3bdf-116">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="a3bdf-116">Flowchart Workflows</span></span>](flowchart-workflows.md)
