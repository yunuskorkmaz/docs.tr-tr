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
ms.openlocfilehash: 6494a154b9b4bd5bf29fc0e2fbd0b4e5e84550ff
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364169"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="2dd05-102">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="2dd05-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="2dd05-103">Bu konuda, bileşenleri ve denetimleri geliştirirken ortaya çıkan aşağıdaki yaygın sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="2dd05-104">Daha fazla bilgi için bkz. [bileşenlerle programlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="2dd05-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="2dd05-105">Araç kutusu 'na denetim eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="2dd05-106">Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="2dd05-107">Devralınan denetimde veya bileşende olay Iki kez getirilir</span><span class="sxs-lookup"><span data-stu-id="2dd05-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="2dd05-108">Tasarım zamanı hatası: "'" Bileşen*adı*' "bileşeni oluşturulamadı</span><span class="sxs-lookup"><span data-stu-id="2dd05-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="2dd05-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="2dd05-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="2dd05-110">Bileşen simgesi araç kutusunda görünmüyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="2dd05-111">Araç kutusu 'na denetim eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="2dd05-112">**Araç kutusu**için başka bir projede veya üçüncü taraf denetiminde oluşturduğunuz özel bir denetim eklemek istiyorsanız, bunu el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="2dd05-113">Geçerli proje denetim veya bileşeninizi içeriyorsa **araç kutusunda** otomatik olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="2dd05-114">Daha fazla bilgi için bkz [. İzlenecek yol: Araç kutusunu özel bileşenlerle](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)otomatik olarak doldurma.</span><span class="sxs-lookup"><span data-stu-id="2dd05-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="2dd05-115">Araç kutusuna denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="2dd05-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="2dd05-116">**Araç kutusuna** sağ tıklayıp kısayol menüsünden **öğeleri seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="2dd05-117">**Araç kutusu öğelerini Seç** iletişim kutusunda, bileşeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2dd05-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="2dd05-118">.NET Framework bir bileşen veya denetim eklemek istiyorsanız, **.NET Framework bileşenleri** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="2dd05-119">– veya –</span><span class="sxs-lookup"><span data-stu-id="2dd05-119">– or –</span></span>  
  
    - <span data-ttu-id="2dd05-120">COM bileşeni veya ActiveX denetimi eklemek istiyorsanız **com bileşenleri** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="2dd05-121">Denetiminiz iletişim kutusunda listeleniyorsa, seçili olduğunu onaylayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2dd05-122">Denetim **araç kutusuna**eklenir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="2dd05-123">Denetiminiz iletişim kutusunda listelenmiyorsa, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="2dd05-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="2dd05-124">**Araştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="2dd05-125">Denetiminizi içeren. dll dosyasını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="2dd05-126">. Dll dosyasını seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="2dd05-127">Denetiminiz iletişim kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="2dd05-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="2dd05-128">Denetiminizin seçili olduğunu doğrulayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="2dd05-129">Denetiminiz **araç kutusuna**eklenir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="2dd05-130">Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="2dd05-131">Denetiminiz <xref:System.Windows.Forms.UserControl> sınıftan türetildiğinden, çalışma zamanı davranışının hata ayıklaması için test kapsayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="2dd05-132">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="2dd05-133">Diğer özel denetimler ve bileşenler tek başına projeler değildir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="2dd05-134">Bunlar, Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dd05-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="2dd05-135">Bir denetimin veya bileşenin hatalarını ayıklamak için bir Windows Forms projesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="2dd05-136">Bir denetimin veya bileşenin hatalarını ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="2dd05-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="2dd05-137">Çözümünüzü derlemek için **Build (derleme** ) menüsünde **çözüm oluştur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="2dd05-138">Uygulamanıza bir test projesi eklemek için **Dosya** menüsünden **Ekle**' yi ve ardından **Yeni proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="2dd05-139">**Yeni Proje Ekle** iletişim kutusunda proje türü Için **Windows uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="2dd05-140">**Çözüm Gezgini**, yeni proje için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="2dd05-141">Denetim veya bileşen içeren projeye başvuru eklemek için kısayol menüsünde **Başvuru Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="2dd05-142">Test projesinde denetiminizin veya bileşeninizin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2dd05-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="2dd05-143">Bileşeniniz **araç kutusunda**ise tasarımcı yüzeyine sürükleyebilirsiniz veya aşağıdaki kod örneğinde gösterildiği gibi örneği programlı bir şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="2dd05-144">Artık, denetim veya bileşeninizdeki hataları her zamanki gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="2dd05-145">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio) ve [izlenecek yol: Tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)özel Windows Forms Denetimlerinde hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="2dd05-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="2dd05-146">Devralınan denetimde veya bileşende olay Iki kez getirilir</span><span class="sxs-lookup"><span data-stu-id="2dd05-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="2dd05-147">Bunun nedeni, bir yinelenen `Handles` yan tümcesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="2dd05-148">Daha fazla bilgi için bkz. [Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="2dd05-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="2dd05-149">Tasarım zamanı hatası: "'" Bileşen adı ' "bileşeni oluşturulamadı</span><span class="sxs-lookup"><span data-stu-id="2dd05-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="2dd05-150">Bileşeninizin veya denetiminizin parametresiz bir Oluşturucu sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-150">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="2dd05-151">Tasarım ortamı, bileşeninizin veya denetiminizin bir örneğini oluşturduğunda, parametreleri alan Oluşturucu aşırı yüklerini parametre sağlamaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="2dd05-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="2dd05-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="2dd05-153">, <xref:System.STAThreadAttribute> Windows Forms tek iş parçacıklı grup modelini kullanan ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="2dd05-154">Bu özniteliği Windows Forms uygulamanızın `Main` yöntemine uygulamadıysanız istenmeden bir davranış fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="2dd05-155">Örneğin, gibi <xref:System.Windows.Forms.ListView>denetimler için arka plan görüntüleri görünmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="2dd05-156">Bazı denetimler, doğru otomatik tamamlama ve sürükle ve bırak davranışı için de bu özniteliği gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="2dd05-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="2dd05-157">Bileşen simgesi araç kutusunda görünmüyor</span><span class="sxs-lookup"><span data-stu-id="2dd05-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="2dd05-158">Özel bileşeninizdeki <xref:System.Drawing.ToolboxBitmapAttribute> bir simgeyi ilişkilendirmek için kullandığınızda, otomatik olarak oluşturulmuş bileşenler için araç kutusunda bit eşlem görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="2dd05-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="2dd05-159">Bit eşlemi görmek için **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak denetimi yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2dd05-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="2dd05-160">Daha fazla bilgi için [nasıl yapılır: Bir denetim](how-to-provide-a-toolbox-bitmap-for-a-control.md)Için araç kutusu bit eşlemi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2dd05-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd05-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd05-161">See also</span></span>

- [<span data-ttu-id="2dd05-162">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="2dd05-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="2dd05-163">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="2dd05-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="2dd05-164">Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="2dd05-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="2dd05-165">İzlenecek yol: Tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2dd05-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="2dd05-166">[Bileşen yazma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2dd05-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="2dd05-167">[Tasarım zamanı geliştirme sorunlarını giderme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2dd05-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
