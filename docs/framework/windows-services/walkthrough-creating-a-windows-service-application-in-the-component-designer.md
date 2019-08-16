---
title: 'Öğretici: Windows hizmet uygulaması oluşturma'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: df2a99b6fe288cfa8b8a5d60bb127849323ed3a9
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545313"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="380e3-102">Öğretici: Windows hizmet uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="380e3-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="380e3-103">Bu makalede, Visual Studio 'da bir olay günlüğüne ileti yazan bir Windows hizmet uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="380e3-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="380e3-104">Bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="380e3-104">Create a service</span></span>

<span data-ttu-id="380e3-105">Başlamak için projeyi oluşturun ve hizmetin düzgün çalışması için gereken değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="380e3-106">Visual Studio **Dosya** menüsünden **Yeni** > **Proje** ' yi seçin (veya **CTRL**+**SHIFT**+**N**tuşlarına basarak) **Yeni proje** penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="380e3-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="380e3-107">' A gidin ve **Windows hizmeti (.NET Framework)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="380e3-108">Bunu bulmak için, **yüklü** ve **Visual C#**  veya **Visual Basic**' i genişletin ve **Windows Masaüstü**' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="380e3-109">Ya da, sağ üst köşedeki arama kutusuna *Windows hizmeti* girip **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="380e3-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Visual Studio 'da yeni proje iletişim kutusunda Windows hizmet şablonu](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="380e3-111">**Windows hizmet** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="380e3-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="380e3-112">**Yeni proje** iletişim kutusunda sol alttaki **Visual Studio yükleyicisi aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="380e3-113">**.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="380e3-114">**Ad**için *MyNewService*yazın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="380e3-115">**Tasarım** sekmesi görünür (**Service1.cs [Design]** veya **Service1. vb [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="380e3-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="380e3-116">Proje şablonu, öğesinden `Service1` <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>devralan adlı bir bileşen sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="380e3-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="380e3-117">Bu, hizmeti başlatmak için kod gibi temel hizmet kodunun çoğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="380e3-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="380e3-118">Hizmeti yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="380e3-118">Rename the service</span></span>

<span data-ttu-id="380e3-119">Hizmeti **Service1** iken **MyNewService**olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="380e3-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="380e3-120">**Çözüm Gezgini**' de, **Service1.cs**veya **Service1. vb**öğesini seçin ve kısayol menüsünden **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="380e3-121">Dosyayı **MyNewService.cs**veya **MyNewService. vb**olarak yeniden adlandırın ve ardından **ENTER** tuşuna basın</span><span class="sxs-lookup"><span data-stu-id="380e3-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="380e3-122">Kod öğesi *Service1*için tüm başvuruları yeniden adlandırmak isteyip istemediğinizi soran bir açılır pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="380e3-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="380e3-123">Açılır pencerede **Evet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="380e3-124">![Yeniden adlandırma istemi](media/windows-service-rename.png "Windows hizmeti yeniden adlandırma istemi")</span><span class="sxs-lookup"><span data-stu-id="380e3-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="380e3-125">**Tasarım** sekmesinde, kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="380e3-126">**Özellikler** penceresinde **ServiceName** değerini *MyNewService*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="380e3-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="380e3-127">![Hizmet özellikleri](media/windows-service-properties.png "Windows hizmeti özellikleri")</span><span class="sxs-lookup"><span data-stu-id="380e3-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="380e3-128">**Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="380e3-129">Hizmete özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="380e3-129">Add features to the service</span></span>

