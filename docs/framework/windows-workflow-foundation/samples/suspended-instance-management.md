---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182797"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="7c999-102">Askıya Alınmış Örnek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="7c999-102">Suspended Instance Management</span></span>
<span data-ttu-id="7c999-103">Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğiaçık.</span><span class="sxs-lookup"><span data-stu-id="7c999-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="7c999-104">Bunun için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> varsayılan `AbandonAndSuspend`eylem.</span><span class="sxs-lookup"><span data-stu-id="7c999-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="7c999-105">Bu, varsayılan olarak, barındırılan bir iş akışı örneğinden atılan işlenmemiş özel durumların örneğin bellekten atılmasına (terk edilmiş) ve örneğin kalıcı/kalıcı sürümünün askıya alınmış olarak işaretlenecek olmasına neden <xref:System.ServiceModel.WorkflowServiceHost> olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7c999-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="7c999-106">Askıya alınan iş akışı örneği askıya alınmadan çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="7c999-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="7c999-107">Örnek, askıya alınan örnekleri sorgulamak için komut satırı yardımcı lığının nasıl uygulanabileceğini ve kullanıcıya örneği devam ettirme veya sonlandırma seçeneğinin nasıl verileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c999-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="7c999-108">Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum atarak askıya alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c999-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="7c999-109">Komut satırı yardımcı programı daha sonra örnek için sorgu ve daha sonra devam veya örnek sonlandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c999-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7c999-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="7c999-110">Demonstrates</span></span>
 <span data-ttu-id="7c999-111"><xref:System.ServiceModel.WorkflowServiceHost>ve Windows İş Akışı Temeli (WF) ile. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="7c999-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="7c999-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="7c999-112">Discussion</span></span>
 <span data-ttu-id="7c999-113">Bu örnekte uygulanan komut satırı yardımcı programı, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]'de bulunan SQL örnek deposu uygulamasına özgüdür.</span><span class="sxs-lookup"><span data-stu-id="7c999-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="7c999-114">Örnek deposunun özel bir uygulaması varsa, örnek mağazanıza özgü `WorkflowInstanceCommand` uygulamalarla örnekteki uygulamaları değiştirerek bu yardımcı programı uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c999-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="7c999-115">Sağlanan uygulama, askıya alınan örnekleri listelemek için doğrudan SQL örnek deposuna <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> karşı SQL <xref:System.ServiceModel.WorkflowServiceHost> komutlarını çalıştırıyor ve örnekleri devam ettirmek veya sonlandırmak için eklenen ekine dayanır.</span><span class="sxs-lookup"><span data-stu-id="7c999-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c999-116">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7c999-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7c999-117">Bu örnek, aşağıdaki Windows bileşenlerinin etkin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7c999-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="7c999-118">Microsoft İleti Kuyrukları (MSMQ) Sunucusu</span><span class="sxs-lookup"><span data-stu-id="7c999-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="7c999-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="7c999-119">SQL Server Express</span></span>

2. <span data-ttu-id="7c999-120">SQL Server veritabanını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="7c999-121">Visual Studio 2010 komut isteminden, SuspendedInstanceManagement örnek dizininden aşağıdakileri yapan "setup.cmd"yi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7c999-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="7c999-122">SQL Server Express kullanarak kalıcıbir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c999-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="7c999-123">Kalıcılık veritabanı zaten varsa, bırakılır ve yeniden oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7c999-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="7c999-124">Veritabanını kalıcılık için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c999-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="7c999-125">Veritabanını kalıcılık için ayarlarken tanımlanan InstanceStoreUsers rolüne IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service ekler.</span><span class="sxs-lookup"><span data-stu-id="7c999-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="7c999-126">Servis sırasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="7c999-127">Visual Studio 2010'da **SampleWorkflowApp** projesine sağ tıklayın ve **Başlangıç Projesi olarak ayarla'yı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7c999-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="7c999-128">**F5**tuşuna basarak SampleWorkflowApp'ı derleyip çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c999-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="7c999-129">Bu gerekli sırayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c999-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="7c999-130">SampleWorkflowApp'ı durdurmak için **Enter** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c999-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="7c999-131">Compmgmt.msc komut isteminden çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="7c999-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="7c999-132">**Hizmet ve Uygulamaları**Genişlet , İleti **Sırası**, **Özel Kuyruklar**.</span><span class="sxs-lookup"><span data-stu-id="7c999-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="7c999-133">**ReceiveTx** kuyruğunu sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="7c999-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="7c999-134">**Güvenlik** sekmesini seçin ve **Herkesin** **İleti Alma,** **Gözetleme İletisi**ve **İleti Gönderme**İzni almasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="7c999-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="7c999-135">Şimdi, örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c999-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="7c999-136">Visual Studio 2010'da, **Ctrl+F5**tuşuna basarak hata ayıklama yapmadan SampleWorkflowApp projesini tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c999-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="7c999-137">Konsol penceresine iki uç nokta adresi yazdırılır: biri uygulama bitiş noktası <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>için, diğeri .</span><span class="sxs-lookup"><span data-stu-id="7c999-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="7c999-138">Daha sonra bir iş akışı örneği oluşturulur ve bu örneğin izleme kayıtları konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="7c999-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="7c999-139">İş akışı örneği, örneğin askıya alınmasına ve iptal edilmesine neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c999-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="7c999-140">Komut satırı yardımcı programı daha sonra bu örneklerden herhangi biri üzerinde daha fazla eylem yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c999-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="7c999-141">Komut satırı bağımsız değişkenleri için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7c999-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="7c999-142">Desteklenen komutlar `Query`şunlardır: `Resume`, `Terminate`, ve .</span><span class="sxs-lookup"><span data-stu-id="7c999-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="7c999-143">InstanceId anahtarı yalnızca işlemler `Resume` `Terminate` için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7c999-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="7c999-144">Temizlemek için (İsteğe Bağlı)</span><span class="sxs-lookup"><span data-stu-id="7c999-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="7c999-145">Compmgmt.msc komut isteminden çalıştırarak `vs2010` Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="7c999-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="7c999-146">**Hizmet ve Uygulamaları**Genişlet , İleti **Sırası**, **Özel Kuyruklar**.</span><span class="sxs-lookup"><span data-stu-id="7c999-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="7c999-147">**ReceiveTx** sırasını silin.</span><span class="sxs-lookup"><span data-stu-id="7c999-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="7c999-148">Kalıcılık veritabanını kaldırmak için cleanup.cmd'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c999-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c999-149">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c999-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c999-150">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c999-150">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7c999-151">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="7c999-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c999-152">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c999-152">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
