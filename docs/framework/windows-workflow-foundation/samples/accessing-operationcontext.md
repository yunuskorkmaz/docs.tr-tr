---
title: "OperationContext erişimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 861329c3945a53bf6c8ceeb7487aa0ef9902c93a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="928ff-102">OperationContext erişimi</span><span class="sxs-lookup"><span data-stu-id="928ff-102">Accessing OperationContext</span></span>
<span data-ttu-id="928ff-103">Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.Send>) özel kapsam etkinliği ile erişmek için kullanılan <xref:System.ServiceModel.OperationContext.Current%2A> ve ekleyebilir veya bir özel ileti üstbilgisi içinde bir giden veya gelen ileti alma.</span><span class="sxs-lookup"><span data-stu-id="928ff-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="928ff-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="928ff-104">Demonstrates</span></span>  
 <span data-ttu-id="928ff-105">Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="928ff-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="928ff-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="928ff-106">Discussion</span></span>  
 <span data-ttu-id="928ff-107">Bu örnek genişletilebilirlik noktaları kullanmayı gösterir (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) erişmek için Mesajlaşma etkinlikleriyle <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="928ff-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="928ff-108">Geri aramalar içinde iş akışı çalışma zamanı uygulaması kaydedilen <xref:System.Activities.IExecutionProperty> , toplanma yürütme sırasında Mesajlaşma etkinlikleri tarafından.</span><span class="sxs-lookup"><span data-stu-id="928ff-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="928ff-109">Herhangi bir Mesajlaşma etkinlik olarak aynı kapsamda <xref:System.Activities.IExecutionProperty> uygulama etkilenir.</span><span class="sxs-lookup"><span data-stu-id="928ff-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="928ff-110">Özellikle, bu örnek geri çağırma davranışına zorlamak için bir özel kapsam aktivitesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="928ff-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="928ff-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> İstemci iş akışı içinde iş akışının dahil etmek için kullanılan <xref:System.Activities.WorkflowApplication.Id%2A> giden olarak <xref:System.ServiceModel.Channels.MessageHeader>.</span><span class="sxs-lookup"><span data-stu-id="928ff-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="928ff-112">Bu üst sonra hizmetini kullanarak kayıt <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve konsola yazdırılır üstbilgi değeri.</span><span class="sxs-lookup"><span data-stu-id="928ff-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="928ff-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="928ff-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="928ff-114">Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="928ff-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="928ff-115">Bu örnek, uygun URL ACL çalıştırmak için eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio Yönetici olarak çalıştırarak veya uygun ACL'ler eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu çalıştırarak.</span><span class="sxs-lookup"><span data-stu-id="928ff-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="928ff-116">Etki alanı ve kullanıcı adı yerine emin olun.</span><span class="sxs-lookup"><span data-stu-id="928ff-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="928ff-117">URL ACL eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="928ff-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="928ff-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="928ff-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="928ff-119">Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="928ff-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="928ff-120">Ekleme **hizmet** ve **istemci** (sırayla) birden fazla başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="928ff-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="928ff-121">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="928ff-121">Run the application.</span></span> <span data-ttu-id="928ff-122">İstemci Konsolu iki kez çalışan bir iş akışındaki gösterir ve bu iş akışlarının örnek kimliği hizmet penceresi gösterir.</span><span class="sxs-lookup"><span data-stu-id="928ff-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="928ff-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="928ff-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="928ff-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="928ff-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="928ff-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="928ff-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="928ff-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="928ff-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