<span data-ttu-id="380e3-130">Bu bölümde, Windows hizmetine özel bir olay günlüğü eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="380e3-131"><xref:System.Diagnostics.EventLog> Bileşen, bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="380e3-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="380e3-132">Özel olay günlüğü işlevselliği Ekle</span><span class="sxs-lookup"><span data-stu-id="380e3-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="380e3-133">**Çözüm Gezgini**, **MyNewService.cs**Için kısayol menüsünden veya **MyNewService. vb**' de **Görünüm Tasarımcısı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="380e3-134">**Araç kutusu**' nda **Bileşenler**' i genişletin ve ardından **EventLog** bileşenini **Service1.cs [Design]** veya **Service1. vb [Design]** sekmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="380e3-135">**Çözüm Gezgini**' de, **MyNewService.cs**veya **MyNewService. vb**kısayol menüsünde **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="380e3-136">Özel bir olay günlüğü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-136">Define a custom event log.</span></span> <span data-ttu-id="380e3-137">İçin C#, var olan `MyNewService()` oluşturucuyu düzenleyin; `New()` Visual Basic için oluşturucuyu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="380e3-138"><xref:System.Diagnostics?displayProperty=nameWithType> `Imports` Ad alanı için, **MyNewService.cs** (henüz yoksa) veya **MyNewService. vb**ifadesini ekleyin: `using`</span><span class="sxs-lookup"><span data-stu-id="380e3-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="380e3-139">**Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="380e3-140">Hizmet başladığında ne olduğunu tanımlayın</span><span class="sxs-lookup"><span data-stu-id="380e3-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="380e3-141">**MyNewService.cs** veya **MyNewService. vb**için kod düzenleyicisinde, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemini bulun; Projeyi oluştururken Visual Studio otomatik olarak boş bir yöntem tanımı oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="380e3-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="380e3-142">Hizmet başladığında bir girişi olay günlüğüne yazan kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="380e3-143">Masını</span><span class="sxs-lookup"><span data-stu-id="380e3-143">Polling</span></span>

