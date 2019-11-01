---
title: Denetim ve Bileşen Yazmada Sorun Giderme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d3aa715590a10391bafa08a85265842ee8cedfb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197110"
---
# <a name="troubleshoot-control-and-component-authoring"></a><span data-ttu-id="63e39-102">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="63e39-102">Troubleshoot Control and Component Authoring</span></span>

<span data-ttu-id="63e39-103">Bu konuda, bileşenleri ve denetimleri geliştirirken ortaya çıkan aşağıdaki yaygın sorunlar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="63e39-103">This topic lists the following common problems that arise when developing components and controls:</span></span>

- <span data-ttu-id="63e39-104">Araç kutusu 'na denetim eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="63e39-104">Cannot Add Control to Toolbox</span></span>

- <span data-ttu-id="63e39-105">Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="63e39-105">Cannot Debug the Windows Forms User Control or Component</span></span>

- <span data-ttu-id="63e39-106">Devralınan denetimde veya bileşende olay Iki kez getirilir</span><span class="sxs-lookup"><span data-stu-id="63e39-106">Event Is Raised Twice in Inherited Control or Component</span></span>

- <span data-ttu-id="63e39-107">Tasarım zamanı hatası: "' ' bileşen*adı*'" bileşeni oluşturulamadı</span><span class="sxs-lookup"><span data-stu-id="63e39-107">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>

- <span data-ttu-id="63e39-108">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="63e39-108">STAThreadAttribute</span></span>

- <span data-ttu-id="63e39-109">Bileşen simgesi araç kutusunda görünmüyor</span><span class="sxs-lookup"><span data-stu-id="63e39-109">Component Icon Does Not Appear in Toolbox</span></span>

## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="63e39-110">Araç kutusu 'na denetim eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="63e39-110">Cannot Add Control to Toolbox</span></span>

<span data-ttu-id="63e39-111">**Araç kutusu**için başka bir projede veya üçüncü taraf denetiminde oluşturduğunuz özel bir denetim eklemek istiyorsanız, bunu el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e39-111">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="63e39-112">Geçerli proje denetim veya bileşeninizi içeriyorsa **araç kutusunda** otomatik olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="63e39-112">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="63e39-113">Daha fazla bilgi için bkz. [Izlenecek yol: araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="63e39-113">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="63e39-114">Araç kutusuna denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="63e39-114">To add a control to the Toolbox</span></span>

1. <span data-ttu-id="63e39-115">**Araç kutusuna** sağ tıklayıp kısayol menüsünden **öğeleri seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="63e39-115">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>

2. <span data-ttu-id="63e39-116">**Araç kutusu öğelerini Seç** iletişim kutusunda, bileşeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="63e39-116">In the **Choose Toolbox Items** dialog box, add the component:</span></span>

    - <span data-ttu-id="63e39-117">.NET Framework bir bileşen veya denetim eklemek istiyorsanız, **.NET Framework bileşenleri** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-117">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>

         <span data-ttu-id="63e39-118">veya</span><span class="sxs-lookup"><span data-stu-id="63e39-118">– or –</span></span>

    - <span data-ttu-id="63e39-119">COM bileşeni veya ActiveX denetimi eklemek istiyorsanız **com bileşenleri** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-119">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>

3. <span data-ttu-id="63e39-120">Denetiminiz iletişim kutusunda listeleniyorsa, seçili olduğunu onaylayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-120">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>

     <span data-ttu-id="63e39-121">Denetim **araç kutusuna**eklenir.</span><span class="sxs-lookup"><span data-stu-id="63e39-121">The control is added to the **Toolbox**.</span></span>

4. <span data-ttu-id="63e39-122">Denetiminiz iletişim kutusunda listelenmiyorsa, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="63e39-122">If your control is not listed in the dialog box, do the following:</span></span>

    1. <span data-ttu-id="63e39-123">**Araştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-123">Click the **Browse** button.</span></span>

    2. <span data-ttu-id="63e39-124">Denetiminizi içeren. dll dosyasını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="63e39-124">Browse to the folder that contains the .dll file that contains your control.</span></span>

    3. <span data-ttu-id="63e39-125">. Dll dosyasını seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-125">Select the .dll file and click **Open**.</span></span>

         <span data-ttu-id="63e39-126">Denetiminiz iletişim kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="63e39-126">Your control appears in the dialog box.</span></span>

    4. <span data-ttu-id="63e39-127">Denetiminizin seçili olduğunu doğrulayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-127">Confirm that your control is selected, and then click **OK**.</span></span>

         <span data-ttu-id="63e39-128">Denetiminiz **araç kutusuna**eklenir.</span><span class="sxs-lookup"><span data-stu-id="63e39-128">Your control is added to the **Toolbox**.</span></span>

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="63e39-129">Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="63e39-129">Cannot Debug the Windows Forms User Control or Component</span></span>

