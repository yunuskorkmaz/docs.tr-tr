---
title: "İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67bfa913627d33238aea92acdd49b6d2ecfef2a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="91811-102">İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="91811-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="91811-103">Bu kılavuz size nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek için Düzen özelliklerinin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karma uygulama denetimlerinde.</span><span class="sxs-lookup"><span data-stu-id="91811-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="91811-104">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="91811-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="91811-105">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="91811-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="91811-106">Varsayılan düzen ayarlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="91811-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="91811-107">İçeriği boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="91811-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="91811-108">Mutlak konumlandırmayı kullanma.</span><span class="sxs-lookup"><span data-stu-id="91811-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="91811-109">Boyutu açıkça belirtme.</span><span class="sxs-lookup"><span data-stu-id="91811-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="91811-110">Düzen özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="91811-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="91811-111">Z düzeni sınırlamalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="91811-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="91811-112">Yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="91811-112">Docking.</span></span>  
  
-   <span data-ttu-id="91811-113">Görünürlük ayarlama.</span><span class="sxs-lookup"><span data-stu-id="91811-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="91811-114">Uzatma olmayan bir denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="91811-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="91811-115">Ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="91811-115">Scaling.</span></span>  
  
-   <span data-ttu-id="91811-116">Döndürme.</span><span class="sxs-lookup"><span data-stu-id="91811-116">Rotating.</span></span>  
  