<span data-ttu-id="380e3-144">Bir hizmet uygulaması uzun süre çalışan olacak şekilde tasarlandığından, genellikle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yönteminde ayarladığınız sistemi yoklar veya izler.</span><span class="sxs-lookup"><span data-stu-id="380e3-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="380e3-145">Sistemin engellenmemesi için hizmetin işlemi başladıktan sonra yöntemiişletimsisteminedöndürmelidir.`OnStart`</span><span class="sxs-lookup"><span data-stu-id="380e3-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="380e3-146">Basit bir yoklama mekanizması ayarlamak için <xref:System.Timers.Timer?displayProperty=nameWithType> bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="380e3-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="380e3-147">Süreölçer, düzenli aralıklarla <xref:System.Timers.Timer.Elapsed> bir olay oluşturur ve bu süre, hizmetiniz kendi izlemesini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="380e3-148"><xref:System.Timers.Timer> Bileşeni aşağıdaki gibi kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="380e3-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="380e3-149">Yöntemi içindeki bileşenin<xref:System.Timers.Timer> özelliklerini ayarlayın. `MyNewService.OnStart`</span><span class="sxs-lookup"><span data-stu-id="380e3-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="380e3-150"><xref:System.Timers.Timer.Start%2A> Yöntemini çağırarak Zamanlayıcıyı başlatın.</span><span class="sxs-lookup"><span data-stu-id="380e3-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="380e3-151">Yoklama mekanizmasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="380e3-152">Yoklama mekanizmasını ayarlamak için `MyNewService.OnStart` olaya aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="380e3-153"><xref:System.Timers?displayProperty=nameWithType> Ad alanı `using` için **MyNewService.cs**veya bir `Imports` deyime, **MyNewService. vb**öğesine bir ifade ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="380e3-154">Sınıfında, olayı<xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> işleyecek `OnTimer`yöntemiekleyin: `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="380e3-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="380e3-155">`MyNewService` Sınıfında bir üye değişkeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="380e3-156">Olay günlüğüne yazılacak bir sonraki olayın tanımlayıcısını içerir:</span><span class="sxs-lookup"><span data-stu-id="380e3-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="380e3-157">Tüm çalışmalarınızı ana iş parçacığında çalıştırmak yerine, arka plan çalışan iş parçacıklarını kullanarak görevleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="380e3-158">Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="380e3-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="380e3-159">Hizmet durdurulduğunda ne olduğunu tanımlayın</span><span class="sxs-lookup"><span data-stu-id="380e3-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="380e3-160">Hizmet durdurulduğunda olay günlüğüne bir girdi ekleyen <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yönteme bir kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="380e3-161">Hizmet için diğer eylemleri tanımlayın</span><span class="sxs-lookup"><span data-stu-id="380e3-161">Define other actions for the service</span></span>

<span data-ttu-id="380e3-162">Bileşeniniz için ek <xref:System.ServiceProcess.ServiceBase.OnPause%2A>işlem <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>tanımlamak üzere <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> ,, ve yöntemlerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="380e3-163">Aşağıdaki kod, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> `MyNewService` sınıfındaki yöntemini nasıl geçersiz kılabileceğiniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="380e3-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="380e3-164">Hizmet durumunu ayarla</span><span class="sxs-lookup"><span data-stu-id="380e3-164">Set service status</span></span>

<span data-ttu-id="380e3-165">Hizmetler, bir kullanıcının bir hizmetin doğru çalışıp çalışmadığını anlayabilmesi için durumlarını [hizmet denetimi yöneticisine](/windows/desktop/Services/service-control-manager) bildirir.</span><span class="sxs-lookup"><span data-stu-id="380e3-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="380e3-166">Varsayılan olarak, SERVICE_STOPPED, SERVICE_PAUSED ve SERVICE_RUNNING <xref:System.ServiceProcess.ServiceBase> içeren sınırlı bir durum ayarları kümesi raporlarından devralan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="380e3-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="380e3-167">Bir hizmetin başlatılması biraz zaman alıyorsa, SERVICE_START_PENDING durumunu raporlamak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="380e3-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="380e3-168">Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevini çağıran kodu ekleyerek SERVICE_START_PENDING ve SERVICE_STOP_PENDING durum ayarlarını uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="380e3-169">Hizmet bekleme durumunu Uygula</span><span class="sxs-lookup"><span data-stu-id="380e3-169">Implement service pending status</span></span>

1. <span data-ttu-id="380e3-170"><xref:System.Runtime.InteropServices?displayProperty=nameWithType> Ad alanı `using` için **MyNewService.cs**veya bir `Imports` deyime, **MyNewService. vb**öğesine bir ifade ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="380e3-171">`ServiceState` Değerleri bildirmek ve bir platform çağırma çağrısında kullanacağınız durum için bir yapı eklemek üzere **MyNewService.cs**veya **MyNewService. vb**' ye aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="380e3-172">Hizmet denetimi Yöneticisi, bir Windows `dwWaitHint` hizmetinin `dwCheckpoint` başlaması veya kapatılması için ne kadar süre bekleneceğini öğrenmek için [SERVICE_STATUS yapısının](/windows/win32/api/winsvc/ns-winsvc-service_status) ve üyelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="380e3-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="380e3-173">Ve `OnStart` `SetServiceStatus` `dwCheckPoint` yöntemleriniz uzun bir süre çalışıyorsa, hizmetiniz arttırılan bir değerle tekrar çağırarak daha fazla zaman isteğinde bulunabilir. `OnStop`</span><span class="sxs-lookup"><span data-stu-id="380e3-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="380e3-174">Sınıfında, [Platform Invoke](../interop/consuming-unmanaged-dll-functions.md)kullanarak [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevini bildirin: `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="380e3-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="380e3-175">SERVICE_START_PENDING durumunu uygulamak için, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yönteminin başına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="380e3-176">Durumu SERVICE_RUNNING olarak ayarlamak için `OnStart` yönteminin sonuna kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="380e3-177">Seçim Uzun süre çalışan bir yöntem ise, `OnStop` yöntemi içinde bu yordamı tekrarlayın. <xref:System.ServiceProcess.ServiceBase.OnStop%2A></span><span class="sxs-lookup"><span data-stu-id="380e3-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="380e3-178">SERVICE_STOP_PENDING durumunu uygulayın ve `OnStop` yöntemin çıkış yapmadan önce SERVICE_STOPPED durumunu döndürün.</span><span class="sxs-lookup"><span data-stu-id="380e3-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="380e3-179">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="380e3-179">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="380e3-180">Hizmete yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="380e3-180">Add installers to the service</span></span>

