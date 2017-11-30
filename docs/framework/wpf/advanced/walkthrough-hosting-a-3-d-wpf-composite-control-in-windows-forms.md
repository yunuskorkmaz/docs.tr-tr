---
title: "İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="92a14-102">İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="92a14-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="92a14-103">Bu kılavuz, nasıl oluşturabileceğinizi gösterir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim ve içinde ana bilgisayar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve kullanarak forms <xref:System.Windows.Forms.Integration.ElementHost> denetim.</span><span class="sxs-lookup"><span data-stu-id="92a14-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="92a14-104">Bu kılavuzda, uygulayacak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> iki alt denetimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="92a14-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="92a14-105"><xref:System.Windows.Controls.UserControl> Üç boyutlu (3-b) koni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="92a14-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="92a14-106">3-b nesneleri işleme ile çok daha kolay [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fazla ile [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a14-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="92a14-107">Bu nedenle, bu konağa mantıklı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 3B grafik oluşturmak için sınıf [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a14-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="92a14-108">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="92a14-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="92a14-109">Oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="92a14-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="92a14-110">Windows Forms konak projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="92a14-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="92a14-111">Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="92a14-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="92a14-112">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [3-b WPF bileşik denetim Windows Forms örnekteki barındırma](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="92a14-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="92a14-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="92a14-113">Prerequisites</span></span>  
 <span data-ttu-id="92a14-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="92a14-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="92a14-115">.</span><span class="sxs-lookup"><span data-stu-id="92a14-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="92a14-116">UserControl oluşturma</span><span class="sxs-lookup"><span data-stu-id="92a14-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="92a14-117">UserControl oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="92a14-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="92a14-118">Adlı bir WPF kullanıcı denetimi kitaplığı projesi oluşturun `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="92a14-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="92a14-119">' Da UserControl1.xaml'i açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a14-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="92a14-120">Oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92a14-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="92a14-121">Bu kodu tanımlayan bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> iki alt denetimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="92a14-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="92a14-122">İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetim; ikinci olan bir <xref:System.Windows.Controls.Viewport3D> 3-b koni görüntüleyen denetim.</span><span class="sxs-lookup"><span data-stu-id="92a14-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="92a14-123">Windows Forms konak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="92a14-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="92a14-124">Konak projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="92a14-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="92a14-125">Adlı bir Windows uygulaması projesi eklemek `WpfUserControlHost` çözüme.</span><span class="sxs-lookup"><span data-stu-id="92a14-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="92a14-126">Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="92a14-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="92a14-127">Çözüm Gezgininde WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92a14-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="92a14-128">Aşağıdaki başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler:</span><span class="sxs-lookup"><span data-stu-id="92a14-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="92a14-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="92a14-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="92a14-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="92a14-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="92a14-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="92a14-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="92a14-132">Bir başvuru ekleyin `HostingWpfUserControlInWf` projesi.</span><span class="sxs-lookup"><span data-stu-id="92a14-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="92a14-133">Çözüm Gezgininde ayarlayın `WpfUserControlHost` projesini başlangıç projesi olacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="92a14-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="92a14-134">Windows Presentation Foundation UserControl barındırma</span><span class="sxs-lookup"><span data-stu-id="92a14-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="92a14-135">UserControl barındırmak için</span><span class="sxs-lookup"><span data-stu-id="92a14-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="92a14-136">Windows Forms Tasarımcısı'nda Form1 açın.</span><span class="sxs-lookup"><span data-stu-id="92a14-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="92a14-137">Özellikler penceresinde **olayları**, çift tıklayın ve ardından <xref:System.Windows.Forms.Form.Load> olay olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92a14-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="92a14-138">Kod Düzenleyicisi yeni oluşturulan açar `Form1_Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="92a14-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="92a14-139">Form1.cs içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92a14-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="92a14-140">`Form1_Load` Olay işleyicisi oluşturur örneği `UserControl1` ve yönlendirir ekler <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetimler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="92a14-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="92a14-141"><xref:System.Windows.Forms.Integration.ElementHost> Denetimi formun alt denetimler koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="92a14-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="92a14-142">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="92a14-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a14-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92a14-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="92a14-144">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="92a14-144">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="92a14-145">İzlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="92a14-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="92a14-146">İzlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma</span><span class="sxs-lookup"><span data-stu-id="92a14-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="92a14-147">Windows Forms örnek bir WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="92a14-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
