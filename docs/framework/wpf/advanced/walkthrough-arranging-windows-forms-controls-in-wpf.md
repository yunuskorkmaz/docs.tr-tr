---
title: 'İzlenecek yol: Düzenleme Windows Forms denetimlerini düzenleme'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: bfb0aba2798179c31674377104bbff633b6f48fc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367199"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="0189a-102">İzlenecek yol: Düzenleme Windows Forms denetimlerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="0189a-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="0189a-103">Bu izlenecek yol size nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek için düzen özelliklerini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karma uygulamada denetimleri.</span><span class="sxs-lookup"><span data-stu-id="0189a-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="0189a-104">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="0189a-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="0189a-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="0189a-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="0189a-106">Varsayılan düzen ayarları kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="0189a-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="0189a-107">İçeriği boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="0189a-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="0189a-108">Konumlandırmayı mutlak kullanma.</span><span class="sxs-lookup"><span data-stu-id="0189a-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="0189a-109">Açıkça boyutunu belirtme.</span><span class="sxs-lookup"><span data-stu-id="0189a-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="0189a-110">Düzen özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0189a-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="0189a-111">Z düzenini sınırlamaları anlama.</span><span class="sxs-lookup"><span data-stu-id="0189a-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="0189a-112">Yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="0189a-112">Docking.</span></span>  
  
-   <span data-ttu-id="0189a-113">Görünürlük ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0189a-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="0189a-114">Esnetme değil bir denetim barındırma.</span><span class="sxs-lookup"><span data-stu-id="0189a-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="0189a-115">Ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="0189a-115">Scaling.</span></span>  
  
-   <span data-ttu-id="0189a-116">Döndürme.</span><span class="sxs-lookup"><span data-stu-id="0189a-116">Rotating.</span></span>  
  
-   <span data-ttu-id="0189a-117">Ayar doldurma ve kenar boşlukları.</span><span class="sxs-lookup"><span data-stu-id="0189a-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="0189a-118">Dinamik düzen kapsayıcıları kullanma.</span><span class="sxs-lookup"><span data-stu-id="0189a-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="0189a-119">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF Örneği'nde Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="0189a-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="0189a-120">İşlemi tamamladığınızda, bir anlayışa sahip [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="0189a-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0189a-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0189a-121">Prerequisites</span></span>  