<span data-ttu-id="380e3-181">Bir Windows hizmetini çalıştırmadan önce, onu yüklemeniz gerekir, bunu hizmet denetimi Yöneticisi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e3-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="380e3-182">Kayıt ayrıntılarını işlemek için projenize yükleyiciler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="380e3-183">**Çözüm Gezgini**, **MyNewService.cs**Için kısayol menüsünden veya **MyNewService. vb**' de **Görünüm Tasarımcısı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="380e3-184">**Tasarım** görünümünde, arka plan alanını seçin, sonra kısayol menüsünden **Yükleyici Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="380e3-185">Varsayılan olarak, Visual Studio projenize iki yükleyici içeren adlı `ProjectInstaller`bir bileşen sınıfı ekler.</span><span class="sxs-lookup"><span data-stu-id="380e3-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="380e3-186">Bu yükleyiciler hizmetinize ve hizmetin ilişkili sürecine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="380e3-186">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="380e3-187">**ProjectInstaller**için **Tasarım** görünümünde, bir görsel C# proje Için **Serviceınstaller1 & lt** veya Visual Basic projesi için **Serviceınstaller1 & lt** ' i seçin, sonra kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="380e3-188">**Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliğin **MyNewService**olarak ayarlandığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="380e3-189"><xref:System.ServiceProcess.ServiceInstaller.Description%2A> Özelliğe *örnek bir hizmet*gibi metin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="380e3-190">Bu metin, **Hizmetler** penceresinin **Açıklama** sütununda görüntülenir ve kullanıcıya hizmeti açıklar.</span><span class="sxs-lookup"><span data-stu-id="380e3-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="380e3-191">![Hizmetler penceresinde hizmet açıklaması.](media/windows-service-description.png "Hizmet açıklaması")</span><span class="sxs-lookup"><span data-stu-id="380e3-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="380e3-192"><xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Özelliğe metin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="380e3-193">Örneğin, *MyNewService görünen adı*.</span><span class="sxs-lookup"><span data-stu-id="380e3-193">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="380e3-194">Bu metin, **Hizmetler** penceresinin **görünen ad** sütununda görünür.</span><span class="sxs-lookup"><span data-stu-id="380e3-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="380e3-195">Bu ad, sistem tarafından kullanılan ad <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> (örneğin, hizmetinizi başlatmak için kullandığınız `net start` ad) özelliğinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="380e3-196">Özelliğini, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> açılan listeden <xref:System.ServiceProcess.ServiceStartMode.Automatic> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="380e3-197">İşiniz bittiğinde, **Özellikler** penceresi aşağıdaki şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="380e3-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="380e3-198">![Windows hizmeti Için yükleyici özellikleri](media/windows-service-installer-properties.png "Windows hizmeti yükleyicisi özellikleri")</span><span class="sxs-lookup"><span data-stu-id="380e3-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="380e3-199">**ProjectInstaller**için **Tasarım** görünümünde, bir görsel C# proje Için **Serviceprocessınstaller1** veya Visual Basic projesi için **Serviceprocessınstaller1** ' i seçin, sonra kısayol menüsünden **Özellikler** ' i seçin. .</span><span class="sxs-lookup"><span data-stu-id="380e3-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="380e3-200">Özelliğini, <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> açılan listeden <xref:System.ServiceProcess.ServiceAccount.LocalSystem> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="380e3-201">Bu ayar hizmeti yükleyip yerel sistem hesabını kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="380e3-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="380e3-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabın, olay günlüğüne yazma özelliği de dahil olmak üzere geniş izinleri vardır.</span><span class="sxs-lookup"><span data-stu-id="380e3-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="380e3-203">Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="380e3-204">Diğer görevler için, yerel bilgisayarda ayrıcalıklı <xref:System.ServiceProcess.ServiceAccount.LocalService> olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan hesabı kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="380e3-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="380e3-205">Bu örnek, <xref:System.ServiceProcess.ServiceAccount.LocalService> hesap günlüğüne yazmak için izin gerektiğinden hesabı kullanmayı denerseniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="380e3-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="380e3-206">Yükleyiciler hakkında daha fazla bilgi için bkz [. nasıl yapılır: Hizmet uygulamanıza](how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e3-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="380e3-207">Seçim Başlangıç parametrelerini ayarla</span><span class="sxs-lookup"><span data-stu-id="380e3-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="380e3-208">Başlangıç parametrelerini eklemeye karar vermeden önce, hizmetinize bilgileri iletmenin en iyi yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="380e3-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="380e3-209">Kullanımı ve ayrıştırma kolaysa da, bir kullanıcı bunları kolayca geçersiz kılabilir, ancak kullanıcıların belge olmadan bulması ve kullanması daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="380e3-210">Genel olarak, hizmetiniz yalnızca birkaç başlangıç parametresi gerektiriyorsa, bunun yerine kayıt defteri veya yapılandırma dosyası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="380e3-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="380e3-211">Windows hizmeti komut satırı bağımsız değişkenlerini veya başlangıç parametrelerini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="380e3-212">Başlangıç parametrelerini işlemek için kod eklediğinizde, bir Kullanıcı Hizmeti Özellikler penceresinde kendi özel başlangıç parametreleriyle hizmetinizi başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="380e3-213">Ancak, bu başlangıç parametreleri hizmetin bir sonraki başlatılışında kalıcı olmaz.</span><span class="sxs-lookup"><span data-stu-id="380e3-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="380e3-214">Başlangıç parametrelerini kalıcı olarak ayarlamak için kayıt defterinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="380e3-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="380e3-215">Her bir Windows hizmetinin, **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** alt anahtarında bir kayıt defteri girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="380e3-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="380e3-216">Her bir hizmetin alt anahtarı altında, hizmetinizin erişebileceği bilgileri depolamak için **Parameters** alt anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="380e3-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="380e3-217">Windows hizmeti için uygulama yapılandırma dosyalarını, diğer tür programlar için yaptığınız şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="380e3-218">Örnek kod için bkz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="380e3-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="380e3-219">Başlangıç parametreleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="380e3-219">To add startup parameters</span></span>

