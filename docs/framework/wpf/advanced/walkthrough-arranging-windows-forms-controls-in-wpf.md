---
title: 'İzlenecek yol: WPF’de Windows Forms Denetimlerini Düzenleme'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972304"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="e09bd-102">İzlenecek yol: WPF’de Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e09bd-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="e09bd-103">Bu izlenecek yol, karma uygulamadaki denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] için Düzen özelliklerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="e09bd-104">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e09bd-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="e09bd-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="e09bd-105">Creating the project.</span></span>

- <span data-ttu-id="e09bd-106">Varsayılan düzen ayarlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="e09bd-106">Using default layout settings.</span></span>

- <span data-ttu-id="e09bd-107">İçeriğe boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="e09bd-107">Sizing to content.</span></span>

- <span data-ttu-id="e09bd-108">Mutlak konumlandırmayı kullanma.</span><span class="sxs-lookup"><span data-stu-id="e09bd-108">Using absolute positioning.</span></span>

- <span data-ttu-id="e09bd-109">Boyutu açıkça belirtme.</span><span class="sxs-lookup"><span data-stu-id="e09bd-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="e09bd-110">Düzen özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="e09bd-110">Setting layout properties.</span></span>

- <span data-ttu-id="e09bd-111">Z düzeni sınırlamalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="e09bd-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="e09bd-112">Tanımlaya.</span><span class="sxs-lookup"><span data-stu-id="e09bd-112">Docking.</span></span>

- <span data-ttu-id="e09bd-113">Görünürlük ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e09bd-113">Setting visibility.</span></span>

- <span data-ttu-id="e09bd-114">UZAMAYAN bir denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="e09bd-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="e09bd-115">Lemeyle.</span><span class="sxs-lookup"><span data-stu-id="e09bd-115">Scaling.</span></span>

- <span data-ttu-id="e09bd-116">Döner.</span><span class="sxs-lookup"><span data-stu-id="e09bd-116">Rotating.</span></span>

- <span data-ttu-id="e09bd-117">Doldurma ve kenar boşlukları ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e09bd-117">Setting padding and margins.</span></span>

- <span data-ttu-id="e09bd-118">Dinamik Düzen kapsayıcıları kullanma.</span><span class="sxs-lookup"><span data-stu-id="e09bd-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="e09bd-119">Bu izlenecek yolda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="e09bd-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="e09bd-120">İşiniz bittiğinde, temel [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]özellikli uygulamalardaki düzen özelliklerinin anlaşılmasına sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e09bd-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e09bd-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e09bd-121">Prerequisites</span></span>

<span data-ttu-id="e09bd-122">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="e09bd-123">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e09bd-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="e09bd-124">Projeyi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-124">To create and set up the project</span></span>

1. <span data-ttu-id="e09bd-125">Adlı `WpfLayoutHostingWf`bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e09bd-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="e09bd-126">Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e09bd-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="e09bd-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="e09bd-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="e09bd-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="e09bd-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="e09bd-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="e09bd-129">System.Drawing</span></span>

3. <span data-ttu-id="e09bd-130">MainWindow. xaml ' ye çift tıklayarak XAML görünümünde açın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="e09bd-131">Öğesinde, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin. <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="e09bd-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="e09bd-132"><xref:System.Windows.Controls.Grid> Öğesinde <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini olarak`true` ayarlayın ve beş satırı ve üç sütunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="e09bd-133">Varsayılan düzen ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e09bd-133">Using Default Layout Settings</span></span>

<span data-ttu-id="e09bd-134">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin yerleşimini işler.</span><span class="sxs-lookup"><span data-stu-id="e09bd-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="e09bd-135">Varsayılan düzen ayarlarını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-135">To use default layout settings</span></span>

1. <span data-ttu-id="e09bd-136">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="e09bd-137">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-138">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimiçinde<xref:System.Windows.Controls.Canvas>görüntülenir. <xref:System.Windows.Forms.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e09bd-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="e09bd-139">Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="e09bd-140">Içeriğe boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="e09bd-140">Sizing to Content</span></span>

<span data-ttu-id="e09bd-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi barındırılan denetimin içeriğini düzgün şekilde görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e09bd-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="e09bd-142">İçeriğe göre boyut</span><span class="sxs-lookup"><span data-stu-id="e09bd-142">To size to content</span></span>

1. <span data-ttu-id="e09bd-143">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="e09bd-144">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-145">İki yeni düğme denetimi daha uzun metin dizesi ve daha büyük yazı tipi boyutunu düzgün şekilde görüntüleyecek şekilde boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeler barındırılan denetimlere uyum sağlayacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="e09bd-146">Mutlak konumlandırmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="e09bd-146">Using Absolute Positioning</span></span>

