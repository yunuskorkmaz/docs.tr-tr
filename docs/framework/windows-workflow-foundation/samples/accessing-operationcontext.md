---
description: "Daha fazla bilgi edinin: OperationContext 'e erişme"
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 768475f115f653630aaedeee976d0c96bc9e4dd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792628"
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="ac990-103">OperationContext Erişimi</span><span class="sxs-lookup"><span data-stu-id="ac990-103">Accessing OperationContext</span></span>

<span data-ttu-id="ac990-104">Bu örnek, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send> ) <xref:System.ServiceModel.OperationContext.Current%2A> giden veya gelen bir ileti içinde özel bir ileti başlığına erişmek ve bunları eklemek veya almak için özel bir kapsam etkinliğiyle nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac990-104">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ac990-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="ac990-105">Demonstrates</span></span>  

 <span data-ttu-id="ac990-106">Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback> , <xref:System.ServiceModel.Activities.IReceiveMessageCallback> .</span><span class="sxs-lookup"><span data-stu-id="ac990-106">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ac990-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="ac990-107">Discussion</span></span>  

 <span data-ttu-id="ac990-108">Bu örnek <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> , erişim için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının ()) nasıl kullanılacağını gösterir <xref:System.ServiceModel.OperationContext.Current%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac990-108">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="ac990-109">Geri çağrılar, <xref:System.Activities.IExecutionProperty> yürütme sonrasında mesajlaşma etkinlikleri tarafından oluşturulan bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ac990-109">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="ac990-110">Bu uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri <xref:System.Activities.IExecutionProperty> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="ac990-110">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="ac990-111">Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac990-111">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="ac990-112">, <xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışında, iş akışını <xref:System.Activities.WorkflowApplication.Id%2A> giden bir giden olarak dahil etmek için kullanılır <xref:System.ServiceModel.Channels.MessageHeader> .</span><span class="sxs-lookup"><span data-stu-id="ac990-112">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="ac990-113">Bu üst bilgi daha sonra hizmetinde kullanılarak alınır <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve üst bilgi değeri konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="ac990-113">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac990-114">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ac990-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ac990-115">Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="ac990-115">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="ac990-116">Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek.</span><span class="sxs-lookup"><span data-stu-id="ac990-116">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="ac990-117">Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ac990-117">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="ac990-118">URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac990-118">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="ac990-119">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="ac990-119">Build the solution.</span></span>  
  
    2. <span data-ttu-id="ac990-120">Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ac990-120">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3. <span data-ttu-id="ac990-121">**Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac990-121">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4. <span data-ttu-id="ac990-122">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac990-122">Run the application.</span></span> <span data-ttu-id="ac990-123">İstemci konsolunda, iki kez çalışan bir iş akışı gösterilir ve hizmet penceresinde bu iş akışlarının örnek KIMLIĞI gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ac990-123">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac990-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac990-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ac990-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ac990-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ac990-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ac990-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac990-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ac990-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
