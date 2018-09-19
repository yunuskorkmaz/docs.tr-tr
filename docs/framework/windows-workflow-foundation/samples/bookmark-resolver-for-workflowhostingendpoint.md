---
title: WorkflowHostingEndpoint için yer işareti çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 48053ec7882b2e742b61fdc293b6bc5f8a129ca5
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000576"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="e8da5-102">WorkflowHostingEndpoint için yer işareti çözümleyici</span><span class="sxs-lookup"><span data-stu-id="e8da5-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="e8da5-103">Bu örnek gösterir nasıl <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e8da5-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e8da5-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e8da5-104">Demonstrates</span></span>  
 <span data-ttu-id="e8da5-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="e8da5-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e8da5-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e8da5-106">Discussion</span></span>  
 <span data-ttu-id="e8da5-107">Bu örnekte <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> barındırılan iş akışı örnekleri oluşturmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e8da5-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="e8da5-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> bir genişletilebilirlik noktası <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e8da5-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="e8da5-109">Yeni iş akışı örnekleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e8da5-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="e8da5-110">İş akışı örneği yer işaretlerini sürdürme barındırılan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e8da5-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="e8da5-111">Bir iş akışı oluşturmak için işlemler sağlar ve örnek kimliği döndürür ya da belirli bir kimliğe sahip bir örneği oluşturan bir sözleşme bulunan örnek uç noktasını kullanıma sunar</span><span class="sxs-lookup"><span data-stu-id="e8da5-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="e8da5-112">Örnek konsol uygulaması oluşturan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> ekler ve örnek bir iş akışı tanımıyla bir `CreationEndpoint` konağa.</span><span class="sxs-lookup"><span data-stu-id="e8da5-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="e8da5-113">Ardından `Create` işlemi yeni bir iş akışı örneği oluşturmak için uç nokta.</span><span class="sxs-lookup"><span data-stu-id="e8da5-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8da5-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e8da5-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e8da5-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8da5-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="e8da5-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8da5-116">Run the application.</span></span> <span data-ttu-id="e8da5-117">`CreationEndpoint` Konsol örnek kimliği iş akışı örneği oluşturulduğunda içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8da5-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="e8da5-118">"Hello World!" iletisi</span><span class="sxs-lookup"><span data-stu-id="e8da5-118">The message "Hello World!"</span></span> <span data-ttu-id="e8da5-119">İş akışı örneği tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="e8da5-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8da5-120">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="e8da5-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8da5-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e8da5-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8da5-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e8da5-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8da5-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e8da5-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
