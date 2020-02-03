---
title: Windows Forms yeni WPF Içeriği oluştur
titleSuffix: ''
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 69a0598b05d1b2bff84b203317d6d5a166ce109d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746393"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="bba57-102">İzlenecek yol: tasarım zamanında Windows Forms yeni WPF içeriği oluşturma</span><span class="sxs-lookup"><span data-stu-id="bba57-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="bba57-103">Bu makalede, Windows Forms tabanlı uygulamalarınızda kullanılmak üzere bir Windows Presentation Foundation (WPF) denetimi oluşturma konusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bba57-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bba57-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="bba57-104">Prerequisites</span></span>

<span data-ttu-id="bba57-105">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="bba57-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="bba57-106">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bba57-106">Create the project</span></span>

<span data-ttu-id="bba57-107">Visual Studio 'Yu açın ve Visual Basic ya da görsel C# olarak adlandırılan `HostingWpf`yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bba57-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="bba57-108">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bba57-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="bba57-109">Yeni bir WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bba57-109">Create a new WPF control</span></span>

<span data-ttu-id="bba57-110">Yeni bir WPF denetimi oluşturmak ve projenize eklemek, projenize başka herhangi bir öğe eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="bba57-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="bba57-111">Windows Form Tasarımcısı, *bileşik denetim*veya *Kullanıcı denetimi*olarak adlandırılan belirli bir denetim türü ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bba57-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="bba57-112">WPF Kullanıcı denetimleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="bba57-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="bba57-113">WPF <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> türü, Windows Forms tarafından sunulan Kullanıcı denetim türünden farklıdır, bu da <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bba57-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bba57-114">Yeni bir WPF denetimi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="bba57-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="bba57-115">**Çözüm Gezgini**, çözüme yeni bir **WPF Kullanıcı denetimi kitaplığı (.NET Framework)** projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bba57-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="bba57-116">Denetim kitaplığı için varsayılan adı kullanın, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="bba57-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="bba57-117">Varsayılan denetim adı `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bba57-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="bba57-118">Yeni denetimin eklenmesi aşağıdaki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bba57-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="bba57-119">Dosya UserControl1. xaml eklendi.</span><span class="sxs-lookup"><span data-stu-id="bba57-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="bba57-120">UserControl1.xaml.cs (veya UserControl1. xaml. vb) dosyası eklendi.</span><span class="sxs-lookup"><span data-stu-id="bba57-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="bba57-121">Bu dosya olay işleyicileri ve diğer uygulama için arka plan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="bba57-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="bba57-122">WPF derlemelerinin başvuruları eklendi.</span><span class="sxs-lookup"><span data-stu-id="bba57-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="bba57-123">Dosya UserControl1. xaml, Visual Studio için WPF Tasarımcısı 'nda açılır.</span><span class="sxs-lookup"><span data-stu-id="bba57-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="bba57-124">Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bba57-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="bba57-125">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bba57-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="bba57-126">**Araç kutusundan**bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="bba57-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="bba57-127">**Özellikler** penceresinde, <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bba57-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="bba57-128">Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="bba57-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="bba57-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi yalnızca tanım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bba57-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="bba57-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bba57-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="bba57-131">Windows formuna WPF denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="bba57-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="bba57-132">Yeni WPF denetiminiz form üzerinde kullanıma yönelik kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bba57-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="bba57-133">Windows Forms WPF içeriğini barındırmak için <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bba57-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="bba57-134">Bir Windows formuna WPF denetimi eklemek için:</span><span class="sxs-lookup"><span data-stu-id="bba57-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="bba57-135">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="bba57-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="bba57-136">**Araç kutusunda**, **WPFUSERCONTROLLIBRARY WPF Kullanıcı denetimleri**etiketli sekmeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="bba57-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="bba57-137">Bir `UserControl1` örneğini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="bba57-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="bba57-138">WPF denetimini barındırmak için form üzerinde otomatik olarak bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bba57-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="bba57-139"><xref:System.Windows.Forms.Integration.ElementHost> denetim `elementHost1` olarak adlandırılır ve **Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl1**olarak ayarlandığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba57-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="bba57-140">WPF derlemelerine başvurular projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="bba57-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="bba57-141">`elementHost1` denetimi, kullanılabilir barındırma seçeneklerini gösteren bir akıllı etiket paneline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bba57-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="bba57-142">**ElementHost görevleri** akıllı etiketi panelinde **üst kapsayıcıda yerleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bba57-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="bba57-143">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bba57-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bba57-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bba57-144">Next steps</span></span>

<span data-ttu-id="bba57-145">Windows Forms ve WPF farklı teknolojilerdir, ancak yakından birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bba57-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="bba57-146">Uygulamalarınızda daha zengin görünüm ve davranış sağlamak için aşağıdakileri deneyin:</span><span class="sxs-lookup"><span data-stu-id="bba57-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="bba57-147">WPF sayfasında bir Windows Forms denetimi barındırın.</span><span class="sxs-lookup"><span data-stu-id="bba57-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="bba57-148">Daha fazla bilgi için bkz. [Izlenecek yol: WPF 'de Windows Forms denetimi barındırma](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="bba57-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="bba57-149">Windows Forms Görsel stilleri WPF içeriğinize uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bba57-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="bba57-150">Daha fazla bilgi için bkz. [nasıl yapılır: karma uygulamada görsel stilleri etkinleştirme](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="bba57-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="bba57-151">WPF içeriğinizin stilini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bba57-151">Change the style of your WPF content.</span></span> <span data-ttu-id="bba57-152">Daha fazla bilgi için bkz. [Izlenecek yol: WPF Içeriğini stillendirme](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="bba57-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bba57-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba57-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="bba57-154">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="bba57-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="bba57-155">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bba57-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="bba57-156">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="bba57-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