<span data-ttu-id="e09bd-147"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi Kullanıcı arabiriminde (UI) herhangi bir yere yerleştirmek için mutlak konumlandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e09bd-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="e09bd-148">Mutlak konumlandırmayı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-148">To use absolute positioning</span></span>

1. <span data-ttu-id="e09bd-149">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="e09bd-150">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, kılavuz hücresinin üst tarafından 20 piksel ve soldan 20 piksel yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="e09bd-152">Boyutu açıkça belirtme</span><span class="sxs-lookup"><span data-stu-id="e09bd-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="e09bd-153">Ve<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> özelliklerinikullanarak<xref:System.Windows.FrameworkElement.Height%2A> öğenin boyutunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e09bd-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="e09bd-154">Boyutu açıkça belirtmek için</span><span class="sxs-lookup"><span data-stu-id="e09bd-154">To specify size explicitly</span></span>

1. <span data-ttu-id="e09bd-155">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="e09bd-156">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, varsayılan düzen ayarlarından daha küçük olan 50 piksel genişliğinde, 70 piksel yüksekliğinde bir boyut olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="e09bd-158">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimin içeriği buna göre yeniden düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="e09bd-159">Düzen özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="e09bd-159">Setting Layout Properties</span></span>

<span data-ttu-id="e09bd-160">Barındırılan denetimde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin özelliklerini kullanarak her zaman düzenle ilgili özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="e09bd-161">Doğrudan barındırılan denetimde düzen özelliklerinin ayarlanması, istenmeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="e09bd-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="e09bd-162">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] barındırılan denetimde düzen ile ilgili özelliklerin ayarlanması hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="e09bd-163">Barındırılan denetimde özellikleri ayarlamanın etkilerini görmek için</span><span class="sxs-lookup"><span data-stu-id="e09bd-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="e09bd-164">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="e09bd-165">Çözüm Gezgini, MainWindow. xaml ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="e09bd-166">vb veya MainWindow.xaml.cs, kod düzenleyicisinde açmak için.</span><span class="sxs-lookup"><span data-stu-id="e09bd-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="e09bd-167">Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="e09bd-168">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="e09bd-169">**Bana tıklama** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-169">Click the **Click me** button.</span></span> <span data-ttu-id="e09bd-170">Olay işleyicisi barındırılan denetimdeki <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> özelliklerini ayarlar. `button1_Click`</span><span class="sxs-lookup"><span data-stu-id="e09bd-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="e09bd-171">Bu, barındırılan denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe içinde yeniden konumlandırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e09bd-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="e09bd-172">Konak aynı ekran alanını korur, ancak barındırılan denetim kırpılır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="e09bd-173">Bunun yerine, barındırılan denetim her zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeyi doldurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="e09bd-174">Z düzeni sınırlamalarını anlama</span><span class="sxs-lookup"><span data-stu-id="e09bd-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="e09bd-175">Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeler her zaman diğer WPF öğelerinin üzerine çizilir ve z düzeninde etkilenirler.</span><span class="sxs-lookup"><span data-stu-id="e09bd-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="e09bd-176">Bu z sırası davranışını görmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="e09bd-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="e09bd-177">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="e09bd-178">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, etiket öğesi üzerinde boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="e09bd-180">Tanımlaya</span><span class="sxs-lookup"><span data-stu-id="e09bd-180">Docking</span></span>

<span data-ttu-id="e09bd-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>öğe yerleştirmeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="e09bd-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="e09bd-182">Barındırılan denetimi bir <xref:System.Windows.Controls.DockPanel> öğede sabitlemek için iliştirilmişözelliğiayarlayın.<xref:System.Windows.Controls.DockPanel.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="e09bd-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="e09bd-183">Barındırılan bir denetimi sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="e09bd-183">To dock a hosted control</span></span>

1. <span data-ttu-id="e09bd-184">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="e09bd-185">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-186">Öğesi, <xref:System.Windows.Controls.DockPanel> öğesinin sağ tarafına yerleştirildi. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="e09bd-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="e09bd-187">Ayar görünürlüğü</span><span class="sxs-lookup"><span data-stu-id="e09bd-187">Setting Visibility</span></span>

