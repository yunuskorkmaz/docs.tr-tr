---
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 017c5f959ed109ffe9b5e5c4bf2b9de9d04fdcdb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964937"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="0b6d7-102">WorkflowHostingEndpoint için Yer İşareti Çözümleyici</span><span class="sxs-lookup"><span data-stu-id="0b6d7-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="0b6d7-103">Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iş akışı örnekleri oluşturmak için ile <xref:System.ServiceModel.Activities.WorkflowServiceHost> nasıl kullanılabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0b6d7-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0b6d7-104">Demonstrates</span></span>  
 <span data-ttu-id="0b6d7-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="0b6d7-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0b6d7-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="0b6d7-106">Discussion</span></span>  
 <span data-ttu-id="0b6d7-107">Bu örnek kullanılarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iş akışı örnekleri oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="0b6d7-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="0b6d7-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="0b6d7-109">Yeni iş akışı örnekleri oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="0b6d7-110">İçinde barındırılan iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="0b6d7-111">Dahil edilen örnek uç nokta, iş akışı oluşturmak için işlem sağlayan ve örnek KIMLIĞINI döndüren veya belirli bir KIMLIĞE sahip bir örnek oluşturan bir sözleşme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="0b6d7-112">Örnek konsol uygulaması, iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımıyla bir örnek oluşturur ve konağa bir `CreationEndpoint` ekler.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="0b6d7-113">Ardından, yeni bir `Create` iş akışı örneği oluşturmak için uç noktada işlemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b6d7-114">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0b6d7-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0b6d7-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="0b6d7-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-116">Run the application.</span></span> <span data-ttu-id="0b6d7-117">`CreationEndpoint` Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="0b6d7-118">"Merhaba Dünya!" iletisi</span><span class="sxs-lookup"><span data-stu-id="0b6d7-118">The message "Hello World!"</span></span> <span data-ttu-id="0b6d7-119">, iş akışı örneği tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0b6d7-120">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b6d7-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b6d7-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b6d7-123">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b6d7-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
