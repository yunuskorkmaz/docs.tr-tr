---
title: 'Öğretici: Windows hizmeti uygulaması oluşturma'
description: Bu öğreticide, Visual Studio 'da bir olay günlüğüne ileti yazan bir Windows hizmeti uygulaması oluşturun. Özellik ekleyin, durum ayarlayın, yükleyiciler ekleyin ve daha fazlasını yapın.
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 487a974af2280a02b83fe685324c9464df705585
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925637"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="d0435-104">Öğretici: Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0435-104">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="d0435-105">Bu makalede, Visual Studio 'da bir olay günlüğüne ileti yazan bir Windows hizmet uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0435-105">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="d0435-106">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0435-106">Create a service</span></span>

<span data-ttu-id="d0435-107">Başlamak için projeyi oluşturun ve hizmetin düzgün çalışması için gereken değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-107">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="d0435-108">Visual Studio **Dosya** menüsünden **Yeni**  >  **Proje** ' yi seçin (veya **CTRL** + **SHIFT** + **N**tuşlarına basarak) **Yeni proje** penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="d0435-108">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="d0435-109">' A gidin ve **Windows hizmeti (.NET Framework)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-109">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="d0435-110">Bunu bulmak için, **yüklü** ve **Visual C#** veya **Visual Basic**genişletin, sonra **Windows Masaüstü**' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-110">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="d0435-111">Ya da, sağ üst köşedeki arama kutusuna *Windows hizmeti* girip **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d0435-111">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Visual Studio 'da yeni proje iletişim kutusunda Windows hizmet şablonu](./media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="d0435-113">**Windows hizmet** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="d0435-113">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="d0435-114">**Yeni proje** iletişim kutusunda sol alttaki **Visual Studio yükleyicisi aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-114">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="d0435-115">**.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-115">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="d0435-116">**Ad**için *MyNewService*yazın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-116">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="d0435-117">**Tasarım** sekmesi görünür (**Service1.cs [Design]** veya **Service1. vb [Design]**).</span><span class="sxs-lookup"><span data-stu-id="d0435-117">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="d0435-118">Proje şablonu, öğesinden devralan adlı bir bileşen sınıfı içerir `Service1` <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0435-118">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d0435-119">Bu, hizmeti başlatmak için kod gibi temel hizmet kodunun çoğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d0435-119">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="d0435-120">Hizmeti yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="d0435-120">Rename the service</span></span>

