---
title: WPF 'te ActiveX denetimi barındırma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742618"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="7b52f-102">İzlenecek yol: WPF'te ActiveX Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="7b52f-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="7b52f-103">Tarayıcılarla geliştirilmiş etkileşimi etkinleştirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamanızda Microsoft ActiveX denetimlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b52f-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="7b52f-104">Bu izlenecek yol, Microsoft Windows Media Player bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında denetim olarak nasıl barındırabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b52f-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="7b52f-105">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7b52f-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="7b52f-106">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="7b52f-106">Creating the project.</span></span>

- <span data-ttu-id="7b52f-107">ActiveX denetimi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="7b52f-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="7b52f-108">Bir WPF sayfasında ActiveX denetimini barındırma.</span><span class="sxs-lookup"><span data-stu-id="7b52f-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="7b52f-109">Bu yönergeyi tamamladığınızda, Microsoft ActiveX denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamanızda nasıl kullanacağınızı anlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="7b52f-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b52f-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7b52f-110">Prerequisites</span></span>
 <span data-ttu-id="7b52f-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="7b52f-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="7b52f-112">Microsoft Windows Media Player, Visual Studio 'Nun yüklü olduğu bilgisayarda yüklüdür.</span><span class="sxs-lookup"><span data-stu-id="7b52f-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="7b52f-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="7b52f-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="7b52f-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b52f-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="7b52f-115">Projeyi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7b52f-115">To create and set up the project</span></span>

1. <span data-ttu-id="7b52f-116">`HostingAxInWpf`adlı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b52f-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="7b52f-117">Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin ve proje `WmpAxLib`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="7b52f-118">WmpAxLib projesinde, WMP. dll adlı Windows Media Player derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="7b52f-119">**Araç kutusunu**açın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="7b52f-120">**Araç kutusuna**sağ tıklayın ve ardından **öğeleri seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="7b52f-121">**Com bileşenleri** sekmesine tıklayın, **Windows Media Player** denetimini seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="7b52f-122">Windows Media Player denetimi **araç kutusuna**eklenir.</span><span class="sxs-lookup"><span data-stu-id="7b52f-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="7b52f-123">Çözüm Gezgini, **UserControl1** dosyasına sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="7b52f-124">`WmpAxControl.vb` veya `WmpAxControl.cs`dile bağlı olarak adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="7b52f-125">Tüm başvuruları yeniden adlandırmanız istenirse, **Evet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="7b52f-126">ActiveX denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b52f-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="7b52f-127">Visual Studio, denetim tasarım yüzeyine eklendiğinde Microsoft ActiveX denetimi için otomatik olarak bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b52f-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="7b52f-128">Aşağıdaki yordam, AxInterop. WMPLib. dll adlı bir yönetilen derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b52f-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="7b52f-129">ActiveX denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7b52f-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="7b52f-130">Windows Form Tasarımcısı WmpAxControl. vb veya WmpAxControl.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="7b52f-131">**Araç kutusundan**, tasarım yüzeyine Windows Media Player denetimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="7b52f-132">Özellikler penceresi, Windows Media Player denetiminin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="7b52f-133">WmpAxLib denetim kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b52f-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="7b52f-134">Bir WPF sayfasında ActiveX denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="7b52f-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="7b52f-135">ActiveX denetimini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="7b52f-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="7b52f-136">HostingAxInWpf projesinde, oluşturulan ActiveX birlikte çalışabilirlik derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="7b52f-137">Bu derleme, AxInterop. WMPLib. dll olarak adlandırılır ve Windows Media Player denetimini içeri aktardığınızda WmpAxLib projesinin hata ayıklama klasörüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b52f-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="7b52f-138">WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="7b52f-139">System. Windows. Forms. dll adlı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="7b52f-140">WPF Tasarımcısında MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="7b52f-141"><xref:System.Windows.Controls.Grid> öğesi `grid1`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="7b52f-142">Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="7b52f-143">Özellikler penceresi, **Olaylar** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="7b52f-144"><xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="7b52f-145"><xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b52f-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="7b52f-146">Bu kod, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin bir örneğini oluşturur ve `AxWindowsMediaPlayer` denetiminin alt öğesi olarak bir örneğini ekler.</span><span class="sxs-lookup"><span data-stu-id="7b52f-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="7b52f-147">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b52f-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b52f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b52f-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7b52f-149">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="7b52f-149">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="7b52f-150">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="7b52f-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="7b52f-151">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="7b52f-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
