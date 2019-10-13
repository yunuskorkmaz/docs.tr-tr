---
title: 'Nasıl yapılır: UI döndüren eklenti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: e32987355a6c7ad32b5e0e8522dc4daa63783fdd
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291252"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="d0e42-102">Nasıl yapılır: UI döndüren eklenti oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0e42-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="d0e42-103">Bu örnek, bir konak WPF tek başına uygulamasına Windows Presentation Foundation (WPF) döndüren bir eklentinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="d0e42-104">Eklenti, WPF Kullanıcı denetimi olan bir kullanıcı arabirimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0e42-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="d0e42-105">Kullanıcı denetiminin içeriği, tıklandığında bir ileti kutusu görüntüleyen tek bir düğmedir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="d0e42-106">WPF tek başına uygulaması eklentiyi barındırır ve Kullanıcı denetimini (eklenti tarafından döndürülen) ana uygulama penceresinin içeriği olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0e42-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="d0e42-107">**Önkoşullar**</span><span class="sxs-lookup"><span data-stu-id="d0e42-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="d0e42-108">Bu örnek, WPF uzantılarını bu senaryoyu etkinleştiren .NET Framework eklenti modeline vurgular ve şunları varsayar:</span><span class="sxs-lookup"><span data-stu-id="d0e42-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="d0e42-109">İşlem hattı, eklenti ve konak geliştirme dahil .NET Framework eklenti modeli hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="d0e42-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="d0e42-110">Bu kavramları tanımıyorsanız, bkz. eklentiler [ve genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="d0e42-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="d0e42-111">Bir işlem hattının, eklentinin ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için bkz. [Izlenecek yol: Genişletilebilir uygulama oluşturma](../../add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="d0e42-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
- <span data-ttu-id="d0e42-112">.NET Framework eklenti modeli için WPF uzantıları hakkında bilgi, burada bulunabilir: [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d0e42-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0e42-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0e42-113">Example</span></span>  
 <span data-ttu-id="d0e42-114">WPF Kullanıcı arabirimini döndüren bir eklenti oluşturmak için her bir ardışık düzen segmenti, eklentisi ve ana bilgisayar uygulaması için belirli bir kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="d0e42-115">Sözleşme ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="d0e42-116">Bir yöntem, Kullanıcı arabirimi döndürmek için anlaşma tarafından tanımlanmalıdır ve dönüş değeri <xref:System.AddIn.Contract.INativeHandleContract> türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0e42-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="d0e42-117">Bu, aşağıdaki kodda `IWPFAddInContract` sözleşmesinin `GetAddInUI` yöntemi tarafından gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="d0e42-118">Eklenti görünümü ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="d0e42-119">Eklenti Usıs 'yi <xref:System.Windows.FrameworkElement> ' ın alt sınıfları olarak sağladığından, `IWPFAddInView.GetAddInUI` ' i ile ilişkili eklenti görünümündeki Yöntem <xref:System.Windows.FrameworkElement> türünde bir değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="d0e42-120">Aşağıdaki kod, bir arabirim olarak uygulanan, sözleşmenin eklenti görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="d0e42-121">Eklenti tarafı bağdaştırıcısı ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="d0e42-122">Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract> döndürür, ancak eklenti bir <xref:System.Windows.FrameworkElement> döndürür (eklenti görünümü tarafından belirtilen şekilde).</span><span class="sxs-lookup"><span data-stu-id="d0e42-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="d0e42-123">Sonuç olarak, yalıtım sınırını geçmeden önce <xref:System.Windows.FrameworkElement> ' ı bir <xref:System.AddIn.Contract.INativeHandleContract> ' e dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="d0e42-124">Bu iş, aşağıdaki kodda gösterildiği gibi <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ' ı çağırarak eklenti tarafı bağdaştırıcısı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="d0e42-125">Konak görünümü ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="d0e42-126">Ana bilgisayar uygulaması <xref:System.Windows.FrameworkElement> olarak görüntüleyeceği için, konak görünümündeki `IWPFAddInHostView.GetAddInUI` ile ilişkili Yöntem <xref:System.Windows.FrameworkElement> türünde bir değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="d0e42-127">Aşağıdaki kod, bir arabirim olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="d0e42-128">Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="d0e42-129">Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract> döndürür, ancak konak uygulama bir @no__t (konak görünümü tarafından belirtildiği gibi) bekliyor.</span><span class="sxs-lookup"><span data-stu-id="d0e42-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="d0e42-130">Sonuç olarak, yalıtım sınırını geçirdikten sonra <xref:System.AddIn.Contract.INativeHandleContract> ' ı bir <xref:System.Windows.FrameworkElement> ' e dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="d0e42-131">Bu iş, aşağıdaki kodda gösterildiği gibi <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ' ı çağırarak ana bilgisayar tarafı bağdaştırıcısı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="d0e42-132">Eklentiyi uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="d0e42-133">Eklenti tarafı bağdaştırıcısı ve eklenti görünümü oluşturulduğunda, eklenti (`WPFAddIn1.AddIn`), bir <xref:System.Windows.FrameworkElement> nesnesi (Bu örnekte bir <xref:System.Windows.Controls.UserControl>) döndürmek için `IWPFAddInView.GetAddInUI` metodunu uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0e42-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="d0e42-134">@No__t-0 `AddInUI` ' in uygulanması aşağıdaki kodla gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="d0e42-135">@No__t-0 ' ın uygulanması, aşağıdaki kodda gösterildiği gibi, tek yapmanız gereken yeni bir `AddInUI` örneği döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="d0e42-136">Konak uygulamasını uygulama</span><span class="sxs-lookup"><span data-stu-id="d0e42-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="d0e42-137">Konak tarafı bağdaştırıcısı ve konak görünümü oluşturulduğunda konak uygulama, .NET Framework eklenti modelini kullanarak işlem hattını açabilir, eklentinin bir konak görünümünü alabilir ve `IWPFAddInHostView.GetAddInUI` yöntemini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="d0e42-138">Bu adımlar aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0e42-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="d0e42-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e42-139">See also</span></span>

- <span data-ttu-id="d0e42-140">[Eklentiler ve genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="d0e42-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="d0e42-141">WPF Eklentilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0e42-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
