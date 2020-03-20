---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182738"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="faf72-102">WorkflowHostingEndpoint Sürdürme Yer İşareti</span><span class="sxs-lookup"><span data-stu-id="faf72-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="faf72-103">Bu örnek, iş <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> akışı örnekleri <xref:System.ServiceModel.Activities.WorkflowServiceHost> oluşturmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="faf72-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="faf72-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="faf72-104">Demonstrates</span></span>  
 <span data-ttu-id="faf72-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="faf72-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="faf72-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="faf72-106">Discussion</span></span>  
 <span data-ttu-id="faf72-107">Bu örnek <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı örneği oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="faf72-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="faf72-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>aşağıdaki senaryolarda kullanılabilecek bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> genişletilebilirlik noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="faf72-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="faf72-109">Yeni iş akışı örnekleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="faf72-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="faf72-110">Bir iş akışı örneğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>yer imleri devam .</span><span class="sxs-lookup"><span data-stu-id="faf72-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="faf72-111">Dahil edilen örnek bitiş noktası, iş akışı oluşturmak ve örnek kimliği döndürmek veya belirli bir tağa sahip bir örnek oluşturmak için işlemler sağlayan bir sözleşmeyi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="faf72-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="faf72-112">Örnek konsol uygulaması temel <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımına sahip bir `CreationEndpoint` örnek oluşturur ve ana bilgisayara bir örnek ekler.</span><span class="sxs-lookup"><span data-stu-id="faf72-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="faf72-113">Daha sonra `Create` yeni bir iş akışı örneği oluşturmak için bitiş noktasında ki işlemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="faf72-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="faf72-114">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="faf72-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="faf72-115">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="faf72-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="faf72-116">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="faf72-116">Run the application.</span></span> <span data-ttu-id="faf72-117">Konsol, `CreationEndpoint` iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="faf72-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="faf72-118">Mesaj "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="faf72-118">The message "Hello World!"</span></span> <span data-ttu-id="faf72-119">yer imi nin başarılı bir şekilde yeniden başlatılmasına ilişkin iş akışı tarafından yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="faf72-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="faf72-120">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="faf72-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="faf72-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="faf72-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="faf72-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="faf72-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="faf72-123">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf72-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
