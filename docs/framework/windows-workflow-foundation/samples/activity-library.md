---
title: Etkinlik Kitaplığı
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142907"
---
# <a name="activity-library"></a><span data-ttu-id="75d57-102">Etkinlik Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="75d57-102">Activity Library</span></span>
<span data-ttu-id="75d57-103">Bu bölümde, Windows İş Akışı Temeli'nde (WF) gelişmiş özel etkinlikler gösteren örnekler bulunur.</span><span class="sxs-lookup"><span data-stu-id="75d57-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75d57-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="75d57-104">In This Section</span></span>

 [<span data-ttu-id="75d57-105">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="75d57-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="75d57-106">İş akışı uygulamasında kullanılmak üzere SMTP kullanarak posta <xref:System.Activities.AsyncCodeActivity> göndermekten türeyen özel bir etkinliğin nasıl oluşturulurulur.</span><span class="sxs-lookup"><span data-stu-id="75d57-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="75d57-107">Kısıtlanmış Paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="75d57-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="75d57-108">Eşzamanlı şube `ThrottleParallelForEach` sayısını kısıtlamak <xref:System.Activities.Statements.ParallelForEach%601> için eşzamanlı bir faktör ayarlamaya izin verdiği bir özel durum la birlikte, etkinliğin aktiviteye nasıl benzediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="75d57-109">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="75d57-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="75d57-110">Veritabanlarına erişimin bilgileri almasına veya değiştirmesine ve veritabanına erişmek için [ADO.NET](../../data/adonet/index.md) kullanmasına izin veren etkinliklerin nasıl oluşturulutamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="75d57-111">.NET Framework 4.5’te Dış İlke Etkinliği</span><span class="sxs-lookup"><span data-stu-id="75d57-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="75d57-112">ExternalizedPolicy4 etkinliğinin, WF 3.5'te sevk edilen kurallar altyapısını kullanarak doğrudan <xref:System.Workflow.Activities.Rules.RuleSet> Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) içinde .NET Framework 3.5 (WF 3.5) nesnelerinde varolan Windows İş Akışı Temeli'nin yürütülmesine nasıl izin verdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="75d57-113">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="75d57-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="75d57-114"><xref:System.Activities.Statements.ForEach%601> Etkinliğin genel olmayan bir sürümününasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="75d57-115">Genel Olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="75d57-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="75d57-116"><xref:System.Activities.Statements.ParallelForEach%601> Etkinliğin genel olmayan bir sürümününasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="75d57-117">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="75d57-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="75d57-118">İş akışı örneği kimliğini döndürmek `GetWorkflowInstanceId`için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75d57-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
