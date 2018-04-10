---
title: "İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme"
ms.custom: ''
ms.date: 04/03/2018
ms.prod: .net-framework
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3129b4128444530b1277299f3f95ce49232421
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="97d31-102">İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="97d31-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="97d31-103">Bu kılavuz size nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek için Düzen özelliklerinin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karma uygulama denetimlerinde.</span><span class="sxs-lookup"><span data-stu-id="97d31-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="97d31-104">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="97d31-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="97d31-105">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="97d31-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="97d31-106">Varsayılan düzen ayarlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="97d31-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="97d31-107">İçeriği boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="97d31-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="97d31-108">Mutlak konumlandırmayı kullanma.</span><span class="sxs-lookup"><span data-stu-id="97d31-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="97d31-109">Boyutu açıkça belirtme.</span><span class="sxs-lookup"><span data-stu-id="97d31-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="97d31-110">Düzen özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="97d31-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="97d31-111">Z düzeni sınırlamalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="97d31-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="97d31-112">Yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="97d31-112">Docking.</span></span>  
  
-   <span data-ttu-id="97d31-113">Görünürlük ayarlama.</span><span class="sxs-lookup"><span data-stu-id="97d31-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="97d31-114">Uzatma olmayan bir denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="97d31-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="97d31-115">Ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="97d31-115">Scaling.</span></span>  
  
-   <span data-ttu-id="97d31-116">Döndürme.</span><span class="sxs-lookup"><span data-stu-id="97d31-116">Rotating.</span></span>  
  