1. <span data-ttu-id="380e3-220">**Program.cs**veya **MyNewService. Designer. vb**öğesini seçin, ardından kısayol menüsünde **kodu görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="380e3-221">`Main` Yönteminde, bir giriş parametresi eklemek ve onu Service yapıcısına iletmek için kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="380e3-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="380e3-222">**MyNewService.cs**veya **MyNewService. vb** `MyNewService` ' de, Oluşturucu giriş parametresini aşağıdaki gibi işleyecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="380e3-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="380e3-223">Bu kod, olay kaynağını ve günlük adını kullanıcının sağladığı başlangıç parametrelerine göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="380e3-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="380e3-224">Herhangi bir bağımsız değişken sağlanmadığında, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="380e3-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="380e3-225">Komut satırı bağımsız değişkenlerini belirtmek için, **ProjectInstaller.cs**veya **ProjectInstaller. vb**dosyasındaki `ProjectInstaller` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380e3-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="380e3-226">Genellikle, bu değer Windows hizmeti için yürütülebilir dosyanın tam yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="380e3-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="380e3-227">Hizmetin doğru başlaması için, kullanıcının yol ve her bir parametre için tırnak işaretleri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="380e3-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="380e3-228">Kullanıcı, Windows hizmeti için başlangıç parametrelerini değiştirmek üzere **ImagePath** kayıt defteri girdisindeki parametreleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="380e3-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="380e3-229">Ancak, daha iyi bir yol, değeri programlı bir şekilde değiştirmek ve işlevselliği bir yönetim veya yapılandırma yardımcı programı kullanarak gibi Kullanıcı dostu bir şekilde kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="380e3-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="380e3-230">Hizmeti oluşturun</span><span class="sxs-lookup"><span data-stu-id="380e3-230">Build the service</span></span>

