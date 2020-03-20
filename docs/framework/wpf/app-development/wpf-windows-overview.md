---
title: Windows'a genel bakış
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
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145546"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="5b293-102">WPF Windows'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5b293-102">WPF Windows Overview</span></span>
<span data-ttu-id="5b293-103">Kullanıcılar Windows Presentation Foundation (WPF) bağımsız uygulamaları yla windows üzerinden etkileşimde bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="5b293-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="5b293-104">Bir pencerenin birincil amacı, verileri görselleştiren ve kullanıcıların verilerle etkileşimkurmasını sağlayan içeriği barındırmaktır.</span><span class="sxs-lookup"><span data-stu-id="5b293-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="5b293-105">Bağımsız WPF uygulamaları <xref:System.Windows.Window> sınıfı kullanarak kendi pencerelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="5b293-106">Bu konu, <xref:System.Windows.Window> bağımsız uygulamalarda pencere oluşturma ve yönetme temellerini kapsayan önce tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5b293-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-107">XAML tarayıcı uygulamaları (XBAP'ler) ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfalar da dahil olmak üzere tarayıcı tarafından barındırılan WPF uygulamaları kendi pencerelerini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5b293-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="5b293-108">Bunun yerine, Windows Internet Explorer tarafından sağlanan pencerelerde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="5b293-109">Bkz. [WPF XAML Tarayıcı Uygulamaları Genel Bakış.](wpf-xaml-browser-applications-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5b293-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="5b293-110">Pencere Sınıfı</span><span class="sxs-lookup"><span data-stu-id="5b293-110">The Window Class</span></span>  
 <span data-ttu-id="5b293-111">Aşağıdaki şekil, bir pencerenin kurucu bölümlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5b293-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Pencere öğelerini gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="5b293-113">Bir pencere iki alana ayrılır: istemci olmayan alan ve istemci alanı.</span><span class="sxs-lookup"><span data-stu-id="5b293-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="5b293-114">Pencerenin *istemci olmayan alanı* WPF tarafından uygulanır ve aşağıdakiler de dahil olmak üzere çoğu pencerede ortak olan pencere bölümlerini içerir:</span><span class="sxs-lookup"><span data-stu-id="5b293-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="5b293-115">Bir sınır.</span><span class="sxs-lookup"><span data-stu-id="5b293-115">A border.</span></span>  
  
- <span data-ttu-id="5b293-116">Bir başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="5b293-116">A title bar.</span></span>  
  
- <span data-ttu-id="5b293-117">Bir simge.</span><span class="sxs-lookup"><span data-stu-id="5b293-117">An icon.</span></span>  
  
- <span data-ttu-id="5b293-118">Düğmeleri En Aza Indirin, En Üst Düzeye Çıkarın ve Geri Yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5b293-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="5b293-119">Kapat düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5b293-119">A Close button.</span></span>  
  
- <span data-ttu-id="5b293-120">Kullanıcıların bir pencereyi en aza indirmesine, en üst düzeye çıkarmasına, geri yüklemesine, taşımasına, yeniden boyutlandırmasına ve kapatmasına olanak tanıyan menü öğeleriiçeren bir Sistem menüsü.</span><span class="sxs-lookup"><span data-stu-id="5b293-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="5b293-121">Pencerenin *istemci alanı,* pencerenin istemci olmayan alanı içindeki alandır ve geliştiriciler tarafından menü çubukları, araç çubukları ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="5b293-122">WPF'de, bir pencere aşağıdakileri <xref:System.Windows.Window> yapmak için kullandığınız sınıf tarafından kapsüllenir:</span><span class="sxs-lookup"><span data-stu-id="5b293-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="5b293-123">Bir pencere görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="5b293-123">Display a window.</span></span>  
  
