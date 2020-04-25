---
title: Windows genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: 24f2d1fc64333230c10afb79baed5dc373b3d590
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141168"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="3e474-102">WPF Windows'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e474-102">WPF Windows Overview</span></span>
<span data-ttu-id="3e474-103">Kullanıcılar Windows aracılığıyla Windows Presentation Foundation (WPF) tek başına uygulamalarıyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="3e474-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="3e474-104">Bir pencerenin birincil amacı, verileri görselleştirerek kullanıcıların verilerle etkileşime geçmesini sağlayan içeriği barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="3e474-105">Tek başına WPF uygulamaları, <xref:System.Windows.Window> sınıfını kullanarak kendi pencerelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="3e474-106">Bu konu, <xref:System.Windows.Window> Windows 'un tek başına uygulamalarda oluşturulması ve yönetilmesi ile ilgili temel bilgileri kapsamadan önce tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e474-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-107">XAML tarayıcı uygulamaları (XBAP 'ler) ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfalar dahil olmak üzere TARAYıCıDA barındırılan WPF uygulamaları kendi pencerelerini sağlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="3e474-108">Bunun yerine, Windows Internet Explorer tarafından sunulan Windows 'da barındırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="3e474-109">Bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e474-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="3e474-110">Pencere sınıfı</span><span class="sxs-lookup"><span data-stu-id="3e474-110">The Window Class</span></span>  
 <span data-ttu-id="3e474-111">Aşağıdaki şekilde pencerenin yapısal kısımları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e474-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Pencere öğelerini gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="3e474-113">Bir pencere iki alana ayrılmıştır: istemci olmayan alan ve istemci alanı.</span><span class="sxs-lookup"><span data-stu-id="3e474-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="3e474-114">Bir pencerenin *istemci olmayan alanı* WPF tarafından uygulanır ve aşağıdakiler dahil olmak üzere çoğu Windows için ortak olan bir pencerenin parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="3e474-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="3e474-115">Bir kenarlık.</span><span class="sxs-lookup"><span data-stu-id="3e474-115">A border.</span></span>  
  
- <span data-ttu-id="3e474-116">Başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="3e474-116">A title bar.</span></span>  
  
- <span data-ttu-id="3e474-117">Bir simge.</span><span class="sxs-lookup"><span data-stu-id="3e474-117">An icon.</span></span>  
  
- <span data-ttu-id="3e474-118">Küçült, Ekranı Kapla ve geri yükle düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="3e474-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="3e474-119">Kapat düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-119">A Close button.</span></span>  
  
- <span data-ttu-id="3e474-120">Kullanıcıların bir pencereyi en aza indirmenize, ekranı kaplamaya, geri yüklemelerine, taşımasına, yeniden boyutlandırmaya ve kapatılmasına izin veren menü öğeleriyle bir sistem menüsü.</span><span class="sxs-lookup"><span data-stu-id="3e474-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="3e474-121">Pencerenin *istemci alanı* , bir pencerenin istemci olmayan alanındaki alanıdır ve geliştiriciler tarafından menü çubukları, araç çubukları ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="3e474-122">WPF 'de, bir pencere, aşağıdakileri yapmak için <xref:System.Windows.Window> kullandığınız sınıfa göre kapsüllenir:</span><span class="sxs-lookup"><span data-stu-id="3e474-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="3e474-123">Bir pencere görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3e474-123">Display a window.</span></span>  
  
- <span data-ttu-id="3e474-124">Pencerenin boyutunu, konumunu ve görünümünü yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3e474-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="3e474-125">Uygulamaya özgü içeriği barındırın.</span><span class="sxs-lookup"><span data-stu-id="3e474-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="3e474-126">Pencerenin ömrünü yönetin.</span><span class="sxs-lookup"><span data-stu-id="3e474-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="3e474-127">Pencere uygulama</span><span class="sxs-lookup"><span data-stu-id="3e474-127">Implementing a Window</span></span>  
 <span data-ttu-id="3e474-128">Tipik bir pencerenin uygulanması, görünümün ve davranışın yanı sıra, *görünümün* kullanıcılar tarafından kullanıcılara nasıl göründüğünü ve *davranışın* Kullanıcı tarafından etkileşim kurma şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="3e474-129">WPF 'de, kod veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanarak bir pencerenin görünümünü ve davranışını uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="3e474-130">Ancak, genel olarak, bir pencerenin görünümü biçimlendirme kullanılarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulanır ve davranışı aşağıdaki örnekte gösterildiği gibi arka plan kodu kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="3e474-131">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme dosyası ve arka plan kod dosyasının birlikte çalışmasını sağlamak için aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3e474-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="3e474-132">Biçimlendirme ' de, `Window` öğesi `x:Class` özniteliğini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="3e474-133">Uygulama yapılandırıldığında `x:Class` , biçimlendirme dosyasında bulunması Microsoft Build Engine (MSBuild) ' den `partial` <xref:System.Windows.Window> türetilen ve `x:Class` özniteliği tarafından belirtilen adı içeren bir sınıf oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3e474-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="3e474-134">Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ) için bir XML ad alanı bildiriminin eklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="3e474-135">Oluşturulan `partial` sınıf, olayları kaydetmek `InitializeComponent` ve biçimlendirmede uygulanan özellikleri ayarlamak için çağrılan yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="3e474-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="3e474-136">Arka plan kod içinde, sınıf, biçimlendirme içindeki `partial` `x:Class` özniteliği tarafından belirtilen aynı ada sahip bir sınıf olmalıdır ve ' den <xref:System.Windows.Window>türetmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="3e474-137">Bu, arka plan kod dosyasının, uygulama oluşturulduğunda biçimlendirme dosyası için `partial` oluşturulan sınıfla ilişkilendirilmesini sağlar (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="3e474-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="3e474-138">Arka plan kod içinde, <xref:System.Windows.Window> sınıfının `InitializeComponent` yöntemini çağıran bir Oluşturucu uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="3e474-139">`InitializeComponent`, biçimlendirme dosyasının oluşturulan `partial` sınıfı tarafından olayları kaydetmek ve biçimlendirmede tanımlanan özellikleri ayarlamak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-140">Projenize Visual Studio <xref:System.Windows.Window> kullanarak yeni <xref:System.Windows.Window> bir eklediğinizde, hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır ve burada açıklanan biçimlendirme ve arka plan kod dosyaları arasındaki ilişkiyi oluşturmak için gereken yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="3e474-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="3e474-141">Bu yapılandırmayla birlikte, biçimlendirme ' de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pencerenin görünümünü tanımlamaya ve davranışını arka plan kodu ' nda uygulamaya odaklanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3e474-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="3e474-142">Aşağıdaki örnek, bir düğme içeren bir pencereyi, biçimlendirme ' de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulanan bir pencere ve düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir olay işleyicisi gösterir ve arka plan kod içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="3e474-143">MSBuild için pencere tanımı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e474-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="3e474-144">Pencerenizi nasıl uyguladığınız, MSBuild için nasıl yapılandırıldığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3e474-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="3e474-145">Hem biçimlendirme hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arka plan kodu kullanılarak tanımlanan bir pencere için:</span><span class="sxs-lookup"><span data-stu-id="3e474-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="3e474-146">XAML biçimlendirme dosyaları MSBuild `Page` öğeleri olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="3e474-147">Arka plan kod dosyaları MSBuild `Compile` öğeleri olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="3e474-148">Bu, aşağıdaki MSBuild proje dosyasında gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e474-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="3e474-149">WPF uygulamaları oluşturma hakkında daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3e474-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="3e474-150">Pencere ömrü</span><span class="sxs-lookup"><span data-stu-id="3e474-150">Window Lifetime</span></span>  
 <span data-ttu-id="3e474-151">Herhangi bir sınıfta olduğu gibi, bir pencere ilk kez başlatıldığında başlayan, açıldıktan sonra, etkin ve devre dışı bırakılmış ve sonunda kapatılan bir yaşam süresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e474-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="3e474-152">Pencere açma</span><span class="sxs-lookup"><span data-stu-id="3e474-152">Opening a Window</span></span>  
 <span data-ttu-id="3e474-153">Bir pencereyi açmak için ilk olarak bir örneği oluşturursunuz, bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e474-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="3e474-154">Bu örnekte `MarkupAndCodeBehindWindow` , uygulama başladığında oluşur ve <xref:System.Windows.Application.Startup> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="3e474-155">Bir pencere oluşturulduğunda, <xref:System.Windows.Application> nesne tarafından yönetilen bir Windows listesine otomatik olarak bir başvuru eklenir (bkz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>.).</span><span class="sxs-lookup"><span data-stu-id="3e474-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="3e474-156">Ayrıca, örneği oluşturulacak ilk pencere, varsayılan olarak, ana uygulama penceresi (bkz <xref:System.Windows.Application> <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>.) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="3e474-157">Pencere son olarak <xref:System.Windows.Window.Show%2A> yöntemi çağırarak açılır. Sonuç aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e474-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Window. Show çağırarak bir pencere açıldı](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="3e474-159">Çağırarak <xref:System.Windows.Window.Show%2A> açılan bir pencere, uygulamanın, kullanıcıların aynı uygulamadaki diğer pencereleri etkinleştirmesine izin veren bir modda çalıştığı, geçici bir pencere olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e474-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-160"><xref:System.Windows.Window.ShowDialog%2A>, iletişim kutuları gibi pencere açmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="3e474-161">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="3e474-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="3e474-162"><xref:System.Windows.Window.Show%2A> Çağrıldığında, bir pencere, Kullanıcı girişi almasına izin veren altyapıyı kurmak üzere gösterilmeden önce başlatma işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="3e474-163">Pencere başlatıldığında <xref:System.Windows.Window.SourceInitialized> olay tetiklenir ve pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="3e474-164">Bir kısayol olarak, <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılan ilk pencereyi belirtmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="3e474-165">Uygulama başlatıldığında, değeri <xref:System.Windows.Application.StartupUri%2A> tarafından belirtilen pencere, modelessly olarak açılır. dahili olarak, pencere <xref:System.Windows.Window.Show%2A> yöntemi çağırarak açılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="3e474-166">Pencere sahipliği</span><span class="sxs-lookup"><span data-stu-id="3e474-166">Window Ownership</span></span>  
 <span data-ttu-id="3e474-167"><xref:System.Windows.Window.Show%2A> Yöntemi kullanılarak açılan bir pencere, onu oluşturan pencereyle örtük bir ilişkiye sahip değildir; Kullanıcılar, herhangi bir pencereden bağımsız olarak etkileşime girebilir, yani her iki pencere de şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="3e474-168">Diğerini (pencerelerin bir <xref:System.Windows.Window.Topmost%2A> özelliği olarak `true`ayarlanmış değilse) kapsar.</span><span class="sxs-lookup"><span data-stu-id="3e474-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="3e474-169">Diğerini etkilemeden simge durumuna küçültülmüş, ekranı kaplamış ve geri yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="3e474-170">Bazı pencereler, açan pencereyle bir ilişki gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="3e474-171">Örneğin, tümleşik bir geliştirme ortamı (IDE) uygulaması, normal davranışı kendilerini oluşturan pencereyi kapsayan özellik pencerelerini ve araç pencerelerini açabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="3e474-172">Ayrıca, bu gibi pencerelerin her zaman, bunları oluşturan pencereyle birlikte her zaman kapatmaları, en üst düzeye çıkarması ve geri yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="3e474-173">Bu tür bir ilişki, *bir pencere diğeri* tarafından oluşturulabilir ve sahip <xref:System.Windows.Window.Owner%2A> *pencerenin özelliği* *sahip penceresine*bir başvuru olarak ayarlanarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="3e474-174">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="3e474-175">Sahiplik kurulduktan sonra:</span><span class="sxs-lookup"><span data-stu-id="3e474-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="3e474-176">Sahibi olan pencere, <xref:System.Windows.Window.Owner%2A> özelliğinin değerini inceleyerek sahip penceresine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="3e474-177">Sahip penceresi, <xref:System.Windows.Window.OwnedWindows%2A> özelliğinin değerini inceleyerek sahip olduğu tüm pencereleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="3e474-178">Windows etkinleştirmesini önler</span><span class="sxs-lookup"><span data-stu-id="3e474-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="3e474-179">Internet Messenger stili uygulamanın konuşma pencereleri veya bir e-posta uygulamasının bildirim pencereleri gibi, gösterildiğinde Windows 'un etkinleştirilmemesi gereken senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="3e474-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="3e474-180">Uygulamanızda, gösterildiğinde etkinleştirilmemelidir bir pencere varsa, <xref:System.Windows.Window.ShowActivated%2A> `false` <xref:System.Windows.Window.Show%2A> yöntemi ilk kez çağrılmadan önce özelliğini olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="3e474-181">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="3e474-181">As a consequence:</span></span>  
  
- <span data-ttu-id="3e474-182">Pencere etkin değil.</span><span class="sxs-lookup"><span data-stu-id="3e474-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="3e474-183">Pencerenin <xref:System.Windows.Window.Activated> olayı çıkarılmadı.</span><span class="sxs-lookup"><span data-stu-id="3e474-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="3e474-184">Etkin durumda olan pencere etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="3e474-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="3e474-185">Ancak, Kullanıcı istemciyi veya istemci dışı alanı tıklatarak etkinleştirdiğinde, pencere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="3e474-186">Bu durumda:</span><span class="sxs-lookup"><span data-stu-id="3e474-186">In this case:</span></span>  
  
- <span data-ttu-id="3e474-187">Pencere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-187">The window is activated.</span></span>  
  
- <span data-ttu-id="3e474-188">Pencerenin <xref:System.Windows.Window.Activated> olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="3e474-189">Önceden etkinleştirilen pencere devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3e474-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="3e474-190">Pencere <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayları daha sonra kullanıcı eylemlerine yanıt olarak beklendiği gibi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e474-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="3e474-191">Pencere etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3e474-191">Window Activation</span></span>  
 <span data-ttu-id="3e474-192">Bir pencere ilk açıldığında etkin pencere olur (olarak <xref:System.Windows.Window.ShowActivated%2A> `false`ayarlanmış olarak gösterilmediği takdirde).</span><span class="sxs-lookup"><span data-stu-id="3e474-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="3e474-193">*Etkin pencere* , anahtar vuruşları ve fare tıklamaları gibi şu anda Kullanıcı girişi yakalama penceresidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="3e474-194">Bir pencere etkin olduğunda <xref:System.Windows.Window.Activated> olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="3e474-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-195">Bir pencere ilk açıldığında, <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.Window.ContentRendered> olayları yalnızca <xref:System.Windows.Window.Activated> olay oluşturulduktan sonra tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="3e474-196">Bu şekilde aklınızda, bir pencere başlatıldığında açık <xref:System.Windows.Window.ContentRendered> olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="3e474-197">Bir pencere etkin olduktan sonra, Kullanıcı aynı uygulamadaki başka bir pencereyi etkinleştirebilir veya başka bir uygulamayı etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="3e474-198">Bu durumda, etkin olan pencere devre dışı bırakılır ve <xref:System.Windows.Window.Deactivated> olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="3e474-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="3e474-199">Benzer şekilde, Kullanıcı şu anda devre dışı bırakılmış bir pencere seçtiğinde pencere yeniden etkin hale gelir <xref:System.Windows.Window.Activated> ve oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e474-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="3e474-200">İşlemenin <xref:System.Windows.Window.Activated> yaygın bir nedeni ve <xref:System.Windows.Window.Deactivated> yalnızca bir pencere etkin olduğunda çalışabilen işlevselliği etkinleştirmek ve devre dışı bırakmak.</span><span class="sxs-lookup"><span data-stu-id="3e474-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="3e474-201">Örneğin, bazı pencereler, Oyunlar ve video oynatıcılar dahil olmak üzere sabit Kullanıcı girişi veya ilgilenilmesi gereken etkileşimli içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3e474-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="3e474-202">Aşağıdaki örnek, bu davranışın nasıl işleneceğini <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> uygulanacağını gösteren basitleştirilmiş bir video oynatıcı örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="3e474-203">Bir pencere devre dışı bırakıldığında diğer uygulama türleri de arka planda kod çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="3e474-204">Örneğin, bir posta istemcisi, Kullanıcı başka uygulamalar kullanırken posta sunucusunu yoklamaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="3e474-205">Bunlar gibi uygulamalar, ana pencere devre dışı bırakıldığında farklı veya ek bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="3e474-206">Posta programına göre, bu durum hem gelen kutusuna yeni posta öğesini ekleyip hem de sistem tepsisine bir bildirim simgesi eklemeye anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="3e474-207">Bildirim simgesi yalnızca posta penceresi etkin olmadığında, <xref:System.Windows.Window.IsActive%2A> özelliği inceleyerek belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="3e474-208">Bir arka plan görevi tamamlanırsa, bir pencere, metodu çağırarak <xref:System.Windows.Window.Activate%2A> kullanıcıya daha akıllıca bildirimde bulunmasını isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="3e474-209">Kullanıcı çağrıldığında etkinleştirilen <xref:System.Windows.Window.Activate%2A> başka bir uygulamayla etkileşim kurmaktadır, pencerenin görev çubuğu düğmesi yanıp sönmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="3e474-210">Bir Kullanıcı geçerli uygulamayla etkileşim kursunsam, çağıran <xref:System.Windows.Window.Activate%2A> pencereyi ön plana getirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-211">Uygulama kapsamı etkinleştirmesini <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olaylarını kullanarak işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="3e474-212">Pencereyi kapatma</span><span class="sxs-lookup"><span data-stu-id="3e474-212">Closing a Window</span></span>  
 <span data-ttu-id="3e474-213">Bir pencerenin ömrü, bir kullanıcı tarafından kapandığında bir uca geliyor.</span><span class="sxs-lookup"><span data-stu-id="3e474-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="3e474-214">Bir pencere, aşağıdakiler de dahil olmak üzere istemci olmayan alandaki öğeler kullanılarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="3e474-215">**Sistem** menüsünün **Kapanış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="3e474-216">ALT + F4 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="3e474-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="3e474-217">**Kapat** düğmesine basma.</span><span class="sxs-lookup"><span data-stu-id="3e474-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="3e474-218">Bir pencereyi kapatmak için istemci alanına ek mekanizmalar sağlayabilirsiniz, daha yaygın olarak şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3e474-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="3e474-219">Genellikle ana uygulama pencereleri için **Dosya** menüsündeki **Çıkış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="3e474-220">**Dosya** menüsünde, genellikle ikincil bir uygulama penceresinde bir **Kapanış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="3e474-221">Genellikle kalıcı iletişim kutusunda bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="3e474-222">Genellikle kalıcı olmayan iletişim kutusunda **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3e474-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="3e474-223">Bu özel mekanizmalardan birine yanıt olarak bir pencereyi kapatmak için <xref:System.Windows.Window.Close%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="3e474-224">Aşağıdaki örnek, **Dosya** menüsünden **Çıkış** ' i seçerek bir pencereyi kapatma özelliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="3e474-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="3e474-225">Bir pencere kapandığında iki olay oluşturur: <xref:System.Windows.Window.Closing> ve. <xref:System.Windows.Window.Closed></span><span class="sxs-lookup"><span data-stu-id="3e474-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="3e474-226"><xref:System.Windows.Window.Closing>pencere kapandıktan sonra tetiklenir ve pencere kapanışının önlenbileceği bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="3e474-227">Pencere kapanışı önlemediği bir yaygın nedeni, pencere içeriğinin değiştirilen verileri içermi.</span><span class="sxs-lookup"><span data-stu-id="3e474-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="3e474-228">Bu durumda, verilerin kirli <xref:System.Windows.Window.Closing> olup olmadığını ve bu durumda kullanıcıdan, verileri kaydetmeden pencereyi kapatmaya devam edip etmediğini veya pencere kapanışını iptal etmeyi isteyip istemediğini sormak için olay işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="3e474-229">Aşağıdaki örnek, işlemenin <xref:System.Windows.Window.Closing>önemli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e474-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="3e474-230"><xref:System.Windows.Window.Closing> Olay işleyicisi, bir pencerenin kapatmasını engellemek <xref:System.ComponentModel.CancelEventArgs>için olarak `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ayarladığınız özelliğini uygulayan bir öğesine `true` geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="3e474-231"><xref:System.Windows.Window.Closing> İşlenmezse veya işlenirse ancak iptal edilmezse pencere kapanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="3e474-232">Pencerenin gerçekten kapanmadan hemen önce, <xref:System.Windows.Window.Closed> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="3e474-233">Bu noktada, bir pencerenin kapatılması engellenemez.</span><span class="sxs-lookup"><span data-stu-id="3e474-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-234">Uygulama, ana uygulama penceresi kapandığında (bkz <xref:System.Windows.Application.MainWindow%2A>.) ya da son pencere kapandığında otomatik olarak kapatılacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="3e474-235">Ayrıntılar için bkz. <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e474-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="3e474-236">Bir pencere, istemci olmayan ve istemci alanlarında belirtilen mekanizmalarla açıkça kapatılaken, aşağıdakiler de dahil olmak üzere uygulamanın veya pencerelerin diğer bölümlerinde davranış sonucu olarak bir pencere de dolaylı olarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="3e474-237">Kullanıcı oturumu kapatır veya Windows oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="3e474-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="3e474-238">Pencerenin sahibi kapanır (bkz <xref:System.Windows.Window.Owner%2A>.).</span><span class="sxs-lookup"><span data-stu-id="3e474-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="3e474-239">Ana uygulama penceresi kapalıdır ve ' <xref:System.Windows.Application.ShutdownMode%2A> dir. <xref:System.Windows.ShutdownMode.OnMainWindowClose></span><span class="sxs-lookup"><span data-stu-id="3e474-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="3e474-240"><xref:System.Windows.Application.Shutdown%2A>çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-241">Pencere kapatıldıktan sonra yeniden açılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e474-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="3e474-242">Pencere yaşam süresi olayları</span><span class="sxs-lookup"><span data-stu-id="3e474-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="3e474-243">Aşağıdaki çizimde, bir pencerenin kullanım ömrü içinde asıl olayların sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e474-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Bir pencerenin ömrü içindeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="3e474-245">Aşağıdaki çizimde, bir pencerenin kullanım ömrü olmadan gösterilen (<xref:System.Windows.Window.ShowActivated%2A> pencere gösterilmeden önce olarak `false` ayarlanır) bir pencerenin ömrü içindeki asıl olayların sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e474-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Etkin olmayan olayları etkinleştirme olmadan bir pencerede gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="3e474-247">Pencere konumu</span><span class="sxs-lookup"><span data-stu-id="3e474-247">Window Location</span></span>  
 <span data-ttu-id="3e474-248">Bir pencere açıkken, masaüstüne göre x ve y boyutlarında bir konum vardır.</span><span class="sxs-lookup"><span data-stu-id="3e474-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="3e474-249">Bu konum, sırasıyla <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özelliklerini inceleyerek belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="3e474-250">Bu özellikleri pencerenin konumunu değiştirmek için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="3e474-251">Aşağıdaki <xref:System.Windows.WindowStartupLocation> sabit listesi değerlerinden biriyle <xref:System.Windows.Window.WindowStartupLocation%2A> özelliği ayarlayarak ilk göründüğünde <xref:System.Windows.Window> bir başlangıç konumunu da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="3e474-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="3e474-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="3e474-253"><xref:System.Windows.WindowStartupLocation.Manual>Başlangıç konumu olarak belirtilmişse <xref:System.Windows.Window.Left%2A> ve ve <xref:System.Windows.Window.Top%2A> özellikleri ayarlanmamışsa <xref:System.Windows.Window> , Windows 'un bir konum görünmesini ister.</span><span class="sxs-lookup"><span data-stu-id="3e474-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="3e474-254">En üstteki pencere ve Z düzeni</span><span class="sxs-lookup"><span data-stu-id="3e474-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="3e474-255">X ve y konumuna sahip olmanın yanı sıra, bir pencere z boyutunda bir konuma da sahiptir ve bu da diğer pencereler açısından dikey konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="3e474-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="3e474-256">Bu, pencerenin z düzeni olarak bilinir ve iki tür vardır: normal z düzeni ve en üstteki z düzeni.</span><span class="sxs-lookup"><span data-stu-id="3e474-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="3e474-257">*Normal z düzeninde* pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="3e474-258">Varsayılan olarak, bir pencere normal z düzeninde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e474-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="3e474-259">*En üstteki z düzeninde* pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="3e474-260">Ayrıca, en üstteki z düzeninde bulunan pencereler her zaman normal z düzeninde Windows üzerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e474-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="3e474-261">Bir pencere, <xref:System.Windows.Window.Topmost%2A> özelliği olarak `true`ayarlanarak en üstteki z düzeninde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e474-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="3e474-262">Her z düzeninde, etkin olan pencere aynı z düzeninde diğer tüm pencerelerin üstünde görünür.</span><span class="sxs-lookup"><span data-stu-id="3e474-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="3e474-263">Pencere boyutu</span><span class="sxs-lookup"><span data-stu-id="3e474-263">Window Size</span></span>  
 <span data-ttu-id="3e474-264">Masaüstü konumuna sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve yükseklik özellikleri de dahil olmak üzere çeşitli özelliklerle belirlenen bir boyuta sahiptir <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e474-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="3e474-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> bir pencerenin ömrü boyunca sahip olduğu ve aşağıdaki örnekte gösterildiği gibi yapılandırıldığı genişlikler aralığını yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="3e474-266">Pencere yüksekliği, <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.MaxHeight%2A>tarafından yönetilir ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="3e474-267">Çeşitli genişlik değerleri ve yükseklik değerleri her biri bir Aralık belirttiği için, yeniden boyutlandırılabilir bir pencerenin genişlik ve yüksekliğinin ilgili boyut için belirtilen aralık dahilinde herhangi bir yerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3e474-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="3e474-268">Geçerli genişlik ve yüksekliğini algılamak için sırasıyla ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>' yi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3e474-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="3e474-269">Pencerenin genişlik ve yüksekliğinin pencere içeriğinin boyutuna uygun bir boyuta sahip olmasını istiyorsanız, aşağıdaki değerlere sahip olan <xref:System.Windows.Window.SizeToContent%2A> özelliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="3e474-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="3e474-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="3e474-271">Efekt yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="3e474-271">No effect (default).</span></span>  
  
- <span data-ttu-id="3e474-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="3e474-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="3e474-273">Hem hem de <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> içeriğin genişliğine göre aynı etkiye sahip olan içerik genişliğine uygun hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3e474-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="3e474-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="3e474-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="3e474-275">Hem hem de <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> içeriğin yüksekliğine göre aynı etkiye sahip olan içerik yüksekliğine Sığdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="3e474-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="3e474-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="3e474-277">Hem <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> hem de içeriğin yüksekliğine ayarlanmasına ve hem hem de <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> içeriğin genişliğine ayarlanmasına benzer etkiye sahip içerik genişliğine ve yüksekliğe uygun hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3e474-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="3e474-278">Aşağıdaki örnek, ilk başta gösterildiği gibi, hem dikey hem de yatay olarak içeriğini sığdırmak için otomatik olarak ölçeklenebilen bir pencere gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e474-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="3e474-279">Aşağıdaki örnek, bir pencerenin içeriği sığdırmak için <xref:System.Windows.Window.SizeToContent%2A> nasıl yeniden boyutlandırılacağını belirtmek üzere koddaki özelliğinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e474-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="3e474-280">Boyutlandırma özellikleri için öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="3e474-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="3e474-281">Temelde, bir pencerenin çeşitli boyutlar özellikleri, yeniden boyutlandırılabilir bir pencerenin genişlik ve yükseklik aralığını tanımlamak için birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="3e474-282">Geçerli bir aralığın korunduğundan emin olmak için, <xref:System.Windows.Window> aşağıdaki öncelik emirlerini kullanarak boyut özelliklerinin değerlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="3e474-283">**Yükseklik özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="3e474-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3e474-284">**Genişlik özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="3e474-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3e474-285">Öncelik sırası, <xref:System.Windows.Window.WindowState%2A> özelliği ile yönetilen, ekranı kaplayan bir pencerenin boyutunu da belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="3e474-286">Pencere durumu</span><span class="sxs-lookup"><span data-stu-id="3e474-286">Window State</span></span>  
 <span data-ttu-id="3e474-287">Yeniden boyutlandırılabilir bir pencerenin ömrü boyunca üç durum olabilir: normal, simge durumuna küçültülmüş ve ekranı kaplamış.</span><span class="sxs-lookup"><span data-stu-id="3e474-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="3e474-288">*Normal* duruma sahip bir pencere, pencerenin varsayılan durumudur.</span><span class="sxs-lookup"><span data-stu-id="3e474-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="3e474-289">Bu duruma sahip bir pencere, yeniden boyutlandırılması durumunda bir yeniden boyutlandırma tutamacı veya kenarlık kullanarak, kullanıcının onu taşımasını ve yeniden boyutlandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="3e474-290">*Simge durumuna küçültülmüş* bir pencere, olarak <xref:System.Windows.Window.ShowInTaskbar%2A> `true`ayarlandıysa görev çubuğu düğmesine daraltılır; Aksi takdirde, mümkün olan en küçük boyutu daraltır ve masaüstünün sol alt köşesine doğru bir şekilde yeniden konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="3e474-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="3e474-291">Simge durumuna küçültülmüş pencere türü, bir kenarlık veya yeniden boyutlandırma tutamacı kullanılarak yeniden boyutlandırılabilir, ancak görev çubuğunda görünmeyen simge durumuna küçültülmüş bir pencere masaüstü etrafında sürüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="3e474-292">*Ekranı kaplayan* bir pencere <xref:System.Windows.FrameworkElement.MaxWidth%2A>, en büyük boyuta genişletilir, bu da yalnızca,, <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve <xref:System.Windows.Window.SizeToContent%2A> özellikleri dikte eder.</span><span class="sxs-lookup"><span data-stu-id="3e474-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="3e474-293">Simge durumuna küçültülmüş bir pencere gibi, ekranı kaplayan bir pencere yeniden boyutlandırma tutamacı kullanılarak veya kenarlıkları sürükleyerek yeniden boyutlandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e474-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e474-294">Pencerenin <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A>,, ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerleri, pencere şu anda büyütülmüş veya küçültülmüş olsa bile normal durum için her zaman değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3e474-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="3e474-295">Bir pencerenin durumu, <xref:System.Windows.Window.WindowState%2A> özelliği ayarlanarak yapılandırılabilir ve bu, aşağıdaki <xref:System.Windows.WindowState> sabit listesi değerlerinden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="3e474-296"><xref:System.Windows.WindowState.Normal>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="3e474-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="3e474-297">Aşağıdaki örnek, açıldığında ekranı kaplamış olarak gösterilen bir pencerenin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e474-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="3e474-298">Genel olarak, bir pencerenin başlangıç <xref:System.Windows.Window.WindowState%2A> durumunu yapılandırmak için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="3e474-299">Yeniden boyutlandırılabilir bir pencere gösterildiğinde, kullanıcılar pencere durumunu değiştirmek için pencerenin başlık çubuğundaki simge durumuna küçült, Ekranı Kapla ve geri yükle düğmelerine basabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="3e474-300">Pencere görünümü</span><span class="sxs-lookup"><span data-stu-id="3e474-300">Window Appearance</span></span>  
 <span data-ttu-id="3e474-301">Pencerenin istemci alanının görünümünü, düğme, Etiketler ve metin kutuları gibi pencereye özgü içerik ekleyerek değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="3e474-302">İstemci dışı alanı yapılandırmak için, <xref:System.Windows.Window> bir pencerenin simgesini ayarlamak ve <xref:System.Windows.Window.Icon%2A> <xref:System.Windows.Window.Title%2A> başlığını ayarlamak için dahil olmak üzere çeşitli özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="3e474-303">Ayrıca, bir pencerenin yeniden boyutlandırma modu, pencere stili ve masaüstü görev çubuğunda düğme olarak görünüp görüntülenmediğini yapılandırarak, istemci olmayan alan kenarlığının görünümünü ve davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="3e474-304">Yeniden boyutlandırma modu</span><span class="sxs-lookup"><span data-stu-id="3e474-304">Resize Mode</span></span>  
 <span data-ttu-id="3e474-305"><xref:System.Windows.Window.WindowStyle%2A> Özelliğine bağlı olarak, kullanıcıların pencereyi yeniden boyutlandırıp nasıl (ve ne olduğunu) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="3e474-306">Pencere stili seçimi, bir kullanıcının kenarlığını fareyle sürükleyerek, **simge durumuna küçültme**, **Ekranı Kapla**ve **yeniden boyutlandır** düğmelerinin istemci olmayan alanda görünüp görünmediğini ve etkin olup olmadıkları gösterilmediğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="3e474-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="3e474-307">Aşağıdaki <xref:System.Windows.Window.ResizeMode%2A> <xref:System.Windows.ResizeMode> sabit listesi değerlerinden biri olabilecek özelliğini ayarlayarak pencerenin nasıl yeniden boyutlandırılacağını yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="3e474-308"><xref:System.Windows.ResizeMode.CanResize>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="3e474-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="3e474-309"><xref:System.Windows.Window.WindowStyle%2A>' De olduğu gibi, bir pencerenin yeniden boyutlandırma modunun ömrü boyunca değişmeme olasılığı düşüktür, bu da büyük olasılıkla bu değeri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmeden ayarlamanız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3e474-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="3e474-310"><xref:System.Windows.Window.WindowState%2A> Özelliği inceleyerek pencerenin ekranı kaplayacağını, simge durumuna küçültülmüş veya geri yüklendiğini tespit edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="3e474-311">Pencere stili</span><span class="sxs-lookup"><span data-stu-id="3e474-311">Window Style</span></span>  
 <span data-ttu-id="3e474-312">Pencerenin istemci olmayan alanından gösterilen kenarlık çoğu uygulama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="3e474-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="3e474-313">Bununla birlikte, farklı tür kenarlıkların gerekli olduğu veya pencere türüne bağlı olarak hiçbir kenarlığı gerekmeyen durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="3e474-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="3e474-314">Pencerenin ne tür kenarlığı kontrol etmek için, <xref:System.Windows.Window.WindowStyle%2A> özelliğini, <xref:System.Windows.WindowStyle> numaralandırmanın aşağıdaki değerlerinden biriyle ayarlarsınız:</span><span class="sxs-lookup"><span data-stu-id="3e474-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="3e474-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="3e474-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="3e474-316">Bu pencere stillerinin etkisi aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3e474-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Pencere kenarlık stillerinin çizimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="3e474-318">Biçimlendirme ya da <xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod kullanarak ayarlayabilirsiniz; bir pencerenin ömrü boyunca değiştirilmesi muhtemel olmadığından, büyük olasılıkla bunu biçimlendirme kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="3e474-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="3e474-319">Dikdörtgen olmayan pencere stili</span><span class="sxs-lookup"><span data-stu-id="3e474-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="3e474-320">Ayrıca, <xref:System.Windows.Window.WindowStyle%2A> izin veren kenarlık stillerinin yeterli olmadığı durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="3e474-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="3e474-321">Örneğin, Microsoft Windows Media Player 'nin kullandığı gibi dikdörtgen olmayan bir kenarlığa sahip bir uygulama oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="3e474-322">Örneğin, aşağıdaki şekilde gösterilen konuşma balonu penceresini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e474-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Beni sürükle olarak belirten bir konuşma balonu penceresi.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="3e474-324">Bu tür bir pencere <xref:System.Windows.Window.WindowStyle%2A> <xref:System.Windows.WindowStyle.None>, özelliği olarak ayarlanarak ve saydamlık için olan özel destek <xref:System.Windows.Window> kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="3e474-325">Bu değer birleşimi, pencereye tamamen saydam bir şekilde işlemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="3e474-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="3e474-326">Bu durumda, pencerenin istemci olmayan alanı donnlar (kapatma menüsü, simge durumuna küçült, Ekranı Kapla ve geri yükleme düğmeleri vb.) kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e474-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="3e474-327">Sonuç olarak, kendinizinkini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="3e474-328">Görev çubuğu varlığı</span><span class="sxs-lookup"><span data-stu-id="3e474-328">Task Bar Presence</span></span>  

<span data-ttu-id="3e474-329">Pencerenin varsayılan görünümü, aşağıdaki şekilde gösterildiği gibi bir görev çubuğu düğmesi içerir:</span><span class="sxs-lookup"><span data-stu-id="3e474-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Görev çubuğu düğmesi olan bir pencere gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="3e474-331">Bazı Windows türlerinde ileti kutuları ve iletişim kutuları gibi bir görev çubuğu düğmesi yoktur (bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="3e474-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="3e474-332">Bir pencere için görev çubuğu düğmesinin, <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği ayarlayarak (`true` varsayılan olarak) gösterilip gösterilmeyeceğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="3e474-333">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="3e474-333">Security Considerations</span></span>  
 <span data-ttu-id="3e474-334"><xref:System.Windows.Window>örneği `UnmanagedCode` oluşturulacak güvenlik izninin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="3e474-335">Üzerinde yüklü olan ve yerel makineden başlatılan uygulamalar için, bu, uygulamaya verilen izinler kümesi içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="3e474-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="3e474-336">Bununla birlikte, bu, ClickOnce kullanılarak Internet 'ten veya yerel intranet bölgesinden başlatılan uygulamalara verilen izin kümesinin dışındadır.</span><span class="sxs-lookup"><span data-stu-id="3e474-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="3e474-337">Sonuç olarak, kullanıcılar bir ClickOnce güvenlik uyarısı alır ve uygulamanın izin kümesini tam güvenle yükseltmek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="3e474-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="3e474-338">Ayrıca, XBAP varsayılan olarak Windows veya iletişim kutularını gösteremez.</span><span class="sxs-lookup"><span data-stu-id="3e474-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="3e474-339">Tek başına uygulama güvenliği konuları hakkında bir tartışma için bkz. [WPF Güvenlik Stratejisi-Platform güvenliği](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="3e474-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="3e474-340">Diğer Windows türleri</span><span class="sxs-lookup"><span data-stu-id="3e474-340">Other Types of Windows</span></span>  
 <span data-ttu-id="3e474-341"><xref:System.Windows.Navigation.NavigationWindow>, gezinebilir içeriği barındırmak için tasarlanan bir penceredir.</span><span class="sxs-lookup"><span data-stu-id="3e474-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="3e474-342">Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="3e474-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="3e474-343">İletişim kutuları, genellikle bir işlevi bir kullanıcıdan tamamlamaya yönelik bilgi toplamak için kullanılan bir Windows.</span><span class="sxs-lookup"><span data-stu-id="3e474-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="3e474-344">Örneğin, bir Kullanıcı bir dosyayı açmak istediğinde dosya **Aç** iletişim kutusu genellikle bir uygulama tarafından dosya adını kullanıcıdan almak için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="3e474-345">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e474-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e474-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e474-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="3e474-347">İletişim Kutularına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e474-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="3e474-348">WPF Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="3e474-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
