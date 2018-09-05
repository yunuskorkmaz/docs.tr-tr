---
title: 'İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: dc72b86a69d44ad282e30b000313b73211cad09c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671745"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="9e581-102">İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e581-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>

<span data-ttu-id="9e581-103">Bu konuda kullanım için bir Windows Presentation Foundation (WPF) denetimini Windows Forms tabanlı uygulamalarınızı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e581-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="9e581-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="9e581-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="9e581-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e581-105">Create the project.</span></span>

- <span data-ttu-id="9e581-106">Yeni bir WPF denetiminde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e581-106">Create a new WPF control.</span></span>

- <span data-ttu-id="9e581-107">Yeni WPF denetimi için bir Windows formu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e581-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="9e581-108">WPF denetiminde barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9e581-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e581-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9e581-109">Prerequisites</span></span>

<span data-ttu-id="9e581-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="9e581-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="9e581-111">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9e581-111">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="9e581-112">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e581-112">Creating the Project</span></span>

<span data-ttu-id="9e581-113">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9e581-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="9e581-114">Visual Studio'yu açın ve yeni bir **Windows Forms uygulaması (.NET Framework)** Visual Basic veya Visual C# adlı proje `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="9e581-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="9e581-115">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e581-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="9e581-116">Yeni bir WPF denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e581-116">Creating a New WPF Control</span></span>

<span data-ttu-id="9e581-117">Yeni bir WPF denetim oluşturma ve bunu projenize ekleyerek herhangi bir öğeyi projenize eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9e581-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="9e581-118">Windows Form Tasarımcısı adlı Denetim belirli bir türünü çalışır *bileşik denetim*, veya *kullanıcı denetimi*.</span><span class="sxs-lookup"><span data-stu-id="9e581-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="9e581-119">WPF kullanıcı denetimleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="9e581-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="9e581-120"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> WPF farklı olarak da adlandırılır Windows Forms tarafından sağlanan kullanıcı Denetim türü için tür <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e581-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="9e581-121">Yeni bir WPF denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9e581-121">To create a new WPF control</span></span>

1. <span data-ttu-id="9e581-122">İçinde **Çözüm Gezgini**, yeni bir **WPF kullanıcı denetimi kitaplığı (.NET Framework)** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="9e581-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="9e581-123">Denetim Kitaplığı için varsayılan adı kullanın `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="9e581-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="9e581-124">Varsayılan Denetim adı `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="9e581-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="9e581-125">Yeni denetim ekleme, aşağıdaki etkileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="9e581-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="9e581-126">Dosya UserControl1.xaml eklenir.</span><span class="sxs-lookup"><span data-stu-id="9e581-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="9e581-127">Dosya UserControl1.xaml.cs veya UserControl1.xaml.vb eklenir.</span><span class="sxs-lookup"><span data-stu-id="9e581-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="9e581-128">Bu dosya, arka plan kod olay işleyicileri ve diğer uygulaması içerir.</span><span class="sxs-lookup"><span data-stu-id="9e581-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="9e581-129">WPF derlemelerine başvurular eklenir.</span><span class="sxs-lookup"><span data-stu-id="9e581-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="9e581-130">Dosya UserControl1.xaml açılır [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e581-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="9e581-131">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="9e581-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="9e581-132">Daha fazla bilgi için [nasıl yapılır: seçin ve tasarım yüzeyinde taşımak öğeleri](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="9e581-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>

3. <span data-ttu-id="9e581-133">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine **200**.</span><span class="sxs-lookup"><span data-stu-id="9e581-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="9e581-134">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="9e581-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="9e581-135">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="9e581-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9e581-136">Genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9e581-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="9e581-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e581-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="9e581-138">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e581-138">Build the project.</span></span>

## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="9e581-139">Bir Windows forma bir WPF denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="9e581-139">Adding a WPF Control to a Windows Form</span></span>

<span data-ttu-id="9e581-140">Yeni WPF denetimi form üzerinde kullanılmaya hazırdır.</span><span class="sxs-lookup"><span data-stu-id="9e581-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="9e581-141">Windows Forms kullanan <xref:System.Windows.Forms.Integration.ElementHost> konak WPF içeriği için denetim.</span><span class="sxs-lookup"><span data-stu-id="9e581-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="9e581-142">Bir WPF denetiminde bir Windows forma eklemek için</span><span class="sxs-lookup"><span data-stu-id="9e581-142">To add a WPF control to a Windows Form</span></span>

1. <span data-ttu-id="9e581-143">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="9e581-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="9e581-144">İçinde **araç kutusu**, etiketlenmiş sekmeyi bulun **WPFUserControlLibrary WPF kullanıcı denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="9e581-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="9e581-145">Örneği sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="9e581-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="9e581-146">Bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi WPF denetimini barındırmak için bir form üzerinde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e581-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="9e581-147"><xref:System.Windows.Forms.Integration.ElementHost> Denetimine `elementHost1` ve **özellikleri** penceresinde görebilirsiniz, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="9e581-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="9e581-148">WPF derlemelerine başvurular projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="9e581-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="9e581-149">`elementHost1` Denetim barındırma seçeneklerini gösteren bir akıllı etiket paneli sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9e581-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="9e581-150">İçinde **ElementHost görevleri** akıllı etiket paneli, select **üst kapsayıcıya Yerleştir**.</span><span class="sxs-lookup"><span data-stu-id="9e581-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="9e581-151">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e581-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e581-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="9e581-152">Next Steps</span></span>

<span data-ttu-id="9e581-153">Windows Forms ve WPF farklı teknolojilerdir, ancak yakın çalışmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9e581-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="9e581-154">Daha zengin görünümünü ve davranışını uygulamalarınızda sağlamak için aşağıdakileri deneyin:</span><span class="sxs-lookup"><span data-stu-id="9e581-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="9e581-155">Bir WPF sayfasındaki bir Windows Forms denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="9e581-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="9e581-156">Daha fazla bilgi için [izlenecek yol: WPF'de Windows Forms denetimini barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="9e581-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="9e581-157">Windows Forms görsel stiller, WPF içeriği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9e581-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="9e581-158">Daha fazla bilgi için [nasıl yapılır: karma uygulamada görsel stilleri etkinleştirme](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="9e581-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="9e581-159">WPF İçerik stilini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9e581-159">Change the style of your WPF content.</span></span> <span data-ttu-id="9e581-160">Daha fazla bilgi için [izlenecek yol: WPF içeriği stil](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="9e581-160">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e581-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e581-161">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="9e581-162">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="9e581-162">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="9e581-163">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="9e581-163">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="9e581-164">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="9e581-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