<span data-ttu-id="e09bd-188">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Öğesinde özelliğini<xref:System.Windows.UIElement.Visibility%2A> ayarlayarak denetiminizi görünmez hale getirebilirsiniz veya daraltabilirsiniz. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="e09bd-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="e09bd-189">Bir denetim görünmez olduğunda, görüntülenmez, ancak düzen alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="e09bd-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="e09bd-190">Bir denetim daraltıldığında, görüntülenmez ve düzen alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="e09bd-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="e09bd-191">Barındırılan bir denetimin görünürlüğünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="e09bd-192">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="e09bd-193">MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, aşağıdaki kodu sınıf tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="e09bd-194">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="e09bd-195"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi görünmez hale getirmek için **tıkla, görünmeyen** düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="e09bd-196"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi düzenden tamamen gizlemek için **daraltmak için tıklama** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="e09bd-197">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetim daraltıldığında, çevreleyen öğeler alanını kaplamak için yeniden düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="e09bd-198">UZAMAYAN bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="e09bd-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="e09bd-199">Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin sabit bir boyutu vardır ve mizanpajda kullanılabilir alanı dolduracak şekilde uzamayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="e09bd-200">Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetim bir ayı sabit bir alanda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e09bd-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="e09bd-201">UZAMAYAN bir denetimi barındırmak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="e09bd-202">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="e09bd-203">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz satırında ortalanır, ancak kullanılabilir alanı doldurmak için uzatılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="e09bd-205">Pencere yeterince büyükse, barındırılan <xref:System.Windows.Forms.MonthCalendar> denetim tarafından iki veya daha fazla ay görüntülenmiş olabilir, ancak bunlar satırda ortalanır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="e09bd-206">Yerleşim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] altyapısı, kullanılabilir alanı dolduracak şekilde boyutlandırılabilen öğeleri ortalar.</span><span class="sxs-lookup"><span data-stu-id="e09bd-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="e09bd-207">Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="e09bd-207">Scaling</span></span>

<span data-ttu-id="e09bd-208">WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="e09bd-209">Özel ölçeklendirme sağlamak için <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="e09bd-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="e09bd-210">Barındırılan bir denetimi varsayılan davranışı kullanarak ölçeklendirmek için</span><span class="sxs-lookup"><span data-stu-id="e09bd-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="e09bd-211">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="e09bd-212">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-213">Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörü ile ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="e09bd-214">Ancak, barındırılan denetimin yazı tipi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="e09bd-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="e09bd-215">Döner</span><span class="sxs-lookup"><span data-stu-id="e09bd-215">Rotating</span></span>

<span data-ttu-id="e09bd-216">WPF öğelerinden farklı olarak Windows Forms denetimleri döndürmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e09bd-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="e09bd-217">Bir döndürme dönüştürmesi uygulandığında öğesidiğerWPFöğeleriylebirliktedöndürülmez.<xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="e09bd-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="e09bd-218">180 dereceden başka bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="e09bd-219">Karma uygulamada döndürmenin etkisini görmek için</span><span class="sxs-lookup"><span data-stu-id="e09bd-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="e09bd-220">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="e09bd-221">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-222">Barındırılan denetim döndürülmez, ancak çevreleyen öğeleri 180 derece bir açıda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e09bd-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="e09bd-223">Öğeleri görmek için pencereyi yeniden boyutlandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="e09bd-224">Doldurma ve kenar boşlukları ayarlama</span><span class="sxs-lookup"><span data-stu-id="e09bd-224">Setting Padding and Margins</span></span>

<span data-ttu-id="e09bd-225">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzendeki doldurma ve kenar boşlukları, içindeki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]doldurma ve kenar boşluklarıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="e09bd-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="e09bd-226">Öğesi üzerinde <xref:System.Windows.Controls.Control.Padding%2A> <xref:System.Windows.FrameworkElement.Margin%2A> ve özelliklerini ayarlamanız yeterlidir. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="e09bd-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="e09bd-227">Barındırılan bir denetim için doldurma ve kenar boşluklarını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="e09bd-228">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="e09bd-229">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-230">Doldurma ve kenar boşluğu ayarları, barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlere, içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]uygulandıkları şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e09bd-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="e09bd-231">Dinamik Düzen kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="e09bd-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="e09bd-232">iki dinamik düzen kapsayıcısı <xref:System.Windows.Forms.FlowLayoutPanel> sağlar ve. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="e09bd-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="e09bd-233">Bu kapsayıcıları mizanpajlar halinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e09bd-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="e09bd-234">Dinamik düzen kapsayıcısını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e09bd-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="e09bd-235">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="e09bd-236">MainWindow. xaml. vb veya MainWindow.xaml.cs içinde aşağıdaki kodu sınıf tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="e09bd-237">Kurucudaki `InitializeFlowLayoutPanel` yöntemine bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e09bd-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="e09bd-238">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09bd-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="e09bd-239">Öğesi öğesini <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>doldurur ve alt<xref:System.Windows.Forms.FlowLayoutPanel> denetimlerini varsayılan olarak düzenler. <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="e09bd-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e09bd-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e09bd-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e09bd-241">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="e09bd-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="e09bd-242">WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar</span><span class="sxs-lookup"><span data-stu-id="e09bd-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="e09bd-243">WPF örneğindeki Windows Forms denetimlerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="e09bd-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="e09bd-244">İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma</span><span class="sxs-lookup"><span data-stu-id="e09bd-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="e09bd-245">İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="e09bd-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