<span data-ttu-id="d0435-121">Hizmeti **Service1** iken **MyNewService**olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d0435-121">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="d0435-122">**Çözüm Gezgini**' de, **Service1.cs**veya **Service1. vb**öğesini seçin ve kısayol menüsünden **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-122">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="d0435-123">Dosyayı **MyNewService.cs**veya **MyNewService. vb**olarak yeniden adlandırın ve ardından **ENTER** tuşuna basın</span><span class="sxs-lookup"><span data-stu-id="d0435-123">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="d0435-124">Kod öğesi *Service1*için tüm başvuruları yeniden adlandırmak isteyip istemediğinizi soran bir açılır pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0435-124">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="d0435-125">Açılır pencerede **Evet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-125">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="d0435-126">![Yeniden adlandırma istemi](./media/windows-service-rename.png "Windows hizmeti yeniden adlandırma istemi")</span><span class="sxs-lookup"><span data-stu-id="d0435-126">![Rename prompt](./media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="d0435-127">**Tasarım** sekmesinde, kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-127">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="d0435-128">**Özellikler** penceresinde **ServiceName** değerini *MyNewService*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0435-128">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="d0435-129">![Hizmet özellikleri](./media/windows-service-properties.png "Windows hizmeti özellikleri")</span><span class="sxs-lookup"><span data-stu-id="d0435-129">![Service properties](./media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="d0435-130">**Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-130">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="d0435-131">Hizmete özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="d0435-131">Add features to the service</span></span>

<span data-ttu-id="d0435-132">Bu bölümde, Windows hizmetine özel bir olay günlüğü eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="d0435-133"><xref:System.Diagnostics.EventLog>Bileşen, bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="d0435-133">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="d0435-134">Özel olay günlüğü işlevselliği Ekle</span><span class="sxs-lookup"><span data-stu-id="d0435-134">Add custom event log functionality</span></span>

1. <span data-ttu-id="d0435-135">**Çözüm Gezgini**, **MyNewService.cs**Için kısayol menüsünden veya **MyNewService. vb**' de **Görünüm Tasarımcısı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="d0435-136">**Araç kutusu**' nda **Bileşenler**' i genişletin ve ardından **EventLog** bileşenini **Service1.cs [Design]** veya **Service1. vb [Design]** sekmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d0435-136">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="d0435-137">**Çözüm Gezgini**' de, **MyNewService.cs**veya **MyNewService. vb**kısayol menüsünde **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-137">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="d0435-138">Özel bir olay günlüğü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-138">Define a custom event log.</span></span> <span data-ttu-id="d0435-139">C# için, var olan `MyNewService()` oluşturucuyu düzenleyin; Visual Basic için `New()` oluşturucuyu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-139">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="d0435-140">`using`Ad alanı için, **MyNewService.cs** (henüz yoksa) veya `Imports` **MyNewService. vb**ifadesini ekleyin <xref:System.Diagnostics?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="d0435-140">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="d0435-141">**Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-141">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="d0435-142">Hizmet başladığında ne olduğunu tanımlayın</span><span class="sxs-lookup"><span data-stu-id="d0435-142">Define what occurs when the service starts</span></span>

<span data-ttu-id="d0435-143">**MyNewService.cs** veya **MyNewService. vb**için kod düzenleyicisinde, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemini bulun; Projeyi oluştururken Visual Studio otomatik olarak boş bir yöntem tanımı oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="d0435-143">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="d0435-144">Hizmet başladığında bir girişi olay günlüğüne yazan kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-144">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="d0435-145">Yoklama</span><span class="sxs-lookup"><span data-stu-id="d0435-145">Polling</span></span>

<span data-ttu-id="d0435-146">Bir hizmet uygulaması uzun süre çalışan olacak şekilde tasarlandığından, genellikle yönteminde ayarladığınız sistemi yoklar veya izler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> .</span><span class="sxs-lookup"><span data-stu-id="d0435-146">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="d0435-147">`OnStart`Sistemin engellenmemesi için hizmetin işlemi başladıktan sonra yöntemi işletim sistemine döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0435-147">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="d0435-148">Basit bir yoklama mekanizması ayarlamak için <xref:System.Timers.Timer?displayProperty=nameWithType> bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0435-148">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="d0435-149">Süreölçer, <xref:System.Timers.Timer.Elapsed> düzenli aralıklarla bir olay oluşturur ve bu süre, hizmetiniz kendi izlemesini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-149">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="d0435-150"><xref:System.Timers.Timer>Bileşeni aşağıdaki gibi kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="d0435-150">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="d0435-151"><xref:System.Timers.Timer>Yöntemi içindeki bileşenin özelliklerini ayarlayın `MyNewService.OnStart` .</span><span class="sxs-lookup"><span data-stu-id="d0435-151">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="d0435-152">Yöntemini çağırarak Zamanlayıcıyı başlatın <xref:System.Timers.Timer.Start%2A> .</span><span class="sxs-lookup"><span data-stu-id="d0435-152">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="d0435-153">Yoklama mekanizmasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-153">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="d0435-154">`MyNewService.OnStart`Yoklama mekanizmasını ayarlamak için olaya aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-154">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="d0435-155">`using`Ad alanı için **MyNewService.cs**veya bir deyime, `Imports` **MyNewService. vb**öğesine bir ifade ekleyin <xref:System.Timers?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="d0435-155">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="d0435-156">`MyNewService`Sınıfında, `OnTimer` olayı işleyecek yöntemi ekleyin <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="d0435-156">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="d0435-157">`MyNewService`Sınıfında bir üye değişkeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d0435-157">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="d0435-158">Olay günlüğüne yazılacak bir sonraki olayın tanımlayıcısını içerir:</span><span class="sxs-lookup"><span data-stu-id="d0435-158">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="d0435-159">Tüm çalışmalarınızı ana iş parçacığında çalıştırmak yerine, arka plan çalışan iş parçacıklarını kullanarak görevleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-159">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="d0435-160">Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0435-160">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="d0435-161">Hizmet durdurulduğunda ne olduğunu tanımlayın</span><span class="sxs-lookup"><span data-stu-id="d0435-161">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="d0435-162"><xref:System.ServiceProcess.ServiceBase.OnStop%2A>Hizmet durdurulduğunda olay günlüğüne bir girdi ekleyen yönteme bir kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-162">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="d0435-163">Hizmet için diğer eylemleri tanımlayın</span><span class="sxs-lookup"><span data-stu-id="d0435-163">Define other actions for the service</span></span>

<span data-ttu-id="d0435-164"><xref:System.ServiceProcess.ServiceBase.OnPause%2A> <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> Bileşeniniz için ek işlem tanımlamak üzere,, ve yöntemlerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-164">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="d0435-165">Aşağıdaki kod, sınıfındaki yöntemini nasıl geçersiz kılabileceğiniz gösterilmektedir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> `MyNewService` :</span><span class="sxs-lookup"><span data-stu-id="d0435-165">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="d0435-166">Hizmet durumunu ayarla</span><span class="sxs-lookup"><span data-stu-id="d0435-166">Set service status</span></span>

<span data-ttu-id="d0435-167">Hizmetler, bir kullanıcının bir hizmetin doğru çalışıp çalışmadığını anlayabilmesi için durumlarını [hizmet denetimi yöneticisine](/windows/desktop/Services/service-control-manager) bildirir.</span><span class="sxs-lookup"><span data-stu-id="d0435-167">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="d0435-168">Varsayılan olarak, <xref:System.ServiceProcess.ServiceBase> SERVICE_STOPPED, SERVICE_PAUSED ve SERVICE_RUNNING içeren sınırlı bir durum ayarları kümesi raporlarından devralan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="d0435-168">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="d0435-169">Bir hizmetin başlatılması biraz zaman alıyorsa, SERVICE_START_PENDING durumunu raporlamak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d0435-169">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="d0435-170">Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevini çağıran kodu ekleyerek SERVICE_START_PENDING ve SERVICE_STOP_PENDING durum ayarlarını uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-170">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="d0435-171">Hizmet bekleme durumunu Uygula</span><span class="sxs-lookup"><span data-stu-id="d0435-171">Implement service pending status</span></span>

1. <span data-ttu-id="d0435-172">`using`Ad alanı için **MyNewService.cs**veya bir deyime, `Imports` **MyNewService. vb**öğesine bir ifade ekleyin <xref:System.Runtime.InteropServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="d0435-172">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="d0435-173">Değerleri bildirmek ve bir platform çağırma çağrısında kullanacağınız durum için bir yapı eklemek üzere **MyNewService.cs**veya **MyNewService. vb**' ye aşağıdaki kodu ekleyin `ServiceState` :</span><span class="sxs-lookup"><span data-stu-id="d0435-173">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="d0435-174">Hizmet denetimi Yöneticisi, `dwWaitHint` `dwCheckpoint` bir Windows hizmetinin başlamasını veya kapatılmasını ne kadar bekleyeceğini öğrenmek için [SERVICE_STATUS yapısının](/windows/win32/api/winsvc/ns-winsvc-service_status) ve üyelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0435-174">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="d0435-175">`OnStart`Ve `OnStop` yöntemleriniz uzun bir süre çalışıyorsa, hizmetiniz `SetServiceStatus` arttırılan bir değerle tekrar çağırarak daha fazla zaman isteğinde bulunabilir `dwCheckPoint` .</span><span class="sxs-lookup"><span data-stu-id="d0435-175">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="d0435-176">`MyNewService`Sınıfında, [Platform Invoke](../interop/consuming-unmanaged-dll-functions.md)kullanarak [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevini bildirin:</span><span class="sxs-lookup"><span data-stu-id="d0435-176">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="d0435-177">SERVICE_START_PENDING durumunu uygulamak için, yönteminin başına aşağıdaki kodu ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> :</span><span class="sxs-lookup"><span data-stu-id="d0435-177">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="d0435-178">`OnStart`Durumu SERVICE_RUNNING olarak ayarlamak için yöntemin sonuna kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-178">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="d0435-179">Seçim <xref:System.ServiceProcess.ServiceBase.OnStop%2A>Uzun süre çalışan bir yöntem ise, yöntemi içinde bu yordamı tekrarlayın `OnStop` .</span><span class="sxs-lookup"><span data-stu-id="d0435-179">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="d0435-180">SERVICE_STOP_PENDING durumunu uygulayın ve yöntemin uygulamadan önce SERVICE_STOPPED durumunu döndürün `OnStop` .</span><span class="sxs-lookup"><span data-stu-id="d0435-180">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="d0435-181">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d0435-181">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="d0435-182">Hizmete yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="d0435-182">Add installers to the service</span></span>

<span data-ttu-id="d0435-183">Bir Windows hizmetini çalıştırmadan önce, onu yüklemeniz gerekir, bunu hizmet denetimi Yöneticisi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0435-183">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="d0435-184">Kayıt ayrıntılarını işlemek için projenize yükleyiciler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d0435-184">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="d0435-185">**Çözüm Gezgini**, **MyNewService.cs**Için kısayol menüsünden veya **MyNewService. vb**' de **Görünüm Tasarımcısı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-185">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="d0435-186">**Tasarım** görünümünde, arka plan alanını seçin, sonra kısayol menüsünden **Yükleyici Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-186">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="d0435-187">Varsayılan olarak, Visual Studio `ProjectInstaller` projenize iki yükleyici içeren adlı bir bileşen sınıfı ekler.</span><span class="sxs-lookup"><span data-stu-id="d0435-187">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="d0435-188">Bu yükleyiciler hizmetinize ve hizmetin ilişkili sürecine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d0435-188">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="d0435-189">**ProjectInstaller**için **Tasarım** görünümünde, bir Visual C# projesi için **Serviceınstaller1 & lt** veya Visual Basic projesi için **Serviceınstaller1 & lt** ' i seçin, sonra kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-189">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="d0435-190">**Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliğin **MyNewService**olarak ayarlandığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-190">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="d0435-191"><xref:System.ServiceProcess.ServiceInstaller.Description%2A>Özelliğe *örnek bir hizmet*gibi metin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d0435-191">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="d0435-192">Bu metin, **Hizmetler** penceresinin **Açıklama** sütununda görüntülenir ve kullanıcıya hizmeti açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0435-192">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="d0435-193">![Hizmetler penceresinde hizmet açıklaması.](./media/windows-service-description.png "Hizmet açıklaması")</span><span class="sxs-lookup"><span data-stu-id="d0435-193">![Service description in the Services window.](./media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="d0435-194">Özelliğe metin ekleyin <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> .</span><span class="sxs-lookup"><span data-stu-id="d0435-194">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="d0435-195">Örneğin, *MyNewService görünen adı*.</span><span class="sxs-lookup"><span data-stu-id="d0435-195">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="d0435-196">Bu metin, **Hizmetler** penceresinin **görünen ad** sütununda görünür.</span><span class="sxs-lookup"><span data-stu-id="d0435-196">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="d0435-197">Bu ad, <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sistem tarafından kullanılan ad (örneğin, hizmetinizi başlatmak için kullandığınız ad) özelliğinden farklı olabilir `net start` .</span><span class="sxs-lookup"><span data-stu-id="d0435-197">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="d0435-198">Özelliğini, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> <xref:System.ServiceProcess.ServiceStartMode.Automatic> açılan listeden olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-198">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="d0435-199">İşiniz bittiğinde, **Özellikler** penceresi aşağıdaki şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d0435-199">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="d0435-200">![Windows hizmeti için yükleyici özellikleri](./media/windows-service-installer-properties.png "Windows hizmeti yükleyicisi özellikleri")</span><span class="sxs-lookup"><span data-stu-id="d0435-200">![Installer Properties for a Windows service](./media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="d0435-201">**ProjectInstaller**için **Tasarım** görünümünde, bir Visual C# projesi için **Serviceprocessınstaller1** veya Visual Basic projesi için **Serviceprocessınstaller1** ' i seçin, sonra kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-201">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="d0435-202">Özelliğini, <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> <xref:System.ServiceProcess.ServiceAccount.LocalSystem> açılan listeden olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-202">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="d0435-203">Bu ayar hizmeti yükleyip yerel sistem hesabını kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d0435-203">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d0435-204"><xref:System.ServiceProcess.ServiceAccount.LocalSystem>Hesabın, olay günlüğüne yazma özelliği de dahil olmak üzere geniş izinleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d0435-204">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="d0435-205">Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-205">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="d0435-206">Diğer görevler için, <xref:System.ServiceProcess.ServiceAccount.LocalService> yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan hesabı kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d0435-206">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="d0435-207">Bu örnek, <xref:System.ServiceProcess.ServiceAccount.LocalService> Hesap günlüğüne yazmak için izin gerektiğinden hesabı kullanmayı denerseniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0435-207">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="d0435-208">Yükleyiciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="d0435-208">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="d0435-209">Seçim Başlangıç parametrelerini ayarla</span><span class="sxs-lookup"><span data-stu-id="d0435-209">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="d0435-210">Başlangıç parametrelerini eklemeye karar vermeden önce, hizmetinize bilgileri iletmenin en iyi yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d0435-210">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="d0435-211">Kullanımı ve ayrıştırma kolaysa da, bir kullanıcı bunları kolayca geçersiz kılabilir, ancak kullanıcıların belge olmadan bulması ve kullanması daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-211">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="d0435-212">Genel olarak, hizmetiniz yalnızca birkaç başlangıç parametresi gerektiriyorsa, bunun yerine kayıt defteri veya yapılandırma dosyası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0435-212">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="d0435-213">Windows hizmeti komut satırı bağımsız değişkenlerini veya başlangıç parametrelerini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-213">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="d0435-214">Başlangıç parametrelerini işlemek için kod eklediğinizde, bir Kullanıcı Hizmeti Özellikler penceresinde kendi özel başlangıç parametreleriyle hizmetinizi başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-214">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="d0435-215">Ancak, bu başlangıç parametreleri hizmetin bir sonraki başlatılışında kalıcı olmaz.</span><span class="sxs-lookup"><span data-stu-id="d0435-215">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="d0435-216">Başlangıç parametrelerini kalıcı olarak ayarlamak için kayıt defterinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0435-216">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="d0435-217">Her bir Windows hizmetinin **HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services** alt anahtarı altında bir kayıt defteri girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="d0435-217">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="d0435-218">Her bir hizmetin alt anahtarı altında, hizmetinizin erişebileceği bilgileri depolamak için **Parameters** alt anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0435-218">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="d0435-219">Windows hizmeti için uygulama yapılandırma dosyalarını, diğer tür programlar için yaptığınız şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-219">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="d0435-220">Örnek kod için bkz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="d0435-220">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="d0435-221">Başlangıç parametreleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="d0435-221">To add startup parameters</span></span>

1. <span data-ttu-id="d0435-222">**Program.cs**veya **MyNewService. Designer. vb**öğesini seçin, ardından kısayol menüsünde **kodu görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-222">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="d0435-223">Yönteminde, `Main` bir giriş parametresi eklemek ve onu Service yapıcısına iletmek için kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d0435-223">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="d0435-224">**MyNewService.cs**veya **MyNewService. vb**' de, `MyNewService` Oluşturucu giriş parametresini aşağıdaki gibi işleyecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d0435-224">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="d0435-225">Bu kod, olay kaynağını ve günlük adını kullanıcının sağladığı başlangıç parametrelerine göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d0435-225">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="d0435-226">Herhangi bir bağımsız değişken sağlanmadığında, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0435-226">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="d0435-227">Komut satırı bağımsız değişkenlerini belirtmek için, `ProjectInstaller` **ProjectInstaller.cs**veya **ProjectInstaller. vb**dosyasındaki sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0435-227">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="d0435-228">Genellikle, bu değer Windows hizmeti için yürütülebilir dosyanın tam yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d0435-228">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="d0435-229">Hizmetin doğru başlaması için, kullanıcının yol ve her bir parametre için tırnak işaretleri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0435-229">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="d0435-230">Kullanıcı, Windows hizmeti için başlangıç parametrelerini değiştirmek üzere **ImagePath** kayıt defteri girdisindeki parametreleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d0435-230">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="d0435-231">Ancak, daha iyi bir yol, değeri programlı bir şekilde değiştirmek ve işlevselliği bir yönetim veya yapılandırma yardımcı programı kullanarak gibi Kullanıcı dostu bir şekilde kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0435-231">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="d0435-232">Hizmeti oluşturun</span><span class="sxs-lookup"><span data-stu-id="d0435-232">Build the service</span></span>

1. <span data-ttu-id="d0435-233">**Çözüm Gezgini**' de, **MyNewService** projesinin kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-233">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="d0435-234">Projeniz için özellik sayfaları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0435-234">The property pages for your project appear.</span></span>

2. <span data-ttu-id="d0435-235">**Uygulama** sekmesinde, **Başlangıç nesnesi** listesinde, Visual Basic projeler için **MyNewService. program**veya **Sub Main** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-235">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="d0435-236">Projeyi derlemek için, **Çözüm Gezgini**menüsünde, projeniz için kısayol menüsünden **Oluştur** ' u seçin (veya **CTRL** + **+ Shift** + **B**tuşlarına basın).</span><span class="sxs-lookup"><span data-stu-id="d0435-236">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="d0435-237">Hizmeti yükleme</span><span class="sxs-lookup"><span data-stu-id="d0435-237">Install the service</span></span>

<span data-ttu-id="d0435-238">Windows hizmetini oluşturduğunuza göre, artık yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-238">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="d0435-239">Bir Windows hizmetini yüklemek için, yüklendiği bilgisayarda yönetici kimlik bilgilerine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0435-239">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="d0435-240">Yönetim kimlik bilgileriyle [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) açın.</span><span class="sxs-lookup"><span data-stu-id="d0435-240">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="d0435-241">Windows **Başlat** menüsünde, Visual Studio klasöründeki **vs 2017 için geliştirici komut istemi** ' **yi seçin ve**ardından  >  kısayol menüsünde**yönetici olarak çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-241">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="d0435-242">**Visual Studio için geliştirici komut istemi** penceresinde, projenizin çıkışını içeren klasöre gidin (varsayılan olarak, projenizin *\Bin\Debug* alt dizininde).</span><span class="sxs-lookup"><span data-stu-id="d0435-242">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="d0435-243">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="d0435-243">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="d0435-244">Hizmet başarıyla yüklerse, komut başarıyı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d0435-244">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="d0435-245">Sistem *installutil.exe*bulamazsa, bilgisayarınızda bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d0435-245">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="d0435-246">Bu araç, \*%windir%\Microsoft.NET\Framework [64] \\ &lt; Framework sürümü &gt; \*klasörüne .NET Framework yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d0435-246">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="d0435-247">Örneğin, 64 bit sürümü için varsayılan yol *% windir% \Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="d0435-247">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="d0435-248">**installutil.exe** işlemi başarısız olursa, nedenini öğrenmek için yüklemenin günlüğünü denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d0435-248">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="d0435-249">Varsayılan olarak, günlük hizmet yürütülebiliri ile aynı klasörsdır.</span><span class="sxs-lookup"><span data-stu-id="d0435-249">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="d0435-250">Yükleme şu durumlarda başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="d0435-250">The installation can fail if:</span></span>
    - <span data-ttu-id="d0435-251">Sınıf <xref:System.ComponentModel.RunInstallerAttribute> `ProjectInstaller` sınıfında yok.</span><span class="sxs-lookup"><span data-stu-id="d0435-251">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="d0435-252">Özniteliği olarak ayarlanmadı `true` .</span><span class="sxs-lookup"><span data-stu-id="d0435-252">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="d0435-253">`ProjectInstaller`Sınıfı olarak tanımlanmamıştır `public` .</span><span class="sxs-lookup"><span data-stu-id="d0435-253">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="d0435-254">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0435-254">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="d0435-255">Hizmeti başlatma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d0435-255">Start and run the service</span></span>

1. <span data-ttu-id="d0435-256">Windows 'ta, **Hizmetler** masaüstü uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="d0435-256">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="d0435-257">**Windows** + **R** tuşuna basarak **Çalıştır** kutusunu açın, *Services. msc*yazın ve ardından **ENTER** tuşuna basın veya **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-257">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="d0435-258">Hizmetinizi, sizin için ayarladığınız görünen ada göre alfabetik olarak görüntülenen **Hizmetler**bölümünde görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0435-258">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![Hizmetler penceresinde MyNewService.](./media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="d0435-260">Hizmeti başlatmak için hizmetin kısayol menüsünden **Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-260">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="d0435-261">Hizmeti durdurmak için hizmetin kısayol menüsünden **Durdur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-261">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="d0435-262">Seçim Hizmetinizi başlatmak ve durdurmak için komut satırından \*\*net start &lt; Service Name &gt; \*\* ve \*\*net stop &lt; hizmet adı &gt; \*\* komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0435-262">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="d0435-263">Hizmetinizin olay günlüğü çıkışını doğrulama</span><span class="sxs-lookup"><span data-stu-id="d0435-263">Verify the event log output of your service</span></span>

1. <span data-ttu-id="d0435-264">Windows 'ta **Olay Görüntüleyicisi** masaüstü uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="d0435-264">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="d0435-265">Windows Search çubuğuna *Olay Görüntüleyicisi* girin ve sonra arama sonuçlarından **Olay Görüntüleyicisi** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0435-265">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="d0435-266">Visual Studio 'da, **Görünüm** menüsünden **Sunucu Gezgini** açarak (veya **CTRL** + **alt** + **öğeleri**' ne basarak) ve yerel bilgisayarın **olay günlükleri** düğümünü genişleterek olay günlüklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-266">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="d0435-267">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="d0435-267">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="d0435-268">**MyNewLog** listesini bulun (veya komut satırı bağımsız değişkenleri ekleme yordamını Izlediyseniz **MyLogFile1** ) ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="d0435-268">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="d0435-269">Hizmetinizin gerçekleştirdiği iki eylem (başlatma ve durdurma) için girişleri görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0435-269">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi kullanın](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="d0435-271">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="d0435-271">Clean up resources</span></span>

<span data-ttu-id="d0435-272">Artık Windows hizmeti uygulamasına ihtiyacınız yoksa, bunu kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0435-272">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="d0435-273">Yönetim kimlik bilgileriyle **Visual Studio için geliştirici komut istemi** açın.</span><span class="sxs-lookup"><span data-stu-id="d0435-273">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="d0435-274">**Visual Studio için geliştirici komut istemi** penceresinde, projenizin çıkışını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="d0435-274">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="d0435-275">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="d0435-275">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="d0435-276">Hizmet başarıyla kaldırılırsa, komut hizmetinizin başarıyla kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d0435-276">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="d0435-277">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0435-277">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d0435-278">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d0435-278">Next steps</span></span>

<span data-ttu-id="d0435-279">Hizmeti oluşturduğumuz artık şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0435-279">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="d0435-280">Başkalarının Windows hizmetinizi yüklemek için kullanması için tek başına bir kurulum programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0435-280">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="d0435-281">[Wix araç takımını](https://wixtoolset.org/) kullanarak bir Windows hizmeti için yükleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0435-281">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="d0435-282">Diğer fikirler için bkz. [Yükleyici paketi oluşturma](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="d0435-282">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="d0435-283"><xref:System.ServiceProcess.ServiceController>Yüklemiş olduğunuz hizmete komutlar göndermenizi sağlayan bileşeni gezin.</span><span class="sxs-lookup"><span data-stu-id="d0435-283">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="d0435-284">Uygulama çalışırken olay günlüğü oluşturmak yerine, uygulamayı yüklerken bir olay günlüğü oluşturmak için bir yükleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0435-284">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="d0435-285">Uygulamayı kaldırdığınızda olay günlüğü yükleyici tarafından silinir.</span><span class="sxs-lookup"><span data-stu-id="d0435-285">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="d0435-286">Daha fazla bilgi için bkz. <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="d0435-286">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0435-287">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0435-287">See also</span></span>

- [<span data-ttu-id="d0435-288">Windows hizmeti uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d0435-288">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="d0435-289">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="d0435-289">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="d0435-290">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d0435-290">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="d0435-291">Hizmetler (Windows)</span><span class="sxs-lookup"><span data-stu-id="d0435-291">Services (Windows)</span></span>](/windows/desktop/Services/services)
