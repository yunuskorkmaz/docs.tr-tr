---
description: 'Daha fazla bilgi edinin: etkinlik kitaplığı'
title: Etkinlik Kitaplığı
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e59846d34b63683266fed2c4ec1ad4ed5cb9566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792615"
---
# <a name="activity-library"></a><span data-ttu-id="4b0be-103">Etkinlik Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4b0be-103">Activity Library</span></span>

<span data-ttu-id="4b0be-104">Bu bölüm Windows Workflow Foundation (WF) içinde gelişmiş özel etkinlikleri gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-104">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b0be-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4b0be-105">In This Section</span></span>

 [<span data-ttu-id="4b0be-106">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="4b0be-106">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="4b0be-107"><xref:System.Activities.AsyncCodeActivity>Bir iş akışı uygulamasında kullanmak üzere SMTP kullanarak e-posta göndermek için öğesinden türetilen özel bir etkinliğin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-107">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="4b0be-108">Kısıtlanmış Paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="4b0be-108">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="4b0be-109">`ThrottleParallelForEach`Etkinliğin, <xref:System.Activities.Statements.ParallelForEach%601> eşzamanlı dalların yürütülmesi için bir eşzamanlılık faktörü ayarlanmasını olanaklı hale verdiği bir özel durumla nasıl benzediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-109">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="4b0be-110">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="4b0be-110">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="4b0be-111">Veritabanlarına erişilmesine, bilgileri alma veya değiştirme ve veritabanına erişmek için [ADO.net](../../data/adonet/index.md) kullanma izni veren etkinliklerin nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-111">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="4b0be-112">.NET Framework 4.5’te Dış İlke Etkinliği</span><span class="sxs-lookup"><span data-stu-id="4b0be-112">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="4b0be-113">ExternalizedPolicy4 etkinliğinin, <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] WF 3,5 ' te sunulan Rules altyapısını kullanarak doğrudan (WF 4,5) içindeki Windows Workflow Foundation .NET Framework 3,5 (WF 3,5) nesnelerinde var olan Windows Workflow Foundation nasıl yürütmeye izin verdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-113">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="4b0be-114">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="4b0be-114">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="4b0be-115">Etkinliğin genel olmayan bir sürümünün nasıl oluşturulacağını gösterir <xref:System.Activities.Statements.ForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="4b0be-115">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="4b0be-116">Genel Olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="4b0be-116">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="4b0be-117">Etkinliğin genel olmayan bir sürümünün nasıl oluşturulacağını gösterir <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="4b0be-117">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="4b0be-118">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="4b0be-118">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="4b0be-119">`GetWorkflowInstanceId`İş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b0be-119">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
