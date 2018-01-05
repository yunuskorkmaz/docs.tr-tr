---
title: "İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7731456cfcf35cd16b1df304fee4f4c138db84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="d4e67-102">İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e67-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="d4e67-103">Bu konu, Windows Forms tabanlı uygulamalarda kullanım için bir Windows Presentation Foundation (WPF) denetimini oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="d4e67-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="d4e67-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d4e67-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4e67-105">Create the project.</span></span>  
  
-   <span data-ttu-id="d4e67-106">Yeni bir WPF denetim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4e67-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="d4e67-107">Yeni WPF denetimi için Windows formu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4e67-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="d4e67-108">WPF denetimi içinde barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetim.</span><span class="sxs-lookup"><span data-stu-id="d4e67-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4e67-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d4e67-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d4e67-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d4e67-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d4e67-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4e67-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d4e67-112">Prerequisites</span></span>  
 <span data-ttu-id="d4e67-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="d4e67-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="d4e67-114">.</span><span class="sxs-lookup"><span data-stu-id="d4e67-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d4e67-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e67-115">Creating the Project</span></span>  
 <span data-ttu-id="d4e67-116">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="d4e67-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4e67-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d4e67-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4e67-118">To create the project</span></span>  
  
-   <span data-ttu-id="d4e67-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="d4e67-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="d4e67-120">Yeni bir WPF denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e67-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="d4e67-121">Yeni bir WPF denetim oluşturma ve projenize ekleme projenize başka bir öğe ekleme olarak kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="d4e67-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="d4e67-122">Belirli bir tür adlı denetimi ile Windows Form Tasarımcısı çalışır *bileşik denetim*, veya *kullanıcı denetimi*.</span><span class="sxs-lookup"><span data-stu-id="d4e67-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="d4e67-123">WPF kullanıcı denetimi hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="d4e67-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4e67-124"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> WPF olarak da adlandırılır Windows Forms tarafından sağlanan kullanıcı denetimi türü farklıdır türüyle <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4e67-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="d4e67-125">Yeni bir WPF denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4e67-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="d4e67-126">İçinde **Çözüm Gezgini**, yeni bir ekleme **WPF kullanıcı denetimi Kitaplığı** çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="d4e67-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="d4e67-127">Denetim Kitaplığı için varsayılan adı kullanacak `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="d4e67-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="d4e67-128">Varsayılan Denetim adı `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d4e67-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="d4e67-129">Yeni denetim ekleme aşağıdaki etkileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="d4e67-130">Dosya da UserControl1.XAML'i eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="d4e67-131">Dosya UserControl1.xaml.cs veya UserControl1.xaml.vb eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="d4e67-132">Bu dosya, arka plan koduna olay işleyicileri ve diğer uygulama içerir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="d4e67-133">WPF derlemelerine başvurular eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="d4e67-134">Dosya da UserControl1.XAML'i açılır [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4e67-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="d4e67-135">Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="d4e67-136">Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="d4e67-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="d4e67-137">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="d4e67-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="d4e67-138">Gelen **araç**, sürükleyin bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> tasarım yüzeyine denetim.</span><span class="sxs-lookup"><span data-stu-id="d4e67-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="d4e67-139">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="d4e67-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4e67-140">Genel olarak, daha karmaşık WPF içeriği barındırma.</span><span class="sxs-lookup"><span data-stu-id="d4e67-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="d4e67-141"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca tanım yalnızca amacıyla burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4e67-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="d4e67-142">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4e67-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="d4e67-143">Bir Windows formu WPF denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="d4e67-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="d4e67-144">Yeni WPF denetiminizi formdaki kullanılmaya hazırdır.</span><span class="sxs-lookup"><span data-stu-id="d4e67-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="d4e67-145">Windows Forms kullanan <xref:System.Windows.Forms.Integration.ElementHost> denetlemek için konak WPF içeriği</span><span class="sxs-lookup"><span data-stu-id="d4e67-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="d4e67-146">Bir WPF denetimi için Windows formu eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4e67-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="d4e67-147">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="d4e67-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d4e67-148">İçinde **araç**, etiketli sekmesini bulmak **WPFUserControlLibrary WPF kullanıcı denetimi**.</span><span class="sxs-lookup"><span data-stu-id="d4e67-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="d4e67-149">Bir örneğini sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="d4e67-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="d4e67-150">Bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi WPF denetimi barındırmak için form üzerinde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4e67-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="d4e67-151"><xref:System.Windows.Forms.Integration.ElementHost> Denetim adlandırılan `elementHost1` ve **özellikleri** penceresinde görebilirsiniz kendi <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği ayarlanmış **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="d4e67-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="d4e67-152">WPF derlemelerine başvurular projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="d4e67-153">`elementHost1` Denetim kullanılabilir barındırma seçenekleri gösterilir bir akıllı etiket panel sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="d4e67-154">İçinde **ElementHost görevleri** akıllı etiket paneli, select **Ana kapsayıcıda yerleştir**.</span><span class="sxs-lookup"><span data-stu-id="d4e67-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="d4e67-155">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d4e67-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d4e67-156">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d4e67-156">Next Steps</span></span>  
 <span data-ttu-id="d4e67-157">Windows Forms ve WPF farklı teknolojilerdir ancak yakından birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d4e67-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="d4e67-158">Daha zengin bir görünüm ve davranış uygulamalarınızda sağlamak için aşağıdakileri deneyin.</span><span class="sxs-lookup"><span data-stu-id="d4e67-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="d4e67-159">Windows Forms denetimini bir WPF sayfada barındırır.</span><span class="sxs-lookup"><span data-stu-id="d4e67-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="d4e67-160">Daha fazla bilgi için bkz: [izlenecek yol: WPF bir Windows Forms denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="d4e67-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="d4e67-161">Windows Forms görsel stiller, WPF içeriği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d4e67-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="d4e67-162">Daha fazla bilgi için bkz: [nasıl yapılır: görsel stiller etkinleştirmek karma uygulamada](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="d4e67-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="d4e67-163">WPF içeriği stilini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4e67-163">Change the style of your WPF content.</span></span> <span data-ttu-id="d4e67-164">Daha fazla bilgi için bkz: [izlenecek yol: WPF içeriği stil oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="d4e67-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e67-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e67-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d4e67-166">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d4e67-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="d4e67-167">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d4e67-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="d4e67-168">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d4e67-168">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
