---
title: Windows genel bakış
description: Windows Presentation Foundation (WPF) ' de tek başına uygulamalar için Windows oluşturma ve yönetme temellerini öğrenin.
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
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622893"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="6f04e-103">WPF Windows'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f04e-103">WPF Windows Overview</span></span>
<span data-ttu-id="6f04e-104">Kullanıcılar Windows aracılığıyla Windows Presentation Foundation (WPF) tek başına uygulamalarıyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="6f04e-104">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="6f04e-105">Bir pencerenin birincil amacı, verileri görselleştirerek kullanıcıların verilerle etkileşime geçmesini sağlayan içeriği barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-105">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="6f04e-106">Tek başına WPF uygulamaları, sınıfını kullanarak kendi pencerelerini sağlar <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-106">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="6f04e-107">Bu konu <xref:System.Windows.Window> , Windows 'un tek başına uygulamalarda oluşturulması ve yönetilmesi ile ilgili temel bilgileri kapsamadan önce tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-107">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-108">XAML tarayıcı uygulamaları (XBAP 'ler) ve gevşek sayfalar dahil olmak üzere tarayıcıda barındırılan WPF uygulamaları [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kendi pencerelerini sağlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-108">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="6f04e-109">Bunun yerine, Windows Internet Explorer tarafından sunulan Windows 'da barındırılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-109">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="6f04e-110">Bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6f04e-110">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="6f04e-111">Pencere sınıfı</span><span class="sxs-lookup"><span data-stu-id="6f04e-111">The Window Class</span></span>  
 <span data-ttu-id="6f04e-112">Aşağıdaki şekilde pencerenin yapısal kısımları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-112">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Pencere öğelerini gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="6f04e-114">Bir pencere iki alana ayrılmıştır: istemci olmayan alan ve istemci alanı.</span><span class="sxs-lookup"><span data-stu-id="6f04e-114">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="6f04e-115">Bir pencerenin *istemci olmayan alanı* WPF tarafından uygulanır ve aşağıdakiler dahil olmak üzere çoğu Windows için ortak olan bir pencerenin parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-115">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="6f04e-116">Bir kenarlık.</span><span class="sxs-lookup"><span data-stu-id="6f04e-116">A border.</span></span>  
  
- <span data-ttu-id="6f04e-117">Başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="6f04e-117">A title bar.</span></span>  
  
- <span data-ttu-id="6f04e-118">Bir simge.</span><span class="sxs-lookup"><span data-stu-id="6f04e-118">An icon.</span></span>  
  
- <span data-ttu-id="6f04e-119">Küçült, Ekranı Kapla ve geri yükle düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="6f04e-119">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="6f04e-120">Kapat düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-120">A Close button.</span></span>  
  
- <span data-ttu-id="6f04e-121">Kullanıcıların bir pencereyi en aza indirmenize, ekranı kaplamaya, geri yüklemelerine, taşımasına, yeniden boyutlandırmaya ve kapatılmasına izin veren menü öğeleriyle bir sistem menüsü.</span><span class="sxs-lookup"><span data-stu-id="6f04e-121">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="6f04e-122">Pencerenin *istemci alanı* , bir pencerenin istemci olmayan alanındaki alanıdır ve geliştiriciler tarafından menü çubukları, araç çubukları ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-122">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="6f04e-123">WPF 'de, bir pencere, <xref:System.Windows.Window> aşağıdakileri yapmak için kullandığınız sınıfa göre kapsüllenir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-123">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="6f04e-124">Bir pencere görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="6f04e-124">Display a window.</span></span>  
  
- <span data-ttu-id="6f04e-125">Pencerenin boyutunu, konumunu ve görünümünü yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="6f04e-125">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="6f04e-126">Uygulamaya özgü içeriği barındırın.</span><span class="sxs-lookup"><span data-stu-id="6f04e-126">Host application-specific content.</span></span>  
  
- <span data-ttu-id="6f04e-127">Pencerenin ömrünü yönetin.</span><span class="sxs-lookup"><span data-stu-id="6f04e-127">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="6f04e-128">Pencere uygulama</span><span class="sxs-lookup"><span data-stu-id="6f04e-128">Implementing a Window</span></span>  
 <span data-ttu-id="6f04e-129">Tipik bir pencerenin uygulanması, görünümün ve davranışın yanı sıra, *görünümün* kullanıcılar tarafından kullanıcılara nasıl göründüğünü ve *davranışın* Kullanıcı tarafından etkileşim kurma şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-129">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="6f04e-130">WPF 'de, kod veya biçimlendirme kullanarak bir pencerenin görünümünü ve davranışını uygulayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f04e-130">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="6f04e-131">Ancak, genel olarak, bir pencerenin görünümü biçimlendirme kullanılarak uygulanır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve davranışı aşağıdaki örnekte gösterildiği gibi arka plan kodu kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-131">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="6f04e-132">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme dosyası ve arka plan kod dosyasının birlikte çalışmasını sağlamak için aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-132">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="6f04e-133">Biçimlendirme ' de, `Window` öğesi `x:Class` özniteliğini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-133">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="6f04e-134">Uygulama yapılandırıldığında, `x:Class` biçimlendirme dosyasında bulunması Microsoft Build Engine (MSBuild) ' `partial` den türetilen <xref:System.Windows.Window> ve özniteliği tarafından belirtilen adı içeren bir sınıf oluşturmasına neden olur `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-134">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="6f04e-135">Bu, şema () için bir XML ad alanı bildiriminin eklenmesini gerektirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-135">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="6f04e-136">Oluşturulan `partial` sınıf, `InitializeComponent` olayları kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağrılan yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="6f04e-136">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="6f04e-137">Arka plan kod içinde, sınıf, `partial` biçimlendirme içindeki özniteliği tarafından belirtilen aynı ada sahip bir sınıf olmalıdır `x:Class` ve ' den türetmelidir <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-137">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6f04e-138">Bu, arka plan kod dosyasının, `partial` uygulama oluşturulduğunda biçimlendirme dosyası için oluşturulan sınıfla ilişkilendirilmesini sağlar (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="6f04e-138">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="6f04e-139">Arka plan kod içinde, <xref:System.Windows.Window> sınıfının yöntemini çağıran bir Oluşturucu uygulaması gerekir `InitializeComponent` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-139">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="6f04e-140">`InitializeComponent`, biçimlendirme dosyasının oluşturulan `partial` sınıfı tarafından olayları kaydetmek ve biçimlendirmede tanımlanan özellikleri ayarlamak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-140">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-141"><xref:System.Windows.Window>Projenize Visual Studio kullanarak yeni bir eklediğinizde, <xref:System.Windows.Window> hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır ve burada açıklanan biçimlendirme ve arka plan kod dosyaları arasındaki ilişkiyi oluşturmak için gereken yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-141">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="6f04e-142">Bu yapılandırmayla birlikte, biçimlendirme ' de pencerenin görünümünü tanımlamaya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve davranışını arka plan kodu ' nda uygulamaya odaklanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f04e-142">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="6f04e-143">Aşağıdaki örnek, bir düğme içeren bir pencereyi, biçimlendirme ' de uygulanan bir pencere [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve düğmenin olayı için bir olay işleyicisi gösterir ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> arka plan kod içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-143">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="6f04e-144">MSBuild için pencere tanımı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f04e-144">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="6f04e-145">Pencerenizi nasıl uyguladığınız, MSBuild için nasıl yapılandırıldığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6f04e-145">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="6f04e-146">Hem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme hem de arka plan kodu kullanılarak tanımlanan bir pencere için:</span><span class="sxs-lookup"><span data-stu-id="6f04e-146">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="6f04e-147">XAML biçimlendirme dosyaları MSBuild öğeleri olarak yapılandırılır `Page` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-147">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="6f04e-148">Arka plan kod dosyaları MSBuild öğeleri olarak yapılandırılır `Compile` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-148">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="6f04e-149">Bu, aşağıdaki MSBuild proje dosyasında gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-149">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="6f04e-150">WPF uygulamaları oluşturma hakkında daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6f04e-150">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="6f04e-151">Pencere ömrü</span><span class="sxs-lookup"><span data-stu-id="6f04e-151">Window Lifetime</span></span>  
 <span data-ttu-id="6f04e-152">Herhangi bir sınıfta olduğu gibi, bir pencere ilk kez başlatıldığında başlayan, açıldıktan sonra, etkin ve devre dışı bırakılmış ve sonunda kapatılan bir yaşam süresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-152">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="6f04e-153">Pencere açma</span><span class="sxs-lookup"><span data-stu-id="6f04e-153">Opening a Window</span></span>  
 <span data-ttu-id="6f04e-154">Bir pencereyi açmak için ilk olarak bir örneği oluşturursunuz, bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-154">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="6f04e-155">Bu örnekte, `MarkupAndCodeBehindWindow` uygulama başladığında oluşur ve <xref:System.Windows.Application.Startup> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-155">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="6f04e-156">Bir pencere oluşturulduğunda, nesne tarafından yönetilen bir Windows listesine otomatik olarak bir başvuru eklenir <xref:System.Windows.Application> (bkz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> .).</span><span class="sxs-lookup"><span data-stu-id="6f04e-156">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="6f04e-157">Ayrıca, örneği oluşturulacak ilk pencere, varsayılan olarak, <xref:System.Windows.Application> ana uygulama penceresi (bkz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> .) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-157">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="6f04e-158">Pencere son olarak yöntemi çağırarak açılır <xref:System.Windows.Window.Show%2A> ; sonuç aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-158">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Window. Show çağırarak bir pencere açıldı](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="6f04e-160">Çağırarak açılan bir pencere, uygulamanın, <xref:System.Windows.Window.Show%2A> kullanıcıların aynı uygulamadaki diğer pencereleri etkinleştirmesine izin veren bir modda çalıştığı, geçici bir pencere olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-160">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-161"><xref:System.Windows.Window.ShowDialog%2A>, iletişim kutuları gibi pencere açmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-161"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="6f04e-162">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="6f04e-162">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="6f04e-163"><xref:System.Windows.Window.Show%2A>Çağrıldığında, bir pencere, Kullanıcı girişi almasına izin veren altyapıyı kurmak üzere gösterilmeden önce başlatma işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-163">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="6f04e-164">Pencere başlatıldığında <xref:System.Windows.Window.SourceInitialized> olay tetiklenir ve pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-164">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="6f04e-165">Bir kısayol olarak, <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılan ilk pencereyi belirtmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-165">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="6f04e-166">Uygulama başlatıldığında, değeri tarafından belirtilen pencere <xref:System.Windows.Application.StartupUri%2A> modelessly olarak açılır; dahili olarak pencere yöntemi çağırarak açılır <xref:System.Windows.Window.Show%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-166">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="6f04e-167">Pencere sahipliği</span><span class="sxs-lookup"><span data-stu-id="6f04e-167">Window Ownership</span></span>  
 <span data-ttu-id="6f04e-168">Yöntemi kullanılarak açılan bir pencere, <xref:System.Windows.Window.Show%2A> kendisini oluşturan pencereyle örtük bir ilişkiye sahip değildir; kullanıcılar, herhangi bir pencereyle bağımsız olarak etkileşime girebilir, yani her iki pencere de şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-168">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="6f04e-169">Diğerini (pencerelerin bir <xref:System.Windows.Window.Topmost%2A> özelliği olarak ayarlanmış değilse `true` ) kapsar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-169">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="6f04e-170">Diğerini etkilemeden simge durumuna küçültülmüş, ekranı kaplamış ve geri yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-170">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="6f04e-171">Bazı pencereler, açan pencereyle bir ilişki gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-171">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="6f04e-172">Örneğin, tümleşik bir geliştirme ortamı (IDE) uygulaması, normal davranışı kendilerini oluşturan pencereyi kapsayan özellik pencerelerini ve araç pencerelerini açabilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-172">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="6f04e-173">Ayrıca, bu gibi pencerelerin her zaman, bunları oluşturan pencereyle birlikte her zaman kapatmaları, en üst düzeye çıkarması ve geri yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-173">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="6f04e-174">Bu *tür bir ilişki, bir pencere diğeri* tarafından oluşturulabilir ve sahip pencerenin <xref:System.Windows.Window.Owner%2A> özelliği *sahip penceresine*bir başvuru olarak ayarlanarak elde edilebilir *owned window* .</span><span class="sxs-lookup"><span data-stu-id="6f04e-174">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="6f04e-175">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-175">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="6f04e-176">Sahiplik kurulduktan sonra:</span><span class="sxs-lookup"><span data-stu-id="6f04e-176">After ownership is established:</span></span>  
  
- <span data-ttu-id="6f04e-177">Sahibi olan pencere, özelliğinin değerini inceleyerek sahip penceresine başvurabilir <xref:System.Windows.Window.Owner%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-177">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="6f04e-178">Sahip penceresi, özelliğinin değerini inceleyerek sahip olduğu tüm pencereleri bulabilir <xref:System.Windows.Window.OwnedWindows%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-178">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="6f04e-179">Windows etkinleştirmesini önler</span><span class="sxs-lookup"><span data-stu-id="6f04e-179">Preventing Window Activation</span></span>  
 <span data-ttu-id="6f04e-180">Internet Messenger stili uygulamanın konuşma pencereleri veya bir e-posta uygulamasının bildirim pencereleri gibi, gösterildiğinde Windows 'un etkinleştirilmemesi gereken senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-180">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="6f04e-181">Uygulamanızda, gösterildiğinde etkinleştirilmemelidir bir pencere varsa, <xref:System.Windows.Window.ShowActivated%2A> `false` yöntemi ilk kez çağrılmadan önce özelliğini olarak ayarlayabilirsiniz <xref:System.Windows.Window.Show%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-181">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="6f04e-182">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="6f04e-182">As a consequence:</span></span>  
  
- <span data-ttu-id="6f04e-183">Pencere etkin değil.</span><span class="sxs-lookup"><span data-stu-id="6f04e-183">The window is not activated.</span></span>  
  
- <span data-ttu-id="6f04e-184">Pencerenin <xref:System.Windows.Window.Activated> olayı çıkarılmadı.</span><span class="sxs-lookup"><span data-stu-id="6f04e-184">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="6f04e-185">Etkin durumda olan pencere etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-185">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="6f04e-186">Ancak, Kullanıcı istemciyi veya istemci dışı alanı tıklatarak etkinleştirdiğinde, pencere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-186">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="6f04e-187">Bu durumda:</span><span class="sxs-lookup"><span data-stu-id="6f04e-187">In this case:</span></span>  
  
- <span data-ttu-id="6f04e-188">Pencere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-188">The window is activated.</span></span>  
  
- <span data-ttu-id="6f04e-189">Pencerenin <xref:System.Windows.Window.Activated> olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-189">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="6f04e-190">Önceden etkinleştirilen pencere devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6f04e-190">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="6f04e-191">Pencere <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayları daha sonra kullanıcı eylemlerine yanıt olarak beklendiği gibi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-191">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="6f04e-192">Pencere etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6f04e-192">Window Activation</span></span>  
 <span data-ttu-id="6f04e-193">Bir pencere ilk açıldığında etkin pencere olur (olarak ayarlanmış olarak gösterilmediği takdirde <xref:System.Windows.Window.ShowActivated%2A> `false` ).</span><span class="sxs-lookup"><span data-stu-id="6f04e-193">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="6f04e-194">*Etkin pencere* , anahtar vuruşları ve fare tıklamaları gibi şu anda Kullanıcı girişi yakalama penceresidir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-194">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="6f04e-195">Bir pencere etkin olduğunda <xref:System.Windows.Window.Activated> olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-195">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-196">Bir pencere ilk açıldığında, <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.Window.ContentRendered> olayları yalnızca olay oluşturulduktan sonra tetiklenir <xref:System.Windows.Window.Activated> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-196">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="6f04e-197">Bu şekilde aklınızda, bir pencere başlatıldığında açık olarak kabul edilebilir <xref:System.Windows.Window.ContentRendered> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-197">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="6f04e-198">Bir pencere etkin olduktan sonra, Kullanıcı aynı uygulamadaki başka bir pencereyi etkinleştirebilir veya başka bir uygulamayı etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-198">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="6f04e-199">Bu durumda, etkin olan pencere devre dışı bırakılır ve <xref:System.Windows.Window.Deactivated> olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-199">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="6f04e-200">Benzer şekilde, Kullanıcı şu anda devre dışı bırakılmış bir pencere seçtiğinde pencere yeniden etkin hale gelir ve <xref:System.Windows.Window.Activated> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-200">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="6f04e-201">İşlemenin yaygın bir nedeni <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> yalnızca bir pencere etkin olduğunda çalışabilen işlevselliği etkinleştirmek ve devre dışı bırakmak.</span><span class="sxs-lookup"><span data-stu-id="6f04e-201">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="6f04e-202">Örneğin, bazı pencereler, Oyunlar ve video oynatıcılar dahil olmak üzere sabit Kullanıcı girişi veya ilgilenilmesi gereken etkileşimli içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6f04e-202">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="6f04e-203">Aşağıdaki örnek, bu davranışın nasıl işleneceğini ve uygulanacağını gösteren basitleştirilmiş bir video oynatıcı örneğidir <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-203">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="6f04e-204">Bir pencere devre dışı bırakıldığında diğer uygulama türleri de arka planda kod çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-204">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="6f04e-205">Örneğin, bir posta istemcisi, Kullanıcı başka uygulamalar kullanırken posta sunucusunu yoklamaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-205">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="6f04e-206">Bunlar gibi uygulamalar, ana pencere devre dışı bırakıldığında farklı veya ek bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-206">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="6f04e-207">Posta programına göre, bu durum hem gelen kutusuna yeni posta öğesini ekleyip hem de sistem tepsisine bir bildirim simgesi eklemeye anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-207">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="6f04e-208">Bildirim simgesi yalnızca posta penceresi etkin olmadığında, özelliği inceleyerek belirlenebilir <xref:System.Windows.Window.IsActive%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-208">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="6f04e-209">Bir arka plan görevi tamamlanırsa, bir pencere, metodu çağırarak kullanıcıya daha akıllıca bildirimde bulunmasını isteyebilir <xref:System.Windows.Window.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-209">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="6f04e-210">Kullanıcı çağrıldığında etkinleştirilen başka bir uygulamayla etkileşim kurmaktadır <xref:System.Windows.Window.Activate%2A> , pencerenin görev çubuğu düğmesi yanıp sönmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-210">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="6f04e-211">Bir Kullanıcı geçerli uygulamayla etkileşim <xref:System.Windows.Window.Activate%2A> kursunsam, çağıran pencereyi ön plana getirir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-211">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-212">Uygulama kapsamı etkinleştirmesini <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve olaylarını kullanarak işleyebilirsiniz <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-212">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="6f04e-213">Pencereyi kapatma</span><span class="sxs-lookup"><span data-stu-id="6f04e-213">Closing a Window</span></span>  
 <span data-ttu-id="6f04e-214">Bir pencerenin ömrü, bir kullanıcı tarafından kapandığında bir uca geliyor.</span><span class="sxs-lookup"><span data-stu-id="6f04e-214">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="6f04e-215">Bir pencere, aşağıdakiler de dahil olmak üzere istemci olmayan alandaki öğeler kullanılarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-215">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="6f04e-216">**Sistem** menüsünün **Kapanış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-216">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="6f04e-217">ALT + F4 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="6f04e-217">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="6f04e-218">**Kapat** düğmesine basma.</span><span class="sxs-lookup"><span data-stu-id="6f04e-218">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="6f04e-219">Bir pencereyi kapatmak için istemci alanına ek mekanizmalar sağlayabilirsiniz, daha yaygın olarak şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-219">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="6f04e-220">Genellikle ana uygulama pencereleri için **Dosya** menüsündeki **Çıkış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-220">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="6f04e-221">**Dosya** menüsünde, genellikle ikincil bir uygulama penceresinde bir **Kapanış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-221">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="6f04e-222">Genellikle kalıcı iletişim kutusunda bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-222">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="6f04e-223">Genellikle kalıcı olmayan iletişim kutusunda **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-223">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="6f04e-224">Bu özel mekanizmalardan birine yanıt olarak bir pencereyi kapatmak için yöntemini çağırmanız gerekir <xref:System.Windows.Window.Close%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-224">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="6f04e-225">Aşağıdaki örnek, **Dosya** menüsünden **Çıkış** ' i seçerek bir pencereyi kapatma özelliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="6f04e-225">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="6f04e-226">Bir pencere kapandığında iki olay oluşturur: <xref:System.Windows.Window.Closing> ve <xref:System.Windows.Window.Closed> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-226">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="6f04e-227"><xref:System.Windows.Window.Closing>pencere kapandıktan sonra tetiklenir ve pencere kapanışının önlenbileceği bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-227"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="6f04e-228">Pencere kapanışı önlemediği bir yaygın nedeni, pencere içeriğinin değiştirilen verileri içermi.</span><span class="sxs-lookup"><span data-stu-id="6f04e-228">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="6f04e-229">Bu durumda, <xref:System.Windows.Window.Closing> verilerin kirli olup olmadığını ve bu durumda kullanıcıdan, verileri kaydetmeden pencereyi kapatmaya devam edip etmediğini veya pencere kapanışını iptal etmeyi isteyip istemediğini sormak için olay işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-229">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="6f04e-230">Aşağıdaki örnek, işlemenin önemli yönlerini gösterir <xref:System.Windows.Window.Closing> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-230">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="6f04e-231"><xref:System.Windows.Window.Closing>Olay işleyicisi <xref:System.ComponentModel.CancelEventArgs> , bir `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` pencerenin kapatmasını engellemek için olarak ayarladığınız özelliğini uygulayan bir öğesine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-231">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="6f04e-232"><xref:System.Windows.Window.Closing>İşlenmezse veya işlenirse ancak iptal edilmezse pencere kapanır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-232">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="6f04e-233">Pencerenin gerçekten kapanmadan hemen önce, <xref:System.Windows.Window.Closed> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-233">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="6f04e-234">Bu noktada, bir pencerenin kapatılması engellenemez.</span><span class="sxs-lookup"><span data-stu-id="6f04e-234">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-235">Uygulama, ana uygulama penceresi kapandığında (bkz <xref:System.Windows.Application.MainWindow%2A> .) ya da son pencere kapandığında otomatik olarak kapatılacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-235">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="6f04e-236">Ayrıntılar için bkz. <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f04e-236">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="6f04e-237">Bir pencere, istemci olmayan ve istemci alanlarında belirtilen mekanizmalarla açıkça kapatılaken, aşağıdakiler de dahil olmak üzere uygulamanın veya pencerelerin diğer bölümlerinde davranış sonucu olarak bir pencere de dolaylı olarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-237">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="6f04e-238">Kullanıcı oturumu kapatır veya Windows oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-238">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="6f04e-239">Pencerenin sahibi kapanır (bkz <xref:System.Windows.Window.Owner%2A> .).</span><span class="sxs-lookup"><span data-stu-id="6f04e-239">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="6f04e-240">Ana uygulama penceresi kapalıdır ve ' <xref:System.Windows.Application.ShutdownMode%2A> dir <xref:System.Windows.ShutdownMode.OnMainWindowClose> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-240">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="6f04e-241"><xref:System.Windows.Application.Shutdown%2A>çağırılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-241"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-242">Pencere kapatıldıktan sonra yeniden açılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-242">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="6f04e-243">Pencere yaşam süresi olayları</span><span class="sxs-lookup"><span data-stu-id="6f04e-243">Window Lifetime Events</span></span>  
 <span data-ttu-id="6f04e-244">Aşağıdaki çizimde, bir pencerenin kullanım ömrü içinde asıl olayların sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-244">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Bir pencerenin ömrü içindeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="6f04e-246">Aşağıdaki çizimde, bir pencerenin kullanım ömrü olmadan gösterilen ( <xref:System.Windows.Window.ShowActivated%2A> pencere gösterilmeden önce olarak ayarlanır) bir pencerenin ömrü içindeki asıl olayların sırası gösterilmektedir `false` :</span><span class="sxs-lookup"><span data-stu-id="6f04e-246">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Etkin olmayan olayları etkinleştirme olmadan bir pencerede gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="6f04e-248">Pencere konumu</span><span class="sxs-lookup"><span data-stu-id="6f04e-248">Window Location</span></span>  
 <span data-ttu-id="6f04e-249">Bir pencere açıkken, masaüstüne göre x ve y boyutlarında bir konum vardır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-249">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="6f04e-250">Bu konum, <xref:System.Windows.Window.Left%2A> sırasıyla ve özelliklerini inceleyerek belirlenebilir <xref:System.Windows.Window.Top%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-250">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="6f04e-251">Bu özellikleri pencerenin konumunu değiştirmek için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-251">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="6f04e-252"><xref:System.Windows.Window> <xref:System.Windows.Window.WindowStartupLocation%2A> Aşağıdaki sabit listesi değerlerinden biriyle özelliği ayarlayarak ilk göründüğünde bir başlangıç konumunu da belirtebilirsiniz <xref:System.Windows.WindowStartupLocation> :</span><span class="sxs-lookup"><span data-stu-id="6f04e-252">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="6f04e-253"><xref:System.Windows.WindowStartupLocation.CenterOwner>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="6f04e-253"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="6f04e-254">Başlangıç konumu olarak belirtilmişse <xref:System.Windows.WindowStartupLocation.Manual> ve <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikleri ayarlanmamışsa, <xref:System.Windows.Window> Windows 'un bir konum görünmesini ister.</span><span class="sxs-lookup"><span data-stu-id="6f04e-254">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="6f04e-255">En üstteki pencere ve Z düzeni</span><span class="sxs-lookup"><span data-stu-id="6f04e-255">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="6f04e-256">X ve y konumuna sahip olmanın yanı sıra, bir pencere z boyutunda bir konuma da sahiptir ve bu da diğer pencereler açısından dikey konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="6f04e-256">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="6f04e-257">Bu, pencerenin z düzeni olarak bilinir ve iki tür vardır: normal z düzeni ve en üstteki z düzeni.</span><span class="sxs-lookup"><span data-stu-id="6f04e-257">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="6f04e-258">*Normal z düzeninde* pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-258">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="6f04e-259">Varsayılan olarak, bir pencere normal z düzeninde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-259">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="6f04e-260">*En üstteki z düzeninde* pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-260">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="6f04e-261">Ayrıca, en üstteki z düzeninde bulunan pencereler her zaman normal z düzeninde Windows üzerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-261">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="6f04e-262">Bir pencere, özelliği olarak ayarlanarak en üstteki z düzeninde bulunur <xref:System.Windows.Window.Topmost%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-262">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="6f04e-263">Her z düzeninde, etkin olan pencere aynı z düzeninde diğer tüm pencerelerin üstünde görünür.</span><span class="sxs-lookup"><span data-stu-id="6f04e-263">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="6f04e-264">Pencere boyutu</span><span class="sxs-lookup"><span data-stu-id="6f04e-264">Window Size</span></span>  
 <span data-ttu-id="6f04e-265">Masaüstü konumuna sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve yükseklik özellikleri de dahil olmak üzere çeşitli özelliklerle belirlenen bir boyuta sahiptir <xref:System.Windows.Window.SizeToContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-265">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="6f04e-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> bir pencerenin ömrü boyunca sahip olduğu ve aşağıdaki örnekte gösterildiği gibi yapılandırıldığı genişlikler aralığını yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="6f04e-267">Pencere yüksekliği,, ve tarafından yönetilir <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-267">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="6f04e-268">Çeşitli genişlik değerleri ve yükseklik değerleri her biri bir Aralık belirttiği için, yeniden boyutlandırılabilir bir pencerenin genişlik ve yüksekliğinin ilgili boyut için belirtilen aralık dahilinde herhangi bir yerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6f04e-268">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="6f04e-269">Geçerli genişlik ve yüksekliğini algılamak için <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> sırasıyla ve ' yi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="6f04e-269">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="6f04e-270">Pencerenin genişlik ve yüksekliğinin pencere içeriğinin boyutuna uygun bir boyuta sahip olmasını istiyorsanız, <xref:System.Windows.Window.SizeToContent%2A> aşağıdaki değerlere sahip olan özelliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f04e-270">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="6f04e-271"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="6f04e-271"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="6f04e-272">Efekt yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6f04e-272">No effect (default).</span></span>  
  
- <span data-ttu-id="6f04e-273"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="6f04e-273"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="6f04e-274">Hem hem de içeriğin genişliğine göre aynı etkiye sahip olan içerik genişliğine uygun hale gelir <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-274">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="6f04e-275"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="6f04e-275"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="6f04e-276">Hem hem de <xref:System.Windows.FrameworkElement.MinHeight%2A> içeriğin yüksekliğine göre aynı etkiye sahip olan içerik yüksekliğine Sığdır <xref:System.Windows.FrameworkElement.MaxHeight%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-276">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="6f04e-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="6f04e-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="6f04e-278">Hem hem de <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> içeriğin yüksekliğine ayarlanmasına ve hem hem de <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> içeriğin genişliğine ayarlanmasına benzer etkiye sahip içerik genişliğine ve yüksekliğe uygun hale gelir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-278">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="6f04e-279">Aşağıdaki örnek, ilk başta gösterildiği gibi, hem dikey hem de yatay olarak içeriğini sığdırmak için otomatik olarak ölçeklenebilen bir pencere gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-279">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="6f04e-280">Aşağıdaki örnek, <xref:System.Windows.Window.SizeToContent%2A> bir pencerenin içeriği sığdırmak için nasıl yeniden boyutlandırılacağını belirtmek üzere koddaki özelliğinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-280">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="6f04e-281">Boyutlandırma özellikleri için öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="6f04e-281">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="6f04e-282">Temelde, bir pencerenin çeşitli boyutlar özellikleri, yeniden boyutlandırılabilir bir pencerenin genişlik ve yükseklik aralığını tanımlamak için birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-282">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="6f04e-283">Geçerli bir aralığın korunduğundan emin olmak için, <xref:System.Windows.Window> aşağıdaki öncelik emirlerini kullanarak boyut özelliklerinin değerlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-283">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="6f04e-284">**Yükseklik özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="6f04e-284">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6f04e-285">**Genişlik özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="6f04e-285">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6f04e-286">Öncelik sırası, özelliği ile yönetilen, ekranı kaplayan bir pencerenin boyutunu da belirleyebilir <xref:System.Windows.Window.WindowState%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-286">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="6f04e-287">Pencere durumu</span><span class="sxs-lookup"><span data-stu-id="6f04e-287">Window State</span></span>  
 <span data-ttu-id="6f04e-288">Yeniden boyutlandırılabilir bir pencerenin ömrü boyunca üç durum olabilir: normal, simge durumuna küçültülmüş ve ekranı kaplamış.</span><span class="sxs-lookup"><span data-stu-id="6f04e-288">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="6f04e-289">*Normal* duruma sahip bir pencere, pencerenin varsayılan durumudur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-289">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="6f04e-290">Bu duruma sahip bir pencere, yeniden boyutlandırılması durumunda bir yeniden boyutlandırma tutamacı veya kenarlık kullanarak, kullanıcının onu taşımasını ve yeniden boyutlandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-290">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="6f04e-291">*Simge durumuna küçültülmüş* bir pencere, olarak ayarlandıysa görev çubuğu düğmesine daraltılır <xref:System.Windows.Window.ShowInTaskbar%2A> `true` ; Aksi takdirde, mümkün olan en küçük boyuta daraltır ve masaüstünün sol alt köşesine yeniden konumlandırmalar.</span><span class="sxs-lookup"><span data-stu-id="6f04e-291">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="6f04e-292">Simge durumuna küçültülmüş pencere türü, bir kenarlık veya yeniden boyutlandırma tutamacı kullanılarak yeniden boyutlandırılabilir, ancak görev çubuğunda görünmeyen simge durumuna küçültülmüş bir pencere masaüstü etrafında sürüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-292">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="6f04e-293">*Ekranı kaplayan* bir pencere, en büyük boyuta genişletilir, bu da yalnızca <xref:System.Windows.FrameworkElement.MaxWidth%2A> ,, <xref:System.Windows.FrameworkElement.MaxHeight%2A> ve <xref:System.Windows.Window.SizeToContent%2A> özellikleri dikte eder.</span><span class="sxs-lookup"><span data-stu-id="6f04e-293">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="6f04e-294">Simge durumuna küçültülmüş bir pencere gibi, ekranı kaplayan bir pencere yeniden boyutlandırma tutamacı kullanılarak veya kenarlıkları sürükleyerek yeniden boyutlandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-294">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f04e-295">Pencerenin,,, <xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A> ve özelliklerinin değerleri, <xref:System.Windows.FrameworkElement.Height%2A> pencere şu anda büyütülmüş veya küçültülmüş olsa bile normal durum için her zaman değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f04e-295">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="6f04e-296">Bir pencerenin durumu <xref:System.Windows.Window.WindowState%2A> , özelliği ayarlanarak yapılandırılabilir ve bu, aşağıdaki <xref:System.Windows.WindowState> sabit listesi değerlerinden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-296">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="6f04e-297"><xref:System.Windows.WindowState.Normal>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="6f04e-297"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="6f04e-298">Aşağıdaki örnek, açıldığında ekranı kaplamış olarak gösterilen bir pencerenin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-298">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="6f04e-299">Genel olarak, <xref:System.Windows.Window.WindowState%2A> bir pencerenin başlangıç durumunu yapılandırmak için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-299">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="6f04e-300">Yeniden boyutlandırılabilir bir pencere gösterildiğinde, kullanıcılar pencere durumunu değiştirmek için pencerenin başlık çubuğundaki simge durumuna küçült, Ekranı Kapla ve geri yükle düğmelerine basabilir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-300">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="6f04e-301">Pencere görünümü</span><span class="sxs-lookup"><span data-stu-id="6f04e-301">Window Appearance</span></span>  
 <span data-ttu-id="6f04e-302">Pencerenin istemci alanının görünümünü, düğme, Etiketler ve metin kutuları gibi pencereye özgü içerik ekleyerek değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-302">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="6f04e-303">İstemci dışı alanı yapılandırmak için, <xref:System.Windows.Window> <xref:System.Windows.Window.Icon%2A> bir pencerenin simgesini ayarlamak ve başlığını ayarlamak için dahil olmak üzere çeşitli özellikler sağlar <xref:System.Windows.Window.Title%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-303">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="6f04e-304">Ayrıca, bir pencerenin yeniden boyutlandırma modu, pencere stili ve masaüstü görev çubuğunda düğme olarak görünüp görüntülenmediğini yapılandırarak, istemci olmayan alan kenarlığının görünümünü ve davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-304">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="6f04e-305">Yeniden boyutlandırma modu</span><span class="sxs-lookup"><span data-stu-id="6f04e-305">Resize Mode</span></span>  
 <span data-ttu-id="6f04e-306">Özelliğine bağlı olarak <xref:System.Windows.Window.WindowStyle%2A> , kullanıcıların pencereyi yeniden boyutlandırıp nasıl (ve ne olduğunu) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-306">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="6f04e-307">Pencere stili seçimi, bir kullanıcının kenarlığını fareyle sürükleyerek, **simge durumuna küçültme**, **Ekranı Kapla**ve **yeniden boyutlandır** düğmelerinin istemci olmayan alanda görünüp görünmediğini ve etkin olup olmadıkları gösterilmediğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="6f04e-307">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="6f04e-308"><xref:System.Windows.Window.ResizeMode%2A>Aşağıdaki sabit listesi değerlerinden biri olabilecek özelliğini ayarlayarak pencerenin nasıl yeniden boyutlandırılacağını yapılandırabilirsiniz <xref:System.Windows.ResizeMode> :</span><span class="sxs-lookup"><span data-stu-id="6f04e-308">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="6f04e-309"><xref:System.Windows.ResizeMode.CanResize>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="6f04e-309"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="6f04e-310">' De olduğu gibi <xref:System.Windows.Window.WindowStyle%2A> , bir pencerenin yeniden boyutlandırma modunun ömrü boyunca değişmeme olasılığı düşüktür, bu da büyük olasılıkla bu değeri biçimlendirmeden ayarlamanız anlamına gelir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f04e-310">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="6f04e-311">Özelliği inceleyerek pencerenin ekranı kaplayacağını, simge durumuna küçültülmüş veya geri yüklendiğini tespit edebilirsiniz <xref:System.Windows.Window.WindowState%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-311">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="6f04e-312">Pencere stili</span><span class="sxs-lookup"><span data-stu-id="6f04e-312">Window Style</span></span>  
 <span data-ttu-id="6f04e-313">Pencerenin istemci olmayan alanından gösterilen kenarlık çoğu uygulama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6f04e-313">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="6f04e-314">Bununla birlikte, farklı tür kenarlıkların gerekli olduğu veya pencere türüne bağlı olarak hiçbir kenarlığı gerekmeyen durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-314">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="6f04e-315">Pencerenin ne tür kenarlığı kontrol etmek için, <xref:System.Windows.Window.WindowStyle%2A> özelliğini, numaralandırmanın aşağıdaki değerlerinden biriyle ayarlarsınız <xref:System.Windows.WindowStyle> :</span><span class="sxs-lookup"><span data-stu-id="6f04e-315">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="6f04e-316"><xref:System.Windows.WindowStyle.SingleBorderWindow>varsayılanını</span><span class="sxs-lookup"><span data-stu-id="6f04e-316"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="6f04e-317">Bu pencere stillerinin etkisi aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-317">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Pencere kenarlık stillerinin çizimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="6f04e-319"><xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Bir pencerenin ömrü boyunca değiştirilmesi muhtemel olmadığından biçimlendirme veya kod kullanarak ayarlayabilirsiniz; bu, büyük olasılıkla biçimlendirme kullanarak yapılandıracaksınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f04e-319">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="6f04e-320">Dikdörtgen olmayan pencere stili</span><span class="sxs-lookup"><span data-stu-id="6f04e-320">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="6f04e-321">Ayrıca, izin veren kenarlık stillerinin yeterli olmadığı durumlar da vardır <xref:System.Windows.Window.WindowStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-321">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="6f04e-322">Örneğin, Microsoft Windows Media Player 'nin kullandığı gibi dikdörtgen olmayan bir kenarlığa sahip bir uygulama oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-322">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="6f04e-323">Örneğin, aşağıdaki şekilde gösterilen konuşma balonu penceresini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6f04e-323">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Beni sürükle olarak belirten bir konuşma balonu penceresi.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="6f04e-325">Bu tür bir pencere <xref:System.Windows.Window.WindowStyle%2A> , özelliği olarak ayarlanarak <xref:System.Windows.WindowStyle.None> ve saydamlık için olan özel destek kullanılarak oluşturulabilir <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="6f04e-325">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="6f04e-326">Bu değer birleşimi, pencereye tamamen saydam bir şekilde işlemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="6f04e-326">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="6f04e-327">Bu durumda, pencerenin istemci olmayan alanı donnlar (kapatma menüsü, simge durumuna küçült, Ekranı Kapla ve geri yükleme düğmeleri vb.) kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-327">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="6f04e-328">Sonuç olarak, kendinizinkini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-328">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="6f04e-329">Görev çubuğu varlığı</span><span class="sxs-lookup"><span data-stu-id="6f04e-329">Task Bar Presence</span></span>  

<span data-ttu-id="6f04e-330">Pencerenin varsayılan görünümü, aşağıdaki şekilde gösterildiği gibi bir görev çubuğu düğmesi içerir:</span><span class="sxs-lookup"><span data-stu-id="6f04e-330">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Görev çubuğu düğmesi olan bir pencere gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="6f04e-332">Bazı Windows türlerinde ileti kutuları ve iletişim kutuları gibi bir görev çubuğu düğmesi yoktur (bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="6f04e-332">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="6f04e-333">Bir pencere için görev çubuğu düğmesinin, <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği ayarlayarak (varsayılan olarak) gösterilip gösterilmeyeceğini kontrol edebilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="6f04e-333">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="6f04e-334">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="6f04e-334">Security Considerations</span></span>  
 <span data-ttu-id="6f04e-335"><xref:System.Windows.Window>`UnmanagedCode`örneği oluşturulacak güvenlik izninin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-335"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="6f04e-336">Üzerinde yüklü olan ve yerel makineden başlatılan uygulamalar için, bu, uygulamaya verilen izinler kümesi içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-336">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="6f04e-337">Bununla birlikte, bu, ClickOnce kullanılarak Internet 'ten veya yerel intranet bölgesinden başlatılan uygulamalara verilen izin kümesinin dışındadır.</span><span class="sxs-lookup"><span data-stu-id="6f04e-337">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="6f04e-338">Sonuç olarak, kullanıcılar bir ClickOnce güvenlik uyarısı alır ve uygulamanın izin kümesini tam güvenle yükseltmek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-338">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="6f04e-339">Ayrıca, XBAP varsayılan olarak Windows veya iletişim kutularını gösteremez.</span><span class="sxs-lookup"><span data-stu-id="6f04e-339">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="6f04e-340">Tek başına uygulama güvenliği konuları hakkında bir tartışma için bkz. [WPF Güvenlik Stratejisi-Platform güvenliği](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="6f04e-340">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="6f04e-341">Diğer Windows türleri</span><span class="sxs-lookup"><span data-stu-id="6f04e-341">Other Types of Windows</span></span>  
 <span data-ttu-id="6f04e-342"><xref:System.Windows.Navigation.NavigationWindow>, gezinebilir içeriği barındırmak için tasarlanan bir penceredir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-342"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="6f04e-343">Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="6f04e-343">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="6f04e-344">İletişim kutuları, genellikle bir işlevi bir kullanıcıdan tamamlamaya yönelik bilgi toplamak için kullanılan bir Windows.</span><span class="sxs-lookup"><span data-stu-id="6f04e-344">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="6f04e-345">Örneğin, bir Kullanıcı bir dosyayı açmak istediğinde dosya **Aç** iletişim kutusu genellikle bir uygulama tarafından dosya adını kullanıcıdan almak için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f04e-345">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="6f04e-346">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6f04e-346">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f04e-347">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f04e-347">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="6f04e-348">İletişim Kutularına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f04e-348">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="6f04e-349">WPF Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="6f04e-349">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
