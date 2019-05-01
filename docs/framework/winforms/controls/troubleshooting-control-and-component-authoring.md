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
ms.openlocfilehash: 3ae8a889bf69913d234e31804335ddb08560c30c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009220"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="6208b-102">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="6208b-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="6208b-103">Bu konu, bileşenlerin ve denetimlerin geliştirme ortaya çıkan aşağıdaki ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="6208b-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="6208b-104">Daha fazla bilgi için [bileşenler ile programlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="6208b-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="6208b-105">Denetimi araç kutusuna eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="6208b-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="6208b-106">Windows Forms kullanıcı denetimi veya bileşen hataları ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="6208b-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="6208b-107">İki kez devralınan denetim veya bileşen olay tetiklenir</span><span class="sxs-lookup"><span data-stu-id="6208b-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="6208b-108">Tasarım zamanı hata: "Bileşeni oluşturulamadı. '*bileşen adı*'"</span><span class="sxs-lookup"><span data-stu-id="6208b-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="6208b-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="6208b-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="6208b-110">Bileşen simgesi Araç Kutusu'nda görünmez</span><span class="sxs-lookup"><span data-stu-id="6208b-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="6208b-111">Denetimi araç kutusuna eklenemiyor</span><span class="sxs-lookup"><span data-stu-id="6208b-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="6208b-112">Başka bir proje tarafından oluşturulan özel bir denetim veya üçüncü taraf denetime eklemek isteyip istemediğimi **araç kutusu**, bunu el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6208b-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="6208b-113">Geçerli proje denetim veya bileşen içeriyorsa, içinde görünmelidir **araç kutusu** otomatik olarak.</span><span class="sxs-lookup"><span data-stu-id="6208b-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="6208b-114">Daha fazla bilgi için [izlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="6208b-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="6208b-115">Araç kutusuna denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="6208b-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="6208b-116">Sağ **araç kutusu** ve kısayol menüsünden seçin **öğelerini Seç**.</span><span class="sxs-lookup"><span data-stu-id="6208b-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="6208b-117">İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, bileşen ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6208b-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="6208b-118">Bir .NET Framework bileşeni veya denetimi eklemek istiyorsanız, tıklayın **.NET Framework bileşenlerini** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6208b-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="6208b-119">– veya –</span><span class="sxs-lookup"><span data-stu-id="6208b-119">– or –</span></span>  
  
    - <span data-ttu-id="6208b-120">Bir COM bileşeni ya da ActiveX denetiminden eklemek istiyorsanız, tıklayın **COM bileşenlerini** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6208b-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="6208b-121">Denetim iletişim kutusunda listede yoksa seçilir ve ardından onaylamak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6208b-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6208b-122">Denetim eklenir **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="6208b-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="6208b-123">Denetim iletişim kutusunda listede yoksa, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="6208b-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="6208b-124">Tıklayın **Gözat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6208b-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="6208b-125">Denetim içeren .dll dosyasını içeren klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="6208b-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="6208b-126">.Dll dosyasını seçin ve tıklayın **açık**.</span><span class="sxs-lookup"><span data-stu-id="6208b-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="6208b-127">Denetim iletişim kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6208b-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="6208b-128">Denetiminiz seçilir ve ardından onaylamak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6208b-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="6208b-129">Denetim eklenir **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="6208b-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="6208b-130">Windows Forms kullanıcı denetimi veya bileşen hataları ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="6208b-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="6208b-131">Türetilen denetiminiz varsa <xref:System.Windows.Forms.UserControl> sınıfı, çalışma zamanı davranışını test kapsayıcısı ile hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6208b-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="6208b-132">Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6208b-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="6208b-133">Diğer özel denetimleri ve bileşenleri tek başına projeleri değildir.</span><span class="sxs-lookup"><span data-stu-id="6208b-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="6208b-134">Bir Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6208b-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="6208b-135">Bir denetim veya bileşen hatalarını ayıklamak için bir Windows Forms projesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6208b-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="6208b-136">Bir denetim veya bileşen hatalarını ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="6208b-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="6208b-137">Gelen **derleme** menüsünde tıklatın **Çözümü Derle** çözümünüzü derlemek için.</span><span class="sxs-lookup"><span data-stu-id="6208b-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="6208b-138">Gelen **dosya** menüsünde seçin **Ekle**, ardından **yeni proje** uygulamanız için bir test projesi eklemek için.</span><span class="sxs-lookup"><span data-stu-id="6208b-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="6208b-139">İçinde **Yeni Proje Ekle** Seç iletişim kutusu **Windows uygulama** proje türü için.</span><span class="sxs-lookup"><span data-stu-id="6208b-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="6208b-140">İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni proje için düğüm.</span><span class="sxs-lookup"><span data-stu-id="6208b-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="6208b-141">Kısayol menüsünde **Başvuru Ekle** denetim veya bileşen içeren projeye bir başvuru eklemek için.</span><span class="sxs-lookup"><span data-stu-id="6208b-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="6208b-142">Test projesinde bir denetim veya bileşen örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6208b-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="6208b-143">Bileşeniniz ise **araç kutusu**, Tasarımcı yüzeyine sürükleyin veya örneği aşağıdaki kod örneğinde gösterildiği gibi program aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6208b-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="6208b-144">Artık denetim veya bileşen zamanki ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6208b-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="6208b-145">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio) ve [izlenecek yol: Tasarım zamanında Forms denetimleri özel Windows hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6208b-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="6208b-146">İki kez devralınan denetim veya bileşen olay tetiklenir</span><span class="sxs-lookup"><span data-stu-id="6208b-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="6208b-147">Yinelenen nedeni büyük olasılıkla budur `Handles` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6208b-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="6208b-148">Daha fazla bilgi için [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="6208b-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="6208b-149">Tasarım zamanı hata: "Bileşen 'Bileşeni adı' oluşturma başarısız oldu"</span><span class="sxs-lookup"><span data-stu-id="6208b-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="6208b-150">Varsayılan bir parametresiz oluşturucu bileşeni veya denetimi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6208b-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="6208b-151">Tasarım ortamı bileşeni veya denetimi örneğini oluşturduğunda, parametre alan bir oluşturucu aşırı yüklemeleri için herhangi bir parametre sağlamak denemez.</span><span class="sxs-lookup"><span data-stu-id="6208b-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="6208b-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="6208b-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="6208b-153"><xref:System.STAThreadAttribute> Windows Forms tek kullanımlık apartman modeli kullanan ortak dil çalışma zamanı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="6208b-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="6208b-154">Bu öznitelik Windows Forms uygulamanızın için uygulamazsanız istenmeyen davranışı fark edebilirsiniz `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6208b-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="6208b-155">Gibi denetimlerin için arka plan görüntüleri gibi görünmeyebilir <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="6208b-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="6208b-156">Bazı denetimler de doğru otomatik tamamlama ve sürükle-bırak davranışı için bu öznitelik gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="6208b-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="6208b-157">Bileşen simgesi Araç Kutusu'nda görünmez</span><span class="sxs-lookup"><span data-stu-id="6208b-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="6208b-158">Kullanırken <xref:System.Drawing.ToolboxBitmapAttribute> özel bileşeniniz ile bir simge ilişkilendirmek için bit eşlem araç kutusunu otomatik olarak oluşturulan bileşenler için görünmez.</span><span class="sxs-lookup"><span data-stu-id="6208b-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="6208b-159">Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6208b-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="6208b-160">Daha fazla bilgi için [nasıl yapılır: Bir denetim için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="6208b-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6208b-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6208b-161">See also</span></span>

- [<span data-ttu-id="6208b-162">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="6208b-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="6208b-163">İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma</span><span class="sxs-lookup"><span data-stu-id="6208b-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="6208b-164">Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="6208b-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="6208b-165">İzlenecek yol: Hata ayıklama özel Windows Forms denetimleri tasarım zamanında</span><span class="sxs-lookup"><span data-stu-id="6208b-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="6208b-166">[Bileşen yazma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6208b-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="6208b-167">[Tasarım zamanı geliştirme sorunlarını giderme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6208b-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
