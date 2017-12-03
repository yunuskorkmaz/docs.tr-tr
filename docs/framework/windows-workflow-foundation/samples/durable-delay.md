---
title: "Dayanıklı gecikmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0e679b91bd342ed5105fba7b916a8ed0070d0da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="durable-delay"></a><span data-ttu-id="fe160-102">Dayanıklı gecikmesi</span><span class="sxs-lookup"><span data-stu-id="fe160-102">Durable Delay</span></span>
<span data-ttu-id="fe160-103">Bu örnek, sağlam bir aygıt için iş akışı sırasında gecikme devam ederse gecikme dayanıklı bir gecikme kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe160-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="fe160-104">Örnek iş akışı tarafından bir gecikme ayrılmış iki iletilerini konsola içerir.</span><span class="sxs-lookup"><span data-stu-id="fe160-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="fe160-105">Gecikme tetiklendiğinde, iş akışı kaldırılır ve iş akışı örneği deposundaki 5 bellekte yeniden yükleniyor önce saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="fe160-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="fe160-106">İş akışı ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="fe160-106">Workflow Details</span></span>  
 <span data-ttu-id="fe160-107">İş akışı hizmeti ana bilgisayarı, iş akışı barındırır ve yükleme ve bunları kaldırma iş akışı örneklerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="fe160-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="fe160-108">Örnek iş akışı tanımı örneği başlatmak için bir ileti gönderen bir proxy ayarlar <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı.</span><span class="sxs-lookup"><span data-stu-id="fe160-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="fe160-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Özelliği ayarlanmış `true`, iletiyi aldıktan sonra iş akışının yeni bir örneğini oluşturmak üzere etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="fe160-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="fe160-110">Aşağıdaki listede iş akışı hizmeti ana bilgisayarı tarafından Kurulum başlatma sırasında Ayrıntılar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe160-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="fe160-111">Bir Hizmet Konağı (http://localhost: 8080/istemci) olan bir adresi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe160-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="fe160-112">Hizmet ana bilgisayarı ile iletişimi etkinleştirmek için bir uç nokta oluşturuyor <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde.</span><span class="sxs-lookup"><span data-stu-id="fe160-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="fe160-113">Bir SQL örneği deposu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe160-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="fe160-114">SQL Kalıcılık deposu için bir iş akışı örneği iş akışı hizmeti ana bilgisayarı kaldırma koşulları belirtir unload örneği davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="fe160-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="fe160-115">Bu örnek için (gecikme tetiklendiğinde) iş akışı boşta göründükten hemen sonra örneğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fe160-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="fe160-116">Bir ileti gönderir proxy oluşturur <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı.</span><span class="sxs-lookup"><span data-stu-id="fe160-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fe160-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fe160-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="fe160-118">Kalıcılık veritabanı ayarlama.</span><span class="sxs-lookup"><span data-stu-id="fe160-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="fe160-119">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="fe160-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="fe160-120">Gidin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="fe160-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="fe160-121">WorkflowManagementService.exe.config dosyasını düzenleyin ve aşağıdaki bağlantı dizesi içinde eklemek <`database`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe160-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="fe160-122">DurableDelay\CS dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="fe160-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="fe160-123">Setup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe160-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="fe160-124">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklayarak yükseltilmiş izinleri kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="fe160-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="fe160-125">Delay.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fe160-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="fe160-126">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe160-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="fe160-127">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe160-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="fe160-128">Bu örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="fe160-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="fe160-129">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="fe160-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="fe160-130">DurableDelay\CS dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="fe160-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="fe160-131">CleanUp.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe160-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fe160-132">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe160-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fe160-133">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe160-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fe160-134">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fe160-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe160-135">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe160-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`