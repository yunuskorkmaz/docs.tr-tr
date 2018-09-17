---
title: Visual Studio'da bir Windows hizmeti uygulaması oluşturma
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677376"
---
# <a name="walkthrough-create-a-windows-service-app"></a><span data-ttu-id="8bc92-102">İzlenecek yol: bir Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bc92-102">Walkthrough: Create a Windows service app</span></span>

<span data-ttu-id="8bc92-103">Bu makalede, Visual Studio'da bir olay günlüğüne iletiler yazan basit bir Windows hizmeti uygulaması oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-103">This article demonstrates how to create a simple Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="8bc92-104">Bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bc92-104">Create a service</span></span>

<span data-ttu-id="8bc92-105">Başlamak için projeyi oluşturmak ve hizmetin düzgün çalışması için gerekli olan değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8bc92-105">To begin, create the project and set values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="8bc92-106">Visual Studio'da menü çubuğunda, **dosya** > **yeni** > **proje** (veya basın **Ctrl** + **Shift**+**N**) açmak için **yeni proje** iletişim.</span><span class="sxs-lookup"><span data-stu-id="8bc92-106">In Visual Studio, on the menu bar, choose **File** > **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** dialog.</span></span>

2. <span data-ttu-id="8bc92-107">Bulun ve seçin **Windows hizmeti** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="8bc92-107">Navigate to and select the **Windows Service** project template.</span></span> <span data-ttu-id="8bc92-108">Genişletin **yüklü** > [**Visual C#** veya **Visual Basic**] > **Windows Masaüstü**, veya tür **Windowshizmeti** sağ üst köşedeki arama kutusuna.</span><span class="sxs-lookup"><span data-stu-id="8bc92-108">Expand **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, or type **Windows Service** in the search box on the upper right.</span></span>

   ![Visual Studio'da yeni proje iletişim kutusunda Windows hizmet şablonu](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="8bc92-110">Görmüyorsanız **Windows hizmeti** şablon yüklemeniz gerekebilir **.NET Masaüstü geliştirmesinden** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="8bc92-110">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload.</span></span> <span data-ttu-id="8bc92-111">İçinde **yeni proje** iletişim kutusunda bağlantısına tıklayın **açık Visual Studio yükleyicisi** sol alt.</span><span class="sxs-lookup"><span data-stu-id="8bc92-111">In the **New Project** dialog, click the link that says **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="8bc92-112">İçinde **Visual Studio yükleyicisi**seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-112">In **Visual Studio Installer**, select the **.NET desktop development** workload and then choose **Modify**.</span></span>

3. <span data-ttu-id="8bc92-113">Projeyi adlandırın **MyNewService**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-113">Name the project **MyNewService**, and then choose **OK**.</span></span>

   <span data-ttu-id="8bc92-114">Proje şablonu adında bir bileşen sınıfını içeren `Service1` öğesinden devralan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8bc92-114">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8bc92-115">Hizmeti başlatmak için kodu gibi temel hizmet kodunun çoğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-115">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="8bc92-116">Hizmet yeniden adlandır</span><span class="sxs-lookup"><span data-stu-id="8bc92-116">Rename the service</span></span>

<span data-ttu-id="8bc92-117">Hizmet Yeniden Adlandır **Service1** için **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-117">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="8bc92-118">İçinde **tasarım** Service1.cs (veya gt;service1.vb) görünümüne tıklayın bağlantısını **kod görünümüne geçin**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-118">In the **Design** view for Service1.cs (or Service1.vb), click the link to **switch to code view**.</span></span> <span data-ttu-id="8bc92-119">Sağ **Service1** seçip **Yeniden Adlandır** bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="8bc92-119">Right-click on **Service1** and select **Rename** from the context menu.</span></span> <span data-ttu-id="8bc92-120">ENTER **MyNewService** ve tuşuna **Enter** veya **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-120">Enter **MyNewService** and then press **Enter** or click **Apply**.</span></span>

2. <span data-ttu-id="8bc92-121">İçinde **özellikleri** penceresi **Service1.cs [Design]** veya **gt;service1.vb [Design]**, değiştirme **ServiceName** değerine**MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-121">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, change the **ServiceName** value to **MyNewService**.</span></span>

3. <span data-ttu-id="8bc92-122">İçinde **Çözüm Gezgini**, yeniden adlandırma **Service1.cs** için **MyNewService.cs**, veya yeniden adlandırmak **Service1.vb** için  **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-122">In **Solution Explorer**, rename **Service1.cs** to **MyNewService.cs**, or rename **Service1.vb** to **MyNewService.vb**.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="8bc92-123">Hizmete özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="8bc92-123">Add features to the service</span></span>

<span data-ttu-id="8bc92-124">Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bc92-124">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="8bc92-125">Olay günlükleri, Windows hizmetleri ile hiçbir şekilde ilişkili değildir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-125">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="8bc92-126"><xref:System.Diagnostics.EventLog> Bileşen kullanılan bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnek burada.</span><span class="sxs-lookup"><span data-stu-id="8bc92-126">The <xref:System.Diagnostics.EventLog> component is used here as an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="8bc92-127">Özel olay günlüğü işlevselliği ekleme</span><span class="sxs-lookup"><span data-stu-id="8bc92-127">Add custom event log functionality</span></span>

1. <span data-ttu-id="8bc92-128">İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-128">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="8bc92-129">Gelen **bileşenleri** bölümünü **araç kutusu**, sürükleyin bir <xref:System.Diagnostics.EventLog> tasarımcıya bileşeni.</span><span class="sxs-lookup"><span data-stu-id="8bc92-129">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>

3. <span data-ttu-id="8bc92-130">İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Kodu Görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-130">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>

4. <span data-ttu-id="8bc92-131">Özel bir olay günlüğü tanımlamak için oluşturucuyu Düzenle:</span><span class="sxs-lookup"><span data-stu-id="8bc92-131">Edit the constructor to define a custom event log:</span></span>

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="8bc92-132">Hizmet başlatıldığında ne olacağını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="8bc92-132">Define what occurs when the service starts</span></span>

<span data-ttu-id="8bc92-133">Kod Düzenleyicisi'nde bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> projeyi oluşturduğunuzda otomatik olarak geçersiz kılınan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bc92-133">In the code editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project.</span></span> <span data-ttu-id="8bc92-134">Hizmet başlatıldığında, bir giriş olay günlüğüne yazan kod satırını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bc92-134">Add a line of code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

<span data-ttu-id="8bc92-135">Bir hizmet uygulaması, uzun süre çalışan, genellikle yoklar veya sistemde izleyen bir şey olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bc92-135">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="8bc92-136">İzleme ayarlanır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bc92-136">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="8bc92-137">Ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> aslında izleme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-137">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="8bc92-138"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi hizmetin çalışması başladıktan sonra işletim sistemine döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-138">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="8bc92-139">Sonsuza kadar döngü veya engelleme gerçekleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-139">It must not loop forever or block.</span></span> <span data-ttu-id="8bc92-140">Basit bir yoklama mekanizması kurmak için kullanabileceğiniz <xref:System.Timers.Timer?displayProperty=nameWithType> aşağıdaki gibi bileşeni: içinde <xref:System.ServiceProcess.ServiceBase.OnStart%2A> bileşen üzerinde parametreleri ayarlayın ve ardından yöntemi <xref:System.Timers.Timer.Enabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="8bc92-140">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="8bc92-141">Zamanlayıcı, aynı zamanda hizmetiniz izlemeyi yapabileceği kodunuzda olayları periyodik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="8bc92-141">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="8bc92-142">Bunu yapmak için aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8bc92-142">You can use the following code to do this:</span></span>

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

<span data-ttu-id="8bc92-143">Üye değişkeni sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bc92-143">Add a member variable to the class.</span></span> <span data-ttu-id="8bc92-144">Bu, olay günlüğüne yazmak için sonraki olayı tanımlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-144">It contains the identifier of the next event to write into the event log.</span></span>

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

<span data-ttu-id="8bc92-145">Zamanlayıcı olayı işlemek için yeni bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bc92-145">Add a new method to handle the timer event:</span></span>

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

<span data-ttu-id="8bc92-146">Tüm iş ana iş parçacığında çalıştırmak yerine arka plan çalışan iş parçacıkları kullanarak görevleri gerçekleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-146">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="8bc92-147">Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="8bc92-147">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="8bc92-148">Hizmet durdurulduğunda ne olacağını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="8bc92-148">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="8bc92-149">Bir kod satırını ekleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmet durdurulduğunda, olay günlüğüne bir giriş ekler yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8bc92-149">Add a line of code to the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="8bc92-150">Diğer Eylemler için hizmet tanımlama</span><span class="sxs-lookup"><span data-stu-id="8bc92-150">Define other actions for the service</span></span>

<span data-ttu-id="8bc92-151">Geçersiz kılabilirsiniz <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işlemler tanımlamak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8bc92-151">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> <span data-ttu-id="8bc92-152">Aşağıdaki kod nasıl geçersiz gösterir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8bc92-152">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

<span data-ttu-id="8bc92-153">Bazı özel eylemler ile bir Windows hizmeti yüklendiğinde ortaya zorunda <xref:System.Configuration.Install.Installer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8bc92-153">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="8bc92-154">Visual Studio, bu yükleyicileri bir Windows hizmeti için özel olarak oluşturabilir ve sonra da projenize ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-154">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>

## <a name="set-service-status"></a><span data-ttu-id="8bc92-155">Hizmet durumunu ayarla</span><span class="sxs-lookup"><span data-stu-id="8bc92-155">Set service status</span></span>

<span data-ttu-id="8bc92-156">Böylece kullanıcılar bir hizmet doğru şekilde çalışıp çalışmadığını söyleyebilirsiniz Hizmetleri durumlarını hizmet denetimi yöneticisine bildirir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-156">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="8bc92-157">Varsayılan olarak, devralınan Hizmetleri <xref:System.ServiceProcess.ServiceBase> rapor durdurulmuş, duraklatılmış ve çalıştıran sınırlı sayıda dahil olmak üzere durumu ayarları.</span><span class="sxs-lookup"><span data-stu-id="8bc92-157">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="8bc92-158">Bunun başlatmak için bir başlangıç bekleme durumu raporlamak faydalı olabilir ancak bir hizmet biraz uzun sürerse.</span><span class="sxs-lookup"><span data-stu-id="8bc92-158">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="8bc92-159">Windows çağıran kod ekleyerek de bekleyen başlatmak ve durdurmak bekleyen durum ayarlarını uygulayabilirsiniz [artırılmış işlevi](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="8bc92-159">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>

<span data-ttu-id="8bc92-160">Hizmet Durumu Beklemede uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="8bc92-160">To implement service pending status:</span></span>

1. <span data-ttu-id="8bc92-161">Ekleme bir `using` deyimi veya `Imports` bildirimi <xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs veya MyNewService.vb dosyasında ad alanı:</span><span class="sxs-lookup"><span data-stu-id="8bc92-161">Add a `using` statement or `Imports` declaration for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="8bc92-162">Bildirmek için MyNewService.cs için aşağıdaki kodu ekleyin `ServiceState` değerleri ve platform kullanacağınız durum için bir yapı eklemek için çağrı çağırın:</span><span class="sxs-lookup"><span data-stu-id="8bc92-162">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

3. <span data-ttu-id="8bc92-163">Şimdi, `MyNewService` sınıfı, bildirmek [artırılmış işlevi](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) kullanarak [platform çağırma](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="8bc92-163">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="8bc92-164">Başlangıç bekleme durumu uygulamak için aşağıdaki kodu ekleyin başlangıcına <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8bc92-164">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="8bc92-165">Sonunda çalışan durum için kod ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bc92-165">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>

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

6. <span data-ttu-id="8bc92-166">(İsteğe bağlı) İçin bu yordamı yineleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bc92-166">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="8bc92-167">[Hizmet Denetimi Yöneticisi](/windows/desktop/Services/service-control-manager) kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](/windows/desktop/api/winsvc/ns-winsvc-_service_status) bir Windows hizmeti başlatmak veya kapatmak beklenecek ne kadar süre belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="8bc92-167">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="8bc92-168">Varsa, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri çalıştırmak uzun, hizmetinizin daha fazla zaman çağırarak isteyebilir [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) yeniden ile bir artımlı `dwCheckPoint` değeri.</span><span class="sxs-lookup"><span data-stu-id="8bc92-168">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>

## <a name="add-installers-to-the-service"></a><span data-ttu-id="8bc92-169">Hizmete yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="8bc92-169">Add installers to the service</span></span>

<span data-ttu-id="8bc92-170">Bir Windows hizmeti çalıştırmadan önce Hizmet Denetimi Yöneticisi ile kaydeden yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-170">Before you can run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="8bc92-171">Kayıt ayrıntıları işleyen projenize yükleyicileri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-171">You can add installers to your project that handle the registration details.</span></span>

1. <span data-ttu-id="8bc92-172">İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-172">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="8bc92-173">Hizmetin herhangi bir içeriğini değil de, hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8bc92-173">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>

3. <span data-ttu-id="8bc92-174">Tasarımcı penceresini (bir işaretleme penceresi içine sağ kullanıyorsanız) için bağlam menüsünü açın ve ardından **Yükleyici Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-174">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>

   <span data-ttu-id="8bc92-175">Varsayılan olarak, projenize iki yükleyici içeren bir bileşen sınıfı eklenir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-175">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="8bc92-176">Bileşene **ProjectInstaller**ve içerdiği yükleyiciler hizmetinize yükleyici ve yükleyici hizmeti için işlem ilişkili.</span><span class="sxs-lookup"><span data-stu-id="8bc92-176">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>

4. <span data-ttu-id="8bc92-177">İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **Serviceınstaller1** Visual C# proje için veya **Serviceınstaller1** bir görsel için Temel Proje.</span><span class="sxs-lookup"><span data-stu-id="8bc92-177">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>

5. <span data-ttu-id="8bc92-178">İçinde **özellikleri** penceresinde emin <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-178">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="8bc92-179">Ayarlama **açıklama** özelliğini "Örnek hizmeti" gibi şeyler.</span><span class="sxs-lookup"><span data-stu-id="8bc92-179">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="8bc92-180">Bu metin hizmetleri penceresinde görüntülenmesi ve kullanıcının hizmetinizi tanımlamak ve ne için kullanıldığını anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8bc92-180">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>

7. <span data-ttu-id="8bc92-181">Ayarlama <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Hizmetleri penceresinde görünmesini istediğiniz metni özelliğini **adı** sütun.</span><span class="sxs-lookup"><span data-stu-id="8bc92-181">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="8bc92-182">Örneğin, "MyNewService görünen ad" girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-182">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="8bc92-183">Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sistem tarafından kullanılan ad özelliği (örneğin, kullandığınızda `net start` hizmetinizi başlatmak için komut).</span><span class="sxs-lookup"><span data-stu-id="8bc92-183">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>

8. <span data-ttu-id="8bc92-184">Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="8bc92-184">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>

     <span data-ttu-id="8bc92-185">![Bir Windows hizmeti için yükleyici özelliklerini](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="8bc92-185">![Installer Properties for a Windows service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>

9. <span data-ttu-id="8bc92-186">Tasarımcısı'nda **ServiceProcessInstaller1** Visual C# proje için veya **ServiceProcessInstaller1** Visual Basic projesi için.</span><span class="sxs-lookup"><span data-stu-id="8bc92-186">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="8bc92-187">Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="8bc92-187">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="8bc92-188">Bu hizmet yüklü olmasını ve yerel sistem hesabı kullanarak çalıştırılacak neden olur.</span><span class="sxs-lookup"><span data-stu-id="8bc92-188">This causes the service to be installed and to run using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8bc92-189"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma olanağı dahil olmak üzere geniş izinlere sahip.</span><span class="sxs-lookup"><span data-stu-id="8bc92-189">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="8bc92-190">Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-190">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="8bc92-191">Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> hesabı yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgilerini sunar.</span><span class="sxs-lookup"><span data-stu-id="8bc92-191">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="8bc92-192">Bu örnek kullanmaya çalışırsanız başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> olay günlüğüne yazma izni gerektiğinden, hesap.</span><span class="sxs-lookup"><span data-stu-id="8bc92-192">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="8bc92-193">Yükleyiciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: ekleme yükleyiciler hizmetinize uygulama](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="8bc92-193">For more information about installers, see [How to: Add Installers to Your service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="8bc92-194">(İsteğe bağlı) Başlangıç parametrelerini ayarlayın</span><span class="sxs-lookup"><span data-stu-id="8bc92-194">(Optional) Set startup parameters</span></span>

<span data-ttu-id="8bc92-195">Diğer herhangi bir yürütülebilir gibi bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-195">A Windows service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="8bc92-196">İşlem Başlangıç parametrelerine kod eklediğinizde, kullanıcılar Windows Denetim Masası'ndaki Hizmetler penceresini kullanarak kendi özel başlatma parametrelerle hizmetinizi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-196">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="8bc92-197">Ancak, bu başlangıç parametreleri hizmet bir sonraki başlatılışında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-197">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="8bc92-198">Başlangıç parametreleri kalıcı olarak ayarlamak için bunları kayıt defterinde, bu yordamda gösterildiği gibi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-198">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="8bc92-199">Başlangıç parametreleri eklemek karar vermeden önce hizmetinize bilgi geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8bc92-199">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="8bc92-200">Başlangıç parametreleri kullanımı kolay olsa ve için ayrıştırma ve kullanıcıların kolayca bunları geçersiz kılabilirsiniz, kullanıcıların keşfetmesi ve kullanması belgeleri daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-200">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="8bc92-201">Genel olarak, hizmetiniz birkaç taneden fazla yalnızca başlangıç parametre gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-201">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="8bc92-202">Her bir Windows hizmetinde altında kayıt defterinde girişi olmayan **HKLM\System\CurrentControlSet\services**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-202">Every Windows service has an entry in the registry under **HKLM\System\CurrentControlSet\services**.</span></span> <span data-ttu-id="8bc92-203">Hizmet anahtarı altında kullanabileceğiniz **parametreleri** hizmetinizi erişebileceği bilgileri depolamak için alt.</span><span class="sxs-lookup"><span data-stu-id="8bc92-203">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="8bc92-204">Uygulama yapılandırma dosyaları programlar diğer türleri için yaptığınız şekilde bir Windows hizmeti için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-204">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="8bc92-205">Örnek kod için bkz: <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bc92-205">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>

<span data-ttu-id="8bc92-206">Başlangıç parametreleri eklemek için:</span><span class="sxs-lookup"><span data-stu-id="8bc92-206">To add startup parameters:</span></span>

1. <span data-ttu-id="8bc92-207">İçinde `Main` yöntemi Program.cs veya MyNewService.Designer.vb, hizmet oluşturucuya geçirilecek giriş parametresi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bc92-207">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an input parameter to pass to the service constructor:</span></span>

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. <span data-ttu-id="8bc92-208">Değişiklik `MyNewService` Oluşturucu aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="8bc92-208">Change the `MyNewService` constructor as follows:</span></span>

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
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

   <span data-ttu-id="8bc92-209">Bu kod, sağlanan başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar veya herhangi bir bağımsız değişken sağlanmadıysa varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bc92-209">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>

3. <span data-ttu-id="8bc92-210">Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin. `ProjectInstaller` ProjectInstaller.cs veya ProjectInstaller.vb sınıfı:</span><span class="sxs-lookup"><span data-stu-id="8bc92-210">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>

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

   <span data-ttu-id="8bc92-211">Bu kodu değiştirir **ImagePath** genellikle varsayılan parametre değerlerini ekleyerek Windows hizmeti için yürütülebilir dosyanın tam yolunu içeren kayıt defteri anahtarı.</span><span class="sxs-lookup"><span data-stu-id="8bc92-211">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows service, by adding the default parameter values.</span></span> <span data-ttu-id="8bc92-212">Yolun (ve tek tek her parametreyi) tırnak işareti, hizmetin doğru şekilde başlatmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-212">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="8bc92-213">Bu Windows hizmeti için başlangıç parametreleri değiştirmek için kullanıcıların belirtilen parametrelerle değiştirip **ImagePath** kayıt defteri anahtarı, program aracılığıyla değiştirme ve kullanıcılara işlevselliği göstermek için daha iyi şekilde olmasına rağmen bir kolay bir yolla (örneğin, bir yönetim veya yapılandırma yardımcı programını kullanarak).</span><span class="sxs-lookup"><span data-stu-id="8bc92-213">To change the startup parameters for this Windows service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>

## <a name="build-the-service"></a><span data-ttu-id="8bc92-214">Derleme hizmeti</span><span class="sxs-lookup"><span data-stu-id="8bc92-214">Build the service</span></span>

1. <span data-ttu-id="8bc92-215">İçinde **Çözüm Gezgini**, projeniz için bağlam menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-215">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span>

   <span data-ttu-id="8bc92-216">Projeniz için özellik sayfaları görünür.</span><span class="sxs-lookup"><span data-stu-id="8bc92-216">The property pages for your project appear.</span></span>

2. <span data-ttu-id="8bc92-217">Üzerinde **uygulama** sekmesinde **Başlangıç nesnesi** listesinde **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-217">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>

3. <span data-ttu-id="8bc92-218">İçinde **Çözüm Gezgini**, projeniz için bağlam menüsünü açın ve ardından **derleme** Projeyi derlemek için (veya basın **Ctrl**+**kaydırma**  + **B**).</span><span class="sxs-lookup"><span data-stu-id="8bc92-218">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="8bc92-219">Hizmet yükleme</span><span class="sxs-lookup"><span data-stu-id="8bc92-219">Install the service</span></span>

<span data-ttu-id="8bc92-220">Windows hizmeti oluşturduğunuza göre bunu yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-220">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="8bc92-221">Bir Windows hizmetini yüklemek için yükleme yaptığınız bilgisayarda yönetici kimlik bilgileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bc92-221">To install a Windows service, you must have administrator credentials on the computer on which you're installing it.</span></span>

1. <span data-ttu-id="8bc92-222">Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="8bc92-222">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span> <span data-ttu-id="8bc92-223">Fare kullanıyorsanız, sağ **VS 2017 için geliştirici komut istemi** içinde Windows Başlat menüsünü ve ardından **daha fazla** > **yönetici olarak çalıştır** .</span><span class="sxs-lookup"><span data-stu-id="8bc92-223">If you’re using a mouse, right-click on **Developer Command Prompt for VS 2017** in the Windows Start menu, and then choose **More** > **Run as Administrator**.</span></span>

2. <span data-ttu-id="8bc92-224">İçinde **Geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin (varsayılan olarak, bu *\bin\Debug* projenizin alt).</span><span class="sxs-lookup"><span data-stu-id="8bc92-224">In the **Developer Command Prompt** window, navigate to the folder that contains your project's output (by default, it's the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="8bc92-225">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="8bc92-225">Enter the following command:</span></span>

    ```shell
    installutil.exe MyNewService.exe
    ```

    <span data-ttu-id="8bc92-226">Hizmet başarıyla yüklerse **installutil.exe** başarılı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-226">If the service installs successfully, **installutil.exe** reports success.</span></span> <span data-ttu-id="8bc92-227">Sistem bulunamadı, **InstallUtil.exe**, bilgisayarınızda mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8bc92-227">If the system could not find **InstallUtil.exe**, make sure that it exists on your computer.</span></span> <span data-ttu-id="8bc92-228">Bu araç, .NET Framework klasörüne yüklenir *% windir%\Microsoft.NET\Framework[64]\\[framework sürümü]*.</span><span class="sxs-lookup"><span data-stu-id="8bc92-228">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\[framework version]*.</span></span> <span data-ttu-id="8bc92-229">Örneğin, 32-bit sürüm için varsayılan yolu olan *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="8bc92-229">For example, the default path for the 32-bit version is *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="8bc92-230">Varsa **installutil.exe** işlem hata raporları, nedenini bulmak için yükleme günlüğüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8bc92-230">If the **installutil.exe** process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="8bc92-231">Varsayılan olarak günlük hizmeti yürütülebilir dosyası ile aynı klasörde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8bc92-231">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="8bc92-232">Yükleme başarısız olabilir <xref:System.ComponentModel.RunInstallerAttribute> sınıfı üzerinde mevcut değil `ProjectInstaller` öznitelik olarak ayarlanmazsa, sınıf **true**, veya `ProjectInstaller` sınıfı işaretlenmemiş **genel**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-232">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, if the attribute is not set to **true**, or if the `ProjectInstaller` class is not marked **public**.</span></span>

<span data-ttu-id="8bc92-233">Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="8bc92-233">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="8bc92-234">Başlat ve Çalıştır hizmeti</span><span class="sxs-lookup"><span data-stu-id="8bc92-234">Start and run the service</span></span>

1. <span data-ttu-id="8bc92-235">Windows içinde açın **Hizmetleri** masaüstü uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8bc92-235">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="8bc92-236">Basın **Windows**+**R** açmak için **çalıştırma** kutusuna ve ardından girin **services.msc** basın **Enter**  veya **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-236">Press **Windows**+**R** to open the **Run** box, and then enter **services.msc** and press **Enter** or click **OK**.</span></span>

     <span data-ttu-id="8bc92-237">Hizmetiniz listede görürsünüz **Hizmetleri**alfabetik olarak ayarladığınız için görünen ada göre gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-237">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService Hizmetleri penceresinde.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="8bc92-239">İçinde **Hizmetleri**, hizmetiniz için kısayol menüsünü açın ve ardından **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-239">In **Services**, open the shortcut menu for your service, and then choose **Start**.</span></span>

3. <span data-ttu-id="8bc92-240">Hizmeti durdurmak için hizmet için kısayol menüsünü açın ve ardından **Durdur**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-240">To stop the service, open the shortcut menu for the service, and then choose **Stop**.</span></span>

4. <span data-ttu-id="8bc92-241">(İsteğe bağlı) Komut satırından komutları kullanabilirsiniz `net start ServiceName` ve `net stop ServiceName` hizmetinizi durdurmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="8bc92-241">(Optional) From the command line, you can use the commands `net start ServiceName` and `net stop ServiceName` to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="8bc92-242">Hizmetinizin olay günlüğü çıktısını doğrulamak</span><span class="sxs-lookup"><span data-stu-id="8bc92-242">Verify the event log output of your service</span></span>

1. <span data-ttu-id="8bc92-243">Açık **Olay Görüntüleyicisi'ni** türüne başlatarak **Olay Görüntüleyicisi'ni** Windows görev çubuğunda ve sonra arama kutusuna **Olay Görüntüleyicisi'ni** Arama sonuçlarından.</span><span class="sxs-lookup"><span data-stu-id="8bc92-243">Open **Event Viewer** by starting to type **Event Viewer** in the search box on the Windows task bar, and then selecting **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="8bc92-244">Visual Studio'da açıp olay günlüklerini erişebilirsiniz **Sunucu Gezgini** (klavye: **Ctrl**+**Alt**+**S**) ve genişletme **olay günlüklerini** düğüm yerel bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="8bc92-244">In Visual Studio, you can access event logs by opening **Server Explorer** (Keyboard: **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="8bc92-245">İçinde **Olay Görüntüleyicisi'ni**, genişletme **uygulama ve hizmet günlükleri**.</span><span class="sxs-lookup"><span data-stu-id="8bc92-245">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="8bc92-246">Bulun **MyNewLog** (veya **MyLogFile1**, komut satırı bağımsız değişkenleri eklemek için isteğe bağlı yordamı izlediyseniz) genişletin.</span><span class="sxs-lookup"><span data-stu-id="8bc92-246">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you followed the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="8bc92-247">Hizmetinizi gerçekleştirilen iki eylem (başlatma ve durdurma) girişleri görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-247">You should see entries for the two actions (start and stop) that your service performed.</span></span>

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi'ni kullanın](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a><span data-ttu-id="8bc92-249">Hizmeti Kaldır</span><span class="sxs-lookup"><span data-stu-id="8bc92-249">Uninstall the service</span></span>

1. <span data-ttu-id="8bc92-250">Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="8bc92-250">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="8bc92-251">Komut İstemi penceresinde, projenizin çıktısını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="8bc92-251">In the command prompt window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="8bc92-252">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="8bc92-252">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="8bc92-253">Hizmet başarıyla kaldırırsa **installutil.exe** hizmetinizin başarıyla kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-253">If the service uninstalls successfully, **installutil.exe** reports that your service was successfully removed.</span></span> <span data-ttu-id="8bc92-254">Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="8bc92-254">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bc92-255">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8bc92-255">Next steps</span></span>

<span data-ttu-id="8bc92-256">Hizmet oluşturduğunuza göre diğerleri Windows hizmetinizi yüklemek için kullanabileceğiniz tek başına Kurulum programını oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-256">Now that you've created the service, you might want to create a standalone setup program that others can use to install your Windows service.</span></span> <span data-ttu-id="8bc92-257">ClickOnce Windows hizmetlerini desteklemiyor, ancak kullanabileceğiniz [WiX Toolset](http://wixtoolset.org/) bir Windows hizmeti için bir yükleyici oluşturmak üzere.</span><span class="sxs-lookup"><span data-stu-id="8bc92-257">ClickOnce doesn't support Windows services, but you can use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="8bc92-258">Diğer fikir edinmek için bkz: [Yükleyici paketi oluştur](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="8bc92-258">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

<span data-ttu-id="8bc92-259">Kullanımını keşfedebilirsiniz bir <xref:System.ServiceProcess.ServiceController> bileşenin yüklediğiniz hizmete komutlar göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bc92-259">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

<span data-ttu-id="8bc92-260">Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulama yüklenirken bir olay günlüğü oluşturmak için bir yükleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-260">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="8bc92-261">Ayrıca, uygulama kaldırıldığında olay günlüğü de yükleyici tarafından silinecektir.</span><span class="sxs-lookup"><span data-stu-id="8bc92-261">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="8bc92-262">Daha fazla bilgi için <xref:System.Diagnostics.EventLogInstaller> başvuru sayfası.</span><span class="sxs-lookup"><span data-stu-id="8bc92-262">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bc92-263">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bc92-263">See also</span></span>

- [<span data-ttu-id="8bc92-264">Windows hizmet uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8bc92-264">Windows service applications</span></span>](../../../docs/framework/windows-services/index.md)
- [<span data-ttu-id="8bc92-265">Windows hizmeti uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="8bc92-265">Introduction to Windows service applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="8bc92-266">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8bc92-266">How to: Debug Windows service applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="8bc92-267">Hizmetleri (Windows)</span><span class="sxs-lookup"><span data-stu-id="8bc92-267">Services (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