<span data-ttu-id="63e39-130">Denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türetildiğinden, çalışma zamanı davranışının test kapsayıcısı ile hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63e39-130">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="63e39-131">Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="63e39-131">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="63e39-132">Diğer özel denetimler ve bileşenler tek başına projeler değildir.</span><span class="sxs-lookup"><span data-stu-id="63e39-132">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="63e39-133">Bunlar, Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63e39-133">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="63e39-134">Bir denetimin veya bileşenin hatalarını ayıklamak için bir Windows Forms projesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e39-134">To debug a control or component, you must add it to a Windows Forms project.</span></span>

### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="63e39-135">Bir denetimin veya bileşenin hatalarını ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="63e39-135">To debug a control or component</span></span>

1. <span data-ttu-id="63e39-136">Çözümünüzü derlemek için **Build (derleme** ) menüsünde **çözüm oluştur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-136">From the **Build** menu, click **Build Solution** to build your solution.</span></span>

2. <span data-ttu-id="63e39-137">Uygulamanıza bir test projesi eklemek için **Dosya** menüsünden **Ekle**' yi ve ardından **Yeni proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="63e39-137">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>

3. <span data-ttu-id="63e39-138">**Yeni Proje Ekle** iletişim kutusunda proje türü Için **Windows uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="63e39-138">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>

4. <span data-ttu-id="63e39-139">**Çözüm Gezgini**, yeni proje için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-139">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="63e39-140">Denetim veya bileşen içeren projeye başvuru eklemek için kısayol menüsünde **Başvuru Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63e39-140">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>

5. <span data-ttu-id="63e39-141">Test projesinde denetiminizin veya bileşeninizin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63e39-141">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="63e39-142">Bileşeniniz **araç kutusunda**ise tasarımcı yüzeyine sürükleyebilirsiniz veya aşağıdaki kod örneğinde gösterildiği gibi örneği programlı bir şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63e39-142">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   <span data-ttu-id="63e39-143">Artık, denetim veya bileşeninizdeki hataları her zamanki gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63e39-143">You can now debug your control or component as usual.</span></span>

<span data-ttu-id="63e39-144">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](/visualstudio/debugger/debugger-feature-tour) ve [Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="63e39-144">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="63e39-145">Devralınan denetimde veya bileşende olay Iki kez getirilir</span><span class="sxs-lookup"><span data-stu-id="63e39-145">Event Is Raised Twice in Inherited Control or Component</span></span>

<span data-ttu-id="63e39-146">Bunun nedeni muhtemelen yinelenen bir `Handles` yan tümcesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="63e39-146">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="63e39-147">Daha fazla bilgi için bkz. [Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="63e39-147">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="63e39-148">Tasarım zamanı hatası: "' ' bileşen adı '" bileşeni oluşturulamadı</span><span class="sxs-lookup"><span data-stu-id="63e39-148">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>

<span data-ttu-id="63e39-149">Bileşeninizin veya denetiminizin parametresiz bir Oluşturucu sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e39-149">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="63e39-150">Tasarım ortamı, bileşeninizin veya denetiminizin bir örneğini oluşturduğunda, parametreleri alan Oluşturucu aşırı yüklerini parametre sağlamaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="63e39-150">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>

## <a name="stathreadattribute"></a><span data-ttu-id="63e39-151">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="63e39-151">STAThreadAttribute</span></span>

<span data-ttu-id="63e39-152"><xref:System.STAThreadAttribute>, Windows Forms tek iş parçacıklı grup modelini kullanan ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="63e39-152">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="63e39-153">Bu özniteliği Windows Forms uygulamanızın `Main` yöntemine uygulamadıysanız istenmeden bir davranış fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63e39-153">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="63e39-154">Örneğin, arka plan görüntüleri <xref:System.Windows.Forms.ListView>gibi denetimler için görünmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="63e39-154">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="63e39-155">Bazı denetimler, doğru otomatik tamamlama ve sürükle ve bırak davranışı için de bu özniteliği gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="63e39-155">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>

## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="63e39-156">Bileşen simgesi araç kutusunda görünmüyor</span><span class="sxs-lookup"><span data-stu-id="63e39-156">Component Icon Does Not Appear in Toolbox</span></span>

<span data-ttu-id="63e39-157">Özel bileşeninizdeki bir simgeyi ilişkilendirmek için <xref:System.Drawing.ToolboxBitmapAttribute> kullandığınızda, otomatik olarak oluşturulmuş bileşenler için araç kutusunda bit eşlem görünmez.</span><span class="sxs-lookup"><span data-stu-id="63e39-157">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="63e39-158">Bit eşlemi görmek için **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak denetimi yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="63e39-158">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="63e39-159">Daha fazla bilgi için bkz. [nasıl yapılır: bir denetim Için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="63e39-159">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63e39-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63e39-160">See also</span></span>

- [<span data-ttu-id="63e39-161">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="63e39-161">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="63e39-162">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="63e39-162">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="63e39-163">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="63e39-163">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="63e39-164">İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="63e39-164">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
