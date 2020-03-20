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
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174595"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="538b8-102">Nasıl yapılır: UI Döndüren Eklenti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="538b8-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="538b8-103">Bu örnek, ana bilgisayar WPF bağımsız uygulamasına Windows Sunu Temeli (WPF) döndüren bir eklentinin nasıl oluşturulacağınÝ gösterir.</span><span class="sxs-lookup"><span data-stu-id="538b8-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="538b8-104">Eklenti, WPF kullanıcı denetimi olan bir Kullanıcı Aracı döndürür.</span><span class="sxs-lookup"><span data-stu-id="538b8-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="538b8-105">Kullanıcı denetiminin içeriği, tıklatıldığında bir ileti kutusu görüntüleyen tek bir düğmedir.</span><span class="sxs-lookup"><span data-stu-id="538b8-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="538b8-106">WPF bağımsız uygulaması eklentiyi barındırAr ve kullanıcı denetimini (eklenti tarafından döndürülür) ana uygulama penceresinin içeriği olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="538b8-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="538b8-107">**Önkoşullar**</span><span class="sxs-lookup"><span data-stu-id="538b8-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="538b8-108">Bu örnek, bu senaryoyu etkinleştiren .NET Framework eklentisi modelindeki WPF uzantılarını vurgular ve aşağıdakileri varsayar:</span><span class="sxs-lookup"><span data-stu-id="538b8-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="538b8-109">Boru hattı, eklenti ve ana bilgisayar geliştirme dahil olmak üzere .NET Framework eklentisi modeli hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="538b8-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="538b8-110">Bu kavramlara aşina değilseniz, [Eklentiler ve Genişletilebilirlik'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="538b8-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="538b8-111">Bir ardışık hatlar, eklenti ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için [bkz.](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="538b8-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="538b8-112">.NET Framework eklenti modeline WPF uzantıları hakkında bilgi, burada bulunabilir: [WPF Eklentiler Genel Bakış](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="538b8-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="538b8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="538b8-113">Example</span></span>  
 <span data-ttu-id="538b8-114">WPF Kullanıcı Arabirimi döndüren bir eklenti oluşturmak için her bir dizi nial, eklenti ve ana bilgisayar uygulaması için belirli bir kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="538b8-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="538b8-115">Sözleşme Boru Hattı Segmentinin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="538b8-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="538b8-116">Bir yöntem, ui'yi döndürmek için sözleşme tarafından tanımlanmalı ve <xref:System.AddIn.Contract.INativeHandleContract>iade değeri türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="538b8-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="538b8-117">Bu, aşağıdaki kodda `GetAddInUI` `IWPFAddInContract` sözleşme yöntemi ile gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="538b8-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="538b8-118">Eklenti Görünüm Ardışık Bölüm'e Uygulama</span><span class="sxs-lookup"><span data-stu-id="538b8-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="538b8-119">Eklenti alt sınıflar olarak sağladığı UIs'leri <xref:System.Windows.FrameworkElement>uyguladığından, eklenti görünümünde ilişkili olan yöntem `IWPFAddInView.GetAddInUI` intifa <xref:System.Windows.FrameworkElement>türünde bir değer döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="538b8-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="538b8-120">Aşağıdaki kod, arabirim olarak uygulanan sözleşmenin eklenti görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="538b8-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="538b8-121">Eklenti Bağdaştırıcı Boru Hattı Segmentinin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="538b8-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="538b8-122">Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti bir <xref:System.Windows.FrameworkElement> döndürür (eklenti görünümünde belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="538b8-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="538b8-123">Sonuç olarak, <xref:System.Windows.FrameworkElement> izolasyon sınırını geçmeden <xref:System.AddIn.Contract.INativeHandleContract> önce bir dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="538b8-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="538b8-124">Bu çalışma, aşağıdaki kodda gösterildiği gibi, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>yan add-in-side bağdaştırıcı tarafından çağrılar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="538b8-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="538b8-125">Ana Bilgisayar Görünümü Ardışık Bölüm'e Uygulama</span><span class="sxs-lookup"><span data-stu-id="538b8-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="538b8-126">Ana bilgisayar uygulaması, <xref:System.Windows.FrameworkElement>ana bilgisayar görünümünde ilişkili olan yöntem `IWPFAddInHostView.GetAddInUI` in türünün <xref:System.Windows.FrameworkElement>bir değerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="538b8-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="538b8-127">Aşağıdaki kod, arabirim olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="538b8-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="538b8-128">Ana Bilgisayar-Yan Bağdaştırıcı Boru Hattı Segmentinin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="538b8-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="538b8-129">Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak ana <xref:System.Windows.FrameworkElement> bilgisayar uygulaması (ana bilgisayar görünümünde belirtildiği gibi) bir bekliyor.</span><span class="sxs-lookup"><span data-stu-id="538b8-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="538b8-130">Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> izolasyon sınırını geçtikten sonra a <xref:System.Windows.FrameworkElement> dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="538b8-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="538b8-131">Bu çalışma, aşağıdaki kodda gösterildiği gibi, ana bilgisayar tarafı bağdaştırıcısı tarafından çağrılarek <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="538b8-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="538b8-132">Eklentinin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="538b8-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="538b8-133">Eklenti tarafı bağdaştırıcısı ve oluşturulan eklenti görünümüyle,`WPFAddIn1.AddIn`eklenti ( `IWPFAddInView.GetAddInUI` ) bir <xref:System.Windows.FrameworkElement> nesneyi <xref:System.Windows.Controls.UserControl> (bu örnekte) döndürmek için yöntemi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="538b8-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="538b8-134">" <xref:System.Windows.Controls.UserControl>, , `AddInUI`uygulanması aşağıdaki kodla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="538b8-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="538b8-135">Eklenti `IWPFAddInView.GetAddInUI` tarafından uygulanması sadece aşağıdaki kod da gösterildiği `AddInUI`gibi, yeni bir örnek döndürmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="538b8-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="538b8-136">Ana Bilgisayar Uygulamasının Uygulanması</span><span class="sxs-lookup"><span data-stu-id="538b8-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="538b8-137">Ana bilgisayar tarafı bağdaştırıcısı ve ana bilgisayar görünümü oluşturulduğunda, ana bilgisayar uygulaması .NET Framework eklentisi modelini `IWPFAddInHostView.GetAddInUI` kullanarak ardışık alanı açabilir, eklentinin ana bilgisayar görünümünü alabilir ve yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="538b8-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="538b8-138">Bu adımlar aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="538b8-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="538b8-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="538b8-139">See also</span></span>

- <span data-ttu-id="538b8-140">[Eklentiler ve Genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="538b8-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="538b8-141">WPF Eklentilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="538b8-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
