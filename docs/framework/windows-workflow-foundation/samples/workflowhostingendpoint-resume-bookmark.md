---
title: WorkflowHostingEndpoint Sürdür yer işareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3af31af17e0c362beb8ba4b9b0479de59cab8ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515681"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="8ec71-102">WorkflowHostingEndpoint Sürdür yer işareti</span><span class="sxs-lookup"><span data-stu-id="8ec71-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="8ec71-103">Bu örnek gösterilmektedir nasıl <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ile kullanılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8ec71-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8ec71-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="8ec71-104">Demonstrates</span></span>  
 <span data-ttu-id="8ec71-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="8ec71-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8ec71-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="8ec71-106">Discussion</span></span>  
 <span data-ttu-id="8ec71-107">Bu örnekte <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanarak barındırılan bir iş akışı örneği oluşturmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8ec71-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8ec71-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> için genişletilebilirlik noktasıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8ec71-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="8ec71-109">Yeni iş akışı örnekleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8ec71-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="8ec71-110">Bir iş akışı örneği yer işaretlerini sürdürme barındırılan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8ec71-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="8ec71-111">Bir iş akışı oluşturmak ve bir örnek kimliği dönmek için veya belirli bir kimliğe sahip bir örneğini oluşturmak için işlemler sağlar bir sözleşme bulunan örnek uç nokta gösterir</span><span class="sxs-lookup"><span data-stu-id="8ec71-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="8ec71-112">Örnek konsol uygulaması oluşturur bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek temel iş akışı tanımıyla ve ekler bir `CreationEndpoint` ana bilgisayara.</span><span class="sxs-lookup"><span data-stu-id="8ec71-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="8ec71-113">Daha sonra çağırır `Create` yeni bir iş akışı örneği oluşturmak için uç nokta işlemi.</span><span class="sxs-lookup"><span data-stu-id="8ec71-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ec71-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8ec71-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ec71-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8ec71-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="8ec71-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8ec71-116">Run the application.</span></span> <span data-ttu-id="8ec71-117">`CreationEndpoint` Konsol iş akışı örneği oluşturulduğunda, örnek kimliği içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ec71-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="8ec71-118">"Hello World!" iletisi</span><span class="sxs-lookup"><span data-stu-id="8ec71-118">The message "Hello World!"</span></span> <span data-ttu-id="8ec71-119">İş akışında yer işaretinin başarılı sürdürme tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="8ec71-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ec71-120">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ec71-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ec71-121">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8ec71-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8ec71-122">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8ec71-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ec71-123">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8ec71-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