1. <span data-ttu-id="380e3-231">**Çözüm Gezgini**' de, **MyNewService** projesinin kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="380e3-232">Projeniz için özellik sayfaları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="380e3-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="380e3-233">**Uygulama** sekmesinde, **Başlangıç nesnesi** listesinde, Visual Basic projeler için **MyNewService. program**veya **Sub Main** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="380e3-234">Projeyi derlemek için, **Çözüm Gezgini**menüsünde, projeniz için kısayol menüsünden **Oluştur** ' u seçin (veya **CTRL**+ **+ Shift**+**B**tuşlarına basın).</span><span class="sxs-lookup"><span data-stu-id="380e3-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="380e3-235">Hizmeti yükler</span><span class="sxs-lookup"><span data-stu-id="380e3-235">Install the service</span></span>

<span data-ttu-id="380e3-236">Windows hizmetini oluşturduğunuza göre, artık yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="380e3-237">Bir Windows hizmetini yüklemek için, yüklendiği bilgisayarda yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="380e3-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="380e3-238">Yönetim kimlik bilgileriyle [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) açın.</span><span class="sxs-lookup"><span data-stu-id="380e3-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="380e3-239">Windows **Başlat** menüsünde, Visual Studio klasöründeki **vs 2017 için geliştirici komut istemi** ' yi seçin ve > ardından kısayol menüsünde**yönetici olarak çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="380e3-240">**Visual Studio için geliştirici komut istemi** penceresinde, projenizin çıkışını içeren klasöre gidin (varsayılan olarak, projenizin *\Bin\Debug* alt dizininde).</span><span class="sxs-lookup"><span data-stu-id="380e3-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="380e3-241">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="380e3-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="380e3-242">Hizmet başarıyla yüklerse, komut başarıyı bildirir.</span><span class="sxs-lookup"><span data-stu-id="380e3-242">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="380e3-243">Sistem *InstallUtil. exe*' yi bulamazsa, bilgisayarınızda bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="380e3-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="380e3-244">Bu araç, *%windir%\Microsoft.NET\Framework [64\\]&lt;&gt;Framework sürümü*klasörüne .NET Framework yüklenir.</span><span class="sxs-lookup"><span data-stu-id="380e3-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="380e3-245">Örneğin, 64 bit sürümü için varsayılan yol *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*' dir.</span><span class="sxs-lookup"><span data-stu-id="380e3-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="380e3-246">**InstallUtil. exe** işlemi başarısız olursa, nedenini öğrenmek için yükleme günlüğünü kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="380e3-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="380e3-247">Varsayılan olarak, günlük hizmet yürütülebiliri ile aynı klasörsdır.</span><span class="sxs-lookup"><span data-stu-id="380e3-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="380e3-248">Yükleme şu durumlarda başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="380e3-248">The installation can fail if:</span></span>
    - <span data-ttu-id="380e3-249"><xref:System.ComponentModel.RunInstallerAttribute> Sınıf `ProjectInstaller` sınıfında yok.</span><span class="sxs-lookup"><span data-stu-id="380e3-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="380e3-250">Özniteliği olarak `true`ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="380e3-250">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="380e3-251">`ProjectInstaller` Sınıfı olarak`public`tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="380e3-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="380e3-252">Daha fazla bilgi için [nasıl yapılır: Hizmetleri](how-to-install-and-uninstall-services.md)yükleme ve kaldırma.</span><span class="sxs-lookup"><span data-stu-id="380e3-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="380e3-253">Hizmeti başlatma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="380e3-253">Start and run the service</span></span>