-   <span data-ttu-id="97d31-117">Ayar doldurma ve kenar boşlukları.</span><span class="sxs-lookup"><span data-stu-id="97d31-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="97d31-118">Dinamik düzen kapsayıcılarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="97d31-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="97d31-119">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [düzenleme Windows Forms denetimlerinde WPF örnek](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="97d31-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="97d31-120">İşiniz bittiğinde, anlaşılması gerekir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="97d31-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="97d31-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="97d31-121">Prerequisites</span></span>  
 <span data-ttu-id="97d31-122">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="97d31-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="97d31-123">.</span><span class="sxs-lookup"><span data-stu-id="97d31-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="97d31-124">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="97d31-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="97d31-125">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="97d31-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="97d31-126">Adlı bir WPF uygulaması projesi oluşturduğunuzda `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="97d31-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="97d31-127">Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97d31-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="97d31-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="97d31-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="97d31-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="97d31-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="97d31-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="97d31-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="97d31-131">MainWindow.xaml XAML görünümünde açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="97d31-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="97d31-132">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="97d31-133">İçinde <xref:System.Windows.Controls.Grid> öğe kümesi <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğine `true` ve beş satır ve üç sütun tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97d31-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="97d31-134">Varsayılan düzen ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="97d31-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="97d31-135">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi işler barındırılan düzenini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="97d31-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="97d31-136">Varsayılan düzen ayarlarını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="97d31-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="97d31-137">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="97d31-138">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Denetimi görünür <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="97d31-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="97d31-140">Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="97d31-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="97d31-141">İçeriği boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="97d31-141">Sizing to Content</span></span>  
 <span data-ttu-id="97d31-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi sağlar barındırılan denetim içeriği düzgün görüntülemek için boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="97d31-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="97d31-143">İçin içerik boyutu</span><span class="sxs-lookup"><span data-stu-id="97d31-143">To size to content</span></span>  
  
1.  <span data-ttu-id="97d31-144">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="97d31-145">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-146">İki yeni düğmesi denetimleri uzun metin dizesini ve büyük yazı tipi boyutunu düzgün görüntülemek için boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlerin sığması için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="97d31-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="97d31-147">Mutlak konumlandırmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="97d31-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="97d31-148">Yerleştirmek için mutlak konumlandırma kullanabilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini herhangi bir kullanıcı arabirimi (UI).</span><span class="sxs-lookup"><span data-stu-id="97d31-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="97d31-149">Mutlak konumlandırma kullanmak için</span><span class="sxs-lookup"><span data-stu-id="97d31-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="97d31-150">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="97d31-151">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz hücresinin üst tarafındaki 20 piksel ve soldan 20 piksel yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="97d31-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="97d31-153">Boyutu açıkça belirtme</span><span class="sxs-lookup"><span data-stu-id="97d31-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="97d31-154">Boyutu belirtebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kullanılarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="97d31-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="97d31-155">Boyutu açıkça belirtmek için</span><span class="sxs-lookup"><span data-stu-id="97d31-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="97d31-156">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="97d31-157">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan düzen ayarlarından daha küçük olan 50 piksel genişliğinde 70 piksel yüksek boyutunu ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="97d31-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="97d31-159">İçeriği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim uygun şekilde düzenlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="97d31-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="97d31-160">Düzen özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="97d31-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="97d31-161">Her zaman Düzen ilgili özelliklerini ayarlama barındırılan denetimde özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="97d31-162">Doğrudan barındırılan denetimde düzen özelliklerini ayarlama, istenmeyen sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="97d31-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="97d31-163">Düzen ilgili özellikler barındırılan denetimi ayarı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="97d31-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="97d31-164">Üzerinde barındırılan denetim özelliklerini ayarlama etkilerini görmek için</span><span class="sxs-lookup"><span data-stu-id="97d31-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="97d31-165">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="97d31-166">Çözüm Gezgini'nde MainWindow.xaml çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="97d31-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="97d31-167">vb veya MainWindow.xaml.cs kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="97d31-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="97d31-168">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="97d31-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="97d31-169">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="97d31-170">Tıklatın **Click me** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-170">Click the **Click me** button.</span></span> <span data-ttu-id="97d31-171">`button1_Click` Olay işleyicisi kümeleri <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> barındırılan denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="97d31-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="97d31-172">Bu içinde konumlandırılmasına denetimden neden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="97d31-173">Ana bilgisayar aynı ekran alanını korur, ancak barındırılan denetim kırpılır.</span><span class="sxs-lookup"><span data-stu-id="97d31-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="97d31-174">Bunun yerine, barındırılan denetim daima doldurmanız <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="97d31-175">Z düzeni sınırlamalarını anlama</span><span class="sxs-lookup"><span data-stu-id="97d31-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="97d31-176">Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman en üstünde diğer WPF öğeleri çizileceğini ve z düzeni tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="97d31-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="97d31-177">Bu z düzeni davranışı görmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="97d31-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="97d31-178">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="97d31-179">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiket öğesinde boyanır.</span><span class="sxs-lookup"><span data-stu-id="97d31-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="97d31-181">Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="97d31-181">Docking</span></span>  
 <span data-ttu-id="97d31-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi tarafından desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="97d31-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="97d31-183">Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> barındırılan denetimi sabitlemek için özelliği eklenmiş bir <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="97d31-184">Barındırılan denetimi sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="97d31-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="97d31-185">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="97d31-186">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi için sağ tarafındaki yerleşik <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="97d31-188">Görünürlüğü ayarlama</span><span class="sxs-lookup"><span data-stu-id="97d31-188">Setting Visibility</span></span>  
 <span data-ttu-id="97d31-189">Yapabileceğiniz, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez veya ayarlayarak Daralt <xref:System.Windows.UIElement.Visibility%2A> özellikte <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="97d31-190">Bir denetim görünmez olduğunda, görüntülenmez, ancak düzeni yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="97d31-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="97d31-191">Bir denetim daraltıldığında görüntülenmez veya düzeni alan kaplar yapar.</span><span class="sxs-lookup"><span data-stu-id="97d31-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="97d31-192">Barındırılan denetimi görünürlüğünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="97d31-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="97d31-193">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="97d31-194">MainWindow.xaml.vb veya MainWindow.xaml.cs, sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="97d31-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="97d31-195">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="97d31-196">Tıklatın **görünmez yapmak için tıklatın** yapmak için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi görünmez.</span><span class="sxs-lookup"><span data-stu-id="97d31-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="97d31-197">Tıklatın **daraltmak için tıklatın** gizlemek için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini düzenden tamamen.</span><span class="sxs-lookup"><span data-stu-id="97d31-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="97d31-198">Zaman [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanı kaplaması için düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="97d31-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="97d31-199">Uzatma olmayan bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="97d31-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="97d31-200">Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve yerleşiminde kullanılabilir alanı dolduracak şekilde uzatılır değil.</span><span class="sxs-lookup"><span data-stu-id="97d31-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="97d31-201">Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi, sabit bir alanda bir ay görüntüler.</span><span class="sxs-lookup"><span data-stu-id="97d31-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="97d31-202">Uzatılamayan denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="97d31-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="97d31-203">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="97d31-204">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-205"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz satırında ortalanır, ancak bunu kullanılabilir alanı dolduracak şekilde genişletilir değil.</span><span class="sxs-lookup"><span data-stu-id="97d31-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="97d31-206">Pencere yeterince büyük ise, barındırılan tarafından görüntülenen iki veya daha fazla ayı görebilirsiniz <xref:System.Windows.Forms.MonthCalendar> denetimi, ancak bunlar satır içinde ortalanır.</span><span class="sxs-lookup"><span data-stu-id="97d31-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="97d31-207">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerleşim altyapısı merkezleri kullanılabilir alanı dolduracak şekilde boyutlandırılmış olamaz öğeleri.</span><span class="sxs-lookup"><span data-stu-id="97d31-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="97d31-208">ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="97d31-208">Scaling</span></span>  
 <span data-ttu-id="97d31-209">WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="97d31-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="97d31-210">Özel ölçeklendirme sağlamak için geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97d31-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="97d31-211">Varsayılan davranış kullanarak barındırılan denetimi ölçeklendirmek için</span><span class="sxs-lookup"><span data-stu-id="97d31-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="97d31-212">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="97d31-213">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-214">Barındırılan denetim ve onun çevresindeki öğeler 0,5 faktörüyle ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="97d31-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="97d31-215">Ancak, barındırılan denetimin yazı tipi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="97d31-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="97d31-216">Döndürme</span><span class="sxs-lookup"><span data-stu-id="97d31-216">Rotating</span></span>  
 <span data-ttu-id="97d31-217">WPF öğelerinden farklı olarak, Windows Forms denetimleri döndürmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="97d31-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="97d31-218"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi döndürme dönüşümü uygulandığında diğer WPF öğelerle döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="97d31-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="97d31-219">180 derece başlatır dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.</span><span class="sxs-lookup"><span data-stu-id="97d31-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="97d31-220">Karma uygulamada döndürme etkisini görmek için</span><span class="sxs-lookup"><span data-stu-id="97d31-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="97d31-221">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="97d31-222">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-223">Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="97d31-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="97d31-224">Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="97d31-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="97d31-225">Ayar doldurma ve kenar boşlukları</span><span class="sxs-lookup"><span data-stu-id="97d31-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="97d31-226">Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97d31-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="97d31-227">Basitçe <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="97d31-228">Doldurma ve barındırılan denetim kenar boşluklarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="97d31-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="97d31-229">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="97d31-230">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-231">Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bunların uygulanacağı aynı şekilde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97d31-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="97d31-232">Dinamik düzen kapsayıcılarını kullanma</span><span class="sxs-lookup"><span data-stu-id="97d31-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="97d31-233"> iki dinamik düzeni kapsayıcıyı sağlar <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="97d31-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="97d31-234">Bu kapsayıcı de kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.</span><span class="sxs-lookup"><span data-stu-id="97d31-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="97d31-235">Dinamik düzen kapsayıcısını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="97d31-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="97d31-236">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="97d31-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="97d31-237">MainWindow.xaml.vb veya MainWindow.xaml.cs sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="97d31-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="97d31-238">Bir çağrı ekleyin `InitializeFlowLayoutPanel` oluşturucuda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97d31-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="97d31-239">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="97d31-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="97d31-240"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi doldurur <xref:System.Windows.Controls.DockPanel>, ve <xref:System.Windows.Forms.FlowLayoutPanel> varsayılan alt öğe denetimlerini düzenler <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="97d31-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d31-241">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97d31-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="97d31-242">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="97d31-242">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="97d31-243">WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar</span><span class="sxs-lookup"><span data-stu-id="97d31-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="97d31-244">WPF örnek Forms denetimlerini pencereleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="97d31-244">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="97d31-245">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="97d31-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="97d31-246">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="97d31-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
