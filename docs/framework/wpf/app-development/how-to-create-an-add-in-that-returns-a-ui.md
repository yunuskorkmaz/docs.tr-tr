---
title: "Nasıl yapılır: UI Döndüren Eklenti Oluşturma"
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
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd6956f1934f8594a941b57066cc2d4d6214a9a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="f72a9-102">Nasıl yapılır: UI Döndüren Eklenti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f72a9-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="f72a9-103">Bu örnek döndüren bir eklenti oluşturmak nasıl gösterir bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir ana bilgisayara [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulama.</span><span class="sxs-lookup"><span data-stu-id="f72a9-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="f72a9-104">Eklenti döndürür bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer bir deyişle bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullanıcı denetimi.</span><span class="sxs-lookup"><span data-stu-id="f72a9-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="f72a9-105">Tek bir düğme, tıklatıldığında, kullanıcı denetimi içeriği olan bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f72a9-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="f72a9-106">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bağımsız uygulaması eklentiyi barındırır ve (eklenti tarafından döndürülen) kullanıcı denetimini ana uygulama penceresi içeriği olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f72a9-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="f72a9-107">**Önkoşullar**</span><span class="sxs-lookup"><span data-stu-id="f72a9-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="f72a9-108">Bu örnek vurgular [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aşağıdakileri varsayar ve bu senaryo etkinleştiren eklenti modeli:</span><span class="sxs-lookup"><span data-stu-id="f72a9-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="f72a9-109">Bilgisi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ardışık düzen, eklenti ve konak geliştirme de dahil olmak üzere eklenti modeli.</span><span class="sxs-lookup"><span data-stu-id="f72a9-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="f72a9-110">Bu kavramları tanımıyorsanız bkz [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md).</span><span class="sxs-lookup"><span data-stu-id="f72a9-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="f72a9-111">Bir ardışık düzen, eklenti ve bir ana bilgisayar uygulaması uygulanmasını gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="f72a9-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="f72a9-112">Bilgisi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , burada bulunabilir eklenti modeli: [WPF eklentileri genel bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f72a9-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72a9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f72a9-113">Example</span></span>  
 <span data-ttu-id="f72a9-114">Döndüren bir eklenti oluşturmak için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , her ardışık düzen segmenti, eklenti ve konak uygulama için belirli bir kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="f72a9-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="f72a9-115">Sözleşme ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="f72a9-116">Bir yöntem döndürmek için anlaşma tarafından tanımlanmalıdır bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ve onun dönüş değeri türü olmalıdır <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="f72a9-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="f72a9-117">Bu tarafından gösterilen `GetAddInUI` yöntemi `IWPFAddInContract` aşağıdaki kodda sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f72a9-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="f72a9-118">Eklenti görünümü ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="f72a9-119">Eklenti uyguladığından [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] alt sınıflarının sağlar <xref:System.Windows.FrameworkElement>, için karşılık gelen eklenti görünümü üzerindeki yöntem `IWPFAddInView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="f72a9-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="f72a9-120">Aşağıdaki kodu arabirim uygulanan anlaşmanın eklenti görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72a9-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="f72a9-121">Ekleme tarafı bağdaştırıcısı ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="f72a9-122">Anlaşma yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti döndürür bir <xref:System.Windows.FrameworkElement> (eklenti görünümü tarafından belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="f72a9-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="f72a9-123">Sonuç olarak, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.</span><span class="sxs-lookup"><span data-stu-id="f72a9-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="f72a9-124">Bu iş çağırarak Ekle tarafı bağdaştırıcı tarafından gerçekleştirilen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f72a9-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="f72a9-125">Ana görünüm ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="f72a9-126">Ana bilgisayar uygulamasını görüntüler çünkü bir <xref:System.Windows.FrameworkElement>, için karşılık gelen ana görünümü üzerindeki yöntem `IWPFAddInHostView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="f72a9-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="f72a9-127">Aşağıdaki kodu arabirim uygulanan anlaşmanın konak görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72a9-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="f72a9-128">Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="f72a9-129">Anlaşma yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak konak uygulama bekler bir <xref:System.Windows.FrameworkElement> (ana görünümü tarafından belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="f72a9-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="f72a9-130">Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmesinden sonra.</span><span class="sxs-lookup"><span data-stu-id="f72a9-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="f72a9-131">Bu iş çağırarak konak tarafı bağdaştırıcı tarafından gerçekleştirilen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f72a9-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="f72a9-132">Eklenti uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="f72a9-133">Oluşturulan, eklenti görünümü eklenti ve Ekle tarafı bağdaştırıcı (`WPFAddIn1.AddIn`) uygulamalıdır `IWPFAddInView.GetAddInUI` döndürülecek yöntemi bir <xref:System.Windows.FrameworkElement> nesne (bir <xref:System.Windows.Controls.UserControl> Bu örnekte).</span><span class="sxs-lookup"><span data-stu-id="f72a9-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="f72a9-134">Uygulaması <xref:System.Windows.Controls.UserControl>, `AddInUI`, aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f72a9-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="f72a9-135">Uygulaması `IWPFAddInView.GetAddInUI` eklenti tarafından yalnızca yeni bir örneğini döndürmesi gerekir `AddInUI`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f72a9-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="f72a9-136">Konak uygulamanın uygulama</span><span class="sxs-lookup"><span data-stu-id="f72a9-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="f72a9-137">Konak tarafı bağdaştırıcısı ile oluşturulan ana görünüm, ana bilgisayar uygulamasını kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Eklenti ardışık düzeni açın, eklenti ve çağrı konak görünümünü edinmek için model `IWPFAddInHostView.GetAddInUI` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f72a9-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="f72a9-138">Bu adımları aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f72a9-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="f72a9-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f72a9-139">See Also</span></span>  
 [<span data-ttu-id="f72a9-140">Eklentiler ve genişletilebilirlik</span><span class="sxs-lookup"><span data-stu-id="f72a9-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="f72a9-141">WPF eklentilere genel bakış</span><span class="sxs-lookup"><span data-stu-id="f72a9-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
