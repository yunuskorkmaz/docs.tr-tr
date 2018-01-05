---
title: "Askıya alınmış örnek Yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e04f1e2f334993975b2c4261efdc28ba318dfa3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="suspended-instance-management"></a><span data-ttu-id="deacf-102">Askıya alınmış örnek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="deacf-102">Suspended Instance Management</span></span>
<span data-ttu-id="deacf-103">Bu örnek, askıya alınan iş akışı örnekleri yönetmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="deacf-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="deacf-104">İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> olan `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="deacf-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="deacf-105">Varsayılan olarak, içinde bir iş akışı örneğinden oluşturulan işlenmeyen özel durumları barındırılan yani <xref:System.ServiceModel.WorkflowServiceHost> örneği (terk) bellekten çıkarılması ve dayanıklı ve kalıcı örneğinin sürümü, askıya alındı olarak işaretlenmesine neden olacak.</span><span class="sxs-lookup"><span data-stu-id="deacf-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="deacf-106">Askıya alınan iş akışı örneği çalıştırabilir ve onu unsuspended kadar olmaz.</span><span class="sxs-lookup"><span data-stu-id="deacf-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="deacf-107">Komut satırı yardımcı programını askıya alınmış örnekleri için sorgu ve kullanıcı sürdürün veya örnek sonlandırmak için seçenek sunmak amacıyla nasıl nasıl uygulanabilir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="deacf-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="deacf-108">Bu örnekte, bir iş akışı hizmeti bilerek, askıya duruma neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deacf-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="deacf-109">Komut satırı yardımcı programı daha sonra örnek için sorgu ve daha sonra sürdürün veya örnek sonlandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="deacf-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="deacf-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="deacf-110">Demonstrates</span></span>  
 <span data-ttu-id="deacf-111"><xref:System.ServiceModel.WorkflowServiceHost>ile <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> içinde [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deacf-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="deacf-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="deacf-112">Discussion</span></span>  
 <span data-ttu-id="deacf-113">Bu örnekte uygulanan komut satırı yardımcı programı içinde birlikte gelen SQL örneği mağaza uygulamasına belirli [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deacf-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="deacf-114">Özel bir örnek deposuna uygulanmasına sahip sonra değiştirerek bu yardımcı program uyarlayabilirsiniz `WorkflowInstanceCommand` örnek uygulamalarında örneği deponuza belirli uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="deacf-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="deacf-115">Sağlanan uygulama SQL komutlarını doğrudan askıya alınmış örneklerini listelemek için SQL örneği depo çalıştırır ve kullanır. bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> eklenen <xref:System.ServiceModel.WorkflowServiceHost> sürdürün veya örnekleri sonlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="deacf-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="deacf-116">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="deacf-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="deacf-117">Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="deacf-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="deacf-118">Microsoft Message sıraları (MSMQ) sunucusu</span><span class="sxs-lookup"><span data-stu-id="deacf-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="deacf-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="deacf-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="deacf-120">SQL Server veritabanı ayarlama.</span><span class="sxs-lookup"><span data-stu-id="deacf-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="deacf-121">Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, aşağıdaki SuspendedInstanceManagement örnek dizinden "setup.cmd" çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="deacf-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="deacf-122">SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deacf-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="deacf-123">Bırakılan ve yeniden oluşturulması Kalıcılık veritabanı zaten varsa</span><span class="sxs-lookup"><span data-stu-id="deacf-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="deacf-124">Veritabanı kalıcılığı için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="deacf-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="deacf-125">IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service kalıcılığı için veritabanı ayarlarken tanımlandı InstanceStoreUsers rolüne ekler.</span><span class="sxs-lookup"><span data-stu-id="deacf-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="deacf-126">Hizmet sırasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="deacf-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="deacf-127">İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], sağ **SampleWorkflowApp** proje ve tıklatın **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="deacf-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="deacf-128">Derleme ve tuşlarına basarak SampleWorkflowApp çalıştırma **F5**.</span><span class="sxs-lookup"><span data-stu-id="deacf-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="deacf-129">Bu, gerekli sıra oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deacf-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="deacf-130">Tuşuna **Enter** SampleWorkflowApp durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="deacf-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="deacf-131">Bir komut isteminden Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="deacf-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="deacf-132">Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="deacf-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="deacf-133">Sağ tıklayın **ReceiveTx** sıraya ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="deacf-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="deacf-134">Seçin **güvenlik** sekmesinde ve izin **herkesin** izinlerine sahip olmasını **İleti Al**, **iletiye**, ve  **İleti gönderme**.</span><span class="sxs-lookup"><span data-stu-id="deacf-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="deacf-135">Şimdi, örnek çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="deacf-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="deacf-136">İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SampleWorkflowApp projeyi yeniden tuşlarına basarak hata ayıklama olmadan çalıştırma **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="deacf-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="deacf-137">İki uç nokta adresleri konsol penceresinde yazdırılan: uygulama uç noktası için bir tane ve öğesinden sonra diğer <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="deacf-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="deacf-138">Bir iş akışı örneği sonra oluşturulur ve bu örnek için kayıtları izleme konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="deacf-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="deacf-139">İş akışı örneği askıya ve iptal örneği neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deacf-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="deacf-140">Komut satırı yardımcı programı daha sonra başka bir işlem bu örnekler hiçbirinde yapmanıza için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="deacf-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="deacf-141">Komut satırı bağımsız değişkenleri için söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="deacf-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="deacf-142">Desteklenen komutlar: `Query`, `Resume`, ve `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="deacf-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="deacf-143">InstanceId anahtar yalnızca gerekli olan `Resume` ve `Terminate` işlemleri.</span><span class="sxs-lookup"><span data-stu-id="deacf-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="deacf-144">Temizleme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="deacf-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="deacf-145">Gelen Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın bir `vs2010` komut istemi.</span><span class="sxs-lookup"><span data-stu-id="deacf-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="deacf-146">Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="deacf-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="deacf-147">Silme **ReceiveTx** sırası.</span><span class="sxs-lookup"><span data-stu-id="deacf-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="deacf-148">Kalıcılık veritabanını kaldırmak için cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="deacf-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="deacf-149">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="deacf-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="deacf-150">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="deacf-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="deacf-151">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="deacf-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="deacf-152">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="deacf-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