-   <span data-ttu-id="91811-117">Ayar doldurma ve kenar boşlukları.</span><span class="sxs-lookup"><span data-stu-id="91811-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="91811-118">Dinamik düzen kapsayıcılarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="91811-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="91811-119">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [düzenleme Windows Forms denetimlerinde WPF örnek](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="91811-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="91811-120">İşiniz bittiğinde, anlaşılması gerekir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="91811-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="91811-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="91811-121">Prerequisites</span></span>  
 <span data-ttu-id="91811-122">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="91811-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="91811-123">.</span><span class="sxs-lookup"><span data-stu-id="91811-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="91811-124">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="91811-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="91811-125">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="91811-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="91811-126">Adlı bir WPF uygulaması projesi oluşturduğunuzda `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="91811-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="91811-127">Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="91811-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="91811-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="91811-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="91811-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="91811-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="91811-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="91811-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="91811-131">MainWindow.xaml XAML görünümünde açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91811-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="91811-132">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="91811-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="91811-133">İçinde <xref:System.Windows.Controls.Grid> öğe kümesi <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğine `true` ve beş satır ve üç sütun tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="91811-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="91811-134">Varsayılan düzen ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="91811-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="91811-135">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi işler barındırılan düzenini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="91811-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="91811-136">Varsayılan düzen ayarlarını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="91811-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="91811-137">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="91811-138">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Denetimi görünür <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="91811-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="91811-140">Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="91811-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="91811-141">İçeriği boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="91811-141">Sizing to Content</span></span>  
 <span data-ttu-id="91811-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi sağlar barındırılan denetim içeriği düzgün görüntülemek için boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91811-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="91811-143">İçin içerik boyutu</span><span class="sxs-lookup"><span data-stu-id="91811-143">To size to content</span></span>  
  
1.  <span data-ttu-id="91811-144">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="91811-145">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-146">İki yeni düğmesi denetimleri uzun metin dizesini ve büyük yazı tipi boyutunu düzgün görüntülemek için boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlerin sığması için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91811-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="91811-147">Mutlak konumlandırmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="91811-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="91811-148">Yerleştirmek için mutlak konumlandırma kullanabilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini herhangi bir kullanıcı arabirimi (UI).</span><span class="sxs-lookup"><span data-stu-id="91811-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="91811-149">Mutlak konumlandırma kullanmak için</span><span class="sxs-lookup"><span data-stu-id="91811-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="91811-150">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="91811-151">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz hücresinin üst tarafındaki 20 piksel ve soldan 20 piksel yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="91811-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="91811-153">Boyutu açıkça belirtme</span><span class="sxs-lookup"><span data-stu-id="91811-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="91811-154">Boyutu belirtebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kullanılarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="91811-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="91811-155">Boyutu açıkça belirtmek için</span><span class="sxs-lookup"><span data-stu-id="91811-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="91811-156">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="91811-157">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan düzen ayarlarından daha küçük olan 50 piksel genişliğinde 70 piksel yüksek boyutunu ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="91811-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="91811-159">İçeriği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim uygun şekilde düzenlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="91811-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="91811-160">Düzen özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="91811-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="91811-161">Her zaman Düzen ilgili özelliklerini ayarlama barındırılan denetimde özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91811-162">Doğrudan barındırılan denetimde düzen özelliklerini ayarlama, istenmeyen sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="91811-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="91811-163">Düzen ilgili özellikler barındırılan denetimi ayarı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="91811-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="91811-164">Üzerinde barındırılan denetim özelliklerini ayarlama etkilerini görmek için</span><span class="sxs-lookup"><span data-stu-id="91811-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="91811-165">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="91811-166">Çözüm Gezgini'nde MainWindow.xaml çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91811-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="91811-167">vb veya MainWindow.xaml.cs kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="91811-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="91811-168">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="91811-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="91811-169">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="91811-170">Tıklatın **Click me** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="91811-170">Click the **Click me** button.</span></span> <span data-ttu-id="91811-171">`button1_Click` Olay işleyicisi kümeleri <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> barındırılan denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="91811-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="91811-172">Bu içinde konumlandırılmasına denetimden neden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91811-173">Ana bilgisayar aynı ekran alanını korur, ancak barındırılan denetim kırpılır.</span><span class="sxs-lookup"><span data-stu-id="91811-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="91811-174">Bunun yerine, barındırılan denetim daima doldurmanız <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="91811-175">Z düzeni sınırlamalarını anlama</span><span class="sxs-lookup"><span data-stu-id="91811-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="91811-176">Varsayılan olarak görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman çizilir diğer üstünde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ve z düzeni tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="91811-176">By default, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="91811-177">Z sıralamasını etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="91811-177">To enable z-ordering, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-default-z-order-behavior"></a><span data-ttu-id="91811-178">Z düzeni davranışı görmek için</span><span class="sxs-lookup"><span data-stu-id="91811-178">To see the default z-order behavior</span></span>  
  
1.  <span data-ttu-id="91811-179">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-179">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  <span data-ttu-id="91811-180">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-180">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiket öğesinde boyanır.</span><span class="sxs-lookup"><span data-stu-id="91811-181">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a><span data-ttu-id="91811-182">Z düzeni davranışını IsRedirected true olduğunda görmek için</span><span class="sxs-lookup"><span data-stu-id="91811-182">To see the z-order behavior when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="91811-183">Önceki z düzeni örnek aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="91811-183">Replace the previous z-order example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     <span data-ttu-id="91811-184">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-184">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-185">Label öğesi üzerinden boyanır <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-185">The label element is painted over the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="docking"></a><span data-ttu-id="91811-186">Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="91811-186">Docking</span></span>  
 <span data-ttu-id="91811-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>öğesi tarafından desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="91811-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="91811-188">Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> barındırılan denetimi sabitlemek için özelliği eklenmiş bir <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-188">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="91811-189">Barındırılan denetimi sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="91811-189">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="91811-190">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-190">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="91811-191">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-191">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-192"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi için sağ tarafındaki yerleşik <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-192">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="91811-193">Görünürlüğü ayarlama</span><span class="sxs-lookup"><span data-stu-id="91811-193">Setting Visibility</span></span>  
 <span data-ttu-id="91811-194">Yapabileceğiniz, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez veya ayarlayarak Daralt <xref:System.Windows.UIElement.Visibility%2A> özellikte <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-194">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="91811-195">Bir denetim görünmez olduğunda, görüntülenmez, ancak düzeni yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="91811-195">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="91811-196">Bir denetim daraltıldığında görüntülenmez veya düzeni alan kaplar yapar.</span><span class="sxs-lookup"><span data-stu-id="91811-196">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="91811-197">Barındırılan denetimi görünürlüğünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="91811-197">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="91811-198">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-198">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="91811-199">MainWindow.xaml.vb veya MainWindow.xaml.cs, sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="91811-199">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="91811-200">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-200">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="91811-201">Tıklatın **görünmez yapmak için tıklatın** yapmak için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi görünmez.</span><span class="sxs-lookup"><span data-stu-id="91811-201">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="91811-202">Tıklatın **daraltmak için tıklatın** gizlemek için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini düzenden tamamen.</span><span class="sxs-lookup"><span data-stu-id="91811-202">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="91811-203">Zaman [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanı kaplaması için düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="91811-203">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="91811-204">Uzatma olmayan bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="91811-204">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="91811-205">Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve yerleşiminde kullanılabilir alanı dolduracak şekilde uzatılır değil.</span><span class="sxs-lookup"><span data-stu-id="91811-205">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="91811-206">Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi, sabit bir alanda bir ay görüntüler.</span><span class="sxs-lookup"><span data-stu-id="91811-206">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="91811-207">Uzatılamayan denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="91811-207">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="91811-208">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-208">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="91811-209">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-209">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-210"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz satırında ortalanır, ancak bunu kullanılabilir alanı dolduracak şekilde genişletilir değil.</span><span class="sxs-lookup"><span data-stu-id="91811-210">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="91811-211">Pencere yeterince büyük ise, barındırılan tarafından görüntülenen iki veya daha fazla ayı görebilirsiniz <xref:System.Windows.Forms.MonthCalendar> denetimi, ancak bunlar satır içinde ortalanır.</span><span class="sxs-lookup"><span data-stu-id="91811-211">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="91811-212">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerleşim altyapısı merkezleri kullanılabilir alanı dolduracak şekilde boyutlandırılmış olamaz öğeleri.</span><span class="sxs-lookup"><span data-stu-id="91811-212">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="91811-213">ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="91811-213">Scaling</span></span>  
 <span data-ttu-id="91811-214">Farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeler, çoğu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sürekli ölçeklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="91811-214">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, most [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls are not continuously scalable.</span></span> <span data-ttu-id="91811-215">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, barındırılan denetimi mümkün olduğunda ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="91811-215">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element scales its hosted control when possible.</span></span>  <span data-ttu-id="91811-216">Tam özellikli ölçeklendirmeyi etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="91811-216">To enable full-fledged scaling, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="91811-217">Varsayılan davranış kullanarak barındırılan denetimi ölçeklendirmek için</span><span class="sxs-lookup"><span data-stu-id="91811-217">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="91811-218">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-218">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="91811-219">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-219">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-220">Barındırılan denetim ve onun çevresindeki öğeler 0,5 faktörüyle ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="91811-220">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="91811-221">Ancak, barındırılan denetimin yazı tipi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="91811-221">However, the hosted control's font is not scaled.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a><span data-ttu-id="91811-222">IsRedirected true olarak ayarlayarak barındırılan denetimi ölçeklendirmek için</span><span class="sxs-lookup"><span data-stu-id="91811-222">To scale a hosted control by setting IsRedirected to true</span></span>  
  
1.  <span data-ttu-id="91811-223">Önceki ölçeklendirme örnek aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="91811-223">Replace the previous scaling example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  <span data-ttu-id="91811-224">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-224">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-225">Barındırılan denetimi, çevreleyen öğeleri ve barındırılan denetimin yazı tipi 0,5 faktörüyle ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="91811-225">The hosted control, its surrounding elements, and the hosted control's font are scaled by a factor of 0.5.</span></span>  
  
## <a name="rotating"></a><span data-ttu-id="91811-226">Döndürme</span><span class="sxs-lookup"><span data-stu-id="91811-226">Rotating</span></span>  
 <span data-ttu-id="91811-227">Farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri döndürmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="91811-227">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls do not support rotation.</span></span> <span data-ttu-id="91811-228">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi diğer döndürülmez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] döndürme dönüşümü uygulandığında öğeleri.</span><span class="sxs-lookup"><span data-stu-id="91811-228">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements when a rotation transformation is applied.</span></span> <span data-ttu-id="91811-229">180 derece başlatır dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.</span><span class="sxs-lookup"><span data-stu-id="91811-229">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>  <span data-ttu-id="91811-230">Herhangi bir açıyla döndürme etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="91811-230">To enable rotating to any angle, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="91811-231">Karma uygulamada döndürme etkisini görmek için</span><span class="sxs-lookup"><span data-stu-id="91811-231">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="91811-232">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-232">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="91811-233">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-233">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-234">Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="91811-234">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="91811-235">Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="91811-235">You may have to resize the window to see the elements.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a><span data-ttu-id="91811-236">IsRedirected true olduğunda karma uygulamada döndürme etkisini görmek için</span><span class="sxs-lookup"><span data-stu-id="91811-236">To see the effect of rotation in a hybrid application when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="91811-237">Önceki döndürme örneği aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="91811-237">Replace the previous rotation example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  <span data-ttu-id="91811-238">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-239">Barındırılan denetim döndürülür.</span><span class="sxs-lookup"><span data-stu-id="91811-239">The hosted control is rotated.</span></span>  <span data-ttu-id="91811-240">Unutmayın <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği herhangi bir değere ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="91811-240">Note that the <xref:System.Windows.Media.RotateTransform.Angle%2A> property can be set to any value.</span></span> <span data-ttu-id="91811-241">Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="91811-241">You may have to resize the window to see the elements.</span></span>  
  
## <a name="setting-padding-and-margins"></a><span data-ttu-id="91811-242">Ayar doldurma ve kenar boşlukları</span><span class="sxs-lookup"><span data-stu-id="91811-242">Setting Padding and Margins</span></span>  
 <span data-ttu-id="91811-243">Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91811-243">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="91811-244">Basitçe <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-244">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="91811-245">Doldurma ve barındırılan denetim kenar boşluklarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="91811-245">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="91811-246">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-246">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="91811-247">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-247">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-248">Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bunların uygulanacağı aynı şekilde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91811-248">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="91811-249">Dinamik düzen kapsayıcılarını kullanma</span><span class="sxs-lookup"><span data-stu-id="91811-249">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="91811-250">iki dinamik düzeni kapsayıcıyı sağlar <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="91811-250"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="91811-251">Bu kapsayıcı de kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.</span><span class="sxs-lookup"><span data-stu-id="91811-251">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="91811-252">Dinamik düzen kapsayıcısını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="91811-252">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="91811-253">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="91811-253">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="91811-254">MainWindow.xaml.vb veya MainWindow.xaml.cs sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="91811-254">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="91811-255">Bir çağrı ekleyin `InitializeFlowLayoutPanel` oluşturucuda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91811-255">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="91811-256">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91811-256">Press F5 to build and run the application.</span></span> <span data-ttu-id="91811-257"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi doldurur <xref:System.Windows.Controls.DockPanel>, ve <xref:System.Windows.Forms.FlowLayoutPanel> varsayılan alt öğe denetimlerini düzenler <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="91811-257">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91811-258">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91811-258">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="91811-259">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="91811-259">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="91811-260">WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar</span><span class="sxs-lookup"><span data-stu-id="91811-260">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="91811-261">WPF örnek Forms denetimlerini pencereleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="91811-261">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="91811-262">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="91811-262">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="91811-263">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="91811-263">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
