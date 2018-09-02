---
title: Askıya alınmış örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: f614770121185644c3395f923cf7835141653f55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394606"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="d3a04-102">Askıya alınmış örnek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="d3a04-102">Suspended Instance Management</span></span>
<span data-ttu-id="d3a04-103">Bu örnek, askıya alınmış iş akışı örneğini yönetmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3a04-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="d3a04-104">İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> olduğu `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="d3a04-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="d3a04-105">Varsayılan olarak, bir iş akışı örneğinden oluşturulan yakalanamayan özel durum barındırılan yani <xref:System.ServiceModel.WorkflowServiceHost> örneği (terk) bellekten çıkarılması ve dayanıklı ve kalıcı örneğinin sürümü, askıya alındı olarak işaretlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="d3a04-106">Askıya alınan iş akışı örneği adlı aşana kadar çalıştırmak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d3a04-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="d3a04-107">Örnek sorgu askıya alınmış örnekleri için ve nasıl sürdürün veya örneği sonlandırma seçeneği kullanıcıya vermek için bir komut satırı yardımcı programını nasıl uygulanabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d3a04-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="d3a04-108">Bu örnekte, bir iş akışı hizmeti kasıtlı olarak askıya için neden bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="d3a04-109">Komut satırı yardımcı programını, ardından örnek için sorgulama ve daha sonra sürdürün veya örneği sonlandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a04-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d3a04-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="d3a04-110">Demonstrates</span></span>  
 <span data-ttu-id="d3a04-111"><xref:System.ServiceModel.WorkflowServiceHost> ile <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> içinde Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="d3a04-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d3a04-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="d3a04-112">Discussion</span></span>  
 <span data-ttu-id="d3a04-113">Bu örnekte uygulanan komut satırı yardımcı programını içinde birlikte gelen SQL örneği mağazası uygulamalarına özeldir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3a04-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="d3a04-114">Örnek deposuna bir özel uygulanışı olması durumunda değiştirerek bu yardımcı program uyarlayabilirsiniz `WorkflowInstanceCommand` örnek uygulamalarında, örnek deposuna belirli uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="d3a04-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="d3a04-115">Sağlanan uygulama doğrudan askıya alınmış örneklerini listelemek için SQL örneği depo SQL komutlarını çalıştırır ve kullanır bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> eklenen <xref:System.ServiceModel.WorkflowServiceHost> sürdürün veya örnekleri sonlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="d3a04-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3a04-116">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d3a04-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d3a04-117">Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d3a04-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="d3a04-118">Microsoft ileti kuyrukları (MSMQ) sunucusu</span><span class="sxs-lookup"><span data-stu-id="d3a04-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="d3a04-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="d3a04-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="d3a04-120">SQL Server veritabanı ayarlama.</span><span class="sxs-lookup"><span data-stu-id="d3a04-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="d3a04-121">Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut isteminde "Setup.cmd'yi" aşağıdaki SuspendedInstanceManagement örnek dizinden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d3a04-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="d3a04-122">SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="d3a04-123">Bırakılan ve yeniden oluşturulduğunda Kalıcılık veritabanı zaten varsa</span><span class="sxs-lookup"><span data-stu-id="d3a04-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="d3a04-124">Kalıcılık veritabanı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3a04-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="d3a04-125">IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\NETWORK SERVICE Kalıcılık veritabanı ayarlarken tanımlandı InstanceStoreUsers rolüne ekler.</span><span class="sxs-lookup"><span data-stu-id="d3a04-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="d3a04-126">Hizmet sırasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3a04-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="d3a04-127">İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], sağ **SampleWorkflowApp** projesine **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="d3a04-128">Derleme ve tuşlarına basarak SampleWorkflowApp çalıştırma **F5**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="d3a04-129">Bu gerekli bir kuyruk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="d3a04-130">Tuşuna **Enter** SampleWorkflowApp durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="d3a04-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="d3a04-131">Bir komut istemi'nden Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="d3a04-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="d3a04-132">Genişletin **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="d3a04-133">Sağ tıklayın **ReceiveTx** seçin ve sıra **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="d3a04-134">Seçin **güvenlik** sekmesini ve izin **herkes** izinlerine sahip olmasını **İleti Al**, **iletiye**, ve  **İleti gönderme**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="d3a04-135">Şimdi, örnek çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a04-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="d3a04-136">İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SampleWorkflowApp projeyi yeniden tuşuna basarak hata ayıklama olmadan çalıştırmak **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="d3a04-137">İki uç nokta adresleri konsol penceresinde yazdırılır: uygulama uç noktası için bir tane ve gelen diğer <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="d3a04-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="d3a04-138">Bir iş akışı örneği sonra oluşturulur ve bu örnek için kayıtları izleme konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="d3a04-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="d3a04-139">İş akışı örneği askıya ve iptal örneği neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="d3a04-140">Komut satırı yardımcı programını, ardından Bu örneklerin herhangi birine üzerinde daha fazla eylemi gerçekleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a04-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="d3a04-141">Komut satırı bağımsız değişkenleri için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d3a04-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="d3a04-142">Desteklenen komutlar: `Query`, `Resume`, ve `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="d3a04-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="d3a04-143">InstanceId geçiş için yalnızca gerekli `Resume` ve `Terminate` operations.</span><span class="sxs-lookup"><span data-stu-id="d3a04-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="d3a04-144">(İsteğe bağlı) temizlemek için</span><span class="sxs-lookup"><span data-stu-id="d3a04-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="d3a04-145">Gelen Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın bir `vs2010` komut istemi.</span><span class="sxs-lookup"><span data-stu-id="d3a04-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="d3a04-146">Genişletin **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="d3a04-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="d3a04-147">Silme **ReceiveTx** kuyruk.</span><span class="sxs-lookup"><span data-stu-id="d3a04-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="d3a04-148">Kalıcılık veritabanı kaldırmak için cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a04-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3a04-149">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="d3a04-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3a04-150">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d3a04-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d3a04-151">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d3a04-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3a04-152">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d3a04-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
