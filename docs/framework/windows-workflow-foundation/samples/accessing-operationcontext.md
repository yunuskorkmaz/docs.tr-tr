---
title: OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 5cffae101c5d39fcc9500aa7ccafde7a836a5023
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245737"
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="41eb9-102">OperationContext Erişimi</span><span class="sxs-lookup"><span data-stu-id="41eb9-102">Accessing OperationContext</span></span>

<span data-ttu-id="41eb9-103">Bu örnek, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send> ) <xref:System.ServiceModel.OperationContext.Current%2A> giden veya gelen bir ileti içinde özel bir ileti başlığına erişmek ve bunları eklemek veya almak için özel bir kapsam etkinliğiyle nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="41eb9-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="41eb9-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="41eb9-104">Demonstrates</span></span>  

 <span data-ttu-id="41eb9-105">Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback> , <xref:System.ServiceModel.Activities.IReceiveMessageCallback> .</span><span class="sxs-lookup"><span data-stu-id="41eb9-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="41eb9-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="41eb9-106">Discussion</span></span>  

 <span data-ttu-id="41eb9-107">Bu örnek <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> , erişim için mesajlaşma etkinliklerinde genişletilebilirlik noktalarının ()) nasıl kullanılacağını gösterir <xref:System.ServiceModel.OperationContext.Current%2A> .</span><span class="sxs-lookup"><span data-stu-id="41eb9-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="41eb9-108">Geri çağrılar, <xref:System.Activities.IExecutionProperty> yürütme sonrasında mesajlaşma etkinlikleri tarafından oluşturulan bir uygulama olarak iş akışı çalışma zamanı içinde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="41eb9-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="41eb9-109">Bu uygulamayla aynı kapsamdaki tüm mesajlaşma etkinlikleri <xref:System.Activities.IExecutionProperty> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="41eb9-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="41eb9-110">Özellikle bu örnek, geri çağırma davranışını zorlamak için özel bir kapsam etkinliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="41eb9-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="41eb9-111">, <xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışında, iş akışını <xref:System.Activities.WorkflowApplication.Id%2A> giden bir giden olarak dahil etmek için kullanılır <xref:System.ServiceModel.Channels.MessageHeader> .</span><span class="sxs-lookup"><span data-stu-id="41eb9-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="41eb9-112">Bu üst bilgi daha sonra hizmetinde kullanılarak alınır <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve üst bilgi değeri konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="41eb9-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41eb9-113">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="41eb9-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="41eb9-114">Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="41eb9-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="41eb9-115">Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek.</span><span class="sxs-lookup"><span data-stu-id="41eb9-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="41eb9-116">Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="41eb9-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="41eb9-117">URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="41eb9-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="41eb9-118">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="41eb9-118">Build the solution.</span></span>  
  
    2. <span data-ttu-id="41eb9-119">Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="41eb9-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3. <span data-ttu-id="41eb9-120">**Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="41eb9-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4. <span data-ttu-id="41eb9-121">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41eb9-121">Run the application.</span></span> <span data-ttu-id="41eb9-122">İstemci konsolunda, iki kez çalışan bir iş akışı gösterilir ve hizmet penceresinde bu iş akışlarının örnek KIMLIĞI gösterilir.</span><span class="sxs-lookup"><span data-stu-id="41eb9-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41eb9-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="41eb9-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41eb9-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="41eb9-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="41eb9-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="41eb9-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41eb9-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="41eb9-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
