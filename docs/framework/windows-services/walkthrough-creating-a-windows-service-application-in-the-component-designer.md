---
title: 'İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmet Uygulaması Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: c33b8badcacd4e228d70f8e770d4bf27144c29eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520519"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a><span data-ttu-id="a8204-102">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmet Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8204-102">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>
<span data-ttu-id="a8204-103">Bu makalede, bir olay günlüğü iletileri Yazar Visual Studio'da basit bir Windows hizmet uygulaması oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8204-103">This article demonstrates how to create a simple Windows Service application in Visual Studio that writes messages to an event log.</span></span> <span data-ttu-id="a8204-104">Hizmetinizi oluşturmak için gerçekleştirdiğiniz temel adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a8204-104">Here are the basic steps that you perform to create and use your service:</span></span>  
  
1.  <span data-ttu-id="a8204-105">[Bir hizmet oluşturma](#BK_CreateProject) kullanarak **Windows hizmeti** proje şablonu ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a8204-105">[Creating a Service](#BK_CreateProject) by using the **Windows Service** project template, and configure it.</span></span> <span data-ttu-id="a8204-106">Bu şablon, devraldığı sizin için bir sınıf oluşturur <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> ve hizmeti başlatmak için kod gibi temel hizmeti kodu çoğunu yazar.</span><span class="sxs-lookup"><span data-stu-id="a8204-106">This template creates a class for you that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> and writes much of the basic service code, such as the code to start the service.</span></span>  
  
2.  <span data-ttu-id="a8204-107">[Hizmete özellik ekleme](#BK_WriteCode) için <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları ve yeniden tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="a8204-107">[Adding Features to the Service](#BK_WriteCode) for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures, and override any other methods that you want to redefine.</span></span>  
  
3.  <span data-ttu-id="a8204-108">[Hizmet durumu ayarı](#BK_SetStatus).</span><span class="sxs-lookup"><span data-stu-id="a8204-108">[Setting Service Status](#BK_SetStatus).</span></span> <span data-ttu-id="a8204-109">Varsayılan olarak, hizmetler ile oluşturulan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> yalnızca bir alt kümesini kullanılabilir durumu bayrakları uygular.</span><span class="sxs-lookup"><span data-stu-id="a8204-109">By default, services created with <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implement only a subset of the available status flags.</span></span> <span data-ttu-id="a8204-110">Hizmet başlatma, duraklatma veya durdurmak için bir uzun sürüyorsa, durum değerleri Beklemede Başlat veya Durdur Beklemede üzerinde bir işlemi çalıştığını göstermek için gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-110">If your service takes a long time to start up, pause, or stop, you can implement status values such as Start Pending or Stop Pending to indicate that it's working on an operation.</span></span>  
  
4.  <span data-ttu-id="a8204-111">[Yükleyici hizmetine ekleme](#BK_AddInstallers) hizmet uygulamanız için.</span><span class="sxs-lookup"><span data-stu-id="a8204-111">[Adding Installers to the Service](#BK_AddInstallers) for your service application.</span></span>  
  
5.  <span data-ttu-id="a8204-112">(İsteğe bağlı) [Ayarlanan başlangıç parametreleri](#BK_StartupParameters), varsayılan başlangıç bağımsız değişkenleri belirtin ve hizmetinizi el ile başlattığınızda, varsayılan ayarları geçersiz kılacak olanağı verir.</span><span class="sxs-lookup"><span data-stu-id="a8204-112">(Optional) [Set Startup Parameters](#BK_StartupParameters), specify default startup arguments, and enable users to override default settings when they start your service manually.</span></span>  
  
6.  <span data-ttu-id="a8204-113">[Hizmet oluşturma](#BK_Build).</span><span class="sxs-lookup"><span data-stu-id="a8204-113">[Building the Service](#BK_Build).</span></span>  
  
7.  <span data-ttu-id="a8204-114">[Hizmeti yükleme](#BK_Install) yerel makine üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a8204-114">[Installing the Service](#BK_Install) on the local machine.</span></span>  
  
8.  <span data-ttu-id="a8204-115">Windows Hizmet Denetimi Yöneticisi'ne erişmek ve [başlatma ve hizmet çalıştırma](#BK_StartService).</span><span class="sxs-lookup"><span data-stu-id="a8204-115">Access the Windows Service Control Manager and [Starting and Running the Service](#BK_StartService).</span></span>  
  
9. <span data-ttu-id="a8204-116">[Bir Windows hizmeti kaldırma](#BK_Uninstall).</span><span class="sxs-lookup"><span data-stu-id="a8204-116">[Uninstalling a Windows Service](#BK_Uninstall).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a8204-117">Bu izlenecek yol için gerekli olan Windows Hizmetleri proje şablonu Visual Studio'nun Express sürümünde bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8204-117">The Windows Services project template that is required for this walkthrough is not available in the Express edition of Visual Studio.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a><span data-ttu-id="a8204-118">Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8204-118">Creating a Service</span></span>  
 <span data-ttu-id="a8204-119">Başlamak için projeyi oluşurun ve hizmetin düzgün çalışması için gerekli değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a8204-119">To begin, you create the project and set values that are required for the service to function correctly.</span></span>  
  
#### <a name="to-create-and-configure-your-service"></a><span data-ttu-id="a8204-120">Hizmetinizi oluşturmak ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a8204-120">To create and configure your service</span></span>  
  
1.  <span data-ttu-id="a8204-121">Menü çubuğunda, Visual Studio'da seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="a8204-121">In Visual Studio, on the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="a8204-122">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="a8204-122">The **New Project** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a8204-123">Visual Basic veya Visual C# proje şablonları listesinden seçip **Windows hizmeti**ve proje adı **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="a8204-123">In the list of Visual Basic or Visual C# project templates, choose **Windows Service**, and name the project **MyNewService**.</span></span> <span data-ttu-id="a8204-124">Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a8204-124">Choose **OK**.</span></span>  
  
     <span data-ttu-id="a8204-125">Proje şablonu otomatik olarak adında bir bileşen sınıfı ekler `Service1` devraldığı <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8204-125">The project template automatically adds a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="a8204-126">Üzerinde **Düzenle** menüsünde seçin **bulma ve değiştirme**, **dosyalarda Bul** (klavye: Ctrl + Shift + F).</span><span class="sxs-lookup"><span data-stu-id="a8204-126">On the **Edit** menu, choose **Find and Replace**, **Find in Files** (Keyboard: Ctrl+Shift+F).</span></span> <span data-ttu-id="a8204-127">Tüm oluşumlarını değiştirme `Service1` için `MyNewService`.</span><span class="sxs-lookup"><span data-stu-id="a8204-127">Change all occurrences of `Service1` to `MyNewService`.</span></span> <span data-ttu-id="a8204-128">Örnekleri service1.cs dosyasını, Program.cs ve Service1.Designer.cs (veya .vb eşdeğerlerine) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-128">You’ll find instances in Service1.cs, Program.cs, and Service1.Designer.cs (or their .vb equivalents).</span></span>  
  
4.  <span data-ttu-id="a8204-129">İçinde **özellikleri** penceresi **service1.cs dosyasını [tasarım]** veya **Service1.vb [tasarım]** ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ve **(ad)** özelliği için `Service1` için **MyNewService**, zaten ayarlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="a8204-129">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> and the **(Name)** property for `Service1` to **MyNewService**, if it's not already set.</span></span>  
  
5.  <span data-ttu-id="a8204-130">Çözüm Gezgini'nde, yeniden adlandırma **service1.cs dosyasını** için **MyNewService.cs**, veya **Service1.vb** için **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="a8204-130">In Solution Explorer, rename **Service1.cs** to **MyNewService.cs**, or **Service1.vb** to **MyNewService.vb**.</span></span>  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a><span data-ttu-id="a8204-131">Hizmete Özellik Ekleme</span><span class="sxs-lookup"><span data-stu-id="a8204-131">Adding Features to the Service</span></span>  
 <span data-ttu-id="a8204-132">Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8204-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="a8204-133">Olay günlükleri, Windows hizmetleri ile hiçbir şekilde ilişkili değildir.</span><span class="sxs-lookup"><span data-stu-id="a8204-133">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="a8204-134">Burada <xref:System.Diagnostics.EventLog> bileşeni Bileşen Ekle, bir Windows hizmeti için tür bir örnek olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8204-134">Here the <xref:System.Diagnostics.EventLog> component is used as an example of the type of component you could add to a Windows service.</span></span>  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a><span data-ttu-id="a8204-135">Hizmetinize özelleştirilmiş olay günlüğü işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="a8204-135">To add custom event log functionality to your service</span></span>  
  
1.  <span data-ttu-id="a8204-136">İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="a8204-136">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="a8204-137">Gelen **bileşenleri** bölümünü **araç**, sürükleyin bir <xref:System.Diagnostics.EventLog> bileşenini tasarımcıya.</span><span class="sxs-lookup"><span data-stu-id="a8204-137">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>  
  
3.  <span data-ttu-id="a8204-138">İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="a8204-138">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>  
  
4.  <span data-ttu-id="a8204-139">İçin bir bildirim eklemek **eventLog** nesnesinde `MyNewService` sağ bildirir satırından sonra bir sınıf `components` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="a8204-139">Add a declaration for the **eventLog** object in the `MyNewService` class, right after the line that declares the `components` variable:</span></span>  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  <span data-ttu-id="a8204-140">Ekle veya özel bir olay günlüğü tanımlamak için oluşturucu düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="a8204-140">Add or edit the constructor to define a custom event log:</span></span>  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a><span data-ttu-id="a8204-141">Hizmet başlatıldığında ne olacağını tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a8204-141">To define what occurs when the service starts</span></span>  
  
-   <span data-ttu-id="a8204-142">Kod Düzenleyicisi'nde bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodun proje oluşturduğunuzda otomatik olarak geçersiz kılındı ve kodu aşağıdakilerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a8204-142">In the Code Editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project, and replace the code with the following.</span></span> <span data-ttu-id="a8204-143">Hizmet çalışmaya başladığında bu olay günlüğüne bir giriş ekler:</span><span class="sxs-lookup"><span data-stu-id="a8204-143">This adds an entry to the event log when the service starts running:</span></span>  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     <span data-ttu-id="a8204-144">Bir hizmet uygulaması genellikle yoklar veya bir şey sistemde izler uzun süreli olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8204-144">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="a8204-145">İzleme ayarlanır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8204-145">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="a8204-146">Ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> gerçekten izleme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a8204-146">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="a8204-147"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi hizmetin işlemi başladıktan sonra işletim sistemine döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8204-147">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="a8204-148">Sonsuza kadar döngü veya engelleme gerçekleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a8204-148">It must not loop forever or block.</span></span> <span data-ttu-id="a8204-149">Basit yoklama mekanizması kurmak için kullanabilirsiniz <xref:System.Timers.Timer?displayProperty=nameWithType> bileşen şekilde: içinde <xref:System.ServiceProcess.ServiceBase.OnStart%2A> bileşeni parametreleri ayarlayın ve ardından yöntemi <xref:System.Timers.Timer.Enabled%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="a8204-149">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="a8204-150">Düzenli aralıklarla, aynı zamanda hizmetiniz izlemeyi yapabileceği olayları kodunuzda süreölçer başlatır.</span><span class="sxs-lookup"><span data-stu-id="a8204-150">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="a8204-151">Bunu yapmak için aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a8204-151">You can use the following code to do this:</span></span>  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     <span data-ttu-id="a8204-152">Üye değişkeni sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8204-152">Add a member variable to the class.</span></span> <span data-ttu-id="a8204-153">Olay günlüğüne yazmak için sonraki olay tanımlayıcı içerecektir.</span><span class="sxs-lookup"><span data-stu-id="a8204-153">It will contain the identifier of the next event to write into the event log.</span></span>

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     <span data-ttu-id="a8204-154">Süreölçer olayı işlemek için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8204-154">Add code to handle the timer event:</span></span>  
  
    ```csharp  
    public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)  
    {  
        // TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);  
    }  
    ```  
  
    ```vb  
    Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)  
        ' TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)  
        eventId = eventId + 1  
    End Sub  
    ```  
  
     <span data-ttu-id="a8204-155">Tüm iş ana iş parçacığında çalıştırmak yerine arka plan iş parçacıklarını kullanarak görevleri isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-155">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="a8204-156">Bu örneği için bkz: <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> başvuru sayfası.</span><span class="sxs-lookup"><span data-stu-id="a8204-156">For an example of this, see the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> reference page.</span></span>  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="a8204-157">Hizmet durdurulduğunda ne olacağını tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a8204-157">To define what occurs when the service is stopped</span></span>  
  
-   <span data-ttu-id="a8204-158">Kodunu değiştir <xref:System.ServiceProcess.ServiceBase.OnStop%2A> aşağıdaki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8204-158">Replace the code for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method with the following.</span></span> <span data-ttu-id="a8204-159">Hizmet durdurulduğunda bu olay günlüğüne bir giriş ekler:</span><span class="sxs-lookup"><span data-stu-id="a8204-159">This adds an entry to the event log when the service is stopped:</span></span>  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 <span data-ttu-id="a8204-160">Sonraki bölümde kılmanız <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işleme tanımlamak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a8204-160">In the next section, you can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>  
  
#### <a name="to-define-other-actions-for-the-service"></a><span data-ttu-id="a8204-161">Hizmete ilişkin diğer eylemleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a8204-161">To define other actions for the service</span></span>  
  
-   <span data-ttu-id="a8204-162">İşlemek istediğiniz yöntemi bulun ve onu gerçekleştirilmesini istediğiniz tanımlamak için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="a8204-162">Locate the method that you want to handle, and override it to define what you want to occur.</span></span>  
  
     <span data-ttu-id="a8204-163">Aşağıdaki kod, nasıl kılabilirsiniz gösterir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a8204-163">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 <span data-ttu-id="a8204-164">Bazı özel eylemler bir Windows hizmeti tarafından yüklendiğinde ortaya zorunda <xref:System.Configuration.Install.Installer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a8204-164">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="a8204-165">Visual Studio, bu yükleyicileri bir Windows hizmeti için özel olarak oluşturabilir ve sonra da projenize ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a8204-165">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a><span data-ttu-id="a8204-166">Ayar hizmet durumu</span><span class="sxs-lookup"><span data-stu-id="a8204-166">Setting Service Status</span></span>  
 <span data-ttu-id="a8204-167">Kullanıcılar bir hizmet doğru şekilde çalışıp çalışmadığını yapıp yapmadığını Hizmetleri için hizmet denetimi yöneticisi, kendi durumlarını bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a8204-167">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="a8204-168">Varsayılan olarak, devralınan Hizmetleri <xref:System.ServiceProcess.ServiceBase> durdurulmuş, duraklatılmış ve çalıştıran sınırlı sayıda durum ayarları dahil olmak üzere, rapor.</span><span class="sxs-lookup"><span data-stu-id="a8204-168">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="a8204-169">Bunun başlatmak için Başlat bekleme durumu raporlamak faydalı olabilir ancak bir hizmet biraz uzun sürerse.</span><span class="sxs-lookup"><span data-stu-id="a8204-169">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="a8204-170">Pencerelere çağıran kodu ekleyerek bekleyen başlatmak ve durdurmak bekleyen durum ayarlarını uygulayabilirsiniz [artırılmış işlevi](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).</span><span class="sxs-lookup"><span data-stu-id="a8204-170">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).</span></span>  
  
#### <a name="to-implement-service-pending-status"></a><span data-ttu-id="a8204-171">Hizmet Durumu Beklemede uygulamak için</span><span class="sxs-lookup"><span data-stu-id="a8204-171">To implement service pending status</span></span>  
  
1.  <span data-ttu-id="a8204-172">Ekleme bir `using` deyimi veya `Imports` bildirimine <xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs veya MyNewService.vb dosyasındaki ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a8204-172">Add a `using` statement or `Imports` declaration to the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  <span data-ttu-id="a8204-173">Bildirmek için MyNewService.cs için aşağıdaki kodu ekleyin `ServiceState` değerleri ve bir platform kullanacağınız durumu için bir yapı çağırma çağrısı eklemek için:</span><span class="sxs-lookup"><span data-stu-id="a8204-173">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>  
  
    ```csharp  
    public enum ServiceState  
      {  
          SERVICE_STOPPED = 0x00000001,  
          SERVICE_START_PENDING = 0x00000002,  
          SERVICE_STOP_PENDING = 0x00000003,  
          SERVICE_RUNNING = 0x00000004,  
          SERVICE_CONTINUE_PENDING = 0x00000005,  
          SERVICE_PAUSE_PENDING = 0x00000006,  
          SERVICE_PAUSED = 0x00000007,  
      }  
  
      [StructLayout(LayoutKind.Sequential)]  
      public struct ServiceStatus  
      {  
          public int dwServiceType;  
          public ServiceState dwCurrentState;  
          public int dwControlsAccepted;  
          public int dwWin32ExitCode;  
          public int dwServiceSpecificExitCode;  
          public int dwCheckPoint;  
          public int dwWaitHint;  
      };  
    ```  
  
    ```vb  
    Public Enum ServiceState  
        SERVICE_STOPPED = 1  
        SERVICE_START_PENDING = 2  
        SERVICE_STOP_PENDING = 3  
        SERVICE_RUNNING = 4  
        SERVICE_CONTINUE_PENDING = 5  
        SERVICE_PAUSE_PENDING = 6  
        SERVICE_PAUSED = 7  
    End Enum  
  
    <StructLayout(LayoutKind.Sequential)>  
    Public Structure ServiceStatus  
        Public dwServiceType As Long  
        Public dwCurrentState As ServiceState  
        Public dwControlsAccepted As Long  
        Public dwWin32ExitCode As Long  
        Public dwServiceSpecificExitCode As Long  
        Public dwCheckPoint As Long  
        Public dwWaitHint As Long  
    End Structure  
    ```  
  
3.  <span data-ttu-id="a8204-174">Şimdi `MyNewService` sınıfı, bildirme [artırılmış işlevi](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) platformu kullanarak çağırın:</span><span class="sxs-lookup"><span data-stu-id="a8204-174">Now, in the `MyNewService` class, declare the [SetServiceStatus function](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) by using platform invoke:</span></span>  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  <span data-ttu-id="a8204-175">Başlangıç bekleme durumu uygulamak için aşağıdaki kodu başlangıcına ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a8204-175">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>  
  
    ```csharp  
    // Update the service state to Start Pending.  
    ServiceStatus serviceStatus = new ServiceStatus();  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;  
    serviceStatus.dwWaitHint = 100000;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Start Pending.  
    Dim serviceStatus As ServiceStatus = New ServiceStatus()  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING  
    serviceStatus.dwWaitHint = 100000  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
5.  <span data-ttu-id="a8204-176">Sonunda çalıştırmaya durumunu ayarlamak için kod ekleme <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8204-176">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>  
  
    ```csharp
    // Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
6.  <span data-ttu-id="a8204-177">(İsteğe bağlı) İçin bu yordamı yineleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8204-177">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a8204-178">[Hizmet Denetim Yöneticisi](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) başlatmak veya kapatmak bir Windows hizmeti için ne kadar süre belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="a8204-178">The [Service Control Manager](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) to determine how much time to wait for a Windows Service to start or shut down.</span></span> <span data-ttu-id="a8204-179">Varsa, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemlerini çalıştırma uzun, hizmetiniz daha fazla zaman çağırarak isteyebilir [artırılmış](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) yeniden ile bir artırılır `dwCheckPoint` değeri.</span><span class="sxs-lookup"><span data-stu-id="a8204-179">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) again with an incremented `dwCheckPoint` value.</span></span>  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a><span data-ttu-id="a8204-180">Hizmete yükleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="a8204-180">Adding Installers to the Service</span></span>  
 <span data-ttu-id="a8204-181">Bir Windows hizmeti çalıştırmadan önce hangi hizmet denetimi Yöneticisi ile kaydeder yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8204-181">Before you can run a Windows Service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="a8204-182">Kayıt ayrıntıları ele projenize yükleyicileri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-182">You can add installers to your project that handle the registration details.</span></span>  
  
#### <a name="to-create-the-installers-for-your-service"></a><span data-ttu-id="a8204-183">Hizmetinize ilişkin yükleyicileri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a8204-183">To create the installers for your service</span></span>  
  
1.  <span data-ttu-id="a8204-184">İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="a8204-184">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="a8204-185">Hizmetin herhangi bir içeriğini değil de, hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a8204-185">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>  
  
3.  <span data-ttu-id="a8204-186">(Sağ penceresi içinde bir işaretleme aygıtı kullanıyorsanız) Tasarımcı penceresinin bağlam menüsünü açın ve ardından **Yükleyici Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a8204-186">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>  
  
     <span data-ttu-id="a8204-187">Varsayılan olarak, projenize iki yükleyici içeren bir bileşen sınıfı eklenir.</span><span class="sxs-lookup"><span data-stu-id="a8204-187">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="a8204-188">Bileşen adlı **ProjectInstaller**ve içerdiği yükleyiciler hizmetiniz için yükleyici ve yükleyici hizmeti için işlem ilişkili.</span><span class="sxs-lookup"><span data-stu-id="a8204-188">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>  
  
4.  <span data-ttu-id="a8204-189">İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **Serviceınstaller1** bir Visual C# projesi için veya **Serviceınstaller1** görsel için Temel projesi.</span><span class="sxs-lookup"><span data-stu-id="a8204-189">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>  
  
5.  <span data-ttu-id="a8204-190">İçinde **özellikleri** penceresinde emin olun <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği ayarlanmış **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="a8204-190">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>  
  
6.  <span data-ttu-id="a8204-191">Ayarlama **açıklama** "Örnek hizmeti" gibi bazı metinleri özelliğine.</span><span class="sxs-lookup"><span data-stu-id="a8204-191">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="a8204-192">Bu metin hizmetleri penceresinde görüntülenir ve kullanıcının Hizmeti'ni tanımlamak ve hangi amaçla kullanıldığına anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a8204-192">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>  
  
7.  <span data-ttu-id="a8204-193">Ayarlama <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Hizmetleri penceresinde görüntülenmesini istediğiniz metin özelliğine **adı** sütun.</span><span class="sxs-lookup"><span data-stu-id="a8204-193">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="a8204-194">Örneğin, "MyNewService görünen ad" girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-194">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="a8204-195">Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sistem tarafından kullanılan ad özelliği (örneğin, kullandığınızda `net start` hizmetinizi başlatmak için komut).</span><span class="sxs-lookup"><span data-stu-id="a8204-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>  
  
8.  <span data-ttu-id="a8204-196">Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğine <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="a8204-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>  
  
     <span data-ttu-id="a8204-197">![Bir Windows hizmeti için yükleyici özelliklerini](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="a8204-197">![Installer Properties for a Windows Service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>  
  
9. <span data-ttu-id="a8204-198">Tasarımcıda seçin **ServiceProcessInstaller1** bir Visual C# projesi için veya **ServiceProcessInstaller1** Visual Basic projesinde için.</span><span class="sxs-lookup"><span data-stu-id="a8204-198">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="a8204-199">Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğine <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="a8204-199">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="a8204-200">Bu, hizmetin yerel hizmet hesabına yüklenmesi ve çalıştırılmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a8204-200">This will cause the service to be installed and to run on a local service account.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a8204-201"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma yeteneği dahil olmak üzere geniş izinlere sahip.</span><span class="sxs-lookup"><span data-stu-id="a8204-201">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="a8204-202">Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="a8204-202">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="a8204-203">Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> yerel bilgisayardaki bir ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya anonim kimlik bilgileri gösterir, hesap.</span><span class="sxs-lookup"><span data-stu-id="a8204-203">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="a8204-204">Bu örnek kullanmaya çalışırsa, başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> , olay günlüğüne yazma izni gerektiği için hesap.</span><span class="sxs-lookup"><span data-stu-id="a8204-204">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>  
  
     <span data-ttu-id="a8204-205">Yükleyiciler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="a8204-205">For more information about installers, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a><span data-ttu-id="a8204-206">Başlangıç parametreleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="a8204-206">Set Startup Parameters</span></span>  
 <span data-ttu-id="a8204-207">Başka bir yürütülebilir dosyayı gibi bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="a8204-207">A Windows Service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="a8204-208">İşlem Başlangıç parametreleri için kod eklediğinizde, kullanıcılar Windows Denetim Masası'ndaki Hizmetler penceresini kullanarak kendi özel başlangıç parametreleri ile hizmetinizi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-208">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="a8204-209">Ancak, bu başlangıç parametreleri hizmet bir sonraki başlatılışında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="a8204-209">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="a8204-210">Başlangıç parametreleri kalıcı olarak ayarlamak için bunları kayıt defterinde, bu yordamda gösterildiği şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-210">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8204-211">Başlangıç parametreleri eklemek karar vermeden önce bilgi hizmetinize geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a8204-211">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="a8204-212">Başlangıç parametreleri kullanımı kolay olmasına rağmen ve için ayrıştırma ve kullanıcıların kolayca bunları kılabilirsiniz, bulmak ve belgeleri kullanmak kullanıcılar için daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8204-212">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="a8204-213">Genellikle, hizmetiniz birden fazla birkaç başlangıç parametreleri gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-213">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="a8204-214">Her Windows hizmeti kayıt defterinde HKLM\System\CurrentControlSet\services altında olan bir giriş var.</span><span class="sxs-lookup"><span data-stu-id="a8204-214">Every Windows Service has an entry in the registry under HKLM\System\CurrentControlSet\services.</span></span> <span data-ttu-id="a8204-215">Hizmetin anahtarında kullandığınız **parametreleri** hizmetinize erişmek bilgileri depolamak için alt anahtar.</span><span class="sxs-lookup"><span data-stu-id="a8204-215">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="a8204-216">Uygulama yapılandırma dosyaları bir Windows hizmeti için diğer programları türler için yaptığınız şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-216">You can use application configuration files for a Windows Service the same way you do for other types of programs.</span></span> <span data-ttu-id="a8204-217">Örnek kod, bkz: <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8204-217">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>  
  
#### <a name="adding-startup-parameters"></a><span data-ttu-id="a8204-218">Başlangıç parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a8204-218">Adding startup parameters</span></span>  
  
1.  <span data-ttu-id="a8204-219">İçinde `Main` yöntemi Program.cs veya MyNewService.Designer.vb, bir komut satırı bağımsız değişkeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8204-219">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an argument for the command line:</span></span>  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  <span data-ttu-id="a8204-220">Değişiklik `MyNewService` şekilde Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="a8204-220">Change the `MyNewService` constructor as follows:</span></span>  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
    {
        logName = args[1];
    }
    eventLog1 = new System.Diagnostics.EventLog();
    if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
    {
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
    }
    eventLog1.Source = eventSourceName;
    eventLog1.Log = logName;        
}
```  
  
```vb  
Public Sub New(ByVal cmdArgs() As String)
    InitializeComponent()
    Dim eventSourceName As String = "MySource"
    Dim logName As String = "MyNewLog"
    If (cmdArgs.Count() > 0) Then
        eventSourceName = cmdArgs(0)
    End If
    If (cmdArgs.Count() > 1) Then
        logName = cmdArgs(1)
    End If
    eventLog1 = New System.Diagnostics.EventLog()
    If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
    End If
    eventLog1.Source = eventSourceName
    eventLog1.Log = logName
End Sub  
```  
  
<span data-ttu-id="a8204-221">Bu kodu sağlanan başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar ya da bağımsız değişkenler sağlandıysa varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8204-221">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>  
  
3. <span data-ttu-id="a8204-222">Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin `ProjectInstaller` ProjectInstaller.cs veya ProjectInstaller.vb sınıfında:</span><span class="sxs-lookup"><span data-stu-id="a8204-222">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>  
  
```csharp  
protected override void OnBeforeInstall(IDictionary savedState)
{
    string parameter = "MySource1\" \"MyLogFile1";
    Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
    base.OnBeforeInstall(savedState);
}
```

```vb  
Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
    Dim parameter As String = "MySource1"" ""MyLogFile1"
    Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
    MyBase.OnBeforeInstall(savedState)
End Sub  
```  
  
<span data-ttu-id="a8204-223">Bu kod değiştirir **ImagePath** varsayılan parametre değerleri ekleyerek Windows hizmeti için genelde yürütülebilir dosyanın tam yolunu içeren bir kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="a8204-223">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows Service, by adding the default parameter values.</span></span> <span data-ttu-id="a8204-224">Tırnak işaretleri yolun geçici (ve tek tek her parametre çevresinde) hizmetinin doğru şekilde başlatmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8204-224">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="a8204-225">Bu Windows hizmeti için başlangıç parametreleri değiştirmek için kullanıcılar verilen parametrelerini değiştirebilirsiniz **ImagePath** kayıt defteri anahtarı, programlı olarak değiştirin ve kullanıcılara işlevselliği kullanıma sunmak için daha iyi şekilde olmasına rağmen bir kolay şekilde (örneğin, bir yönetim veya yapılandırma yardımcı programı).</span><span class="sxs-lookup"><span data-stu-id="a8204-225">To change the startup parameters for this Windows Service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a><span data-ttu-id="a8204-226">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8204-226">Building the Service</span></span>  
  
#### <a name="to-build-your-service-project"></a><span data-ttu-id="a8204-227">Hizmet projenizi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a8204-227">To build your service project</span></span>  
  
1.  <span data-ttu-id="a8204-228">İçinde **Çözüm Gezgini**projeniz için bağlam menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a8204-228">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span> <span data-ttu-id="a8204-229">Özellik sayfaları projeniz için görünür.</span><span class="sxs-lookup"><span data-stu-id="a8204-229">The property pages for your project  appear.</span></span>  
  
2.  <span data-ttu-id="a8204-230">Uygulama sekmesinde de **Başlangıç nesnesi** listesinde, seçin **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="a8204-230">On the Application tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>  
  
3.  <span data-ttu-id="a8204-231">İçinde **Çözüm Gezgini**projeniz için bağlam menüsünü açın ve ardından **yapı** Projeyi derlemek için (klavye: Ctrl + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="a8204-231">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (Keyboard: Ctrl+Shift+B).</span></span>  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a><span data-ttu-id="a8204-232">Hizmetini yükleme</span><span class="sxs-lookup"><span data-stu-id="a8204-232">Installing the Service</span></span>  
 <span data-ttu-id="a8204-233">Windows hizmeti oluşturduğunuza göre yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-233">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="a8204-234">Bir Windows hizmeti yüklemek için üzerinde yüklemekte bilgisayarda yönetici kimlik bilgileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8204-234">To install a Windows service, you must have administrative credentials on the computer on which you're installing it.</span></span>  
  
#### <a name="to-install-a-windows-service"></a><span data-ttu-id="a8204-235">Bir Windows hizmetini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="a8204-235">To install a Windows Service</span></span>  
  
1.  <span data-ttu-id="a8204-236">Windows 7 ve Windows Server ' açık **Geliştirici komut istemi** altında **Visual Studio Araçları** içinde **Başlat** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a8204-236">In Windows 7 and Windows Server, open the **Developer Command Prompt** under **Visual Studio Tools** in the **Start** menu.</span></span> <span data-ttu-id="a8204-237">Windows 8 veya Windows 8.1 belirleyin **Visual Studio Araçları** döşemesinin **Başlat** ekran ve geliştirici komut istemini yönetici kimlik bilgileriyle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8204-237">In Windows 8 or Windows 8.1, choose the **Visual Studio Tools** tile on the **Start** screen, and then run Developer Command Prompt with administrative credentials.</span></span> <span data-ttu-id="a8204-238">(Fare kullanıyorsanız, sağ tıklayın **Geliştirici komut istemi**ve ardından **yönetici olarak çalıştır**.)</span><span class="sxs-lookup"><span data-stu-id="a8204-238">(If you’re using a mouse, right-click on **Developer Command Prompt**, and then choose **Run as Administrator**.)</span></span>  
  
2.  <span data-ttu-id="a8204-239">Komut İstemi penceresinde projenizin çıktısını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="a8204-239">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="a8204-240">Örneğin, Belgelerim klasörünüzün altında Visual Studio 2013\Projects\MyNewService\bin\Debug yoluna gidin.</span><span class="sxs-lookup"><span data-stu-id="a8204-240">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="a8204-241">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="a8204-241">Enter the following command:</span></span>  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     <span data-ttu-id="a8204-242">Hizmet başarılı bir şekilde yüklenirse, installutil.exe durumu başarılı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="a8204-242">If the service installs successfully, installutil.exe will report success.</span></span> <span data-ttu-id="a8204-243">Sistem InstallUtil.exe bulamadı, bilgisayarınızda yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8204-243">If the system could not find InstallUtil.exe, make sure that it exists on your computer.</span></span> <span data-ttu-id="a8204-244">Bu aracı, klasöre .NET Framework ile kurulmuş `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*.</span><span class="sxs-lookup"><span data-stu-id="a8204-244">This tool is installed with the .NET Framework to the folder `%WINDIR%\Microsoft.NET\Framework[64]\`*framework_version*.</span></span> <span data-ttu-id="a8204-245">Örneğin, .NET Framework 4, 4.5, 4.5.1 ve 4.5.2 32-bit sürümü için varsayılan yolu olan `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="a8204-245">For example, the default path for the 32-bit version of the .NET Framework 4, 4.5, 4.5.1, and 4.5.2 is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span>  
  
     <span data-ttu-id="a8204-246">İnstallutil.exe işlem hatası bildirirse, nedenini bulmak için yükleme günlüğüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a8204-246">If the installutil.exe process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="a8204-247">Varsayılan olarak günlük hizmeti yürütülebilir dosyası ile aynı klasörde şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a8204-247">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="a8204-248">Yükleme başarısız <xref:System.ComponentModel.RunInstallerAttribute> sınıfı mevcut değil `ProjectInstaller` sınıfı, aksi takdirde özniteliği ayarlanmamış `true`, aksi takdirde `ProjectInstaller` sınıfı değil `public`.</span><span class="sxs-lookup"><span data-stu-id="a8204-248">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, or else the attribute is not set to `true`, or else the `ProjectInstaller` class is not `public`.</span></span>  
  
     <span data-ttu-id="a8204-249">Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8204-249">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a><span data-ttu-id="a8204-250">Başlangıç ve hizmet çalışıyor</span><span class="sxs-lookup"><span data-stu-id="a8204-250">Starting and Running the Service</span></span>  
  
#### <a name="to-start-and-stop-your-service"></a><span data-ttu-id="a8204-251">Hizmetinizi başlatmak ve durdurmak için</span><span class="sxs-lookup"><span data-stu-id="a8204-251">To start and stop your service</span></span>  
  
1.  <span data-ttu-id="a8204-252">Windows'da açmak **Başlat** ekran veya **Başlat** menü ve türü `services.msc`.</span><span class="sxs-lookup"><span data-stu-id="a8204-252">In Windows, open the **Start** screen or **Start** menu, and type `services.msc`.</span></span>  
  
     <span data-ttu-id="a8204-253">Artık görmelisiniz **MyNewService** listelenen **Hizmetleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="a8204-253">You should now see **MyNewService** listed in the **Services** window.</span></span>  
  
     <span data-ttu-id="a8204-254">![MyNewService Hizmetleri penceresinde. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span><span class="sxs-lookup"><span data-stu-id="a8204-254">![MyNewService in the Services window.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span></span>  
  
2.  <span data-ttu-id="a8204-255">İçinde **Hizmetleri** penceresinde, hizmetiniz için kısayol menüsünü açın ve ardından **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="a8204-255">In the **Services** window, open the shortcut menu for your service, and then choose **Start**.</span></span>  
  
3.  <span data-ttu-id="a8204-256">Hizmet için kısayol menüsünü açın ve ardından **durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="a8204-256">Open the shortcut menu for the service, and then choose **Stop**.</span></span>  
  
4.  <span data-ttu-id="a8204-257">(İsteğe bağlı) Komut satırından komutları kullanabilirsiniz `net start``ServiceName` ve `net stop``ServiceName` hizmetinizi durdurup başlatın.</span><span class="sxs-lookup"><span data-stu-id="a8204-257">(Optional) From the command line, you can use the commands `net start``ServiceName` and `net stop``ServiceName` to start and stop your service.</span></span>  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a><span data-ttu-id="a8204-258">Hizmetinizin olay günlüğü çıktısını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="a8204-258">To verify the event log output of your service</span></span>  
  
1.  <span data-ttu-id="a8204-259">Visual Studio'da açın **Sunucu Gezgini** (klavye: Ctrl + Alt + S) ve erişim **olay günlüklerini** yerel bilgisayar düğümü.</span><span class="sxs-lookup"><span data-stu-id="a8204-259">In Visual Studio, open **Server Explorer** (Keyboard: Ctrl+Alt+S), and access the **Event Logs** node for the local computer.</span></span>  
  
2.  <span data-ttu-id="a8204-260">Listesine bulun **MyNewLog** (veya **MyLogFile1**, komut satırı bağımsız değişkenleri eklemek için isteğe bağlı yordamı kullandıysanız) genişletin.</span><span class="sxs-lookup"><span data-stu-id="a8204-260">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you used the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="a8204-261">Girdiler görmeniz gerekir (başlatma ve durdurma) iki işlemleri hizmetinizin gerçekleştirdiği.</span><span class="sxs-lookup"><span data-stu-id="a8204-261">You should see entries for the two actions (start and stop) your service has performed.</span></span>  
  
     <span data-ttu-id="a8204-262">![Olay günlüğü girişleri görmek için Olay Görüntüleyicisi'ni kullanın. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span><span class="sxs-lookup"><span data-stu-id="a8204-262">![Use the Event Viewer to see the event log entries.](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span></span>  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a><span data-ttu-id="a8204-263">Bir Windows hizmetini kaldırma</span><span class="sxs-lookup"><span data-stu-id="a8204-263">Uninstalling a Windows Service</span></span>  
  
#### <a name="to-uninstall-your-service"></a><span data-ttu-id="a8204-264">Hizmetinizi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a8204-264">To uninstall your service</span></span>  
  
1.  <span data-ttu-id="a8204-265">Yönetici kimlik bilgileriyle bir geliştirici komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="a8204-265">Open a developer command prompt with administrative credentials.</span></span>  
  
2.  <span data-ttu-id="a8204-266">Komut İstemi penceresinde projenizin çıktısını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="a8204-266">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="a8204-267">Örneğin, Belgelerim klasörünüzün altında Visual Studio 2013\Projects\MyNewService\bin\Debug yoluna gidin.</span><span class="sxs-lookup"><span data-stu-id="a8204-267">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="a8204-268">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="a8204-268">Enter the following command:</span></span>  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     <span data-ttu-id="a8204-269">Hizmet başarıyla kaldırırsa, installutil.exe hizmetinizin başarıyla kaldırıldığını size bildirir.</span><span class="sxs-lookup"><span data-stu-id="a8204-269">If the service uninstalls successfully, installutil.exe will report that your service was successfully removed.</span></span> <span data-ttu-id="a8204-270">Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8204-270">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a8204-271">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a8204-271">Next Steps</span></span>  
 <span data-ttu-id="a8204-272">Diğerleri Windows hizmeti yüklemek için kullanabileceğiniz bir tek başına Kurulum programı oluşturabilirsiniz, ancak ek adımlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a8204-272">You can create a standalone setup program that others can use to install your Windows service, but it requires additional steps.</span></span> <span data-ttu-id="a8204-273">ClickOnce Windows hizmetlerini desteklemediğinden, Yayımlama Sihirbazı'nı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a8204-273">ClickOnce doesn't support Windows services, so you can't use the Publish Wizard.</span></span> <span data-ttu-id="a8204-274">Microsoft'u sağlamadığı InstallShield'ın tam sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-274">You can use a full edition of InstallShield, which Microsoft doesn't provide.</span></span> <span data-ttu-id="a8204-275">InstallShield hakkında daha fazla bilgi için bkz: [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span><span class="sxs-lookup"><span data-stu-id="a8204-275">For more information about InstallShield, see [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span></span> <span data-ttu-id="a8204-276">Aynı zamanda [Windows Installer XML araç takımı](http://go.microsoft.com/fwlink/?LinkId=249067) bir Windows hizmeti için bir yükleyici oluşturmak üzere.</span><span class="sxs-lookup"><span data-stu-id="a8204-276">You can also use the [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=249067) to create an installer for a Windows service.</span></span>  
  
 <span data-ttu-id="a8204-277">Kullanımını keşfedebilirsiniz bir <xref:System.ServiceProcess.ServiceController> bileşeni yüklü olan hizmet komutlar göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8204-277">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you have installed.</span></span>  
  
 <span data-ttu-id="a8204-278">Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulama yüklenirken bir olay günlüğü oluşturmak için bir yükleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8204-278">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="a8204-279">Ayrıca, uygulama kaldırıldığında olay günlüğü de yükleyici tarafından silinecektir.</span><span class="sxs-lookup"><span data-stu-id="a8204-279">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="a8204-280">Daha fazla bilgi için bkz: <xref:System.Diagnostics.EventLogInstaller> başvuru sayfası.</span><span class="sxs-lookup"><span data-stu-id="a8204-280">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8204-281">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8204-281">See Also</span></span>  
 [<span data-ttu-id="a8204-282">Windows Hizmeti Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a8204-282">Windows Service Applications</span></span>](../../../docs/framework/windows-services/index.md)  
 [<span data-ttu-id="a8204-283">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="a8204-283">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="a8204-284">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8204-284">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="a8204-285">Hizmetleri (Windows)</span><span class="sxs-lookup"><span data-stu-id="a8204-285">Services (Windows)</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
