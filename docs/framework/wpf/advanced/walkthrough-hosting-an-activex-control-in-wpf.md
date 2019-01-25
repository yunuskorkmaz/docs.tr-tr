---
title: "İzlenecek yol: WPF'te ActiveX denetimi barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 25019444e107af2ad681e9f51adebbf01c444438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668326"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="c8ef5-102">İzlenecek yol: WPF'te ActiveX denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="c8ef5-103">Tarayıcı ile Gelişmiş etkileşimi etkinleştirmek için kullanabileceğiniz [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="c8ef5-104">Bu izlenecek yol, nasıl barındırabilirsiniz gösterir [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] denetim olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="c8ef5-105">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c8ef5-105">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="c8ef5-106">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-106">Creating the project.</span></span>

-   <span data-ttu-id="c8ef5-107">ActiveX denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-107">Creating the ActiveX control.</span></span>

-   <span data-ttu-id="c8ef5-108">WPF sayfasında ActiveX denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="c8ef5-109">Bu izlenecek yolu tamamladığınızda, nasıl kullanılacağını anlayacaksınız [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8ef5-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c8ef5-110">Prerequisites</span></span>
 <span data-ttu-id="c8ef5-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="c8ef5-111">You need the following components to complete this walkthrough:</span></span>

-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="c8ef5-112">Visual Studio'nun yüklü bilgisayarda yüklü.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-112">installed on the computer where Visual Studio is installed.</span></span>

-   <span data-ttu-id="c8ef5-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="c8ef5-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-114">Creating the Project</span></span>

#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="c8ef5-115">Oluşturma ve projesi kurun</span><span class="sxs-lookup"><span data-stu-id="c8ef5-115">To create and set up the project</span></span>

1.  <span data-ttu-id="c8ef5-116">Adlı bir WPF uygulaması projesi oluşturmak `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2.  <span data-ttu-id="c8ef5-117">Bir Windows Forms Denetim Kitaplığı projesi çözüme ekleyin ve projeyi adlandırın `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3.  <span data-ttu-id="c8ef5-118">WmpAxLib projesinde wmp.dll adlı Windows Media Player derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4.  <span data-ttu-id="c8ef5-119">Açık **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-119">Open the **Toolbox**.</span></span>

5.  <span data-ttu-id="c8ef5-120">Sağ **araç kutusu**ve ardından **öğelerini Seç**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6.  <span data-ttu-id="c8ef5-121">Tıklayın **COM bileşenlerini** sekmesinde **Windows Media Player** denetlemek ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="c8ef5-122">Windows Media Player denetimi eklenir **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7.  <span data-ttu-id="c8ef5-123">Çözüm Gezgini'nde sağ **UserControl1** dosya ve ardından **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8.  <span data-ttu-id="c8ef5-124">Adla değiştirin `WmpAxControl.vb` veya `WmpAxControl.cs`dile bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="c8ef5-125">Tüm başvuruları yeniden adlandırmak için istenirse, tıklayın **Evet**.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="c8ef5-126">ActiveX denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="c8ef5-127">otomatik olarak oluşturduğu bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı için bir [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] bir tasarım yüzeyine bir denetim eklendiğinde denetim.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="c8ef5-128">Aşağıdaki yordam AxInterop.WMPLib.dll yönetilen bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

#### <a name="to-create-the-activex-control"></a><span data-ttu-id="c8ef5-129">ActiveX denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c8ef5-129">To create the ActiveX control</span></span>

1.  <span data-ttu-id="c8ef5-130">WmpAxControl.vb veya WmpAxControl.cs Windows Form Tasarımcısı'nda açın.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="c8ef5-131">Gelen **araç kutusu**, Windows Media Player denetimi tasarım yüzeyine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3.  <span data-ttu-id="c8ef5-132">Özellikler penceresinde, Windows Media Player denetimin değerini <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4.  <span data-ttu-id="c8ef5-133">WmpAxLib denetim kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="c8ef5-134">Bir WPF sayfasında ActiveX denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-134">Hosting the ActiveX Control on a WPF Page</span></span>

#### <a name="to-host-the-activex-control"></a><span data-ttu-id="c8ef5-135">ActiveX denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-135">To host the ActiveX control</span></span>

1.  <span data-ttu-id="c8ef5-136">HostingAxInWpf projesinde, oluşturulan bir başvuru ekleyin [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] birlikte çalışma derlemesi.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>

     <span data-ttu-id="c8ef5-137">Bu derleme AxInterop.WMPLib.dll adlandırılır ve Windows Media Player denetimi aktarıldığında WmpAxLib projenin hata ayıklama klasöre eklendi.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2.  <span data-ttu-id="c8ef5-138">WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3.  <span data-ttu-id="c8ef5-139">Bir başvuru ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll adlı bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4.  <span data-ttu-id="c8ef5-140">MainWindow.xaml WPF Tasarımcısı'nda açın.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5.  <span data-ttu-id="c8ef5-141">Adı <xref:System.Windows.Controls.Grid> öğesi `grid1`.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6.  <span data-ttu-id="c8ef5-142">Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7.  <span data-ttu-id="c8ef5-143">Özellikler penceresinde tıklayın **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-143">In the Properties window, click the **Events** tab.</span></span>

8.  <span data-ttu-id="c8ef5-144">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="c8ef5-145">İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="c8ef5-146">Bu kod örneği oluşturur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetlemek ve bir örneğini ekler `AxWindowsMediaPlayer` denetim alt öğesi olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="c8ef5-147">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ef5-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8ef5-148">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c8ef5-149">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="c8ef5-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c8ef5-150">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="c8ef5-151">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="c8ef5-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
