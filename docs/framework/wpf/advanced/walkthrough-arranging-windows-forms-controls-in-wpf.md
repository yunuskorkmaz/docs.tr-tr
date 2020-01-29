---
title: WPF 'de Windows Forms denetimlerini düzenleme
titleSuffix: ''
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 5e7544dfdbee234bb968c9a7f39814e8749ece15
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735291"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="91924-102">İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="91924-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="91924-103">Bu izlenecek yol, karma uygulamada [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri düzenlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen özelliklerini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="91924-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="91924-104">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="91924-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="91924-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="91924-105">Creating the project.</span></span>
- <span data-ttu-id="91924-106">Varsayılan düzen ayarlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="91924-106">Using default layout settings.</span></span>
- <span data-ttu-id="91924-107">İçeriğe boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="91924-107">Sizing to content.</span></span>
- <span data-ttu-id="91924-108">Mutlak konumlandırmayı kullanma.</span><span class="sxs-lookup"><span data-stu-id="91924-108">Using absolute positioning.</span></span>
- <span data-ttu-id="91924-109">Boyutu açıkça belirtme.</span><span class="sxs-lookup"><span data-stu-id="91924-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="91924-110">Düzen özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="91924-110">Setting layout properties.</span></span>
- <span data-ttu-id="91924-111">Z düzeni sınırlamalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="91924-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="91924-112">Tanımlaya.</span><span class="sxs-lookup"><span data-stu-id="91924-112">Docking.</span></span>
- <span data-ttu-id="91924-113">Görünürlük ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="91924-113">Setting visibility.</span></span>
- <span data-ttu-id="91924-114">UZAMAYAN bir denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="91924-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="91924-115">Lemeyle.</span><span class="sxs-lookup"><span data-stu-id="91924-115">Scaling.</span></span>
- <span data-ttu-id="91924-116">Döner.</span><span class="sxs-lookup"><span data-stu-id="91924-116">Rotating.</span></span>
- <span data-ttu-id="91924-117">Doldurma ve kenar boşlukları ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="91924-117">Setting padding and margins.</span></span>
- <span data-ttu-id="91924-118">Dinamik Düzen kapsayıcıları kullanma.</span><span class="sxs-lookup"><span data-stu-id="91924-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="91924-119">Bu izlenecek yolda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="91924-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="91924-120">İşiniz bittiğinde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamalardaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzeni özelliklerinin anlaşılmasına sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="91924-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91924-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="91924-121">Prerequisites</span></span>

<span data-ttu-id="91924-122">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="91924-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="91924-123">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="91924-123">Creating the Project</span></span>

<span data-ttu-id="91924-124">Projeyi oluşturmak ve ayarlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="91924-125">`WpfLayoutHostingWf`adlı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="91924-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="91924-126">Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="91924-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="91924-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="91924-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="91924-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="91924-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="91924-129">System.Drawing</span></span>

3. <span data-ttu-id="91924-130">*MainWindow. xaml* ' ye ÇIFT tıklayarak xaml görünümünde açın.</span><span class="sxs-lookup"><span data-stu-id="91924-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="91924-131"><xref:System.Windows.Window> öğesinde, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="91924-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="91924-132"><xref:System.Windows.Controls.Grid> öğesinde <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini `true` olarak ayarlayın ve beş satırı ve üç sütunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="91924-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="91924-133">Varsayılan düzen ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="91924-133">Using Default Layout Settings</span></span>

<span data-ttu-id="91924-134">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin yerleşimini işler.</span><span class="sxs-lookup"><span data-stu-id="91924-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="91924-135">Varsayılan düzen ayarlarını kullanmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="91924-136">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="91924-137">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-138"><xref:System.Windows.Controls.Canvas>[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="91924-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="91924-139">Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91924-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="91924-140">Içeriğe boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="91924-140">Sizing to Content</span></span>

<span data-ttu-id="91924-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimin içeriğini düzgün şekilde görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91924-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="91924-142">İçeriğe göre boyut için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="91924-143">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="91924-144">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-145">İki yeni düğme denetimi daha uzun metin dizesi ve daha büyük yazı tipi boyutunu düzgün şekilde görüntüleyecek şekilde boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlere uyum sağlayacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91924-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="91924-146">Mutlak konumlandırmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="91924-146">Using Absolute Positioning</span></span>

<span data-ttu-id="91924-147"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini Kullanıcı arabiriminde (UI) herhangi bir yere yerleştirmek için mutlak konumlandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91924-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="91924-148">Mutlak konumlandırmayı kullanmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="91924-149">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="91924-150">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, kılavuz hücresinin üst tarafından 20 piksel ve soldan 20 piksel yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="91924-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="91924-152">Boyutu açıkça belirtme</span><span class="sxs-lookup"><span data-stu-id="91924-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="91924-153"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin boyutunu <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91924-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="91924-154">Boyutu açıkça belirtmek için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="91924-155">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="91924-156">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, varsayılan düzen ayarlarından daha küçük olan 70 piksel yüksekliğinde 50 piksellik bir boyut olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="91924-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="91924-158">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin içeriği buna göre yeniden düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="91924-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="91924-159">Düzen özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="91924-159">Setting Layout Properties</span></span>

<span data-ttu-id="91924-160"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin özelliklerini kullanarak barındırılan denetimde düzen ile ilgili özellikleri her zaman ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="91924-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91924-161">Doğrudan barındırılan denetimde düzen özelliklerinin ayarlanması, istenmeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="91924-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="91924-162">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içinde barındırılan denetimde düzen ile ilgili özelliklerin ayarlanması hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="91924-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="91924-163">Barındırılan denetimde özellikleri ayarlamanın etkilerini görmek için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="91924-164">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="91924-165">**Çözüm Gezgini**' de, *MainWindow. xaml. vb* veya *MainWindow.xaml.cs* ' ye çift tıklayarak kodu düzenleyici 'de açın.</span><span class="sxs-lookup"><span data-stu-id="91924-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="91924-166">Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="91924-167">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="91924-168">**Bana tıklama** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91924-168">Click the **Click me** button.</span></span> <span data-ttu-id="91924-169">`button1_Click` olay işleyicisi barındırılan denetimdeki <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="91924-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="91924-170">Bu, barındırılan denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi içinde yeniden konumlandırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="91924-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91924-171">Konak aynı ekran alanını korur, ancak barındırılan denetim kırpılır.</span><span class="sxs-lookup"><span data-stu-id="91924-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="91924-172">Bunun yerine, barındırılan denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini her zaman doldurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91924-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="91924-173">Z düzeni sınırlamalarını anlama</span><span class="sxs-lookup"><span data-stu-id="91924-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="91924-174">Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman diğer WPF öğelerinin üzerine çizilir ve z düzeninde etkilenirler.</span><span class="sxs-lookup"><span data-stu-id="91924-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="91924-175">Bu z sırası davranışını görmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="91924-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="91924-176">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="91924-177">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-178"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi etiket öğesi üzerinde boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="91924-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="91924-179">Tanımlaya</span><span class="sxs-lookup"><span data-stu-id="91924-179">Docking</span></span>

<span data-ttu-id="91924-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="91924-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="91924-181">Barındırılan denetimi bir <xref:System.Windows.Controls.DockPanel> öğesinde yerleştirmek için <xref:System.Windows.Controls.DockPanel.Dock%2A> ekli özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="91924-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="91924-182">Barındırılan bir denetimi sabitlemek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="91924-183">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="91924-184">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-185"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi <xref:System.Windows.Controls.DockPanel> öğesinin sağ tarafına yerleştirildi.</span><span class="sxs-lookup"><span data-stu-id="91924-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="91924-186">Ayar görünürlüğü</span><span class="sxs-lookup"><span data-stu-id="91924-186">Setting Visibility</span></span>

<span data-ttu-id="91924-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde <xref:System.Windows.UIElement.Visibility%2A> özelliğini ayarlayarak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez hale getirebilirsiniz veya daraltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91924-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91924-188">Bir denetim görünmez olduğunda, görüntülenmez, ancak düzen alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="91924-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="91924-189">Bir denetim daraltıldığında, görüntülenmez ve düzen alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="91924-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="91924-190">Barındırılan bir denetimin görünürlüğünü ayarlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="91924-191">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="91924-192">*MainWindow. xaml. vb* veya *MainWindow.xaml.cs*içinde, aşağıdaki kodu sınıf tanımına kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="91924-193">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="91924-194"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeyi görünmez hale getirmek için **görünmez** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="91924-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="91924-195"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini düzenden tamamen gizlemek için **daraltmak Için tıklama** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91924-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="91924-196">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanını kaplamak için yeniden düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="91924-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="91924-197">UZAMAYAN bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="91924-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="91924-198">Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve mizanpajda kullanılabilir alanı dolduracak şekilde uzatılmaz.</span><span class="sxs-lookup"><span data-stu-id="91924-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="91924-199">Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi sabit bir alanda bir ay görüntüler.</span><span class="sxs-lookup"><span data-stu-id="91924-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="91924-200">UZAMAYAN bir denetimi barındırmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="91924-201">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="91924-202">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-203"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kılavuz satırında ortalanır, ancak kullanılabilir alanı doldurmak için uzatılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="91924-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="91924-204">Pencere yeterince büyükse, barındırılan <xref:System.Windows.Forms.MonthCalendar> denetimi tarafından görüntülenen iki veya daha fazla ay görebilirsiniz, ancak bunlar satırda ortalanır.</span><span class="sxs-lookup"><span data-stu-id="91924-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="91924-205">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleşim altyapısı, kullanılabilir alanı dolduracak şekilde boyutlandırılabilen öğeleri ortalar.</span><span class="sxs-lookup"><span data-stu-id="91924-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="91924-206">Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="91924-206">Scaling</span></span>

<span data-ttu-id="91924-207">WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="91924-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="91924-208">Özel ölçeklendirme sağlamak için <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="91924-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="91924-209">Barındırılan bir denetimi varsayılan davranışı kullanarak ölçeklendirmek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="91924-210">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="91924-211">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-212">Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörü ile ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="91924-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="91924-213">Ancak, barındırılan denetimin yazı tipi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="91924-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="91924-214">Döner</span><span class="sxs-lookup"><span data-stu-id="91924-214">Rotating</span></span>

<span data-ttu-id="91924-215">WPF öğelerinden farklı olarak Windows Forms denetimleri döndürmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="91924-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="91924-216">Bir döndürme dönüştürmesi uygulandığında <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi diğer WPF öğeleriyle birlikte döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="91924-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="91924-217">180 derecenin dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91924-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="91924-218">Bir karma uygulamada döndürmenin etkisini görmek için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="91924-219">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="91924-220">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-221">Barındırılan denetim döndürülmez, ancak çevreleyen öğeleri 180 derece bir açıda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="91924-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="91924-222">Öğeleri görmek için pencereyi yeniden boyutlandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="91924-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="91924-223">Doldurma ve kenar boşlukları ayarlama</span><span class="sxs-lookup"><span data-stu-id="91924-223">Setting Padding and Margins</span></span>

<span data-ttu-id="91924-224">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeninde doldurma ve kenar boşlukları [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]doldurma ve kenar boşluklarıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="91924-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="91924-225"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özelliklerini ayarlamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="91924-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="91924-226">Barındırılan bir denetimin doldurmasını ve kenar boşluklarını ayarlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="91924-227">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="91924-228">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-229">Doldurma ve kenar boşluğu ayarları, barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]uygulandıkları şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="91924-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="91924-230">Dinamik Düzen kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="91924-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="91924-231">, <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>iki dinamik düzen kapsayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91924-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="91924-232">Bu kapsayıcıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeninde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91924-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="91924-233">Dinamik düzen kapsayıcısını kullanmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="91924-234">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="91924-235">*MainWindow. xaml. vb* veya *MainWindow.xaml.cs*içinde, aşağıdaki kodu sınıf tanımına kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="91924-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="91924-236">Oluşturucuda `InitializeFlowLayoutPanel` yöntemine bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="91924-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="91924-237">Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91924-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="91924-238"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi <xref:System.Windows.Controls.DockPanel>doldurur ve <xref:System.Windows.Forms.FlowLayoutPanel> alt denetimlerini varsayılan <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>düzenler.</span><span class="sxs-lookup"><span data-stu-id="91924-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="91924-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91924-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="91924-240">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="91924-240">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="91924-241">WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar</span><span class="sxs-lookup"><span data-stu-id="91924-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="91924-242">WPF örneğindeki Windows Forms denetimlerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="91924-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="91924-243">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="91924-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="91924-244">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="91924-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