- <span data-ttu-id="5b293-124">Bir pencerenin boyutunu, konumunu ve görünümünü yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="5b293-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="5b293-125">Uygulamaya özgü içeriği barındırın.</span><span class="sxs-lookup"><span data-stu-id="5b293-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="5b293-126">Bir pencerenin ömrünü yönetin.</span><span class="sxs-lookup"><span data-stu-id="5b293-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="5b293-127">Pencere Uygulama</span><span class="sxs-lookup"><span data-stu-id="5b293-127">Implementing a Window</span></span>  
 <span data-ttu-id="5b293-128">Tipik bir pencerenin uygulanması, *görünümün* kullanıcılara nasıl göründüğünü tanımladığı hem görünüm hem de davranışiçerir ve *davranış,* kullanıcılar la etkileşim de dahil olmak üzere pencerenin işlevlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="5b293-129">WPF'de, kod veya biçimlendirme kullanarak bir pencerenin görünümünü ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] davranışını uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="5b293-130">Ancak genel olarak, bir pencerenin görünümü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanılarak uygulanır ve davranışı aşağıdaki örnekte gösterildiği gibi kod arkası kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b293-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="5b293-131">Biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasının ve kod arkası dosyanın birlikte çalışmasını sağlamak için aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5b293-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="5b293-132">Biçimlendirmede, `Window` öğe özniteliği `x:Class` içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5b293-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="5b293-133">Uygulama `x:Class` oluşturulduğunda, biçimlendirme dosyasındaki varlığı Microsoft build engine (MSBuild) `partial` türeyen <xref:System.Windows.Window> ve öznitelik tarafından `x:Class` belirtilen adı taşıyan bir sınıf oluşturmak için neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b293-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="5b293-134">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema için bir XML ad alanı bildirimi `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` eklenmesini gerektirir ( ).</span><span class="sxs-lookup"><span data-stu-id="5b293-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="5b293-135">Oluşturulan `partial` sınıf, olayları `InitializeComponent` kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağrılan yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="5b293-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="5b293-136">Kod arkasında, sınıf biçimlendirmeözdeki öznitelik tarafından `partial` `x:Class` belirtilen aynı ada sahip bir sınıf olmalı <xref:System.Windows.Window>ve 'den türemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b293-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5b293-137">Bu, kod arkası dosyasının, uygulama `partial` oluşturulduğunda biçimlendirme dosyası için oluşturulan sınıfla ilişkilendirilmesine izin verir [(bkz.](building-a-wpf-application-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="5b293-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="5b293-138">Kod arkasında, <xref:System.Windows.Window> sınıf `InitializeComponent` yöntemi çağıran bir oluşturucu uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b293-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="5b293-139">`InitializeComponent`olayları kaydetmek ve biçimlendirmede tanımlanan `partial` özellikleri ayarlamak için biçimlendirme dosyasının oluşturulan sınıfı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b293-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-140">Visual Studio'yu <xref:System.Windows.Window> kullanarak projenize yeni bir <xref:System.Windows.Window> ekleme yaptığınızda, biçim hem biçimlendirme hem de kod arkası kullanılarak uygulanır ve burada açıklandığı gibi biçimlendirme ve kod arkası dosyaları arasındaki ilişkilendirme oluşturmak için gerekli yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5b293-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="5b293-141">Bu yapılandırma yerinde olduğu için, biçimlendirmede [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pencerenin görünümünü tanımlamaya ve davranışını kod arkasında uygulamaya odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="5b293-142">Aşağıdaki örnekte, biçimlendirmede [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulanan düğmeli bir pencere ve kod arkasında uygulanan <xref:System.Windows.Controls.Primitives.ButtonBase.Click> düğmeolayı için bir olay işleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b293-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="5b293-143">MSBuild için Pencere Tanımı Nı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5b293-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="5b293-144">Pencerenizi nasıl uyguladığınız, pencerenin MSBuild için nasıl yapılandırılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="5b293-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="5b293-145">Hem biçimlendirme hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod arkası kullanılarak tanımlanan bir pencere için:</span><span class="sxs-lookup"><span data-stu-id="5b293-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="5b293-146">XAML biçimlendirme dosyaları MSBuild `Page` öğeleri olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="5b293-147">Kod arkası dosyalar MSBuild `Compile` öğeleri olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="5b293-148">Bu, aşağıdaki MSBuild proje dosyasında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="5b293-149">WPF uygulamaları oluşturma hakkında daha fazla bilgi için [wpf uygulaması oluşturma](building-a-wpf-application-wpf.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="5b293-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="5b293-150">Pencere Ömrü</span><span class="sxs-lookup"><span data-stu-id="5b293-150">Window Lifetime</span></span>  
 <span data-ttu-id="5b293-151">Herhangi bir sınıfta olduğu gibi, bir pencerenin de ilk anında başlatıldıktan sonra açılan, etkinleştirilen ve devre dışı bırakılan ve sonunda kapandığı bir ömrü vardır.</span><span class="sxs-lookup"><span data-stu-id="5b293-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="5b293-152">Pencere Açma</span><span class="sxs-lookup"><span data-stu-id="5b293-152">Opening a Window</span></span>  
 <span data-ttu-id="5b293-153">Bir pencereyi açmak için, önce aşağıdaki örnekte gösterilen bir örnek oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="5b293-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="5b293-154">Bu örnekte, `MarkupAndCodeBehindWindow` <xref:System.Windows.Application.Startup> uygulama başlatıldığında anlık olarak, olay yükseltildiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b293-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="5b293-155">Bir pencere anında olduğunda, bu pencereye yapılan bir başvuru otomatik olarak nesne tarafından <xref:System.Windows.Application> yönetilen <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>bir pencere listesine eklenir (bkz.</span><span class="sxs-lookup"><span data-stu-id="5b293-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="5b293-156">Ayrıca, anlık olarak ayarlanacak ilk pencere varsayılan <xref:System.Windows.Application> olarak ana uygulama penceresi olarak <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>ayarlanır (bkz.</span><span class="sxs-lookup"><span data-stu-id="5b293-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="5b293-157">Pencere sonunda <xref:System.Windows.Window.Show%2A> yöntemi arayarak açılır; sonuç aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b293-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Window.Show'u arayarak Açılan Pencere](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="5b293-159">Arayarak <xref:System.Windows.Window.Show%2A> açılan pencere, moduz bir penceredir, bu da uygulamanın kullanıcıların aynı uygulamadaki diğer pencereleri etkinleştirmesine olanak tanıyan bir modda çalıştığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b293-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-160"><xref:System.Windows.Window.ShowDialog%2A>iletişim kutuları gibi pencereleri modally açmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="5b293-161">Daha fazla bilgi için [İletişim Kutularına Genel Bakış'a](dialog-boxes-overview.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="5b293-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="5b293-162">Çağrıldığında, <xref:System.Windows.Window.Show%2A> bir pencere, kullanıcı girişi almasına izin veren altyapıyı oluşturmak için gösterilmeden önce başlatma çalışması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5b293-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="5b293-163">Pencere başharfe çarptırıldığında, <xref:System.Windows.Window.SourceInitialized> olay yükseltilir ve pencere gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="5b293-164">Kısayol olarak, <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılan ilk pencereyi belirtmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="5b293-165">Uygulama başladığında, değeri <xref:System.Windows.Application.StartupUri%2A> ile belirtilen pencere modelessly açılır; dahili olarak, pencere yöntemini <xref:System.Windows.Window.Show%2A> çağırarak açılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="5b293-166">Pencere Sahipliği</span><span class="sxs-lookup"><span data-stu-id="5b293-166">Window Ownership</span></span>  
 <span data-ttu-id="5b293-167"><xref:System.Windows.Window.Show%2A> Yöntem kullanılarak açılan pencerenin, onu oluşturan pencereyle örtülü bir ilişkisi yoktur; kullanıcılar diğerpencereden bağımsız olarak her iki pencereyle de etkileşimkurabilir, bu da her iki pencerenin de aşağıdakileri yapabileceği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="5b293-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="5b293-168">Diğerini kapatın (pencerelerden biri <xref:System.Windows.Window.Topmost%2A> özelliği `true`ayarlı değilse).</span><span class="sxs-lookup"><span data-stu-id="5b293-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="5b293-169">Diğerini etkilemeden en aza indirilme, en üst düzeye çıkarma ve geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="5b293-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="5b293-170">Bazı pencereler, onları açan pencereyle ilişki gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b293-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="5b293-171">Örneğin, Tümleşik Geliştirme Ortamı (IDE) uygulaması, tipik davranışı bunları oluşturan pencereyi kapsayacak şekilde özellik pencerelerini ve araç pencerelerini açabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="5b293-172">Ayrıca, bu tür pencereler her zaman kapanmalı, en aza indirilmeli, en üst düzeye çıkarmalı ve onları oluşturan pencereyle uyumlu olarak geri yüklemelidir.</span><span class="sxs-lookup"><span data-stu-id="5b293-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="5b293-173">Böyle bir ilişki bir pencerenin başka bir *penceresinin sahibine ait* hale getirilerek kurulabilir ve sahip <xref:System.Windows.Window.Owner%2A> *penceresinin* *özelliğini*sahip penceresine bir başvuruyla ayarlayarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="5b293-174">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="5b293-175">Mülkiyet kurulduktan sonra:</span><span class="sxs-lookup"><span data-stu-id="5b293-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="5b293-176">Sahip olunan pencere, <xref:System.Windows.Window.Owner%2A> mülkünün değerini inceleyerek sahibinin penceresine başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="5b293-177">Sahip penceresi, <xref:System.Windows.Window.OwnedWindows%2A> sahip olduğu tüm pencereleri mülkünün değerini inceleyerek keşfedebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="5b293-178">Pencere Etkinleştirmesini Önleme</span><span class="sxs-lookup"><span data-stu-id="5b293-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="5b293-179">Gösterildiğinde, Internet messenger tarzı bir uygulamanın konuşma pencereleri veya bir e-posta uygulamasının bildirim pencereleri gibi pencerelerin etkinleştirilmemesi gereken senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="5b293-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="5b293-180">Uygulamanızın gösterildiğinde etkinleştirilmemesi gereken bir penceresi varsa, yöntemi <xref:System.Windows.Window.ShowActivated%2A> ilk `false` kez <xref:System.Windows.Window.Show%2A> aramadan önce özelliğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="5b293-181">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="5b293-181">As a consequence:</span></span>  
  
- <span data-ttu-id="5b293-182">Pencere etkinleştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="5b293-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="5b293-183">Pencerenin <xref:System.Windows.Window.Activated> olayı yükseltilmez.</span><span class="sxs-lookup"><span data-stu-id="5b293-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="5b293-184">Şu anda etkinleştirilen pencere etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="5b293-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="5b293-185">Ancak, kullanıcı istemci veya istemci olmayan alanı tıklatarak pencere etkinleştirir etkinleştirmez pencere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="5b293-186">Bu durumda:</span><span class="sxs-lookup"><span data-stu-id="5b293-186">In this case:</span></span>  
  
- <span data-ttu-id="5b293-187">Pencere etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="5b293-187">The window is activated.</span></span>  
  
- <span data-ttu-id="5b293-188">Pencerenin <xref:System.Windows.Window.Activated> olayı yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="5b293-189">Önceden etkinleştirilen pencere devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="5b293-190">Pencerenin <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayların ardından kullanıcı eylemlerine yanıt olarak beklendiği gibi yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="5b293-191">Pencere Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="5b293-191">Window Activation</span></span>  
 <span data-ttu-id="5b293-192">Bir pencere ilk açıldığında, etkin pencere olur (ayarlı <xref:System.Windows.Window.ShowActivated%2A> olarak `false`gösterilmedikçe).</span><span class="sxs-lookup"><span data-stu-id="5b293-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="5b293-193">*Etkin pencere,* tuş vuruşları ve fare tıklamaları gibi kullanıcı girişlerini yakalayan penceredir.</span><span class="sxs-lookup"><span data-stu-id="5b293-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="5b293-194">Bir pencere etkin hale geldiğinde, <xref:System.Windows.Window.Activated> olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="5b293-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-195">Bir pencere ilk açıldığında, <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> olaylar ancak <xref:System.Windows.Window.Activated> olay yükseltildikten sonra yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="5b293-196">Bunu göz önünde bulundurarak, bir pencere <xref:System.Windows.Window.ContentRendered> etkili bir şekilde açıldığında açılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="5b293-197">Bir pencere etkin hale geldikten sonra, kullanıcı aynı uygulamada başka bir pencereyi etkinleştirebilir veya başka bir uygulamayı etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="5b293-198">Bu durumda, şu anda etkin olan <xref:System.Windows.Window.Deactivated> pencere devre dışı bırakılır ve olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="5b293-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="5b293-199">Aynı şekilde, kullanıcı şu anda devre dışı bırakılmış bir <xref:System.Windows.Window.Activated> pencere seçtiğinde, pencere yeniden etkin olur ve yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="5b293-200">Yalnızca <xref:System.Windows.Window.Activated> bir pencere <xref:System.Windows.Window.Deactivated> etkin olduğunda çalıştırılabilen işlevselliği etkinleştirmek ve devre dışı etmek yaygın bir nedendir.</span><span class="sxs-lookup"><span data-stu-id="5b293-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="5b293-201">Örneğin, bazı pencereler, oyunlar ve video oynatıcılar da dahil olmak üzere sürekli kullanıcı girişi veya dikkat gerektiren etkileşimli içerik görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b293-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="5b293-202">Aşağıdaki örnek, bu davranışın nasıl işleyeceğini <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> uygulanacağını gösteren basitleştirilmiş bir video oynatıcıdır.</span><span class="sxs-lookup"><span data-stu-id="5b293-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="5b293-203">Diğer uygulama türleri, bir pencere devre dışı bırakıldığında arka planda kod çalıştırmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="5b293-204">Örneğin, kullanıcı diğer uygulamaları kullanırken bir posta istemcisi posta sunucusunu yoklamaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="5b293-205">Bu gibi uygulamalar genellikle ana pencere devre dışı bırakılırken farklı veya ek davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="5b293-206">Posta programıyla ilgili olarak, bu hem gelen kutusuna yeni posta öğesi nin eklenmesi hem de sistem tepsisine bir bildirim simgesi eklenmesi anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="5b293-207">Bildirim simgesinin yalnızca posta penceresi etkin olmadığında görüntülenmesi gerekir ve bu <xref:System.Windows.Window.IsActive%2A> simge özelliği inceleyerek belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="5b293-208">Arka plan görevi tamamlanırsa, bir pencere <xref:System.Windows.Window.Activate%2A> arama yöntemini daha acil bir şekilde kullanıcıya bildirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="5b293-209">Kullanıcı çağrıldığında <xref:System.Windows.Window.Activate%2A> etkinleştirilen başka bir uygulamayla etkileşim halindeyse, pencerenin görev çubuğu düğmesi yanıp söner.</span><span class="sxs-lookup"><span data-stu-id="5b293-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="5b293-210">Bir kullanıcı geçerli uygulamayla etkileşim de <xref:System.Windows.Window.Activate%2A> bulunuyorsa, arama penceresi ön plana çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5b293-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-211">Uygulama kapsamı etkinleştirme <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olayları kullanarak işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="5b293-212">Pencereyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="5b293-212">Closing a Window</span></span>  
 <span data-ttu-id="5b293-213">Bir pencerenin ömrü, kullanıcı kapatıldığında sona ermeye başlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="5b293-214">Bir pencere, aşağıdakiler de dahil olmak üzere istemci olmayan alandaki öğeler kullanılarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b293-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="5b293-215">**Sistem** menüsünün **Kapat** öğesi.</span><span class="sxs-lookup"><span data-stu-id="5b293-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="5b293-216">ALT+F4 tuşuna basArak.</span><span class="sxs-lookup"><span data-stu-id="5b293-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="5b293-217">**Kapat** düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="5b293-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="5b293-218">Bir pencereyi kapatmak için istemci alanına ek mekanizmalar sağlayabilirsiniz, bunlardan daha yaygın olan aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="5b293-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="5b293-219">Genellikle ana uygulama pencereleri için **Dosya** menüsündeki bir **Çıkış** öğesi.</span><span class="sxs-lookup"><span data-stu-id="5b293-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="5b293-220">**Dosya** menüsündeki **bir öğeyi genellikle** ikincil bir uygulama penceresinde kapat.</span><span class="sxs-lookup"><span data-stu-id="5b293-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="5b293-221">Genellikle modal iletişim kutusunda bir **İptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5b293-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="5b293-222">Genellikle modeless iletişim kutusunda **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5b293-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="5b293-223">Bu özel mekanizmalardan birine yanıt olarak bir pencereyi <xref:System.Windows.Window.Close%2A> kapatmak için yöntemi aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b293-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="5b293-224">Aşağıdaki örnek, **Dosya** menüsünde **Çıkış'ı** seçerek pencereyi kapatma özelliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="5b293-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="5b293-225">Bir pencere kapandığında, iki olay <xref:System.Windows.Window.Closing> <xref:System.Windows.Window.Closed>yükselir: ve .</span><span class="sxs-lookup"><span data-stu-id="5b293-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="5b293-226"><xref:System.Windows.Window.Closing>pencere kapanmadan önce yükseltilir ve pencere kapanmasının önlenebileceği bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="5b293-227">Pencere kapanmasını önlemenin yaygın nedenlerinden biri, pencere içeriğinin değiştirilmiş veriler içermesidir.</span><span class="sxs-lookup"><span data-stu-id="5b293-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="5b293-228">Bu durumda, <xref:System.Windows.Window.Closing> olay verilerin kirli olup olmadığını belirlemek ve eğer öyleyse, kullanıcıya verileri kaydetmeden pencereyi kapatmaya devam edip etmeyeceğini sormak veya pencere kapatmayı iptal etmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="5b293-229">Aşağıdaki örnek, işlemenin <xref:System.Windows.Window.Closing>temel yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b293-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="5b293-230"><xref:System.Windows.Window.Closing> Olay işleyicisi, <xref:System.ComponentModel.CancelEventArgs>bir pencerenin `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> kapanmasını önlemek `true` için ayarladığınız özelliği uygulayan bir , geçti.</span><span class="sxs-lookup"><span data-stu-id="5b293-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="5b293-231">Ele <xref:System.Windows.Window.Closing> alınmaz veya işlenir ancak iptal edilmezse, pencere kapanır.</span><span class="sxs-lookup"><span data-stu-id="5b293-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="5b293-232">Bir pencere kapanmadan hemen <xref:System.Windows.Window.Closed> önce, yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="5b293-233">Bu noktada, bir pencerenin kapanması engellenemez.</span><span class="sxs-lookup"><span data-stu-id="5b293-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-234">Ana uygulama penceresi kapandığında (bakınız) <xref:System.Windows.Application.MainWindow%2A>veya son pencere kapandığında bir uygulama otomatik olarak kapatılacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="5b293-235">Ayrıntılar için bkz. <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b293-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="5b293-236">Bir pencere istemci olmayan ve istemci olmayan alanlarda sağlanan mekanizmalar aracılığıyla açıkça kapatılabilir, ancak aşağıdakiler de dahil olmak üzere uygulamanın veya Windows'un diğer bölümlerindeki davranışın bir sonucu olarak bir pencere de örtülü olarak kapatılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b293-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="5b293-237">Bir kullanıcı Windows'u kapatır veya kapatır.</span><span class="sxs-lookup"><span data-stu-id="5b293-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="5b293-238">Pencerenin sahibi kapanır (bkz. <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="5b293-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="5b293-239">Ana uygulama penceresi kapalıdır ve <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="5b293-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="5b293-240"><xref:System.Windows.Application.Shutdown%2A>denir.</span><span class="sxs-lookup"><span data-stu-id="5b293-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-241">Pencere kapatıldıktan sonra yeniden açılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b293-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="5b293-242">Pencere Ömrü Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="5b293-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="5b293-243">Aşağıdaki resimde, bir pencerenin ömrü boyunca temel olayların sırasını gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5b293-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Bir pencerenin ömründeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="5b293-245">Aşağıdaki resimde etkinleştirme olmadan gösterilen bir pencerenin ömrü boyunca temel<xref:System.Windows.Window.ShowActivated%2A> olayların sırasını gösterir (pencere gösterilmeden `false` önce ayarlanır):</span><span class="sxs-lookup"><span data-stu-id="5b293-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Etkinleştirme olmadan bir pencerenin ömründeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="5b293-247">Pencere Konumu</span><span class="sxs-lookup"><span data-stu-id="5b293-247">Window Location</span></span>  
 <span data-ttu-id="5b293-248">Bir pencere açıkken, masaüstüne göre x ve y boyutlarında bir konuma sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b293-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="5b293-249">Bu konum, sırasıyla <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> ve özellikleri inceleyerek belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="5b293-250">Bu özellikleri pencerenin konumunu değiştirecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="5b293-251">Ayrıca, <xref:System.Windows.Window.WindowStartupLocation%2A> özelliği aşağıdaki <xref:System.Windows.WindowStartupLocation> numaralandırma <xref:System.Windows.Window> değerlerinden biriyle ayarlayarak bir kişinin ilk görüntülendiğindeki ilk konumunu da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b293-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="5b293-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="5b293-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="5b293-253">Başlangıç <xref:System.Windows.WindowStartupLocation.Manual>konumu olarak belirtilirse <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikler ayarlanmamışsa, <xref:System.Windows.Window> Windows'dan bir konumun görünmesini ister.</span><span class="sxs-lookup"><span data-stu-id="5b293-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="5b293-254">En Üstte Windows ve Z-Order</span><span class="sxs-lookup"><span data-stu-id="5b293-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="5b293-255">X ve y konumuna sahip olmasının yanı sıra, bir pencerenin z boyutunda diğer pencerelere göre dikey konumunu belirleyen bir konumu da vardır.</span><span class="sxs-lookup"><span data-stu-id="5b293-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="5b293-256">Bu pencerenin z sırası olarak bilinir ve iki türü vardır: normal z sırası ve en üstteki z-sırası.</span><span class="sxs-lookup"><span data-stu-id="5b293-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="5b293-257">Normal *z düzenindeki* bir pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5b293-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="5b293-258">Varsayılan olarak, bir pencere normal z-sırada yer alır.</span><span class="sxs-lookup"><span data-stu-id="5b293-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="5b293-259">En *üstteki z-düzenindeki* pencerenin konumu da şu anda etkin olup olmadığına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5b293-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="5b293-260">Ayrıca, en üstteki z-sıralı pencereler her zaman normal z-sırasına göre pencerelerin üzerinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="5b293-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="5b293-261">Bir pencere, özelliğini <xref:System.Windows.Window.Topmost%2A> . `true`</span><span class="sxs-lookup"><span data-stu-id="5b293-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="5b293-262">Her z-sırası içinde, şu anda etkin olan pencere aynı z-order'daki diğer tüm pencerelerin üzerinde görünür.</span><span class="sxs-lookup"><span data-stu-id="5b293-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="5b293-263">Pencere Boyutu</span><span class="sxs-lookup"><span data-stu-id="5b293-263">Window Size</span></span>  
 <span data-ttu-id="5b293-264">Bir masaüstü konumuna sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve <xref:System.Windows.Window.SizeToContent%2A>yükseklik özellikleri ve dahil olmak üzere çeşitli özellikleri tarafından belirlenen bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b293-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="5b293-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A> ve bir pencerenin ömrü boyunca sahip olabileceği genişlik aralığını yönetmek için kullanılır ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="5b293-266">Pencere yüksekliği , <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve , tarafından yönetilir ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b293-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="5b293-267">Çeşitli genişlik değerleri ve yükseklik değerleri her bir aralık belirtir, çünkü genişlik ve yeniden boyutlandırılabilir bir pencerenin yüksekliği için ilgili boyut için belirtilen aralık içinde herhangi bir yerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5b293-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="5b293-268">Geçerli genişliğini ve yüksekliğini <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>algılamak için sırasıyla ve</span><span class="sxs-lookup"><span data-stu-id="5b293-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="5b293-269">Pencerenizin genişliğinin ve yüksekliğinin pencereiçeriğinin boyutuna uygun bir boyuta sahip olmasını istiyorsanız, <xref:System.Windows.Window.SizeToContent%2A> aşağıdaki değerlere sahip özelliği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b293-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="5b293-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="5b293-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="5b293-271">Hiçbir etkisi (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5b293-271">No effect (default).</span></span>  
  
- <span data-ttu-id="5b293-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="5b293-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="5b293-273">İçerik genişliğine sığdır, bu da <xref:System.Windows.FrameworkElement.MinWidth%2A> hem <xref:System.Windows.FrameworkElement.MaxWidth%2A> ayarı hem de içeriğin genişliğiyle aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b293-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="5b293-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="5b293-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="5b293-275">Hem ayarı hem de <xref:System.Windows.FrameworkElement.MinHeight%2A> içeriğin yüksekliğiyle <xref:System.Windows.FrameworkElement.MaxHeight%2A> aynı etkiye sahip içerik yüksekliğine sığdırın.</span><span class="sxs-lookup"><span data-stu-id="5b293-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="5b293-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="5b293-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="5b293-277">Hem <xref:System.Windows.FrameworkElement.MinHeight%2A> içerik hem de içeriğin yüksekliğini ayarlamakla <xref:System.Windows.FrameworkElement.MaxHeight%2A> aynı etkiye sahip olan <xref:System.Windows.FrameworkElement.MinWidth%2A> içerik <xref:System.Windows.FrameworkElement.MaxWidth%2A> genişliğine ve yüksekliğe ve içeriğin hem de genişliğine ayar.</span><span class="sxs-lookup"><span data-stu-id="5b293-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="5b293-278">Aşağıdaki örnekte, ilk gösterildiğinde hem dikey hem de yatay olarak içeriğine uyacak şekilde otomatik olarak boyutlandırılabilen bir pencere gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b293-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="5b293-279">Aşağıdaki örnekte, bir <xref:System.Windows.Window.SizeToContent%2A> pencerenin içeriğine uyacak şekilde nasıl yeniden boyutlandırıldığını belirtmek için özelliğin kod olarak nasıl ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5b293-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="5b293-280">Boyutlandırma Özellikleri için Öncelik Sırası</span><span class="sxs-lookup"><span data-stu-id="5b293-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="5b293-281">Esasen, bir pencerenin çeşitli boyutözellikleri, yeniden boyutlandırılabilir bir pencere için genişlik ve yükseklik aralığını tanımlamak için birleştirir.</span><span class="sxs-lookup"><span data-stu-id="5b293-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="5b293-282">Geçerli bir aralığın tutulmasını <xref:System.Windows.Window> sağlamak için, aşağıdaki öncelik emirlerini kullanarak boyut özelliklerinin değerlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5b293-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="5b293-283">**Yükseklik Özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="5b293-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="5b293-284">**Genişlik Özellikleri için:**</span><span class="sxs-lookup"><span data-stu-id="5b293-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="5b293-285">Öncelik sırası, <xref:System.Windows.Window.WindowState%2A> özellik ile yönetilen en üst düzeye çıktığında bir pencerenin boyutunu da belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="5b293-286">Pencere Durumu</span><span class="sxs-lookup"><span data-stu-id="5b293-286">Window State</span></span>  
 <span data-ttu-id="5b293-287">Yeniden boyutlandırılabilir bir pencerenin ömrü boyunca, üç durum olabilir: normal, en aza indirgenmiş ve en üst düzeye çıkarılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="5b293-288">*Normal* durumu olan bir pencere, pencerenin varsayılan durumudur.</span><span class="sxs-lookup"><span data-stu-id="5b293-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="5b293-289">Bu duruma sahip bir pencere, yeniden boyutlandırılabilirse, yeniden boyutlandırma kavramasını veya kenarlığı kullanarak kullanıcının onu hareket ettirmesine ve yeniden boyutlandırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5b293-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="5b293-290">En aza *indirgenen* durumu olan bir pencere, <xref:System.Windows.Window.ShowInTaskbar%2A> ayarlanmışsa görev çubuğu düğmesine `true`çöker; aksi takdirde, mümkün olan en küçük boyuta çöker ve masaüstünün sol alt köşesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="5b293-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="5b293-291">Görev çubuğunda gösterilmeyen simge durumuna küçültülmüş bir pencere masaüstünde sürüncemede edilse de, kenarlık veya yeniden boyutlandırma kavrama kullanılarak en aza indirgenmiş pencere türü de yeniden boyutlandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b293-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="5b293-292">*Maksimize bir* durum ile bir pencere olabilir maksimum boyutuna genişletir, <xref:System.Windows.FrameworkElement.MaxWidth%2A>hangi <xref:System.Windows.FrameworkElement.MaxHeight%2A>sadece <xref:System.Windows.Window.SizeToContent%2A> onun kadar büyük olacak , ve özellikleri dikte.</span><span class="sxs-lookup"><span data-stu-id="5b293-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="5b293-293">Simge durumuna küçültülmüş bir pencere gibi, en üst düzeye çıkarılmış bir pencere yeniden boyutlandırma kavrama kullanılarak veya kenarlığı sürükleyerek yeniden boyutlandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b293-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b293-294">Pencere nin <xref:System.Windows.Window.Top%2A>değerleri <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A> , , ve bir pencerenin özellikleri, pencere şu anda en üst düzeye çıkarıldığında veya en aza indirilmiş olsa bile, her zaman normal durum değerlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b293-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="5b293-295">Bir pencerenin durumu, aşağıdaki <xref:System.Windows.Window.WindowState%2A> <xref:System.Windows.WindowState> numaralandırma değerlerinden birine sahip olabilecek özelliğini ayarlayarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b293-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="5b293-296"><xref:System.Windows.WindowState.Normal>(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="5b293-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="5b293-297">Aşağıdaki örnek, açıldığında en üst düzey olarak gösterilen bir pencerenin nasıl oluşturulacak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b293-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="5b293-298">Genel olarak, bir <xref:System.Windows.Window.WindowState%2A> pencerenin ilk durumunu yapılandırmak için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b293-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="5b293-299">Yeniden boyutlandırılabilir bir pencere gösterildikten sonra, kullanıcılar pencere durumunu değiştirmek için pencerenin başlık çubuğundaki simge durumuna getirin, en üst düzeye çıkarabilir ve düğmeleri geri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="5b293-300">Pencere Görünümü</span><span class="sxs-lookup"><span data-stu-id="5b293-300">Window Appearance</span></span>  
 <span data-ttu-id="5b293-301">Düğmeler, etiketler ve metin kutuları gibi pencereye özgü içerik ekleyerek pencerenin istemci alanının görünümünü değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="5b293-302">İstemci olmayan alanı yapılandırmak için, <xref:System.Windows.Window> bir <xref:System.Windows.Window.Icon%2A> pencere simgesini ayarlamak <xref:System.Windows.Window.Title%2A> ve başlığını ayarlamak için dahil olmak üzere çeşitli özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="5b293-303">Ayrıca, pencerenin yeniden boyutlandırma modunu, pencere stilini ve masaüstü görev çubuğunda bir düğme olarak görünüp görünmediğini yapılandırarak istemci olmayan alan kenarlığı görünümünü ve davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="5b293-304">Modu Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="5b293-304">Resize Mode</span></span>  
 <span data-ttu-id="5b293-305"><xref:System.Windows.Window.WindowStyle%2A> Özelliğine bağlı olarak, kullanıcıların pencereyi nasıl (ve varsa) nasıl yeniden boyutlandırabileceğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="5b293-306">Pencere stili seçimi, kullanıcının kenarlığını fareyle sürükleyerek pencereyi yeniden boyutlandırıp yeniden boyutlandıramayacağını, **Simge durumuna küçült,** Üst **düzeye çıkar**ve yeniden **boyutlandırma** düğmelerinin istemci olmayan alanda görünüp görünmediğini ve görünürlerse etkin olup olmadıklarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="5b293-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="5b293-307">Aşağıdaki numaralandırma değerlerinden biri olabilecek özelliğini <xref:System.Windows.Window.ResizeMode%2A> ayarlayarak bir pencerenin <xref:System.Windows.ResizeMode> nasıl yeniden boyutlandırılabildiğini yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b293-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="5b293-308"><xref:System.Windows.ResizeMode.CanResize>(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="5b293-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="5b293-309">Olduğu <xref:System.Windows.Window.WindowStyle%2A>gibi, bir pencerenin yeniden boyutlandırma modu nun kullanım ömrü boyunca değişmesi olası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değildir, bu da büyük olasılıkla onu biçimlendirmeden ayarladığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b293-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="5b293-310">Bir pencerenin en üst düzeye çıkarılıp küçültülmediğini, simge <xref:System.Windows.Window.WindowState%2A> durumuna küçültülmediğini veya özelliği inceleyerek geri yüklenip geri yüklenmediğini tespit edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="5b293-311">Pencere Stili</span><span class="sxs-lookup"><span data-stu-id="5b293-311">Window Style</span></span>  
 <span data-ttu-id="5b293-312">Bir pencerenin istemci olmayan alanından açığa çıkan kenarlık çoğu uygulama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5b293-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="5b293-313">Ancak, pencere türüne bağlı olarak farklı sınır türlerine ihtiyaç duyulduğu veya hiç kenarlık gerekmeden gerek olmadığı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="5b293-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="5b293-314">Bir pencerenin ne tür kenarlık aldığını <xref:System.Windows.Window.WindowStyle%2A> denetlemek için, özelliğini <xref:System.Windows.WindowStyle> aşağıdaki numaralandırma değerlerinden biriyle ayarlarsınız:</span><span class="sxs-lookup"><span data-stu-id="5b293-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="5b293-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="5b293-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="5b293-316">Bu pencere stillerinin etkisi aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5b293-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Pencere kenarlığı stillerinin çizimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="5b293-318">Biçimlendirme veya kodu kullanarak ayarlayabilirsiniz; <xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir pencerenin ömrü boyunca değişme olasılığı düşük olduğundan, büyük olasılıkla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanarak yapılandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="5b293-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="5b293-319">Dikdörtgen Olmayan Pencere Stili</span><span class="sxs-lookup"><span data-stu-id="5b293-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="5b293-320">Sahip olmak için izin veren <xref:System.Windows.Window.WindowStyle%2A> sınır stilleri yeterli olmadığı durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="5b293-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="5b293-321">Örneğin, Microsoft Windows Media Player'ın kullandığı gibi dikdörtgen olmayan kenarlıklı bir uygulama oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="5b293-322">Örneğin, aşağıdaki şekilde gösterilen konuşma balonu penceresini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5b293-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Beni Sürükley in yazan bir konuşma kabarcığı penceresi.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="5b293-324">Bu tür bir pencere <xref:System.Windows.Window.WindowStyle%2A> <xref:System.Windows.WindowStyle.None>özelliği ayarlayarak ve saydamlık için <xref:System.Windows.Window> özel destek kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5b293-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="5b293-325">Bu değerler birleşimi, pencerenin tamamen saydam hale getirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b293-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="5b293-326">Bu durumda, pencerenin istemci olmayan alan süslemeleri (Kapat menüsü, Simge durumuna Küçült ve Geri Yükle düğmeleri vb.) kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b293-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="5b293-327">Sonuç olarak, kendi sağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b293-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="5b293-328">Görev Çubuğu Varlığı</span><span class="sxs-lookup"><span data-stu-id="5b293-328">Task Bar Presence</span></span>  

<span data-ttu-id="5b293-329">Pencerenin varsayılan görünümü, aşağıdaki şekilde gösterilen gibi bir görev çubuğu düğmesi içerir:</span><span class="sxs-lookup"><span data-stu-id="5b293-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Görev çubuğu düğmesi olan bir pencereyi gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="5b293-331">Bazı pencere türlerinin ileti kutuları ve iletişim kutuları gibi görev çubuğu düğmesi yoktur (bkz. [İletişim Kutuları Genel Bakış).](dialog-boxes-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5b293-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="5b293-332">Pencere için görev çubuğu düğmesinin <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği (varsayılan`true` olarak) ayarlayarak gösterip gösterilmediğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b293-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="5b293-333">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="5b293-333">Security Considerations</span></span>  
 <span data-ttu-id="5b293-334"><xref:System.Windows.Window>anlık `UnmanagedCode` olarak güvenlik izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b293-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="5b293-335">Yerel makineye yüklenen ve başlatılan uygulamalar için bu, uygulamaya verilen izinler kümesiiçinde yer eder.</span><span class="sxs-lookup"><span data-stu-id="5b293-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="5b293-336">Ancak bu, ClickOnce kullanarak Internet veya Yerel intranet bölgesinden başlatılan uygulamalara verilen izinler kümesinin dışında kalır.</span><span class="sxs-lookup"><span data-stu-id="5b293-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="5b293-337">Sonuç olarak, kullanıcılar bir ClickOnce güvenlik uyarısı alır ve uygulama için izin kümesini tam güvene yükseltmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b293-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="5b293-338">Ayrıca, XBAP'lar varsayılan olarak pencereleri veya iletişim kutularını gösteremez.</span><span class="sxs-lookup"><span data-stu-id="5b293-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="5b293-339">Bağımsız uygulama güvenliği yle ilgili bir tartışma için [WPF Güvenlik Stratejisi - Platform Güvenliği'ne](../wpf-security-strategy-platform-security.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5b293-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="5b293-340">Diğer Windows Türleri</span><span class="sxs-lookup"><span data-stu-id="5b293-340">Other Types of Windows</span></span>  
 <span data-ttu-id="5b293-341"><xref:System.Windows.Navigation.NavigationWindow>gezilebilir içeriği barındırmak için tasarlanmış bir penceredir.</span><span class="sxs-lookup"><span data-stu-id="5b293-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="5b293-342">Daha fazla bilgi için [Gezintiye Genel Bakış'a](navigation-overview.md)bakın).</span><span class="sxs-lookup"><span data-stu-id="5b293-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="5b293-343">İletişim kutuları, bir işlevi tamamlamak için genellikle kullanıcıdan bilgi toplamak için kullanılan pencerelerdir.</span><span class="sxs-lookup"><span data-stu-id="5b293-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="5b293-344">Örneğin, bir kullanıcı bir dosyayı açmak istediğinde, **Dosyayı Aç** iletişim kutusu genellikle dosya adını kullanıcıdan almak için bir uygulama tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5b293-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="5b293-345">Daha fazla bilgi için İletişim [Kutularına Genel Bakış'a](dialog-boxes-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5b293-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b293-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b293-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="5b293-347">İletişim Kutularına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5b293-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="5b293-348">WPF Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="5b293-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
