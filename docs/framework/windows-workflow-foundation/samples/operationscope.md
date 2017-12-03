---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 242a9e32063deda0593552b70bf91dec3af7c346
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operationscope"></a><span data-ttu-id="10e8b-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="10e8b-102">OperationScope</span></span>
<span data-ttu-id="10e8b-103">Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> var olan bir özel etkinlik bir iş akışı hizmetinde bir işlem olarak kullanıma sunmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10e8b-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="10e8b-104">Bu örnek olarak adlandırılan yeni bir özel etkinlik içeren bir `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="10e8b-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="10e8b-105">Kullanıcıların kendi işlemleri ayrı olarak özel etkinlikler olarak gövdesi Yazar izin vermek ve ardından bunları kullanarak hizmet işlemleri kolayca gösterme tarafından bir iş akışı hizmeti geliştirmeyi kolaylaştırmak için tasarlanmıştır `OperationScope` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="10e8b-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="10e8b-106">Örneğin, bir özel `Add` iki alan etkinlik `in` bağımsız değişkenleri ve döndürür bir `out` bağımsız değişkeni ortaya olarak bir `Add` içine bırakmadan tarafından iş akışı hizmeti işlemi bir `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="10e8b-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="10e8b-107">Kapsam, kendi gövdesi olarak sağlanan etkinlik inceleyerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="10e8b-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="10e8b-108">Herhangi bir ilişkisiz `in` bağımsız değişkenleri varsayılır girişleri gelen iletisi.</span><span class="sxs-lookup"><span data-stu-id="10e8b-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="10e8b-109">Tüm `out` olup bağlandıktan, bağımsız olarak bağımsız değişkenler, varsayılır çıkışları sonraki yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="10e8b-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="10e8b-110">Sunulan işlemin adı görünen adından alınan `OperationScope` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="10e8b-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="10e8b-111">Gövde etkinlik olarak paketlenir nihai sonucu olan bir <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> bağlı etkinlik bağımsız değişkenler için iletilerden parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="10e8b-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="10e8b-112">Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="10e8b-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="10e8b-113">Çalıştırmak için doğru URL ACL eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="10e8b-113">To run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="10e8b-114">[HTTP ve HTTPS yapılandırma](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="10e8b-114"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="10e8b-115">Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütülürken ekler uygun ACL'ler (kullanıcı adı ve etki alanı için etki alanı % yerine olun\\% UserName %).</span><span class="sxs-lookup"><span data-stu-id="10e8b-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="10e8b-116">**Netsh http add urlacl url = http: / / +: 8000 / kullanıcı etki alanı % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="10e8b-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="10e8b-117">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="10e8b-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="10e8b-118">OperationScope.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10e8b-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="10e8b-119">Çözüm Gezgini'ndeki çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="10e8b-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="10e8b-120">Senaryo ve Scenario_Client (sırayla) birden fazla başlangıç projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10e8b-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="10e8b-121">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="10e8b-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="10e8b-122">Özel Etkinlik nedeniyle BankService.xaml iş akışı görüntülemek için bu adım gereklidir `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="10e8b-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="10e8b-123">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="10e8b-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="10e8b-124">Scenario_Client konsol girdileri ister ve karşılık gelen çıktı senaryo konsolunda görülür.</span><span class="sxs-lookup"><span data-stu-id="10e8b-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10e8b-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="10e8b-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10e8b-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10e8b-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="10e8b-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="10e8b-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10e8b-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="10e8b-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`