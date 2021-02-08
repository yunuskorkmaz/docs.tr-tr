---
description: 'Daha fazla bilgi edinin: Workflowwhostingendpoint özgeçmişi yer Işareti'
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3da4579a7c0c09122cacaa5e3db39359b8e62936
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798140"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="be0eb-103">WorkflowHostingEndpoint Sürdürme Yer İşareti</span><span class="sxs-lookup"><span data-stu-id="be0eb-103">WorkflowHostingEndpoint Resume Bookmark</span></span>

<span data-ttu-id="be0eb-104">Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için ile nasıl kullanılabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="be0eb-104">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="be0eb-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="be0eb-105">Demonstrates</span></span>  

 <span data-ttu-id="be0eb-106"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="be0eb-106"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="be0eb-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="be0eb-107">Discussion</span></span>  

 <span data-ttu-id="be0eb-108">Bu örnek <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılarak barındırılan bir iş akışı örneği oluşturmak için öğesini kullanır <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="be0eb-108">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="be0eb-109"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="be0eb-109"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="be0eb-110">Yeni iş akışı örnekleri oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="be0eb-110">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="be0eb-111">İçinde barındırılan bir iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="be0eb-111">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="be0eb-112">Dahil edilen örnek uç nokta, iş akışı oluşturma ve örnek KIMLIĞI döndürme veya belirli bir KIMLIĞE sahip bir örnek oluşturma işlemlerini sağlayan bir sözleşme sunar.</span><span class="sxs-lookup"><span data-stu-id="be0eb-112">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="be0eb-113">Örnek konsol uygulaması <xref:System.ServiceModel.Activities.WorkflowServiceHost> , temel bir iş akışı tanımına sahip bir örnek oluşturur ve konağa bir ekler `CreationEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="be0eb-113">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="be0eb-114">Ardından `Create` , yeni bir iş akışı örneği oluşturmak için uç noktada işlemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="be0eb-114">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be0eb-115">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="be0eb-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="be0eb-116">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="be0eb-116">Build the solution.</span></span>  
  
2. <span data-ttu-id="be0eb-117">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be0eb-117">Run the application.</span></span> <span data-ttu-id="be0eb-118">`CreationEndpoint`Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="be0eb-118">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="be0eb-119">"Merhaba Dünya!" iletisi</span><span class="sxs-lookup"><span data-stu-id="be0eb-119">The message "Hello World!"</span></span> <span data-ttu-id="be0eb-120">, yer işaretinin başarılı sürdürme iş akışı tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="be0eb-120">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be0eb-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="be0eb-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be0eb-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="be0eb-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="be0eb-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="be0eb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be0eb-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="be0eb-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
