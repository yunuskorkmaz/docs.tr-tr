---
title: "İzlenecek yol: WPF'te ActiveX Denetimi Barındırma"
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
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6980097c074e10efae7fc6ee77c6c9835c3b1b00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="c180b-102">İzlenecek yol: WPF'te ActiveX Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="c180b-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="c180b-103">Tarayıcılarla geliştirilmiş etkileşimi etkinleştirmek için kullanabileceğiniz [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı.</span><span class="sxs-lookup"><span data-stu-id="c180b-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="c180b-104">Bu anlatımda nasıl barındırabilir gösterilir [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] bir denetim olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="c180b-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>  
  
 <span data-ttu-id="c180b-105">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c180b-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="c180b-106">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c180b-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="c180b-107">ActiveX denetimi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c180b-107">Creating the ActiveX control.</span></span>  
  
-   <span data-ttu-id="c180b-108">WPF sayfasında ActiveX denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="c180b-108">Hosting the ActiveX control on a WPF Page.</span></span>  
  
 <span data-ttu-id="c180b-109">Bu kılavuzu tamamladıktan sonra nasıl kullanılacağını anlayabileceği [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı.</span><span class="sxs-lookup"><span data-stu-id="c180b-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c180b-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c180b-110">Prerequisites</span></span>  
 <span data-ttu-id="c180b-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="c180b-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]<span data-ttu-id="c180b-112">bilgisayarda yüklü olduğu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c180b-112"> installed on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="c180b-113">.</span><span class="sxs-lookup"><span data-stu-id="c180b-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c180b-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c180b-114">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="c180b-115">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c180b-115">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="c180b-116">Adlı bir WPF uygulaması projesi oluşturduğunuzda `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="c180b-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>  
  
2.  <span data-ttu-id="c180b-117">Bir Windows Forms Denetim Kitaplığı proje çözüme ekleyin ve proje adı `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="c180b-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>  
  
3.  <span data-ttu-id="c180b-118">WmpAxLib projesinde wmp.dll adlı Windows Media Player derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c180b-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>  
  
4.  <span data-ttu-id="c180b-119">Açık **araç**.</span><span class="sxs-lookup"><span data-stu-id="c180b-119">Open the **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="c180b-120">Sağ **araç**ve ardından **öğeleri Seç**.</span><span class="sxs-lookup"><span data-stu-id="c180b-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="c180b-121">Tıklatın **COM bileşenlerini** sekmesine **Windows Media Player** denetlemek ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c180b-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c180b-122">Windows Media Player denetim eklenir **araç**.</span><span class="sxs-lookup"><span data-stu-id="c180b-122">The Windows Media Player control is added to the **Toolbox**.</span></span>  
  
7.  <span data-ttu-id="c180b-123">Çözüm Gezgini'nde sağ **UserControl1** dosya ve ardından **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="c180b-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>  
  
8.  <span data-ttu-id="c180b-124">Adına değiştirme `WmpAxControl.vb` veya `WmpAxControl.cs`dil bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c180b-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>  
  
9. <span data-ttu-id="c180b-125">Tüm başvuruları yeniden adlandırma istenirse tıklatın **Evet**.</span><span class="sxs-lookup"><span data-stu-id="c180b-125">If you are prompted to rename all references, click **Yes**.</span></span>  
  
## <a name="creating-the-activex-control"></a><span data-ttu-id="c180b-126">ActiveX denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c180b-126">Creating the ActiveX Control</span></span>  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]<span data-ttu-id="c180b-127">otomatik olarak oluşturan bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı için bir [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimi tasarım yüzeyine eklendiğinde denetim.</span><span class="sxs-lookup"><span data-stu-id="c180b-127"> automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="c180b-128">Aşağıdaki yordam AxInterop.WMPLib.dll yönetilen bir bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c180b-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>  
  
#### <a name="to-create-the-activex-control"></a><span data-ttu-id="c180b-129">ActiveX denetimi oluşturulamıyor</span><span class="sxs-lookup"><span data-stu-id="c180b-129">To create the ActiveX control</span></span>  
  
1.  <span data-ttu-id="c180b-130">Windows Forms Tasarımcısı'nda WmpAxControl.vb veya WmpAxControl.cs açın.</span><span class="sxs-lookup"><span data-stu-id="c180b-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="c180b-131">Gelen **araç**, Windows Media Player denetimi tasarım yüzeyine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c180b-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>  
  
3.  <span data-ttu-id="c180b-132">Özellikler penceresinde Windows Media Player denetimin değerini <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c180b-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
4.  <span data-ttu-id="c180b-133">WmpAxLib denetim kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c180b-133">Build the WmpAxLib control library project.</span></span>  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="c180b-134">WPF sayfasında ActiveX denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="c180b-134">Hosting the ActiveX Control on a WPF Page</span></span>  
  
#### <a name="to-host-the-activex-control"></a><span data-ttu-id="c180b-135">ActiveX denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="c180b-135">To host the ActiveX control</span></span>  
  
1.  <span data-ttu-id="c180b-136">HostingAxInWpf projesinde oluşturulan bir başvuru ekleyin [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] birlikte çalışabilirlik derleme.</span><span class="sxs-lookup"><span data-stu-id="c180b-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>  
  
     <span data-ttu-id="c180b-137">Bu derleme AxInterop.WMPLib.dll adlandırılır ve Windows Media Player denetimi aktarıldığında WmpAxLib projesinin Debug klasörüne eklendi.</span><span class="sxs-lookup"><span data-stu-id="c180b-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>  
  
2.  <span data-ttu-id="c180b-138">WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c180b-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="c180b-139">Bir başvuru ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll adlı derleme.</span><span class="sxs-lookup"><span data-stu-id="c180b-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>  
  
4.  <span data-ttu-id="c180b-140">WPF Tasarımcısı'nda MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="c180b-140">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
5.  <span data-ttu-id="c180b-141">Ad <xref:System.Windows.Controls.Grid> öğesi `grid1`.</span><span class="sxs-lookup"><span data-stu-id="c180b-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  <span data-ttu-id="c180b-142">Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c180b-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
7.  <span data-ttu-id="c180b-143">Özellikler penceresinde **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="c180b-143">In the Properties window, click the **Events** tab.</span></span>  
  
8.  <span data-ttu-id="c180b-144">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="c180b-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
9. <span data-ttu-id="c180b-145">İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="c180b-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     <span data-ttu-id="c180b-146">Bu kod örneği oluşturur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetlemek ve bir örneğini ekler `AxWindowsMediaPlayer` alt öğesi olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="c180b-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="c180b-147">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c180b-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c180b-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c180b-148">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c180b-149">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="c180b-149">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="c180b-150">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="c180b-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="c180b-151">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="c180b-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