1. <span data-ttu-id="380e3-254">Windows 'ta, **Hizmetler** masaüstü uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="380e3-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="380e3-255">**Windows**R tuşuna basarak Çalıştır kutusunu açın, Services. msc yazın ve ardından ENTER tuşuna basın veya Tamam ' ı seçin.+</span><span class="sxs-lookup"><span data-stu-id="380e3-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="380e3-256">Hizmetinizi, sizin için ayarladığınız görünen ada göre alfabetik olarak görüntülenen **Hizmetler**bölümünde görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="380e3-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![Hizmetler penceresinde MyNewService.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="380e3-258">Hizmeti başlatmak için hizmetin kısayol menüsünden **Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="380e3-259">Hizmeti durdurmak için hizmetin kısayol menüsünden **Durdur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="380e3-260">Seçim Hizmetinizi başlatmak ve durdurmak için komut satırından **net start &lt;Service Name&gt;**  ve **net stop &lt;hizmet adı&gt;**  komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="380e3-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="380e3-261">Hizmetinizin olay günlüğü çıkışını doğrulama</span><span class="sxs-lookup"><span data-stu-id="380e3-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="380e3-262">Windows 'ta **Olay Görüntüleyicisi** masaüstü uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="380e3-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="380e3-263">Windows Search çubuğuna *Olay Görüntüleyicisi* girin ve sonra arama sonuçlarından **Olay Görüntüleyicisi** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="380e3-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="380e3-264">Visual Studio 'da, **Görünüm** menüsünden **Sunucu Gezgini** açarak (veya **CTRL**+**alt**+**öğeleri**' ne basarak) ve yerel bilgisayarın **olay günlükleri** düğümünü genişleterek olay günlüklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="380e3-265">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="380e3-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="380e3-266">**MyNewLog** listesini bulun (veya komut satırı bağımsız değişkenleri ekleme yordamını Izlediyseniz **MyLogFile1** ) ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="380e3-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="380e3-267">Hizmetinizin gerçekleştirdiği iki eylem (başlatma ve durdurma) için girişleri görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="380e3-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi kullanın](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="380e3-269">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="380e3-269">Clean up resources</span></span>

<span data-ttu-id="380e3-270">Artık Windows hizmeti uygulamasına ihtiyacınız yoksa, bunu kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380e3-270">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="380e3-271">Yönetim kimlik bilgileriyle **Visual Studio için geliştirici komut istemi** açın.</span><span class="sxs-lookup"><span data-stu-id="380e3-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="380e3-272">**Visual Studio için geliştirici komut istemi** penceresinde, projenizin çıkışını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="380e3-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="380e3-273">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="380e3-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="380e3-274">Hizmet başarıyla kaldırılırsa, komut hizmetinizin başarıyla kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="380e3-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="380e3-275">Daha fazla bilgi için [nasıl yapılır: Hizmetleri](how-to-install-and-uninstall-services.md)yükleme ve kaldırma.</span><span class="sxs-lookup"><span data-stu-id="380e3-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="380e3-276">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="380e3-276">Next steps</span></span>

<span data-ttu-id="380e3-277">Hizmeti oluşturduğumuz artık şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="380e3-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="380e3-278">Başkalarının Windows hizmetinizi yüklemek için kullanması için tek başına bir kurulum programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="380e3-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="380e3-279">[Wix araç takımını](https://wixtoolset.org/) kullanarak bir Windows hizmeti için yükleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="380e3-279">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="380e3-280">Diğer fikirler için bkz. [Yükleyici paketi oluşturma](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="380e3-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="380e3-281">Yüklemiş olduğunuz hizmete komutlar göndermenizi sağlayan bileşenigezin.<xref:System.ServiceProcess.ServiceController></span><span class="sxs-lookup"><span data-stu-id="380e3-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="380e3-282">Uygulama çalışırken olay günlüğü oluşturmak yerine, uygulamayı yüklerken bir olay günlüğü oluşturmak için bir yükleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="380e3-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="380e3-283">Uygulamayı kaldırdığınızda olay günlüğü yükleyici tarafından silinir.</span><span class="sxs-lookup"><span data-stu-id="380e3-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="380e3-284">Daha fazla bilgi için bkz. <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="380e3-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="380e3-285">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="380e3-285">See also</span></span>

- [<span data-ttu-id="380e3-286">Windows hizmeti uygulamaları</span><span class="sxs-lookup"><span data-stu-id="380e3-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="380e3-287">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="380e3-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="380e3-288">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="380e3-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="380e3-289">Hizmetler (Windows)</span><span class="sxs-lookup"><span data-stu-id="380e3-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
