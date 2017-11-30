---
title: "Denetim ve Bileşen Yazmada Sorun Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="069fa-102">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="069fa-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="069fa-103">Bu konu, bileşenleri ve denetimleri geliştirirken ortaya aşağıdaki ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="069fa-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="069fa-104">Daha fazla bilgi için bkz: [bileşenlerle programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="069fa-104">For more information, see [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="069fa-105">Denetim araç kutusuna eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="069fa-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="069fa-106">Windows Forms kullanıcı denetimi veya bileşeni hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="069fa-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="069fa-107">İki kez devralınan denetimi veya bileşeni olay tetiklenir</span><span class="sxs-lookup"><span data-stu-id="069fa-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="069fa-108">Tasarım zamanı hata: "bileşeni oluşturulamadı '*bileşen adı*'"</span><span class="sxs-lookup"><span data-stu-id="069fa-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="069fa-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="069fa-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="069fa-110">Bileşen simgesi Araç Kutusu'nda görünmez</span><span class="sxs-lookup"><span data-stu-id="069fa-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="069fa-111">Denetim araç kutusuna eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="069fa-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="069fa-112">Başka bir projede oluşturulan özel bir denetim veya bir üçüncü taraf denetimine eklemek isteyip istemediğinizi **araç**, bunu el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="069fa-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="069fa-113">Geçerli projenin denetimi veya bileşeni içeriyorsa, bu görüntülenmelidir **araç** otomatik olarak.</span><span class="sxs-lookup"><span data-stu-id="069fa-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="069fa-114">Daha fazla bilgi için bkz: [izlenecek yol: araç kutusunu özel bileşenlerle'otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="069fa-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="069fa-115">Araç kutusu denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="069fa-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="069fa-116">Sağ **araç** ve kısayol menüsünden seçin **öğeleri Seç**.</span><span class="sxs-lookup"><span data-stu-id="069fa-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="069fa-117">İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, bileşen ekleyin:</span><span class="sxs-lookup"><span data-stu-id="069fa-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="069fa-118">Bir .NET Framework bileşenini veya denetim eklemek istiyorsanız, **.NET Framework bileşenlerini** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="069fa-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="069fa-119">– veya –</span><span class="sxs-lookup"><span data-stu-id="069fa-119">– or –</span></span>  
  
    -   <span data-ttu-id="069fa-120">Bir COM bileşeni veya ActiveX denetimi eklemek istiyorsanız, **COM bileşenlerini** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="069fa-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="069fa-121">İletişim kutusunda, Denetim listeleniyorsa, seçilir ve ardından onaylamak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="069fa-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="069fa-122">Denetim eklenir **araç**.</span><span class="sxs-lookup"><span data-stu-id="069fa-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="069fa-123">Denetim iletişim kutusunda listede yoksa, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="069fa-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="069fa-124">Tıklatın **Gözat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="069fa-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="069fa-125">Denetim içeren .dll dosyasını içeren klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="069fa-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="069fa-126">.Dll dosyasını tıklatıp **açık**.</span><span class="sxs-lookup"><span data-stu-id="069fa-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="069fa-127">Denetim iletişim kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="069fa-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="069fa-128">Denetim seçilir ve ardından onaylamak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="069fa-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="069fa-129">Denetim eklenen **araç**.</span><span class="sxs-lookup"><span data-stu-id="069fa-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="069fa-130">Windows Forms kullanıcı denetimi veya bileşeni hata ayıklaması yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="069fa-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="069fa-131">Denetim türetilen varsa <xref:System.Windows.Forms.UserControl> sınıfı, çalışma zamanı davranışını test kapsayıcısı ile ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="069fa-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="069fa-132">Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="069fa-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="069fa-133">Diğer özel denetimleri ve bileşenleri tek başına projeleri değildir.</span><span class="sxs-lookup"><span data-stu-id="069fa-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="069fa-134">Bir Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="069fa-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="069fa-135">Bir denetimi veya bileşeni hata ayıklamak için bir Windows Forms projesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="069fa-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="069fa-136">Bir denetimi veya bileşeni hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="069fa-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="069fa-137">Gelen **yapı** menüsünde tıklatın **yapı çözümü** çözümünüzü derlemek için.</span><span class="sxs-lookup"><span data-stu-id="069fa-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="069fa-138">Gelen **dosya** menüsünde seçin **Ekle**ve ardından **yeni proje** uygulamanız için bir test projesi eklemek için.</span><span class="sxs-lookup"><span data-stu-id="069fa-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="069fa-139">İçinde **Yeni Proje Ekle** Seç iletişim kutusu **Windows uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="069fa-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="069fa-140">İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni proje için düğüm.</span><span class="sxs-lookup"><span data-stu-id="069fa-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="069fa-141">Kısayol menüsünde **Başvuru Ekle** denetimi veya bileşeni içeren projeyi bir başvuru eklemek için.</span><span class="sxs-lookup"><span data-stu-id="069fa-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="069fa-142">Test projesinde denetimi veya bileşeni örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="069fa-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="069fa-143">Bileşeniniz ise **araç**Tasarımcı yüzeyine sürükleyin ya da örneği aşağıdaki kod örneğinde gösterildiği gibi program aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="069fa-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="069fa-144">Artık denetimi veya bileşeni zamanki ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="069fa-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="069fa-145">Hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio) ve [izlenecek yol: tasarım zamanında özel Windows Forms denetimleri hata ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="069fa-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="069fa-146">İki kez devralınan denetimi veya bileşeni olay tetiklenir</span><span class="sxs-lookup"><span data-stu-id="069fa-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="069fa-147">Bu yinelenen bir nedeniyle olasıdır `Handles` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="069fa-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="069fa-148">Daha fazla bilgi için bkz: [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="069fa-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="069fa-149">Tasarım zamanı hata: "başarısız bileşeni 'Bileşen adı' oluşturmak için"</span><span class="sxs-lookup"><span data-stu-id="069fa-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="069fa-150">Hiçbir parametre varsayılan bir oluşturucu bileşeni veya denetimi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="069fa-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="069fa-151">Tasarım ortamında bileşeni veya denetimi örneğini oluşturduğunda, herhangi bir parametre için parametre almaz Oluşturucusu aşırı sağlamak denemez.</span><span class="sxs-lookup"><span data-stu-id="069fa-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="069fa-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="069fa-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="069fa-153"><xref:System.STAThreadAttribute> Windows Forms tek iş parçacıklı model kullanan ortak dil çalışma zamanı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="069fa-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="069fa-154">Windows Forms uygulamanızın için bu öznitelik uygulamazsanız beklenmedik davranışlara karşılaşabilirsiniz `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="069fa-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="069fa-155">Gibi denetimlerin için arka plan görüntüleri gibi görünmeyebilir <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="069fa-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="069fa-156">Bazı denetimler de doğru otomatik tamamlama ve sürükle ve bırak davranışı için bu öznitelik gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="069fa-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="069fa-157">Bileşen simgesi Araç Kutusu'nda görünmez</span><span class="sxs-lookup"><span data-stu-id="069fa-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="069fa-158">Kullandığınızda <xref:System.Drawing.ToolboxBitmapAttribute> özel bileşeni ile bir simge ilişkilendirmek için bit eşlem araç kutusunu otomatik olarak oluşturulur bileşenleri için görünmez.</span><span class="sxs-lookup"><span data-stu-id="069fa-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="069fa-159">Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="069fa-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="069fa-160">Daha fazla bilgi için bkz: [nasıl yapılır: bir denetim için araç kutusu bit eşlemi sağlamak](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="069fa-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069fa-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="069fa-161">See Also</span></span>  
 [<span data-ttu-id="069fa-162">Windows Forms denetimleri geliştirme tasarım zamanında</span><span class="sxs-lookup"><span data-stu-id="069fa-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="069fa-163">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="069fa-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="069fa-164">Nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="069fa-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="069fa-165">İzlenecek yol: Özel Windows hata ayıklama tasarım zamanında Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="069fa-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="069fa-166">Bileşen yazma</span><span class="sxs-lookup"><span data-stu-id="069fa-166">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="069fa-167">Tasarım zamanı geliştirme sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="069fa-167">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="069fa-168">Bileşenleri ile programlama</span><span class="sxs-lookup"><span data-stu-id="069fa-168">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