<span data-ttu-id="0189a-122">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="0189a-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="creating-the-project"></a><span data-ttu-id="0189a-123">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0189a-123">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="0189a-124">Oluşturma ve projesi kurun</span><span class="sxs-lookup"><span data-stu-id="0189a-124">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="0189a-125">Adlı bir WPF uygulaması projesi oluşturmak `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="0189a-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="0189a-126">Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0189a-126">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="0189a-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="0189a-127">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="0189a-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="0189a-128">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="0189a-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="0189a-129">System.Drawing</span></span>  
  
3.  <span data-ttu-id="0189a-130">MainWindow.xaml XAML görünümünde açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0189a-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="0189a-131">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="0189a-132">İçinde <xref:System.Windows.Controls.Grid> öğe kümesi <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini `true` ve beş satır ve üç sütun tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0189a-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="0189a-133">Varsayılan düzen ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="0189a-133">Using Default Layout Settings</span></span>  
 <span data-ttu-id="0189a-134">Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan düzenini işler [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="0189a-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="0189a-135">Varsayılan düzen ayarlarını kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0189a-135">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="0189a-136">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="0189a-137">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-138">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Denetimi görünür <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0189a-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0189a-139">Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi boyutta denetimden uyum sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="0189a-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="0189a-140">İçerik boyutu</span><span class="sxs-lookup"><span data-stu-id="0189a-140">Sizing to Content</span></span>  
 <span data-ttu-id="0189a-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini denetimden içeriği düzgün görüntülenmesi için boyutlandırılır sağlar.</span><span class="sxs-lookup"><span data-stu-id="0189a-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="0189a-142">İçerik boyutu</span><span class="sxs-lookup"><span data-stu-id="0189a-142">To size to content</span></span>  
  
1.  <span data-ttu-id="0189a-143">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="0189a-144">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-145">İki yeni düğme denetimleri düzgün bir şekilde, daha büyük yazı tipi boyutu ve uzun metin dizesini görüntülemek için boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlerin sığması için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0189a-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="0189a-146">Mutlak konumlandırmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="0189a-146">Using Absolute Positioning</span></span>  
 <span data-ttu-id="0189a-147">Mutlak konumlandırma yerleştirmek için kullanabileceğiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini herhangi bir kullanıcı arabirimi (UI).</span><span class="sxs-lookup"><span data-stu-id="0189a-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="0189a-148">Mutlak konumlandırma kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0189a-148">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="0189a-149">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="0189a-150">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz hücresi üst tarafındaki 20 piksel ve 20 piksel soldan yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0189a-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="0189a-152">Açıkça boyutunu belirtme</span><span class="sxs-lookup"><span data-stu-id="0189a-152">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="0189a-153">Boyutunu belirtebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini kullanarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0189a-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="0189a-154">Boyutu açıkça belirtmek için</span><span class="sxs-lookup"><span data-stu-id="0189a-154">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="0189a-155">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="0189a-156">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan düzen ayarlarından daha küçük olan bir boyutu 50 piksel genişliğinde ve 70 piksel yüksekliğinde, ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0189a-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="0189a-158">İçeriği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi uygun şekilde düzenlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="0189a-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="0189a-159">Düzen özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="0189a-159">Setting Layout Properties</span></span>  
 <span data-ttu-id="0189a-160">Her zaman düzen ile ilgili özellikleri ayarlamak üzerinde barındırılan denetim özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0189a-161">Doğrudan barındırılan denetimde düzen özelliklerini ayarlama, istenmeyen sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="0189a-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="0189a-162">Düzen ilgili özellikler barındırılan denetimi ayarını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="0189a-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="0189a-163">Üzerinde barındırılan denetim özelliklerini ayarlama etkilere bakın</span><span class="sxs-lookup"><span data-stu-id="0189a-163">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="0189a-164">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="0189a-165">Çözüm Gezgini içinde MainWindow.xaml çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0189a-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="0189a-166">vb veya MainWindow.xaml.cs Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="0189a-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="0189a-167">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.</span><span class="sxs-lookup"><span data-stu-id="0189a-167">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4.  <span data-ttu-id="0189a-168">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-168">Press F5 to build and run the application.</span></span>

5.  <span data-ttu-id="0189a-169">Tıklayın **me tıklayın** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-169">Click the **Click me** button.</span></span> <span data-ttu-id="0189a-170">`button1_Click` Olay işleyicisi kümeleri <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> barındırılan denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0189a-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="0189a-171">Bu içinde konumlandırılmasına denetimden neden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0189a-172">Konak aynı ekran alanını korur, ancak denetimden kırpılır.</span><span class="sxs-lookup"><span data-stu-id="0189a-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="0189a-173">Bunun yerine barındırılan denetimi her zaman dolması gerektiğini <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="0189a-174">Z düzenini sınırlamaları anlama</span><span class="sxs-lookup"><span data-stu-id="0189a-174">Understanding Z-Order Limitations</span></span>
 <span data-ttu-id="0189a-175">Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman diğer WPF öğeleri üzerine çizilmiş ve z-düzeni tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="0189a-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="0189a-176">Bu z düzenini davranışını görmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="0189a-176">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="0189a-177">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2.  <span data-ttu-id="0189a-178">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiketi öğenin boyanır.</span><span class="sxs-lookup"><span data-stu-id="0189a-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>


## <a name="docking"></a><span data-ttu-id="0189a-180">Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="0189a-180">Docking</span></span>
 <span data-ttu-id="0189a-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin desteklediği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="0189a-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="0189a-182">Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> ekli özellik barındırılan denetimi sabitlemek için bir <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="0189a-183">Barındırılan bir denetim sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="0189a-183">To dock a hosted control</span></span>

1.  <span data-ttu-id="0189a-184">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2.  <span data-ttu-id="0189a-185">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-186"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi sağ tarafına yerleştirilmiş <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="0189a-187">Görünürlük ayarlama</span><span class="sxs-lookup"><span data-stu-id="0189a-187">Setting Visibility</span></span>
 <span data-ttu-id="0189a-188">Yapabileceğiniz, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez veya ayarlayarak Daralt <xref:System.Windows.UIElement.Visibility%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0189a-189">Bir denetim görünmez olduğunda görüntülenmez, ancak düzen yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="0189a-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="0189a-190">Bir denetim daraltıldığında görüntülenmez veya Düzen boşluk kaplamaz.</span><span class="sxs-lookup"><span data-stu-id="0189a-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="0189a-191">Barındırılan bir denetim görünürlüğünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0189a-191">To set the visibility of a hosted control</span></span>

1.  <span data-ttu-id="0189a-192">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2.  <span data-ttu-id="0189a-193">MainWindow.xaml.vb veya MainWindow.xaml.cs seçeneğinde, sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0189a-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3.  <span data-ttu-id="0189a-194">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-194">Press F5 to build and run the application.</span></span>

4.  <span data-ttu-id="0189a-195">Tıklayın **görünmez yapmak için tıklatın** düğmesini <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe görünmez.</span><span class="sxs-lookup"><span data-stu-id="0189a-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5.  <span data-ttu-id="0189a-196">Tıklayın **daraltmak için tıklatın** gizlemek için düğme <xref:System.Windows.Forms.Integration.WindowsFormsHost> düzenini öğesinden tamamen.</span><span class="sxs-lookup"><span data-stu-id="0189a-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="0189a-197">Zaman [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanı kaplaması için düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="0189a-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="0189a-198">Esnetme değil bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="0189a-198">Hosting a Control That Does Not Stretch</span></span>
 <span data-ttu-id="0189a-199">Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve düzendeki kullanılabilir alanı dolduracak şekilde uzatılır değil.</span><span class="sxs-lookup"><span data-stu-id="0189a-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="0189a-200">Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi, bir ay sabit boşluk görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0189a-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="0189a-201">Esnetme değil bir denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="0189a-201">To host a control that does not stretch</span></span>

1.  <span data-ttu-id="0189a-202">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2.  <span data-ttu-id="0189a-203">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz satırı içinde ortalanır, ancak bunu kullanılabilir alanı dolduracak şekilde genişletilir değil.</span><span class="sxs-lookup"><span data-stu-id="0189a-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="0189a-205">Pencerenin yeterince büyük ise, iki veya daha fazla aylık barındırılan tarafından görüntülenen görebilirsiniz <xref:System.Windows.Forms.MonthCalendar> denetimidir, ancak bu satırda ortalanır.</span><span class="sxs-lookup"><span data-stu-id="0189a-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="0189a-206">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerleşim altyapısı kullanılabilir alanı dolduracak şekilde boyutlandırılmalıdır olamaz öğeleri ortalar.</span><span class="sxs-lookup"><span data-stu-id="0189a-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="0189a-207">Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="0189a-207">Scaling</span></span>
 <span data-ttu-id="0189a-208">WPF öğesinin aksine, çoğu Windows Forms denetimlerini sürekli olarak ölçeklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0189a-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="0189a-209">Özel bir ölçekleme sağlamak için geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0189a-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="0189a-210">Barındırılan bir denetimin varsayılan davranışını kullanarak ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="0189a-210">To scale a hosted control by using the default behavior</span></span>

1.  <span data-ttu-id="0189a-211">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2.  <span data-ttu-id="0189a-212">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-213">Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörüyle ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="0189a-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="0189a-214">Ancak, barındırılan denetim yazı tipi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="0189a-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="0189a-215">Döndürme</span><span class="sxs-lookup"><span data-stu-id="0189a-215">Rotating</span></span>
 <span data-ttu-id="0189a-216">WPF öğesinin aksine, Windows Forms denetimleri döndürmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0189a-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="0189a-217"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi döndürme dönüşümü uygulandığı zaman diğer WPF öğelerle döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="0189a-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="0189a-218">180 derece harekete geçirirse dışındaki herhangi bir dönüş değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.</span><span class="sxs-lookup"><span data-stu-id="0189a-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="0189a-219">Döndürme karma uygulamada etkisini görmek için</span><span class="sxs-lookup"><span data-stu-id="0189a-219">To see the effect of rotation in a hybrid application</span></span>

1.  <span data-ttu-id="0189a-220">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2.  <span data-ttu-id="0189a-221">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-222">Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0189a-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="0189a-223">Öğeleri görmek için pencereyi boyutlandırmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="0189a-223">You may have to resize the window to see the elements.</span></span>


## <a name="setting-padding-and-margins"></a><span data-ttu-id="0189a-224">Ayar doldurma ve kenar boşlukları</span><span class="sxs-lookup"><span data-stu-id="0189a-224">Setting Padding and Margins</span></span>
 <span data-ttu-id="0189a-225">Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0189a-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="0189a-226">Ayarlamanız yeterlidir <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="0189a-227">Doldurma ve barındırılan denetim kenar boşluklarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="0189a-227">To set padding and margins for a hosted control</span></span>

1.  <span data-ttu-id="0189a-228">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2.  <span data-ttu-id="0189a-229">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-230">Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulanacağı de aynı şekilde denetimleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0189a-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="0189a-231">Dinamik düzen kapsayıcılarını kullanma</span><span class="sxs-lookup"><span data-stu-id="0189a-231">Using Dynamic Layout Containers</span></span>
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="0189a-232">iki dinamik düzen kapsayıcılar sağlayarak <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="0189a-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="0189a-233">Bu kapsayıcıları da kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.</span><span class="sxs-lookup"><span data-stu-id="0189a-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="0189a-234">Dinamik düzen kapsayıcısı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0189a-234">To use a dynamic layout container</span></span>

1.  <span data-ttu-id="0189a-235">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="0189a-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2.  <span data-ttu-id="0189a-236">MainWindow.xaml.vb veya MainWindow.xaml.cs içinde sınıf tanımının içine aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0189a-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3.  <span data-ttu-id="0189a-237">Bir çağrı ekleyin `InitializeFlowLayoutPanel` oluşturucuda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0189a-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="0189a-238">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0189a-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="0189a-239"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi doldurur <xref:System.Windows.Controls.DockPanel>, ve <xref:System.Windows.Forms.FlowLayoutPanel> varsayılan, alt denetimlerini düzenler <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="0189a-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0189a-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0189a-240">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0189a-241">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="0189a-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="0189a-242">WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar</span><span class="sxs-lookup"><span data-stu-id="0189a-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="0189a-243">Düzenleme Windows Forms denetimleri örneği</span><span class="sxs-lookup"><span data-stu-id="0189a-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="0189a-244">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="0189a-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="0189a-245">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="0189a-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
