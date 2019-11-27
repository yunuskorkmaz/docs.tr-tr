---
title: Etkinlik Kitaplığı
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 15260fc2ad96e1761a8a41ccc84b2c199e3d448a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283146"
---
# <a name="activity-library"></a><span data-ttu-id="229b3-102">Etkinlik Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="229b3-102">Activity Library</span></span>
<span data-ttu-id="229b3-103">Bu bölüm Windows Workflow Foundation (WF) içinde gelişmiş özel etkinlikleri gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="229b3-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="229b3-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="229b3-104">In This Section</span></span>

 [<span data-ttu-id="229b3-105">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="229b3-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="229b3-106">Bir iş akışı uygulamasında kullanmak üzere SMTP kullanarak e-posta göndermek için <xref:System.Activities.AsyncCodeActivity> türetilen özel bir etkinliğin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="229b3-107">Kısıtlanmış Paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="229b3-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="229b3-108">`ThrottleParallelForEach` etkinliğin, eş zamanlı dalların yürütülmesi için eşzamanlılık faktörünün ayarlanmasına izin veren bir özel durumla <xref:System.Activities.Statements.ParallelForEach%601> etkinliğe nasıl benzediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="229b3-109">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="229b3-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="229b3-110">Veritabanlarına erişilmesine, bilgileri alma veya değiştirme ve veritabanına erişmek için [ADO.net](https://go.microsoft.com/fwlink/?LinkId=166081) kullanma izni veren etkinliklerin nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="229b3-111">.NET Framework 4.5’te Dış İlke Etkinliği</span><span class="sxs-lookup"><span data-stu-id="229b3-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="229b3-112">ExternalizedPolicy4 etkinliğinin, WF 3,5 ' te sunulan Rules altyapısını kullanarak doğrudan (WF 4,5) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation <xref:System.Workflow.Activities.Rules.RuleSet> nesnelerinde bulunan mevcut Windows Workflow Foundation .NET Framework 3,5 ' de (WF 3,5) nasıl yürütmeye izin verdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="229b3-113">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="229b3-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="229b3-114"><xref:System.Activities.Statements.ForEach%601> etkinliğinin genel olmayan bir sürümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="229b3-115">Genel Olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="229b3-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="229b3-116"><xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin genel olmayan bir sürümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="229b3-117">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="229b3-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="229b3-118">`GetWorkflowInstanceId`, özel etkinliğin, iş akışı örneği KIMLIĞINI döndürmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="229b3-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
