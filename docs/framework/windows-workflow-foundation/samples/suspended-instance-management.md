---
description: 'Daha fazla bilgi edinin: askıya alınmış örnek yönetimi'
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: d68dd8b61b6e0e7a618cf05f1df07e58ab75e27f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741737"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="bde59-103">Askıya Alınmış Örnek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="bde59-103">Suspended Instance Management</span></span>

<span data-ttu-id="bde59-104">Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bde59-104">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="bde59-105">İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> `AbandonAndSuspend` .</span><span class="sxs-lookup"><span data-stu-id="bde59-105">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="bde59-106">Bu, varsayılan olarak, ' de barındırılan bir iş akışı örneğinden oluşturulan işlenmemiş özel durumların, <xref:System.ServiceModel.WorkflowServiceHost> Örneğin bellekten (terk) ve askıya alınmış olarak işaretlenmesine neden olan örneğinin kalıcı/kalıcı sürümü tarafından atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bde59-106">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="bde59-107">Askıya alınmış bir iş akışı örneği askıya alınana kadar çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="bde59-107">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="bde59-108">Örnek, askıya alınmış örnekleri sorgulamak için bir komut satırı yardımcı programının nasıl uygulankullanılabileceğini ve kullanıcıya örneği yeniden başlatma veya sonlandırma seçeneği nasıl sunılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bde59-108">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="bde59-109">Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum oluşturur ve askıya alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bde59-109">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="bde59-110">Daha sonra komut satırı yardımcı programı örneği sorgulamak için kullanılabilir ve ardından örneği sürdürür veya sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bde59-110">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bde59-111">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="bde59-111">Demonstrates</span></span>

 <span data-ttu-id="bde59-112"><xref:System.ServiceModel.WorkflowServiceHost><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> WINDOWS Workflow FOUNDATION (WF) ile.</span><span class="sxs-lookup"><span data-stu-id="bde59-112"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="bde59-113">Tartışma</span><span class="sxs-lookup"><span data-stu-id="bde59-113">Discussion</span></span>

 <span data-ttu-id="bde59-114">Bu örnekte uygulanan komut satırı yardımcı programı, içinde yer alan SQL örnek deposu uygulamasına özgüdür [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bde59-114">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="bde59-115">Örnek deposunun özel bir uygulamasına sahipseniz, `WorkflowInstanceCommand` örnekteki uygulamaları örnek deponuza özgü uygulamalarla değiştirerek bu yardımcı programı uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bde59-115">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="bde59-116">Belirtilen uygulama, askıya alınmış örnekleri listelemek için doğrudan SQL örneği deposunda SQL komutları çalıştırır ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.WorkflowServiceHost> örnekleri yeniden başlatmak veya sonlandırmak için öğesine eklenen öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="bde59-116">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bde59-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bde59-117">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="bde59-118">Bu örnek, aşağıdaki Windows bileşenlerinin etkinleştirilmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bde59-118">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="bde59-119">Microsoft Ileti sıraları (MSMQ) sunucusu</span><span class="sxs-lookup"><span data-stu-id="bde59-119">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="bde59-120">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="bde59-120">SQL Server Express</span></span>

2. <span data-ttu-id="bde59-121">SQL Server veritabanını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bde59-121">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="bde59-122">Visual Studio 2010 komut isteminden, SuspendedInstanceManagement örnek dizininden "Setup. cmd" komutunu çalıştırın ve şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="bde59-122">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="bde59-123">SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bde59-123">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="bde59-124">Kalıcılık veritabanı zaten varsa, bırakılır ve yeniden oluşturulur</span><span class="sxs-lookup"><span data-stu-id="bde59-124">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="bde59-125">Veritabanını kalıcılık için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bde59-125">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="bde59-126">Veritabanı kalıcılığı için ayarlarken tanımlanmış olan InstanceStoreUsers rolüne IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service ekler.</span><span class="sxs-lookup"><span data-stu-id="bde59-126">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="bde59-127">Hizmet kuyruğunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bde59-127">Set up the service queue.</span></span>

    1. <span data-ttu-id="bde59-128">Visual Studio 2010 ' de **SampleWorkflowApp** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bde59-128">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="bde59-129">**F5** tuşuna basarak SampleWorkflowApp 'i derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bde59-129">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="bde59-130">Bu işlem gerekli kuyruğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bde59-130">This will create the required queue.</span></span>

    3. <span data-ttu-id="bde59-131">SampleWorkflowApp 'i durdurmak için **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bde59-131">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="bde59-132">Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="bde59-132">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="bde59-133">**Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="bde59-133">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="bde59-134">**ReceiveTx** kuyruğuna sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bde59-134">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="bde59-135">**Güvenlik** sekmesini seçin ve **herkesin** **ileti alma**, **iletiye göz atma** ve **ileti gönderme** izinlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bde59-135">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="bde59-136">Şimdi, örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bde59-136">Now, run the sample.</span></span>

    1. <span data-ttu-id="bde59-137">Visual Studio 2010 ' de, SampleWorkflowApp projesini hata ayıklama olmadan yeniden çalıştırarak **CTRL + F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bde59-137">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="bde59-138">İki uç nokta adresi konsol penceresinde yazdırılır: bir uygulama uç noktası ve sonrasında diğeri <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bde59-138">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="bde59-139">Daha sonra bir iş akışı örneği oluşturulur ve bu örneğe ilişkin izleme kayıtları konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="bde59-139">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="bde59-140">İş akışı örneği, örneğin askıya alınmasına ve iptal olmasına neden olan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bde59-140">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="bde59-141">Komut satırı yardımcı programı daha sonra bu örneklerden herhangi birinde daha fazla işlem yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bde59-141">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="bde59-142">Komut satırı bağımsız değişkenlerinin sözdizimi şöyledir::</span><span class="sxs-lookup"><span data-stu-id="bde59-142">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="bde59-143">Desteklenen komutlar şunlardır: `Query` , `Resume` , ve `Terminate` .</span><span class="sxs-lookup"><span data-stu-id="bde59-143">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="bde59-144">InstanceId anahtarı yalnızca ve işlemleri için gereklidir `Resume` `Terminate` .</span><span class="sxs-lookup"><span data-stu-id="bde59-144">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="bde59-145">Temizlemek için (Isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="bde59-145">To cleanup (Optional)</span></span>

1. <span data-ttu-id="bde59-146">Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın `vs2010` .</span><span class="sxs-lookup"><span data-stu-id="bde59-146">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="bde59-147">**Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="bde59-147">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="bde59-148">**ReceiveTx** kuyruğunu silin.</span><span class="sxs-lookup"><span data-stu-id="bde59-148">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="bde59-149">Kalıcılık veritabanını kaldırmak için Cleanup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bde59-149">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bde59-150">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bde59-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bde59-151">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bde59-151">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bde59-152">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bde59-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bde59-153">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bde59-153">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
