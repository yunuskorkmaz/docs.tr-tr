---
title: 'Öğretici: Bir Windows hizmeti uygulaması oluşturma'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 35ef113acffbebdcd4cb585970e575f17959f75b
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518038"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="fb138-102">Öğretici: Bir Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="fb138-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="fb138-103">Bu makalede, olay günlüğüne bir ileti yazar Visual Studio'da bir Windows hizmeti uygulaması oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fb138-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="fb138-104">Bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="fb138-104">Create a service</span></span>

<span data-ttu-id="fb138-105">Başlamak için projeyi oluşturmak ve hizmetin düzgün çalışması için gerekli değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fb138-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="fb138-106">Visual Studio'dan **dosya** menüsünde **yeni** > **proje** (veya basın **Ctrl** + **Shift**+**N**) açmak için **yeni proje** penceresi.</span><span class="sxs-lookup"><span data-stu-id="fb138-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="fb138-107">Bulun ve seçin **Windows hizmeti (.NET Framework)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="fb138-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="fb138-108">Bunu bulmak için genişletme **yüklü** ve **Visual C#**  veya **Visual Basic**, ardından **Windows Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="fb138-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="fb138-109">Veya, girin *Windows hizmeti* tuşuna basın ve sağ üst köşedeki arama kutusuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fb138-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Visual Studio'da yeni proje iletişim kutusunda Windows hizmet şablonu](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="fb138-111">Görmüyorsanız **Windows hizmeti** şablon yüklemeniz gerekebilir **.NET Masaüstü geliştirmesinden** iş yükü:</span><span class="sxs-lookup"><span data-stu-id="fb138-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >  
   > <span data-ttu-id="fb138-112">İçinde **yeni proje** iletişim kutusunda **açık Visual Studio yükleyicisi** sol alt.</span><span class="sxs-lookup"><span data-stu-id="fb138-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="fb138-113">Seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="fb138-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="fb138-114">İçin **adı**, girin *MyNewService*ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="fb138-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="fb138-115">**Tasarım** sekmesi görünür (**Service1.cs [Design]** veya **gt;service1.vb [Design]**).</span><span class="sxs-lookup"><span data-stu-id="fb138-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>
   
   <span data-ttu-id="fb138-116">Proje şablonu adında bir bileşen sınıfını içeren `Service1` öğesinden devralan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb138-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb138-117">Hizmeti başlatmak için kodu gibi temel hizmet kodunun çoğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="fb138-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="fb138-118">Hizmet yeniden adlandır</span><span class="sxs-lookup"><span data-stu-id="fb138-118">Rename the service</span></span>

<span data-ttu-id="fb138-119">Hizmet Yeniden Adlandır **Service1** için **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="fb138-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="fb138-120">İçinde **Çözüm Gezgini**seçin **Service1.cs**, veya **Service1.vb**ve **Yeniden Adlandır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="fb138-121">Dosyayı Yeniden Adlandır **MyNewService.cs**, veya **MyNewService.vb**ve tuşuna **girin**</span><span class="sxs-lookup"><span data-stu-id="fb138-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="fb138-122">Kod öğesi için tüm başvuruları yeniden adlandırmak istediğiniz soran bir açılır pencere görünür *Service1*.</span><span class="sxs-lookup"><span data-stu-id="fb138-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="fb138-123">Açılır pencerede seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="fb138-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="fb138-124">![Yeniden adlandırma istemi](media/windows-service-rename.png "Windows hizmetini yeniden adlandırma, istemi")</span><span class="sxs-lookup"><span data-stu-id="fb138-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

2. <span data-ttu-id="fb138-125">İçinde **tasarım** sekmesinde **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="fb138-126">Gelen **özellikleri** penceresinde değişiklik **ServiceName** değerini *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="fb138-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="fb138-127">![Hizmet Özellikleri](media/windows-service-properties.png "Windows hizmet özellikleri")</span><span class="sxs-lookup"><span data-stu-id="fb138-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

3. <span data-ttu-id="fb138-128">Seçin **Tümünü Kaydet** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fb138-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="fb138-129">Hizmete özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="fb138-129">Add features to the service</span></span>

<span data-ttu-id="fb138-130">Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb138-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="fb138-131"><xref:System.Diagnostics.EventLog> Bileşen bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fb138-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="fb138-132">Özel olay günlüğü işlevselliği ekleme</span><span class="sxs-lookup"><span data-stu-id="fb138-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="fb138-133">İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="fb138-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="fb138-134">İçinde **araç kutusu**, genişletin **bileşenleri**ve ardından sürükleyin **EventLog** bileşeni **Service1.cs [Design]**, veya  **[Design] gt;service1.vb** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="fb138-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="fb138-135">İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Kodu Görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="fb138-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="fb138-136">Bir özel olay günlüğü'nü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="fb138-136">Define a custom event log.</span></span> <span data-ttu-id="fb138-137">İçin C#, var olan düzenleme `MyNewService()` Oluşturucusu; Visual Basic için ekleme `New()` Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="fb138-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="fb138-138">Ekleme bir `using` ifadesine **MyNewService.cs** (zaten mevcut değilse), veya bir `Imports` deyimi **MyNewService.vb**, için <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="fb138-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="fb138-139">Seçin **Tümünü Kaydet** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fb138-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="fb138-140">Hizmet başlatıldığında ne olacağını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="fb138-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="fb138-141">Kod düzenleyicisinde **MyNewService.cs** veya **MyNewService.vb**, bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi Projeyi oluşturduğunuzda visual Studio, bir boş yöntem tanımını otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fb138-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="fb138-142">Hizmet başlatıldığında, bir giriş olay günlüğüne yazan kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fb138-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="fb138-143">Yoklama</span><span class="sxs-lookup"><span data-stu-id="fb138-143">Polling</span></span>

<span data-ttu-id="fb138-144">Bir hizmet uygulaması, uzun süre çalışan olacak şekilde tasarlandığından, genellikle yoklar veya izler, ayarlanan sistem <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fb138-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="fb138-145">`OnStart` Yöntemi, böylece sistem kilitli değilse hizmetin çalışması başladıktan sonra işletim sistemine döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="fb138-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span> 

<span data-ttu-id="fb138-146">Basit bir yoklama mekanizması kurmak için kullanın <xref:System.Timers.Timer?displayProperty=nameWithType> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="fb138-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="fb138-147">Süreölçer başlatır bir <xref:System.Timers.Timer.Elapsed> düzenli aralıklarla zaman hizmetinizi yapabilir, izleme olayı.</span><span class="sxs-lookup"><span data-stu-id="fb138-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="fb138-148">Kullandığınız <xref:System.Timers.Timer> bileşeni aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="fb138-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="fb138-149">Özelliklerini ayarlama <xref:System.Timers.Timer> bileşeninin `MyNewService.OnStart` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fb138-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="fb138-150">Çağırarak zamanlayıcıyı başlatmak <xref:System.Timers.Timer.Start%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fb138-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="fb138-151">Yoklama mekanizması kurmak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fb138-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="fb138-152">Aşağıdaki kodu ekleyin `MyNewService.OnStart` yoklama mekanizması kurmak için olay:</span><span class="sxs-lookup"><span data-stu-id="fb138-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. <span data-ttu-id="fb138-153">Ekleme bir `using` ifadesine **MyNewService.cs**, veya bir `Imports` ifadesine **MyNewService.vb**, için <xref:System.Timers?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="fb138-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="fb138-154">İçinde `MyNewService` sınıfı, ekleme `OnTimer` işlemek için gereken yöntemini <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> olay:</span><span class="sxs-lookup"><span data-stu-id="fb138-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
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

4. <span data-ttu-id="fb138-155">İçinde `MyNewService` sınıfı, bir üye değişkeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb138-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="fb138-156">Olay günlüğüne yazmak için bir sonraki olay tanıtıcısı aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="fb138-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="fb138-157">Tüm iş ana iş parçacığında çalıştırmak yerine arka plan çalışan iş parçacıkları kullanarak görevler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="fb138-158">Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fb138-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="fb138-159">Hizmet durdurulduğunda ne olacağını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="fb138-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="fb138-160">Bir kod satırı Ekle <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmet durdurulduğunda, olay günlüğüne bir giriş ekler yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fb138-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="fb138-161">Diğer Eylemler için hizmet tanımlama</span><span class="sxs-lookup"><span data-stu-id="fb138-161">Define other actions for the service</span></span>

<span data-ttu-id="fb138-162">Geçersiz kılabilirsiniz <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işlemler tanımlamak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fb138-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> 

<span data-ttu-id="fb138-163">Aşağıdaki kodda gösterildiği nasıl geçersiz kılmanıza da olanak <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yönteminde `MyNewService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="fb138-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="fb138-164">Hizmet durumunu ayarla</span><span class="sxs-lookup"><span data-stu-id="fb138-164">Set service status</span></span>

<span data-ttu-id="fb138-165">Hizmetleri, kendi durumunu rapor [Hizmet Denetimi Yöneticisi](/windows/desktop/Services/service-control-manager) böylece bir kullanıcı bir hizmet doğru şekilde çalışıp çalışmadığını söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="fb138-166">Varsayılan olarak, bir hizmet öğesinden devralan <xref:System.ServiceProcess.ServiceBase> SERVICE_STOPPED SERVICE_PAUSED ve SERVICE_RUNNING durumu ayarları, sınırlı sayıda raporlar.</span><span class="sxs-lookup"><span data-stu-id="fb138-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="fb138-167">Bir hizmetin başlatılması biraz zaman alır, SERVICE_START_PENDING durumunu raporlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="fb138-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span> 

<span data-ttu-id="fb138-168">Windows çağıran kod ekleyerek SERVICE_START_PENDING ve SERVICE_STOP_PENDING durum ayarlarını uygulayabilirsiniz [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevi.</span><span class="sxs-lookup"><span data-stu-id="fb138-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="fb138-169">Hizmet durumu bekleyen ekleme</span><span class="sxs-lookup"><span data-stu-id="fb138-169">Implement service pending status</span></span>

1. <span data-ttu-id="fb138-170">Ekleme bir `using` ifadesine **MyNewService.cs**, veya bir `Imports` ifadesine **MyNewService.vb**, için <xref:System.Runtime.InteropServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="fb138-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="fb138-171">Aşağıdaki kodu ekleyin **MyNewService.cs**, veya **MyNewService.vb**bildirmek için `ServiceState` değerleri ve platform kullanacağınız durum için bir yapı eklemek için çağrı çağırın:</span><span class="sxs-lookup"><span data-stu-id="fb138-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

    > [!NOTE]
    > <span data-ttu-id="fb138-172">Hizmet Denetimi Yöneticisi kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](/windows/desktop/api/winsvc/ns-winsvc-_service_status) bir Windows hizmeti başlatmak veya kapatmak beklenecek ne kadar süre belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="fb138-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="fb138-173">Varsa, `OnStart` ve `OnStop` yöntemleri çalıştırmak uzun, hizmetinizin daha fazla zaman çağırarak isteyebilir `SetServiceStatus` yeniden ile bir artımlı `dwCheckPoint` değeri.</span><span class="sxs-lookup"><span data-stu-id="fb138-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="fb138-174">İçinde `MyNewService` sınıfı, bildirmek [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevi kullanarak [platform çağırma](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="fb138-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="fb138-175">SERVICE_START_PENDING durum uygulamak için aşağıdaki kodu ekleyin başlangıcına <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fb138-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="fb138-176">Kod sonuna ekleyin `OnStart` yöntemi SERVICE_RUNNING için durum ayarlanamadı:</span><span class="sxs-lookup"><span data-stu-id="fb138-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="fb138-177">(İsteğe bağlı) Varsa <xref:System.ServiceProcess.ServiceBase.OnStop%2A> bir uzun süre çalışan yöntemdir, bu yordamı yineleyin `OnStop` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fb138-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="fb138-178">SERVICE_STOP_PENDING durumu uygulamak ve dönüş önce SERVICE_STOPPED durumu `OnStop` yöntemi çıkar.</span><span class="sxs-lookup"><span data-stu-id="fb138-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="fb138-179">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fb138-179">For example:</span></span>

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)    
    ```

## <a name="add-installers-to-the-service"></a><span data-ttu-id="fb138-180">Hizmete yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="fb138-180">Add installers to the service</span></span>

<span data-ttu-id="fb138-181">Çalıştırmadan önce bir Windows hizmeti, hizmet denetimi Yöneticisi ile kaydeden yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb138-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="fb138-182">Yükleyiciler, kayıt ayrıntılarını işlemek için projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb138-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="fb138-183">İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="fb138-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="fb138-184">İçinde **tasarım** görüntüleyebilir, arka plan alanını seçin ve ardından **Yükleyici Ekle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="fb138-185">Varsayılan olarak, Visual Studio adında bir bileşen sınıfını ekler `ProjectInstaller`, projenize iki yükleyici içeriyor.</span><span class="sxs-lookup"><span data-stu-id="fb138-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="fb138-186">Bu yükleyicilerden hizmetiniz ve hizmetin ilişkili işlem içindir.</span><span class="sxs-lookup"><span data-stu-id="fb138-186">These installers are for your service and for the service's associated process.</span></span>

4. <span data-ttu-id="fb138-187">İçinde **tasarım** görüntüleme **ProjectInstaller**seçin **Serviceınstaller1** bir görsel için C# projesi veya **Serviceınstaller1**Visual Basic projesi için ardından **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

5. <span data-ttu-id="fb138-188">İçinde **özellikleri** penceresinde doğrulayın <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="fb138-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="fb138-189">Metne ekleme <xref:System.ServiceProcess.ServiceInstaller.Description%2A> özelliği gibi *örnek hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="fb138-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span> 

     <span data-ttu-id="fb138-190">Bu metin görünür **açıklama** sütununun **Hizmetleri** penceresi ve kullanıcının hizmete açıklar.</span><span class="sxs-lookup"><span data-stu-id="fb138-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="fb138-191">![Hizmetler penceresini hizmet açıklamasında. ](media/windows-service-description.png "Hizmet açıklaması")</span><span class="sxs-lookup"><span data-stu-id="fb138-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

7. <span data-ttu-id="fb138-192">Metne ekleme <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fb138-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="fb138-193">Örneğin, *MyNewService görünen ad*.</span><span class="sxs-lookup"><span data-stu-id="fb138-193">For example, *MyNewService Display Name*.</span></span> 

     <span data-ttu-id="fb138-194">Bu metin görünür **görünen ad** sütununun **Hizmetleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="fb138-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="fb138-195">Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği adı Sistem kullanır (örneğin, adı için kullandığınız `net start` hizmetinizi başlatmak için komut).</span><span class="sxs-lookup"><span data-stu-id="fb138-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

8. <span data-ttu-id="fb138-196">Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini <xref:System.ServiceProcess.ServiceStartMode.Automatic> aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="fb138-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

9. <span data-ttu-id="fb138-197">İşiniz bittiğinde, **özellikleri** windows gibi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="fb138-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="fb138-198">![Bir Windows hizmeti için yükleyici özelliklerini](media/windows-service-installer-properties.png "Windows Installer özellikleri hizmet")</span><span class="sxs-lookup"><span data-stu-id="fb138-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="fb138-199">İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **ServiceProcessInstaller1** bir görsel için C# projesi veya **ServiceProcessInstaller1**  Visual Basic projesi için ardından **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="fb138-200">Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini <xref:System.ServiceProcess.ServiceAccount.LocalSystem> aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="fb138-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span> 

     <span data-ttu-id="fb138-201">Bu ayar hizmetini yükler ve yerel sistem hesabı kullanılarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="fb138-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fb138-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma olanağı dahil olmak üzere geniş izinlere sahip.</span><span class="sxs-lookup"><span data-stu-id="fb138-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="fb138-203">Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="fb138-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="fb138-204">Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> hesabı yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgilerini sunar.</span><span class="sxs-lookup"><span data-stu-id="fb138-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="fb138-205">Bu örnek kullanmaya çalışırsanız başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> olay günlüğüne yazma izni gerektiğinden, hesap.</span><span class="sxs-lookup"><span data-stu-id="fb138-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="fb138-206">Yükleyiciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="fb138-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="fb138-207">(İsteğe bağlı) Başlangıç parametrelerini ayarlayın</span><span class="sxs-lookup"><span data-stu-id="fb138-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="fb138-208">Başlangıç parametreleri eklemek karar vermeden önce hizmetinize bilgi geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fb138-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="fb138-209">Bunlar, kullanımı kolay ve ayrıştırma ve kullanıcı bir kolayca bunları geçersiz kılabilirsiniz ancak bulmak ve belgeleri kullanmak bir kullanıcı için daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fb138-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="fb138-210">Genel olarak, hizmetiniz birkaç taneden fazla yalnızca başlangıç parametre gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası yerine kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="fb138-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span> 

<span data-ttu-id="fb138-211">Bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="fb138-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="fb138-212">İşlem Başlangıç parametrelerine kod eklediğinizde, bir kullanıcı ile kendi özel başlangıç parametreleri hizmet Özellikler penceresindeki hizmetinizi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="fb138-213">Ancak, bu başlangıç parametreleri, hizmetin bir sonraki başlatılışında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="fb138-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="fb138-214">Başlangıç parametreleri kalıcı olarak ayarlamak için kayıt defterinde ayarlanan.</span><span class="sxs-lookup"><span data-stu-id="fb138-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="fb138-215">Her bir Windows hizmeti altında kayıt defteri girdisini sahip **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** alt.</span><span class="sxs-lookup"><span data-stu-id="fb138-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="fb138-216">Her hizmetin alt anahtarı altında kullanın **parametreleri** hizmetinizi erişebileceği bilgileri depolamak için alt.</span><span class="sxs-lookup"><span data-stu-id="fb138-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="fb138-217">Uygulama yapılandırma dosyaları programlar diğer türleri için yaptığınız şekilde bir Windows hizmeti için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="fb138-218">Örnek kod için bkz: <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb138-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="fb138-219">Başlangıç parametreleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="fb138-219">To add startup parameters</span></span>

1. <span data-ttu-id="fb138-220">Seçin **Program.cs**, veya **MyNewService.Designer.vb**, ardından **kodu görüntüle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="fb138-221">İçinde `Main` yöntemi, bir giriş parametresi ekleyin ve hizmet oluşturucuya geçirmek için kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fb138-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="fb138-222">İçinde **MyNewService.cs**, veya **MyNewService.vb**, değiştirme `MyNewService` Oluşturucusu giriş parametresinin şu şekilde işler:</span><span class="sxs-lookup"><span data-stu-id="fb138-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

   ```csharp
   using System.Diagnostics;

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

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

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
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="fb138-223">Bu kod, kullanıcı kaynakları başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fb138-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="fb138-224">Bağımsız değişken sağlanmadıysa varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb138-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="fb138-225">Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin. `ProjectInstaller` sınıfını **ProjectInstaller.cs**, veya **ProjectInstaller.vb**:</span><span class="sxs-lookup"><span data-stu-id="fb138-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="fb138-226">Genellikle, bu değer, Windows hizmeti için yürütülebilir dosyanın tam yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="fb138-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="fb138-227">Hizmet doğru bir şekilde kullanıcı yolu ve tek tek her parametre için tırnak işaretleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb138-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="fb138-228">Bir kullanıcının parametrelerini değiştirip **ImagePath** Windows hizmeti için başlangıç parametreleri değiştirmek için kayıt defteri girişi.</span><span class="sxs-lookup"><span data-stu-id="fb138-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="fb138-229">Ancak, değeri program aracılığıyla değiştirme ve işlevi kullanımı kolay bir şekilde gibi bir yönetim veya yapılandırma yardımcı programını kullanarak ortaya çıkarmak için daha iyi bir yolu olan.</span><span class="sxs-lookup"><span data-stu-id="fb138-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="fb138-230">Derleme hizmeti</span><span class="sxs-lookup"><span data-stu-id="fb138-230">Build the service</span></span>

1. <span data-ttu-id="fb138-231">İçinde **Çözüm Gezgini**, seçin **özellikleri** için kısayol menüsünden **MyNewService** proje.</span><span class="sxs-lookup"><span data-stu-id="fb138-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="fb138-232">Projeniz için özellik sayfaları görünür.</span><span class="sxs-lookup"><span data-stu-id="fb138-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="fb138-233">Üzerinde **uygulama** sekmesinde **Başlangıç nesnesi** listesinde **MyNewService.Program**, veya **Sub Main** Visual Basic projeleri için.</span><span class="sxs-lookup"><span data-stu-id="fb138-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="fb138-234">İçinde projeyi oluşturmak için **Çözüm Gezgini**, seçin **derleme** projeniz için kısayol menüsünden (veya basın **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="fb138-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="fb138-235">Hizmet yükleme</span><span class="sxs-lookup"><span data-stu-id="fb138-235">Install the service</span></span>

<span data-ttu-id="fb138-236">Windows hizmeti oluşturduğunuza göre bunu yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="fb138-237">Bir Windows hizmetini yüklemek için yüklü olduğu bilgisayarda yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb138-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="fb138-238">Açık [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) yönetici kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="fb138-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="fb138-239">Windows gelen **Başlat** menüsünde **VS 2017 için geliştirici komut istemi** Visual Studio klasöründe seçip **daha fazla** > **Çalıştır Yönetici** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="fb138-240">İçinde **Visual Studio için geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin (varsayılan olarak, *\bin\Debug* projenizin alt).</span><span class="sxs-lookup"><span data-stu-id="fb138-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="fb138-241">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="fb138-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="fb138-242">Hizmet başarıyla yüklerse, komut başarılı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb138-242">If the service installs successfully, the command reports success.</span></span> 

    <span data-ttu-id="fb138-243">Sistem bulamazsa *installutil.exe*, bilgisayarınızda mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb138-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="fb138-244">Bu araç, .NET Framework klasörüne yüklenir *% windir%\Microsoft.NET\Framework[64]\\&lt;framework sürümü&gt;*.</span><span class="sxs-lookup"><span data-stu-id="fb138-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="fb138-245">Örneğin, 64-bit sürüm için varsayılan yolu olan *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="fb138-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="fb138-246">Varsa **installutil.exe** işlem başarısız olursa, nedenini bulmak için yükleme günlüğüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fb138-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="fb138-247">Varsayılan olarak, günlük hizmeti yürütülebilir olarak aynı klasörde olduğu.</span><span class="sxs-lookup"><span data-stu-id="fb138-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="fb138-248">Yükleme başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="fb138-248">The installation can fail if:</span></span> 
    - <span data-ttu-id="fb138-249"><xref:System.ComponentModel.RunInstallerAttribute> Sınıfı üzerinde mevcut değilse `ProjectInstaller` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fb138-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    -  <span data-ttu-id="fb138-250">Öznitelik belirlendiğinden `true`.</span><span class="sxs-lookup"><span data-stu-id="fb138-250">The attribute isn't set to `true`.</span></span> 
    - <span data-ttu-id="fb138-251">`ProjectInstaller` Sınıfı değil olarak tanımlanan `public`.</span><span class="sxs-lookup"><span data-stu-id="fb138-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="fb138-252">Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="fb138-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="fb138-253">Başlat ve Çalıştır hizmeti</span><span class="sxs-lookup"><span data-stu-id="fb138-253">Start and run the service</span></span>

1. <span data-ttu-id="fb138-254">Windows içinde açın **Hizmetleri** masaüstü uygulaması.</span><span class="sxs-lookup"><span data-stu-id="fb138-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="fb138-255">Basın **Windows**+**R** açmak için **çalıştırma** kutusuna *services.msc*ve tuşuna **girin** veya **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="fb138-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="fb138-256">Hizmetiniz listede görürsünüz **Hizmetleri**alfabetik olarak ayarladığınız için görünen ada göre gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fb138-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService Hizmetleri penceresinde.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="fb138-258">Hizmeti başlatmak için **Başlat** hizmetin kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="fb138-259">Hizmeti durdurmak için seçin **Durdur** hizmetin kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fb138-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="fb138-260">(İsteğe bağlı) Komutları komut satırından kullanın **net start &lt;hizmet adı&gt;**  ve **net stop &lt;hizmet adı&gt;**  hizmetinizi durdurmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="fb138-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="fb138-261">Hizmetinizin olay günlüğü çıktısını doğrulamak</span><span class="sxs-lookup"><span data-stu-id="fb138-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="fb138-262">Windows içinde açın **Olay Görüntüleyicisi'ni** masaüstü uygulaması.</span><span class="sxs-lookup"><span data-stu-id="fb138-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="fb138-263">Girin *Olay Görüntüleyicisi'ni* çubuğu ve ardından Windows Search'te **Olay Görüntüleyicisi'ni** Arama sonuçlarından.</span><span class="sxs-lookup"><span data-stu-id="fb138-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="fb138-264">Visual Studio'da açıp olay günlüklerini erişebilirsiniz **Sunucu Gezgini** gelen **görünümü** menü (veya basın **Ctrl**+**Alt** + **S**) ve genişletme **olay günlüklerini** düğüm yerel bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="fb138-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="fb138-265">İçinde **Olay Görüntüleyicisi'ni**, genişletme **uygulama ve hizmet günlükleri**.</span><span class="sxs-lookup"><span data-stu-id="fb138-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="fb138-266">Bulun **MyNewLog** (veya **MyLogFile1** komut satırı bağımsız değişkenleri eklemek için yordamı izlediyseniz) genişletin.</span><span class="sxs-lookup"><span data-stu-id="fb138-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="fb138-267">Hizmetinizi gerçekleştirilen iki eylem (başlatma ve durdurma) girişleri görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb138-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi'ni kullanın](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="fb138-269">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="fb138-269">Clean up resources</span></span>

<span data-ttu-id="fb138-270">Windows hizmet uygulaması artık ihtiyacınız kalmadığında, kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb138-270">If you no longer need the Windows service app, you can remove it.</span></span> 

1. <span data-ttu-id="fb138-271">Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="fb138-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="fb138-272">İçinde **Visual Studio için geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="fb138-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="fb138-273">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="fb138-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="fb138-274">Hizmet başarıyla kaldırırsa, hizmetinizin başarıyla kaldırıldığını komutu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb138-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="fb138-275">Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="fb138-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb138-276">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fb138-276">Next steps</span></span>

<span data-ttu-id="fb138-277">Hizmet oluşturduğunuza göre şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fb138-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="fb138-278">Windows hizmetinizi yüklemek için kullanmak üzere başkalarını için tek başına bir Kurulum programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb138-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="fb138-279">Kullanım [WiX Toolset](http://wixtoolset.org/) bir Windows hizmeti için bir yükleyici oluşturmak üzere.</span><span class="sxs-lookup"><span data-stu-id="fb138-279">Use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="fb138-280">Diğer fikir edinmek için bkz: [Yükleyici paketi oluştur](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="fb138-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="fb138-281">Keşfedin <xref:System.ServiceProcess.ServiceController> bileşenin yüklediğiniz hizmete komutlar göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb138-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="fb138-282">Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulamayı yüklediğinizde, bir olay günlüğü oluşturmak için bir yükleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb138-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="fb138-283">Uygulamayı kaldırdığınızda olay günlüğü de yükleyici tarafından silindi.</span><span class="sxs-lookup"><span data-stu-id="fb138-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="fb138-284">Daha fazla bilgi için bkz. <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="fb138-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb138-285">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb138-285">See also</span></span>

- [<span data-ttu-id="fb138-286">Windows hizmet uygulamaları</span><span class="sxs-lookup"><span data-stu-id="fb138-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="fb138-287">Windows hizmeti uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="fb138-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="fb138-288">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fb138-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="fb138-289">Hizmetleri (Windows)</span><span class="sxs-lookup"><span data-stu-id="fb138-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
