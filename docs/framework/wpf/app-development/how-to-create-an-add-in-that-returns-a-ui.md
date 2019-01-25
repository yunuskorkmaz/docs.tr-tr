---
title: 'Nasıl yapılır: UI Döndüren Eklenti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 0c7a91a53a16012340b5612e19255dfd2f2bad85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654093"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="22e75-102">Nasıl yapılır: UI Döndüren Eklenti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="22e75-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="22e75-103">Bu örnek, bir Windows Presentation Foundation (WPF) bir konak WPF tek başına uygulama döndüren bir eklenti oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22e75-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="22e75-104">Eklentinin bir WPF kullanıcı denetimi olan bir kullanıcı Arabirimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="22e75-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="22e75-105">Tek bir düğme, tıklandığında, kullanıcı denetiminin içeriği olan bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22e75-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="22e75-106">WPF tek başına uygulama eklenti barındırır ve (eklenti tarafından döndürülen) kullanıcı denetimi ana uygulama penceresini içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22e75-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="22e75-107">**Önkoşullar**</span><span class="sxs-lookup"><span data-stu-id="22e75-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="22e75-108">Bu örnekte, bu senaryoyu WPF uzantıları için .NET Framework eklenti modeli vurgular ve aşağıdaki varsayar:</span><span class="sxs-lookup"><span data-stu-id="22e75-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="22e75-109">Bilgi işlem hattı, eklenti ve konak geliştirme gibi .NET Framework eklenti modeli, sahibi.</span><span class="sxs-lookup"><span data-stu-id="22e75-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="22e75-110">Bu kavramları alışkın değilseniz bkz [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="22e75-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="22e75-111">Bir işlem hattı, bir eklenti ve ana bilgisayar uygulamasına uygulanışı gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="22e75-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="22e75-112">WPF uzantıları için burada bulunan .NET Framework eklenti modeli bilgi: [WPF Eklentilerine Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="22e75-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e75-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="22e75-113">Example</span></span>  
 <span data-ttu-id="22e75-114">Bir WPF UI döndüren eklenti oluşturmak için her işlem hattı segment, eklenti ve ana bilgisayar uygulaması için özel kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="22e75-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="22e75-115">Sözleşme ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="22e75-116">Bir yöntem tarafından bir kullanıcı Arabirimi döndürmek için anlaşma tanımlanmalıdır ve dönüş değerinin türü olmalıdır <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="22e75-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="22e75-117">Bu tarafından gösterilmiştir `GetAddInUI` yöntemi `IWPFAddInContract` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="22e75-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="22e75-118">Eklenti görünümü işlem hattı segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="22e75-119">Eklenti uyguladığından [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] alt sınıfları sağlar <xref:System.Windows.FrameworkElement>, belirtilirler eklenti görünümü metodunda `IWPFAddInView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="22e75-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="22e75-120">Aşağıdaki kod, bir arabirim uygulanan sözleşme, eklenti görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="22e75-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="22e75-121">Ekleme tarafı bağdaştırıcısı işlem hattı segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="22e75-122">Sözleşme yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti döndürür bir <xref:System.Windows.FrameworkElement> (eklenti görünümü belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="22e75-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="22e75-123">Sonuç olarak, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.</span><span class="sxs-lookup"><span data-stu-id="22e75-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="22e75-124">Bu iş tarafından Ekle tarafı bağdaştırıcısı çağrılarak gerçekleştirilir <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="22e75-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="22e75-125">Ana görünüm ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="22e75-126">Ana bilgisayar uygulaması görüntüleyeceği için bir <xref:System.Windows.FrameworkElement>, yöntem için karşılık gelen ana görünümünde `IWPFAddInHostView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="22e75-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="22e75-127">Aşağıdaki kod, bir arabirim uygulanan sözleşme ana görünümünde gösterir.</span><span class="sxs-lookup"><span data-stu-id="22e75-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="22e75-128">Konak tarafı bağdaştırıcısı işlem hattı segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="22e75-129">Sözleşme yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ana bilgisayar uygulaması bekliyor, ancak bir <xref:System.Windows.FrameworkElement> (ana görünümünde tarafından belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="22e75-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="22e75-130">Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra.</span><span class="sxs-lookup"><span data-stu-id="22e75-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="22e75-131">Bu iş tarafından konak tarafı bağdaştırıcısı çağrılarak gerçekleştirilir <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="22e75-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="22e75-132">Eklenti uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="22e75-133">Oluşturulan, eklenti görünümü eklenti ve Ekle tarafı bağdaştırıcısı (`WPFAddIn1.AddIn`) uygulamalıdır `IWPFAddInView.GetAddInUI` döndürülecek yöntemi bir <xref:System.Windows.FrameworkElement> nesne (bir <xref:System.Windows.Controls.UserControl> Bu örnekte).</span><span class="sxs-lookup"><span data-stu-id="22e75-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="22e75-134">Uygulamasını <xref:System.Windows.Controls.UserControl>, `AddInUI`, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22e75-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="22e75-135">Uygulamasını `IWPFAddInView.GetAddInUI` eklenti tarafından yeni bir örneğini döndürülecek yalnızca erişmesi `AddInUI`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="22e75-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="22e75-136">Konak uygulamanın uygulama</span><span class="sxs-lookup"><span data-stu-id="22e75-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="22e75-137">Konak tarafı bağdaştırıcısı ile oluşturulan ana görünümünde, konak uygulama .NET Framework eklenti modeli kullanabileceğiniz işlem hattı açmak için bir ana bilgisayar görünümü eklenti ve çağrı alma `IWPFAddInHostView.GetAddInUI` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22e75-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="22e75-138">Aşağıdaki kodda adımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22e75-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="22e75-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22e75-139">See also</span></span>
- <span data-ttu-id="22e75-140">[Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="22e75-140">[Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="22e75-141">WPF Eklentilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="22e75-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
