---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 5c3c996a73d8f88e925d459fae3eb785996eada4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340548"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="d4438-102">WorkflowHostingEndpoint Sürdürme Yer İşareti</span><span class="sxs-lookup"><span data-stu-id="d4438-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="d4438-103">Bu örnek gösterir nasıl <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d4438-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d4438-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="d4438-104">Demonstrates</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint><span data-ttu-id="d4438-105">,</span><span class="sxs-lookup"><span data-stu-id="d4438-105">,</span></span> <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a><span data-ttu-id="d4438-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="d4438-106">Discussion</span></span>  
 <span data-ttu-id="d4438-107">Bu örnekte <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> barındırılan iş akışı örneği oluşturmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d4438-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <span data-ttu-id="d4438-108">bir genişletilebilirlik noktası <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d4438-108">is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="d4438-109">Yeni iş akışı örnekleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d4438-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="d4438-110">Bir iş akışı örneği yer işaretlerini sürdürme barındırılan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d4438-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="d4438-111">Dahil olan örnek uç nokta işlemleri bir iş akışı oluşturmak ve bir örnek kimliği döndürmek için veya belirli bir kimliğe sahip bir örneğini oluşturmak için sağlayan bir sözleşme kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d4438-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="d4438-112">Örnek konsol uygulaması oluşturan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek temel iş akışı tanımıyla ve ekler bir `CreationEndpoint` konağa.</span><span class="sxs-lookup"><span data-stu-id="d4438-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="d4438-113">Ardından `Create` işlemi yeni bir iş akışı örneği oluşturmak için uç nokta.</span><span class="sxs-lookup"><span data-stu-id="d4438-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4438-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d4438-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d4438-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4438-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="d4438-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4438-116">Run the application.</span></span> <span data-ttu-id="d4438-117">`CreationEndpoint` Konsol örnek kimliği iş akışı örneği oluşturulduğunda içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4438-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="d4438-118">"Hello World!" iletisi</span><span class="sxs-lookup"><span data-stu-id="d4438-118">The message "Hello World!"</span></span> <span data-ttu-id="d4438-119">yer işaretinin sürdürme başarılı iş akışı tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="d4438-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4438-120">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="d4438-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4438-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d4438-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4438-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d4438-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4438-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d4438-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
