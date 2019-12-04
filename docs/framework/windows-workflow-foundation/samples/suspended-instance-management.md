---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 3f1f4f8edcbe0e05067d3ca739ef3d5f4fe4d798
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715938"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="65b0a-102">Askıya Alınmış Örnek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="65b0a-102">Suspended Instance Management</span></span>
<span data-ttu-id="65b0a-103">Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="65b0a-104"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> için varsayılan eylem `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="65b0a-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="65b0a-105">Bu, varsayılan olarak, <xref:System.ServiceModel.WorkflowServiceHost> barındırılan bir iş akışı örneğinden oluşturulan işlenmemiş özel durumların, örneğin bellekten (terk) ve askıya alınmış olarak işaretlenmesi için, örneğin, kalıcı/kalıcı hale gelmesine neden olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="65b0a-106">Askıya alınmış bir iş akışı örneği askıya alınana kadar çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="65b0a-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="65b0a-107">Örnek, askıya alınmış örnekleri sorgulamak için bir komut satırı yardımcı programının nasıl uygulankullanılabileceğini ve kullanıcıya örneği yeniden başlatma veya sonlandırma seçeneği nasıl sunılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="65b0a-108">Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum oluşturur ve askıya alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="65b0a-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="65b0a-109">Daha sonra komut satırı yardımcı programı örneği sorgulamak için kullanılabilir ve ardından örneği sürdürür veya sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="65b0a-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="65b0a-110">Gösterir</span><span class="sxs-lookup"><span data-stu-id="65b0a-110">Demonstrates</span></span>
 <span data-ttu-id="65b0a-111">Windows Workflow Foundation (WF) <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="65b0a-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="65b0a-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="65b0a-112">Discussion</span></span>
 <span data-ttu-id="65b0a-113">Bu örnekte uygulanan komut satırı yardımcı programı, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]ile birlikte gelen SQL örnek deposu uygulamasına özgüdür.</span><span class="sxs-lookup"><span data-stu-id="65b0a-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="65b0a-114">Örnek deposunun özel bir uygulamasına sahipseniz, örnekteki `WorkflowInstanceCommand` uygulamalarını örnek deponuza özgü uygulamalarla değiştirerek bu yardımcı programı uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65b0a-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="65b0a-115">Belirtilen uygulama, askıya alınmış örnekleri listelemek için doğrudan SQL örneği deposunda SQL komutları çalıştırır ve örnekleri yeniden başlatmak veya sonlandırmak için <xref:System.ServiceModel.WorkflowServiceHost> eklenmiş bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> kullanır.</span><span class="sxs-lookup"><span data-stu-id="65b0a-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="65b0a-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="65b0a-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="65b0a-117">Bu örnek, aşağıdaki Windows bileşenlerinin etkinleştirilmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="65b0a-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="65b0a-118">Microsoft Ileti sıraları (MSMQ) sunucusu</span><span class="sxs-lookup"><span data-stu-id="65b0a-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="65b0a-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="65b0a-119">SQL Server Express</span></span>

2. <span data-ttu-id="65b0a-120">SQL Server veritabanını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="65b0a-121">Visual Studio 2010 komut isteminden, SuspendedInstanceManagement örnek dizininden "Setup. cmd" komutunu çalıştırın ve şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="65b0a-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="65b0a-122">SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65b0a-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="65b0a-123">Kalıcılık veritabanı zaten varsa, bırakılır ve yeniden oluşturulur</span><span class="sxs-lookup"><span data-stu-id="65b0a-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="65b0a-124">Veritabanını kalıcılık için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65b0a-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="65b0a-125">Veritabanı kalıcılığı için ayarlarken tanımlanmış olan InstanceStoreUsers rolüne IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service ekler.</span><span class="sxs-lookup"><span data-stu-id="65b0a-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="65b0a-126">Hizmet kuyruğunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="65b0a-127">Visual Studio 2010 ' de **SampleWorkflowApp** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="65b0a-128">**F5**tuşuna basarak SampleWorkflowApp 'i derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="65b0a-129">Bu işlem gerekli kuyruğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65b0a-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="65b0a-130">SampleWorkflowApp 'i durdurmak için **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="65b0a-131">Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="65b0a-132">**Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="65b0a-133">**ReceiveTx** kuyruğuna sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="65b0a-134">**Güvenlik** sekmesini seçin ve **herkesin** **ileti alma**, **iletiye göz atma**ve **ileti gönderme**izinlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="65b0a-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="65b0a-135">Şimdi, örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="65b0a-136">Visual Studio 2010 ' de, SampleWorkflowApp projesini hata ayıklama olmadan yeniden çalıştırarak **CTRL + F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="65b0a-137">İki uç nokta adresi konsol penceresinde yazdırılır: bir uygulama uç noktası ve ardından <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>diğeri.</span><span class="sxs-lookup"><span data-stu-id="65b0a-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="65b0a-138">Daha sonra bir iş akışı örneği oluşturulur ve bu örneğe ilişkin izleme kayıtları konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="65b0a-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="65b0a-139">İş akışı örneği, örneğin askıya alınmasına ve iptal olmasına neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65b0a-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="65b0a-140">Komut satırı yardımcı programı daha sonra bu örneklerden herhangi birinde daha fazla işlem yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="65b0a-141">Komut satırı bağımsız değişkenlerinin sözdizimi şöyledir::</span><span class="sxs-lookup"><span data-stu-id="65b0a-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="65b0a-142">Desteklenen komutlar şunlardır: `Query`, `Resume`ve `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="65b0a-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="65b0a-143">InstanceId anahtarı yalnızca `Resume` ve `Terminate` işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="65b0a-144">Temizlemek için (Isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="65b0a-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="65b0a-145">`vs2010` komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="65b0a-146">**Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="65b0a-147">**ReceiveTx** kuyruğunu silin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="65b0a-148">Kalıcılık veritabanını kaldırmak için Cleanup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="65b0a-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65b0a-149">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="65b0a-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="65b0a-150">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-150">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="65b0a-151">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="65b0a-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65b0a-152">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="65b0a-152">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
