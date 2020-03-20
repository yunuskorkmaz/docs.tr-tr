---
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142816"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="3db60-102">WorkflowHostingEndpoint için Yer İşareti Çözümleyici</span><span class="sxs-lookup"><span data-stu-id="3db60-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="3db60-103">Bu örnek, iş <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> akışı örnekleri <xref:System.ServiceModel.Activities.WorkflowServiceHost> oluşturmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3db60-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3db60-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3db60-104">Demonstrates</span></span>  
 <span data-ttu-id="3db60-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="3db60-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3db60-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="3db60-106">Discussion</span></span>  
 <span data-ttu-id="3db60-107">Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılarak barındırılan iş <xref:System.ServiceModel.Activities.WorkflowServiceHost>akışı örneklerini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3db60-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3db60-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>aşağıdaki senaryolarda kullanılabilecek bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> genişletilebilirlik noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="3db60-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="3db60-109">Yeni iş akışı örnekleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3db60-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="3db60-110">İş akışı örneğinde yer imleri <xref:System.ServiceModel.Activities.WorkflowServiceHost>devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="3db60-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="3db60-111">Dahil edilen örnek uç noktası, iş akışı oluşturmak için işlemler sağlayan ve örnek kimliği döndüren veya belirli bir kimliği olan bir örnek oluşturan bir sözleşmeyi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="3db60-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="3db60-112">Örnek konsol uygulaması, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımına sahip `CreationEndpoint` bir örnek oluşturur ve ana bilgisayara bir örnek ekler.</span><span class="sxs-lookup"><span data-stu-id="3db60-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="3db60-113">Daha sonra `Create` yeni bir iş akışı örneği oluşturmak için bitiş noktasında ki işlemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="3db60-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3db60-114">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3db60-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3db60-115">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="3db60-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="3db60-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3db60-116">Run the application.</span></span> <span data-ttu-id="3db60-117">Konsol, `CreationEndpoint` iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="3db60-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="3db60-118">Mesaj "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="3db60-118">The message "Hello World!"</span></span> <span data-ttu-id="3db60-119">iş akışı örneği tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="3db60-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3db60-120">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3db60-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3db60-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3db60-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3db60-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3db60-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3db60-123">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3db60-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
