---
title: WPF Windows'a Genel Bakış
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
ms.openlocfilehash: c3bd76c893c2055f94e321e9c888848d344efa15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166939"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="34cdb-102">WPF Windows'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34cdb-102">WPF Windows Overview</span></span>
<span data-ttu-id="34cdb-103">Kullanıcılar, Windows Presentation Foundation (WPF) tek başına uygulamalar windows aracılığıyla etkileşim.</span><span class="sxs-lookup"><span data-stu-id="34cdb-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="34cdb-104">Birincil amacı bir pencere, verileri görselleştiren ve verilerle etkileşimde bulunmak kullanıcıların sağlayan konak içerik sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="34cdb-105">Tek başına [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları kullanarak kendi windows sağlamak <xref:System.Windows.Window> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34cdb-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="34cdb-106">Bu konu tanıtır <xref:System.Windows.Window> oluşturma ve yönetme windows tek başına uygulamalarda temellerini kapsayan önce.</span><span class="sxs-lookup"><span data-stu-id="34cdb-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-107">Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi uygulamaları [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfaları, kendi windows sağlamadığınızdan.</span><span class="sxs-lookup"><span data-stu-id="34cdb-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="34cdb-108">Windows tarafından sağlanan bunun yerine barındırılan [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34cdb-108">Instead, they are hosted in windows provided by [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span></span> <span data-ttu-id="34cdb-109">Bkz: [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34cdb-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="34cdb-110">Pencere sınıfı</span><span class="sxs-lookup"><span data-stu-id="34cdb-110">The Window Class</span></span>  
 <span data-ttu-id="34cdb-111">Aşağıdaki şekilde, pencerenin oluşturan parçaları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Pencere öğeleri gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="34cdb-113">Bir pencere iki alana ayrılır: istemci alanını ve istemci dışı alan.</span><span class="sxs-lookup"><span data-stu-id="34cdb-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="34cdb-114">*İstemci dışı alan* bir pencerenin tarafından uygulanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve aşağıdakiler dahil olmak üzere çoğu windows için ortak olan bir pencere bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
-   <span data-ttu-id="34cdb-115">Bir sınırı.</span><span class="sxs-lookup"><span data-stu-id="34cdb-115">A border.</span></span>  
  
-   <span data-ttu-id="34cdb-116">Başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="34cdb-116">A title bar.</span></span>  
  
-   <span data-ttu-id="34cdb-117">Bir simge.</span><span class="sxs-lookup"><span data-stu-id="34cdb-117">An icon.</span></span>  
  
-   <span data-ttu-id="34cdb-118">Simge Durumuna Küçült, Ekranı Kapla ve düğmeler geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="34cdb-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
-   <span data-ttu-id="34cdb-119">Bir Kapat düğmesi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-119">A Close button.</span></span>  
  
-   <span data-ttu-id="34cdb-120">En aza indirmek, kullanıcıların menü öğeleri ile bir sistem menüsünü en üst düzeye çıkarmak, geri yükleme, taşıma, yeniden boyutlandırma ve bir penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="34cdb-121">*İstemci alanını* bir pencerenin alanın bir pencerenin istemci olmayan alanda ve geliştiriciler tarafından menü çubukları, araç çubuklarını ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="34cdb-122">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir pencere yalıtılan <xref:System.Windows.Window> aşağıdakileri yapmak için kullandığınız sınıfı:</span><span class="sxs-lookup"><span data-stu-id="34cdb-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
-   <span data-ttu-id="34cdb-123">Bir pencere görüntüler.</span><span class="sxs-lookup"><span data-stu-id="34cdb-123">Display a window.</span></span>  
  
-   <span data-ttu-id="34cdb-124">Boyutunu, konumunu ve görünüm penceresinin yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-124">Configure the size, position, and appearance of a window.</span></span>  
  
-   <span data-ttu-id="34cdb-125">Uygulamaya özgü içerik barındırın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-125">Host application-specific content.</span></span>  
  
-   <span data-ttu-id="34cdb-126">Bir pencere ömrünü yönetmek.</span><span class="sxs-lookup"><span data-stu-id="34cdb-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="34cdb-127">Pencere uygulama</span><span class="sxs-lookup"><span data-stu-id="34cdb-127">Implementing a Window</span></span>  
 <span data-ttu-id="34cdb-128">Hem görünümünü ve davranışını, uygulama normal bir pencerenin oluşur burada *Görünüm* pencere kullanıcılara nasıl göründüğünü tanımlar ve *davranışı* pencere işlevleri kullanıcıların etkileşimli olarak biçimini tanımlar kendisiyle.</span><span class="sxs-lookup"><span data-stu-id="34cdb-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="34cdb-129">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]görünümünü uygulayabilir ve penceresini kullanarak bir davranış veya kod veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="34cdb-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="34cdb-130">Genel olarak, ancak pencerenin görünümünü kullanılarak uygulanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve davranışını gerçekleştirilen arka plan, kod kullanarak aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="34cdb-131">Etkinleştirmek için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme dosyasının ve birlikte çalışması için arka plan kod dosyası, aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
-   <span data-ttu-id="34cdb-132">Biçimlendirme içinde `Window` öğesi içermelidir `x:Class` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="34cdb-133">Ne zaman uygulama oluşturulduğuna göre varlığını `x:Class` işaretlemede dosyası oluşturulmamasını [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] oluşturmak için bir `partial` türetilen sınıf <xref:System.Windows.Window> ve tarafından belirtilen ada sahip `x:Class` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-133">When the application is built, the existence of `x:Class` in the markup file causes [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="34cdb-134">Bu eklenmesini gerektiren bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildirimi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span><span class="sxs-lookup"><span data-stu-id="34cdb-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="34cdb-135">Oluşturulan `partial` sınıfının Implements `InitializeComponent` olaylarını kaydetmek ve işaretlemede uygulanan özellikleri ayarlamak için çağrılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="34cdb-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
-   <span data-ttu-id="34cdb-136">Arka plan, kod sınıfı olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` biçimlendirme ve bu öznitelikte türetilmesi gereken <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="34cdb-137">Bu arka plan kod dosyası ile ilişkili olmasını sağlar `partial` uygulama oluşturulduğunda işaretleme dosyasının için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="34cdb-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
-   <span data-ttu-id="34cdb-138">Arka plan, kod içinde <xref:System.Windows.Window> sınıfı çağıran bir oluşturucu uygulanmalı `InitializeComponent` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> `InitializeComponent` <span data-ttu-id="34cdb-139">uygulanan tarafından işaretleme dosyasının üretilmiş `partial` olaylarını kaydetmek ve biçimlendirme içinde tanımlanan özelliklerini ayarlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="34cdb-139">is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-140">Yeni bir eklediğinizde <xref:System.Windows.Window> kullanarak projenize [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> biçimlendirme hem de arka plan kod kullanılarak uygulanır ve işaretleme ve arka plan kod dosyaları arasındaki ilişki oluşturmak için gerekli yapılandırmayı içerir burada açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="34cdb-141">Bu yapılandırmayla yerinde penceresinde görünümünü tanımlama üzerinde odaklanabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve kod arkasında davranışını uygulama.</span><span class="sxs-lookup"><span data-stu-id="34cdb-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="34cdb-142">Aşağıdaki örnek, uygulanan bir düğme içeren bir pencere gösterir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve düğme için bir olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kod arkasında uygulanan olayı.</span><span class="sxs-lookup"><span data-stu-id="34cdb-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="34cdb-143">MSBuild için bir pencere tanımını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34cdb-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="34cdb-144">Pencereniz nasıl uygulayacağınıza nasıl için yapılandırıldığını belirler [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34cdb-144">How you implement your window determines how it is configured for [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span></span> <span data-ttu-id="34cdb-145">Her ikisini de kullanarak tanımlanan pencere [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve arka plan kod:</span><span class="sxs-lookup"><span data-stu-id="34cdb-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="34cdb-146">Biçimlendirme dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="34cdb-146">markup files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items.</span></span>  
  
-   <span data-ttu-id="34cdb-147">Arka plan kod dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="34cdb-147">Code-behind files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` items.</span></span>  
  
 <span data-ttu-id="34cdb-148">Aşağıda gösterilen [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="34cdb-148">This is shown in the following [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="34cdb-149">Yapı hakkında bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları, [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="34cdb-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="34cdb-150">Yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="34cdb-150">Window Lifetime</span></span>  
 <span data-ttu-id="34cdb-151">Herhangi bir sınıf bir pencere ilk örneği oluşturulduğunda başlayan bir ömrü olduğu gibi sonra açıldı, etkinleştirilir ve devre dışı bırakıldı ve sonunda kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="34cdb-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="34cdb-152">Bir penceresini açma</span><span class="sxs-lookup"><span data-stu-id="34cdb-152">Opening a Window</span></span>  
 <span data-ttu-id="34cdb-153">Bir pencere açmak için önce aşağıdaki örnekte gösterildiği bir örneği, oluşturun.</span><span class="sxs-lookup"><span data-stu-id="34cdb-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="34cdb-154">Bu örnekte, `MarkupAndCodeBehindWindow` örneği uygulama başladığında gerçekleştiği zaman <xref:System.Windows.Application.Startup> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="34cdb-155">Bir pencere örneği oluşturulduğunda, ona bir başvuru tarafından yönetilen windows listesine otomatik olarak eklenir <xref:System.Windows.Application> nesne (bkz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="34cdb-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="34cdb-156">Ayrıca, oluşturulacak ilk penceresi varsayılan olarak ayarlanır <xref:System.Windows.Application> ana uygulama penceresini olarak (bkz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="34cdb-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="34cdb-157">Pencere, son olarak çağırarak açılırsa <xref:System.Windows.Window.Show%2A> yöntemi; sonuç aşağıdaki şekilde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Window.Show çağırarak bir pencere açılır](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="34cdb-159">Çağırarak açılan bir pencere <xref:System.Windows.Window.Show%2A> uygulama kullanıcıların diğer windows aynı uygulama etkinleştirmesine izin veren bir modunda çalıştığı anlamına gelir bir geçici pencere.</span><span class="sxs-lookup"><span data-stu-id="34cdb-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> <span data-ttu-id="34cdb-160">iletişim kutuları gibi Windows kalıcı olarak açmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-160">is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="34cdb-161">Bkz: [iletişim kutularına genel bakış](dialog-boxes-overview.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="34cdb-162">Zaman <xref:System.Windows.Window.Show%2A> olan kullanıcı girişi almasına izin veren altyapı kurabilmek için gösterilmeden önce çağırılır, bir pencere başlatma işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="34cdb-163">Pencerenin başlatıldığında <xref:System.Windows.Window.SourceInitialized> olayı oluşturulur ve penceresi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="34cdb-164">Bir kısayol olarak <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılır pencere ilk belirtmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="34cdb-165">Uygulama başlatıldığında, değeri tarafından belirtilen pencere <xref:System.Windows.Application.StartupUri%2A> açıldığında modelessly; dahili olarak, pencerenin çağırarak açıldığında, <xref:System.Windows.Window.Show%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="34cdb-166">Pencere sahipliği</span><span class="sxs-lookup"><span data-stu-id="34cdb-166">Window Ownership</span></span>  
 <span data-ttu-id="34cdb-167">Kullanılarak açılan bir pencere <xref:System.Windows.Window.Show%2A> yöntemi örtülü bir ilişki oluşturulduğu penceresiyle yok; kullanıcılar, yani herhangi bir pencereye aşağıdaki işlemleri yapabilirsiniz ya da penceresiyle birbirinden, etkileşim kurabilir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
-   <span data-ttu-id="34cdb-168">Diğer kapsar (windows birine sahip olmadığı sürece, <xref:System.Windows.Window.Topmost%2A> özelliğini `true`).</span><span class="sxs-lookup"><span data-stu-id="34cdb-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
-   <span data-ttu-id="34cdb-169">, Diğer planı etkilemeden ekranı kaplamış ve geri yüklenen küçültülmesine.</span><span class="sxs-lookup"><span data-stu-id="34cdb-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="34cdb-170">Bazı windows bunları açılır penceresi ile bir ilişki gerektirir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="34cdb-171">Örneğin, bir [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] özelliği windows ve araç pencerelerini, normal davranış kendilerini oluşturan pencerenin kapsar, uygulamayı açmak.</span><span class="sxs-lookup"><span data-stu-id="34cdb-171">For example, an [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="34cdb-172">Ayrıca, gibi windows her zaman kapatın, en aza indirmek, en üst düzeye çıkarmak ve IPP penceresiyle oluşturuldukları geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="34cdb-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="34cdb-173">Bir pencere yaparak tür bir ilişkiye kurulabilir *kendi* başka bir ve ayarlayarak elde <xref:System.Windows.Window.Owner%2A> özelliği *penceresi ait* başvurusuyla *sahibi Pencere*.</span><span class="sxs-lookup"><span data-stu-id="34cdb-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="34cdb-174">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="34cdb-175">Sahipliği kurulduktan sonra:</span><span class="sxs-lookup"><span data-stu-id="34cdb-175">After ownership is established:</span></span>  
  
-   <span data-ttu-id="34cdb-176">Sahip olunan pencerenin değerini inceleyerek, sahip penceresine başvurabilirsiniz kendi <xref:System.Windows.Window.Owner%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
-   <span data-ttu-id="34cdb-177">Sahip penceresi sahip değerini inceleyerek windows bulabilir, <xref:System.Windows.Window.OwnedWindows%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="34cdb-178">Pencere etkinleştirme önleme</span><span class="sxs-lookup"><span data-stu-id="34cdb-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="34cdb-179">Burada windows Internet messenger stili uygulamanın konuşma windows ya da bir e-posta uygulamasının bildirim windows gibi gösterilen etkinleştirilmesi gereken olmayan senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="34cdb-180">Uygulamanızın gösterilen etkinleştirilmesi karakteri bir pencere varsa ayarlayabileceğiniz kendi <xref:System.Windows.Window.ShowActivated%2A> özelliğini `false` çağırmadan önce <xref:System.Windows.Window.Show%2A> ilk kez yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="34cdb-181">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="34cdb-181">As a consequence:</span></span>  
  
-   <span data-ttu-id="34cdb-182">Pencerenin etkin değil.</span><span class="sxs-lookup"><span data-stu-id="34cdb-182">The window is not activated.</span></span>  
  
-   <span data-ttu-id="34cdb-183">Pencerenin <xref:System.Windows.Window.Activated> olayı oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
-   <span data-ttu-id="34cdb-184">Etkin pencere etkin olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="34cdb-185">Kullanıcı istemci veya istemci dışı alan tıklayarak etkinleştirir hemen sonra penceresi, ancak etkin hale.</span><span class="sxs-lookup"><span data-stu-id="34cdb-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="34cdb-186">Bu durumda:</span><span class="sxs-lookup"><span data-stu-id="34cdb-186">In this case:</span></span>  
  
-   <span data-ttu-id="34cdb-187">Pencerenin etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-187">The window is activated.</span></span>  
  
-   <span data-ttu-id="34cdb-188">Pencerenin <xref:System.Windows.Window.Activated> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
-   <span data-ttu-id="34cdb-189">Daha önce etkinleştirilmiş penceresi devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-189">The previously activated window is deactivated.</span></span>  
  
-   <span data-ttu-id="34cdb-190">Pencerenin <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayları daha sonra kullanıcı eylemlerine beklendiği gibi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="34cdb-191">Pencere etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="34cdb-191">Window Activation</span></span>  
 <span data-ttu-id="34cdb-192">Bir pencere ilk kez açıldığında etkin pencere olur (ile gösterilen sürece <xref:System.Windows.Window.ShowActivated%2A> kümesine `false`).</span><span class="sxs-lookup"><span data-stu-id="34cdb-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="34cdb-193">*Etkin pencere* tuş vuruşlarını ve fare tıklama gibi kullanıcı girişi şu anda yakaladığı penceredir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="34cdb-194">Bir pencere etkin olduğunda bilmemektedir <xref:System.Windows.Window.Activated> olay.</span><span class="sxs-lookup"><span data-stu-id="34cdb-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-195">Bir pencere ilk kez açıldığında <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.Window.ContentRendered> olayları yalnızca sonra oluştuğunda <xref:System.Windows.Window.Activated> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="34cdb-196">Bunu göz önünde bir pencere etkili bir şekilde açıldığında kabul edilebilir <xref:System.Windows.Window.ContentRendered> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="34cdb-197">Bir pencere etkin olduktan sonra bir kullanıcı aynı uygulamada başka bir pencere etkinleştirmek veya başka bir uygulamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="34cdb-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="34cdb-198">Bu durum oluştuğunda, şu andaki etkin pencere devre dışı olur ve başlatır <xref:System.Windows.Window.Deactivated> olay.</span><span class="sxs-lookup"><span data-stu-id="34cdb-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="34cdb-199">Kullanıcı şu anda devre dışı bırakılmış bir pencere seçtiğinde, benzer şekilde, pencereyi tekrar etkin hale gelir ve <xref:System.Windows.Window.Activated> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="34cdb-200">İşlemek için yaygın nedenlerinden biri <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> etkinleştirmek ve bir pencere etkin olduğunda, yalnızca çalıştırabilirsiniz işlevini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="34cdb-201">Örneğin, bazı windows sabit kullanıcı girişini veya oyun ve video oynatıcılar dahil olmak üzere, dikkat gerektiren etkileşimli içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="34cdb-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="34cdb-202">Aşağıdaki örnek, üstesinden nasıl gelineceğini gösterir basitleştirilmiş bir video oynatıcı <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> bu davranışı uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="34cdb-203">Bir pencere devre dışı bırakıldığında diğer uygulama türleri arka planda kod yine de çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="34cdb-204">Örneğin, bir posta istemcisi posta sunucusu kullanıcı diğer uygulamaları kullanırken yoklama devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="34cdb-205">Ana pencereyi devre dışı durumdayken bunlar gibi uygulamalar genellikle farklı veya ek davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="34cdb-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="34cdb-206">Posta program göre bu gelen kutunuza yeni posta öğe ekleme ve bir bildirim simgesi sistem tepsisine ekleme anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="34cdb-207">Posta pencerenin inceleyerek belirlenen etkin değilken, bir bildirim simgesi yalnızca görüntülenmesi <xref:System.Windows.Window.IsActive%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="34cdb-208">Çağırarak daha Acil kullanıcıya bildirmek bir pencere bir arka plan görevi tamamlanırsa isteyebilirsiniz <xref:System.Windows.Window.Activate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="34cdb-209">Kullanıcı ile etkileşim kurma, başka bir uygulamanın ne zaman etkin <xref:System.Windows.Window.Activate%2A> , pencerenin görev çubuğu düğmesinin yanıp çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="34cdb-210">Bir kullanıcının geçerli uygulamayla etkileşim kurma, çağırma <xref:System.Windows.Window.Activate%2A> penceresini öne getirmek.</span><span class="sxs-lookup"><span data-stu-id="34cdb-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-211">Uygulama kapsamı etkinleştirme kullanarak işleyebilir <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olayları.</span><span class="sxs-lookup"><span data-stu-id="34cdb-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="34cdb-212">Bir pencereyi kapatma</span><span class="sxs-lookup"><span data-stu-id="34cdb-212">Closing a Window</span></span>  
 <span data-ttu-id="34cdb-213">Bir pencere kullanıcı kapattığında sona yakında başlar.</span><span class="sxs-lookup"><span data-stu-id="34cdb-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="34cdb-214">Bir pencere aşağıdakiler dahil olmak üzere istemci olmayan alanda öğe kullanarak kapalı olabilir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
-   <span data-ttu-id="34cdb-215">**Kapat** öğesi **sistem** menüsü.</span><span class="sxs-lookup"><span data-stu-id="34cdb-215">The **Close** item of the **System** menu.</span></span>  
  
-   <span data-ttu-id="34cdb-216">ALT + F4 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-216">Pressing ALT+F4.</span></span>  
  
-   <span data-ttu-id="34cdb-217">Tuşuna basarak **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="34cdb-218">Bir pencereyi kapatmak için istemci alanını ek mekanizmalarına biri daha fazla ortak şunlardır sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34cdb-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
-   <span data-ttu-id="34cdb-219">Bir **çıkış** öğesi **dosya** menüsünde, genellikle ana uygulama windows için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
-   <span data-ttu-id="34cdb-220">A **Kapat** öğesi **dosya** menüsünde, genellikle ikincil uygulama penceresi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
-   <span data-ttu-id="34cdb-221">A **iptal** düğmesi, genellikle kalıcı bir iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="34cdb-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
-   <span data-ttu-id="34cdb-222">A **Kapat** düğmesi, genellikle modsuz iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="34cdb-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="34cdb-223">Yanıt olarak özel Bu mekanizmaların birini pencereyi kapatmak için çağırmak gereken <xref:System.Windows.Window.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34cdb-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="34cdb-224">Aşağıdaki örnek seçerek bir pencereyi özelliği uygulayan **çıkış** üzerinde **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="34cdb-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="34cdb-225">Bir pencere kapandığında iki olaylar oluşur: <xref:System.Windows.Window.Closing> ve <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <xref:System.Windows.Window.Closing> <span data-ttu-id="34cdb-226">pencereyi kapatır ve hangi penceresi kapatma engellenebilir bir mekanizma sağlar önce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-226">is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="34cdb-227">Pencerenin kapatılmasını engelleyecek yaygın nedenlerinden biri, pencere içeriğinin değiştirilen veri içeriyorsa, ' dir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="34cdb-228">Bu durumda <xref:System.Windows.Window.Closing> olay verileri olumsuz olup olmadığını ve bu durumda, kullanıcı verileri kaydetmeden pencereyi kapatma ya da devam mı, yoksa pencerenin kapatılmasını engelleyecek şekilde sormak belirlemek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="34cdb-229">Aşağıdaki örnek, işleme önemli yönlerini gösterir <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="34cdb-230"><xref:System.Windows.Window.Closing> Olay işleyicisine geçirilen bir <xref:System.ComponentModel.CancelEventArgs>, uygulayan `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ayarlamak için özellik `true` pencere kapatılmasını engelleyecek.</span><span class="sxs-lookup"><span data-stu-id="34cdb-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="34cdb-231">Varsa <xref:System.Windows.Window.Closing> işlenmiyor, veya ele ancak iptal, pencere kapanacaktır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="34cdb-232">Yalnızca bir pencere gerçekten kapanmadan önce <xref:System.Windows.Window.Closed> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="34cdb-233">Bu noktada, bir pencere kapatmaktan men önlenemeyen.</span><span class="sxs-lookup"><span data-stu-id="34cdb-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-234">Bir uygulamayı otomatik olarak ana uygulama penceresini kapattığı zaman kapatmak için yapılandırılabilir (bkz <xref:System.Windows.Application.MainWindow%2A>) veya son pencereyi kapatır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="34cdb-235">Ayrıntılar için bkz <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="34cdb-236">Bir pencere açıkça istemci olmayan ve istemci bölümlerinde sağlanan mekanizmaları yoluyla kapatılabilir, ancak pencere örtük olarak davranışını uygulamanın diğer kısımlarını sonucunda kapatılabilir veya [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], aşağıdakiler dahil:</span><span class="sxs-lookup"><span data-stu-id="34cdb-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], including the following:</span></span>  
  
-   <span data-ttu-id="34cdb-237">Bir kullanıcı oturumu sonlandırdığında veya Windows kapatır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-237">A user logs off or shuts down Windows.</span></span>  
  
-   <span data-ttu-id="34cdb-238">Bir pencerenin sahibini kapatır (bkz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="34cdb-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
-   <span data-ttu-id="34cdb-239">Ana uygulama penceresi kapatıldığında ve <xref:System.Windows.Application.ShutdownMode%2A> olduğu <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
-   <xref:System.Windows.Application.Shutdown%2A> <span data-ttu-id="34cdb-240">çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-240">is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-241">Pencere kapatılır sonra açılamaz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="34cdb-242">Pencere ömür olayları</span><span class="sxs-lookup"><span data-stu-id="34cdb-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="34cdb-243">Aşağıdaki çizimde, pencerenin yaşam süresi asıl olayların sırasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Bir pencerenin yaşam süresi olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="34cdb-245">Aşağıdaki çizimde asıl olayların sırası etkinleştirme gösterilen bir pencere ömrü gösterir (<xref:System.Windows.Window.ShowActivated%2A> ayarlanır `false` pencere gösterilmeden önce):</span><span class="sxs-lookup"><span data-stu-id="34cdb-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Bir pencerenin etkin kalma süresi olmadan etkinleştirme olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="34cdb-247">Pencere konumu</span><span class="sxs-lookup"><span data-stu-id="34cdb-247">Window Location</span></span>  
 <span data-ttu-id="34cdb-248">Bir penceresi açıkken, x ve y konumu sahip boyutlarına göre Masaüstü.</span><span class="sxs-lookup"><span data-stu-id="34cdb-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="34cdb-249">Bu konum, inceleyerek belirlenebilir <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="34cdb-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="34cdb-250">Pencerenin konumunu değiştirmek için bu özellikleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="34cdb-251">İlk konumunu belirtebilirsiniz bir <xref:System.Windows.Window> zaman ilk göründüğü ayarlayarak <xref:System.Windows.Window.WindowStartupLocation%2A> aşağıdakilerden birini özelliğiyle <xref:System.Windows.WindowStartupLocation> sabit listesi değerleri:</span><span class="sxs-lookup"><span data-stu-id="34cdb-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> <span data-ttu-id="34cdb-252">(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="34cdb-252">(default)</span></span>  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="34cdb-253">Başlangıç konumu olarak belirtilmişse <xref:System.Windows.WindowStartupLocation.Manual>ve <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> değil ayarlandığını, <xref:System.Windows.Window> görünmesini Windows için bir konum ister.</span><span class="sxs-lookup"><span data-stu-id="34cdb-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="34cdb-254">En üstteki Windows ve Z düzeni</span><span class="sxs-lookup"><span data-stu-id="34cdb-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="34cdb-255">X ve y konumu, bir pencere ayrıca sahip olmanın yanı sıra diğer windows göre dikey konumunu belirler z boyutundaki bir konum vardır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="34cdb-256">Bu pencerenin z düzeni bilinir ve iki tür vardır: normal z düzenini ve en üst z düzeni.</span><span class="sxs-lookup"><span data-stu-id="34cdb-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="34cdb-257">Pencerenin konumu *normal z düzenini* , şu anda etkin olup olmamasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="34cdb-258">Varsayılan olarak, bir pencere normal z düzeninde bulunur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="34cdb-259">Pencerenin konumu *üstteki z düzenini* Ayrıca, şu anda etkin olup olmamasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="34cdb-260">Ayrıca, en üst z düzeninde windows her zaman windows normal z düzeninde üstünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="34cdb-261">Bir pencere ayarlayarak en üst z düzeninde bulunan kendi <xref:System.Windows.Window.Topmost%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="34cdb-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="34cdb-262">Her z düzenini içinde şu andaki etkin pencere tüm diğer pencerelerin aynı z düzeninde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="34cdb-263">Pencere boyutu</span><span class="sxs-lookup"><span data-stu-id="34cdb-263">Window Size</span></span>  
 <span data-ttu-id="34cdb-264">Bir masaüstü konuma sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve yükseklik özellikleri dahil olmak üzere çeşitli özellikler tarafından belirlenen bir boyutu vardır ve <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A><span data-ttu-id="34cdb-265">, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> pencere yaşam süresi boyunca olabilir ve aşağıdaki örnekte gösterildiği gibi yapılandırılmış genişlikleri aralığını yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-265">, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="34cdb-266">Pencere yüksekliği yönetilir <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve aşağıdaki örnekte gösterilen şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="34cdb-267">Çeşitli genişliği değerlerini ve yükseklik değerleri aralığını belirtmek için herhangi bir ilgili boyut için belirtilen aralıkta olacak şekilde yeniden boyutlandırılabilir pencere yüksekliğini ve genişliğini mümkündür.</span><span class="sxs-lookup"><span data-stu-id="34cdb-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="34cdb-268">Geçerli genişlik ve yükseklik algılamak için inceleyin <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="34cdb-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="34cdb-269">Genişlik ve yükseklik pencerenizin isterseniz penceresi boyutuna en uygun bir boyut için içerik, kullanabileceğiniz <xref:System.Windows.Window.SizeToContent%2A> özelliği aşağıdaki değerlere sahip:</span><span class="sxs-lookup"><span data-stu-id="34cdb-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
-   <xref:System.Windows.SizeToContent.Manual><span data-ttu-id="34cdb-270">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-270">.</span></span> <span data-ttu-id="34cdb-271">Etki yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="34cdb-271">No effect (default).</span></span>  
  
-   <xref:System.Windows.SizeToContent.Width><span data-ttu-id="34cdb-272">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-272">.</span></span> <span data-ttu-id="34cdb-273">Her ikisi de ayarını aynı etkiye sahip içerik genişliği Sığdır <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.</span><span class="sxs-lookup"><span data-stu-id="34cdb-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
-   <xref:System.Windows.SizeToContent.Height><span data-ttu-id="34cdb-274">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-274">.</span></span> <span data-ttu-id="34cdb-275">Her ikisi de ayarını aynı etkiye sahip içerik yüksekliği Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> yüksekliğine içeriği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight><span data-ttu-id="34cdb-276">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-276">.</span></span> <span data-ttu-id="34cdb-277">İçerik genişliği ve her ikisi de ayarı aynı etkiye sahip yüksekliği Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> içeriği ve ayarı hem yüksekliğine <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.</span><span class="sxs-lookup"><span data-stu-id="34cdb-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="34cdb-278">Aşağıdaki örnek bir pencere otomatik olarak ilk göründüğü içeriğini, dikey ve yatay olarak, uygun boyutları gösterir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="34cdb-279">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Window.SizeToContent%2A> kod nasıl bir içeriği sığdırmak için yeniden boyutlandırır belirtmek için bir özellik.</span><span class="sxs-lookup"><span data-stu-id="34cdb-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="34cdb-280">Boyutlandırma özelliklerini için öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="34cdb-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="34cdb-281">Aslında, genişlik ve yükseklik yeniden boyutlandırılabilir pencere aralığını tanımlamak için bir pencere çeşitli boyutlarda özelliklerini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="34cdb-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="34cdb-282">Geçerli bir aralık korunduğu emin olmak için <xref:System.Windows.Window> öncelik aşağıdaki sıralardan kullanarak boyutu özelliklerin değerlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 **<span data-ttu-id="34cdb-283">Yükseklik özellikleri için:</span><span class="sxs-lookup"><span data-stu-id="34cdb-283">For Height Properties:</span></span>**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **<span data-ttu-id="34cdb-284">Genişlik özellikleri için:</span><span class="sxs-lookup"><span data-stu-id="34cdb-284">For Width Properties:</span></span>**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="34cdb-285">Bu, ile yönetilen büyütüldüğünde öncelik sırasını pencere boyutunu da belirleyebilirsiniz <xref:System.Windows.Window.WindowState%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="34cdb-286">Pencere durumu</span><span class="sxs-lookup"><span data-stu-id="34cdb-286">Window State</span></span>  
 <span data-ttu-id="34cdb-287">Yeniden boyutlandırılabilir bir pencere ömrü boyunca üç duruma sahip olabilir: normal, küçültülmüş ve ekranı.</span><span class="sxs-lookup"><span data-stu-id="34cdb-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="34cdb-288">Bir pencere bir *normal* pencere varsayılan durumuna bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="34cdb-289">Bu durum içeren bir pencere, taşıma ve yeniden boyutlandırılabilir ise boyutlandırma tutamacı ya da kenarlığını kullanarak yeniden boyutlandırın açmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="34cdb-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="34cdb-290">İçeren bir pencere bir *simge durumuna küçültülmüş* durumu varsa, görev çubuğu düğmesinin için daraltır <xref:System.Windows.Window.ShowInTaskbar%2A> ayarlanır `true`; Aksi takdirde, olabilir ve masaüstünde sol alt köşesindeki kendisi yeniden yerleştirir en küçük olası boyuta daraltır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="34cdb-291">Ne tür simge durumuna küçültülmüş pencerenin kenarlık kullanarak yeniden boyutlandırılabilir veya masaüstü görev çubuğuna gösterilmeyen bir simge durumuna küçültülmüş pencereyi sürüklenebilir rağmen tutamacı, yeniden boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="34cdb-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="34cdb-292">Bir pencere bir *ekranı* durumu genişletilir yalnızca büyüklüğünde olur en fazla boyutu olabilir, kendi <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.Window.SizeToContent%2A> özellikleri dikte.</span><span class="sxs-lookup"><span data-stu-id="34cdb-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="34cdb-293">Bir simge durumuna küçültülmüş pencereyi gibi kaplamış boyutlandırma tutamacı kullanarak veya kenarlığı sürükleyerek yeniden boyutlandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="34cdb-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34cdb-294">Değerlerini <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A> penceresinin özellikler veya olsa bile pencere şu anda ekranı simge durumuna küçültülmüş normal durumu değerlerini her zaman gösterir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="34cdb-295">Bir pencerenin durumunu ayarlanarak yapılandırılabilir kendi <xref:System.Windows.Window.WindowState%2A> aşağıdakilerden biri olabilir özelliği <xref:System.Windows.WindowState> sabit listesi değerleri:</span><span class="sxs-lookup"><span data-stu-id="34cdb-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
-   <xref:System.Windows.WindowState.Normal> <span data-ttu-id="34cdb-296">(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="34cdb-296">(default)</span></span>  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="34cdb-297">Aşağıdaki örnek, açıldığında, tam ekran olarak gösterilen bir pencere oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="34cdb-298">Genel olarak, ayarlamalısınız <xref:System.Windows.Window.WindowState%2A> bir pencerenin başlangıç durumunu yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="34cdb-299">Yeniden boyutlandırılabilir penceresinde gösterilen sonra kullanıcılar simge durumuna küçült tuşuna basın, en üst düzeye çıkarmak ve pencere durumu değiştirmek için pencerenin başlık çubuğundaki düğmelere geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="34cdb-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="34cdb-300">Görünüm penceresi</span><span class="sxs-lookup"><span data-stu-id="34cdb-300">Window Appearance</span></span>  
 <span data-ttu-id="34cdb-301">Bir pencerenin istemci alanının görünümü, penceresine özgü içerik, düğmeler, etiketler ve metin kutuları gibi ekleyerek değiştirin.</span><span class="sxs-lookup"><span data-stu-id="34cdb-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="34cdb-302">İstemci olmayan alanın yapılandırmak için <xref:System.Windows.Window> dahil çeşitli özellikler sağlar <xref:System.Windows.Window.Icon%2A> bir pencerenin simgesini ve <xref:System.Windows.Window.Title%2A> başlığını ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="34cdb-303">Bir pencerenin yeniden boyutlandırma modu, pencere stili yapılandırarak istemci dışı alan kenarlık davranışını ve görünümünü de değiştirebilirsiniz ve masaüstü görev çubuğuna bir düğme olarak görülüyor.</span><span class="sxs-lookup"><span data-stu-id="34cdb-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="34cdb-304">Modu yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="34cdb-304">Resize Mode</span></span>  
 <span data-ttu-id="34cdb-305">Yapılandırmanıza bağlı olarak <xref:System.Windows.Window.WindowStyle%2A> özelliğini denetleyebilirsiniz nasıl (ve eğer) kullanıcılar penceresini yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="34cdb-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="34cdb-306">Bir kullanıcı olup olmadığını kenarlığını fare ile sürükleyerek pencereyi boyutlandırabilirsiniz olmadığını styl okna seçimi etkiler **simge durumuna küçült**, **Ekranı Kapla**, ve **yeniden boyutlandırma** düğmeleri İstemci olmayan alanın görünür ve görünüyorlarsa, bunlar etkinleştirilip etkinleştirilmediği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="34cdb-307">Nasıl bir pencereyi yeniden boyutlandırır ayarlayarak yapılandırabilirsiniz, <xref:System.Windows.Window.ResizeMode%2A> aşağıdakilerden biri olabilir özelliği <xref:System.Windows.ResizeMode> sabit listesi değerleri:</span><span class="sxs-lookup"><span data-stu-id="34cdb-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> <span data-ttu-id="34cdb-308">(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="34cdb-308">(default)</span></span>  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="34cdb-309">Olduğu gibi <xref:System.Windows.Window.WindowStyle%2A>, yeniden boyutlandırma modunu pencerenin, büyük olasılıkla ondan ayarlarsınız, yani ömrü boyunca değişme olasılığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="34cdb-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="34cdb-310">Bir pencere ekranı olup olmadığını algılayan Not küçültülebilir ya da inceleyerek geri <xref:System.Windows.Window.WindowState%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34cdb-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="34cdb-311">Pencere stili</span><span class="sxs-lookup"><span data-stu-id="34cdb-311">Window Style</span></span>  
 <span data-ttu-id="34cdb-312">Bir pencerenin istemci olmayan alanından sunulur kenarlık, çoğu uygulama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="34cdb-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="34cdb-313">Ancak, nerede farklı kenarlık türü gereklidir veya hiçbir kenarlık penceresi türüne bağlı olarak, gerekli koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="34cdb-314">Bir pencere kenarlığını ne tür denetlemek için alır, ayarladığınız kendi <xref:System.Windows.Window.WindowStyle%2A> aşağıdaki değerlerden birini özelliğiyle <xref:System.Windows.WindowStyle> sabit listesi:</span><span class="sxs-lookup"><span data-stu-id="34cdb-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> <span data-ttu-id="34cdb-315">(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="34cdb-315">(default)</span></span>  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="34cdb-316">Bu pencere stilleri etkisini aşağıdaki resimde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Pencere sınır stillerini gösterimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="34cdb-318">Ayarlayabileceğiniz <xref:System.Windows.Window.WindowStyle%2A> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme veya kod; bir pencere ömrü boyunca değişme olasılığı olduğu için büyük olasılıkla kullanarak yapılandıracağınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="34cdb-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="34cdb-319">Dikdörtgen olmayan pencere stili</span><span class="sxs-lookup"><span data-stu-id="34cdb-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="34cdb-320">Burada kenarlık stilleri, durumlar da vardır <xref:System.Windows.Window.WindowStyle%2A> sağlayan sahip olmanız yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="34cdb-321">Örneğin, benzer olmayan bir kenarlığa sahip bir uygulama oluşturmak isteyebilirsiniz [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] kullanır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="34cdb-322">Örneğin, aşağıdaki şekilde gösterilen konuşma Kabarcık penceresi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="34cdb-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Sürükleme Me. bildiren bir konuşma Kabarcık penceresi](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="34cdb-324">Bu tür bir pencerede ayarlayarak oluşturulabilir <xref:System.Windows.Window.WindowStyle%2A> özelliğini <xref:System.Windows.WindowStyle.None>ve özel'i kullanarak destekleyen <xref:System.Windows.Window> saydamlık için.</span><span class="sxs-lookup"><span data-stu-id="34cdb-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="34cdb-325">Bu değerlerin birleşimini, tamamen saydam işlemek için pencerenin bildirir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="34cdb-326">Bu durumda, pencerenin istemci olmayan alan Kenarlıklar (menüyü Kapat, Küçült, Ekranı Kapla ve geri düğmeleri ve benzeri) kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="34cdb-327">Sonuç olarak, size sağlamak kendi gerekir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="34cdb-328">Görev çubuğu durum</span><span class="sxs-lookup"><span data-stu-id="34cdb-328">Task Bar Presence</span></span>  

<span data-ttu-id="34cdb-329">Varsayılan görünüm penceresinin aşağıdaki şekilde gösterilene benzer bir görev çubuğu düğme içerir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Bir pencere ile görev çubuğunu gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="34cdb-331">İleti kutuları ve iletişim kutuları gibi bir görev çubuğu düğmesinin windows bazı türleri yok (bkz [iletişim kutularına genel bakış](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="34cdb-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="34cdb-332">Bir pencere için görev çubuğu düğmesinin ayarlayarak gösterilip gösterilmeyeceğini denetleyen <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği (`true` varsayılan olarak).</span><span class="sxs-lookup"><span data-stu-id="34cdb-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="34cdb-333">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="34cdb-333">Security Considerations</span></span>  
 <xref:System.Windows.Window> <span data-ttu-id="34cdb-334">gerektirir `UnmanagedCode` güvenlik izni oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="34cdb-334">requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="34cdb-335">Yüklü ve yerel makineden başlatılan uygulamalar için bu uygulamaya verilen izinleri kümesi içinde döner.</span><span class="sxs-lookup"><span data-stu-id="34cdb-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="34cdb-336">Ancak, bu Internet veya yerel intranet bölgesi kullanımından başlatılan uygulamalara izinler kümesini dışında kalan [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34cdb-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span></span> <span data-ttu-id="34cdb-337">Sonuç olarak, kullanıcılar alır bir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] güvenlik uyarısı ve uygulama tam güven için ayarlanmış izin yükseltmesine gerekir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-337">Consequently, users will receive a [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="34cdb-338">Ayrıca, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] windows veya iletişim kutularında, varsayılan olarak gösteremez.</span><span class="sxs-lookup"><span data-stu-id="34cdb-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="34cdb-339">Tek başına uygulama güvenlik konuları hakkında bir tartışma için bkz. [WPF güvenlik stratejisi - Platform güvenliği](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="34cdb-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="34cdb-340">Diğer Windows türleri</span><span class="sxs-lookup"><span data-stu-id="34cdb-340">Other Types of Windows</span></span>  
 <xref:System.Windows.Navigation.NavigationWindow> <span data-ttu-id="34cdb-341">gezinilebilir içeriği barındırmak için tasarlanmış bir penceredir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-341">is a window that is designed to host navigable content.</span></span> <span data-ttu-id="34cdb-342">Daha fazla bilgi için [gezintiye genel bakış](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="34cdb-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="34cdb-343">Genellikle bir işlev tamamlamak için bir kullanıcıdan bilgi toplamak için kullanılan bir windows iletişim kutularıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="34cdb-344">Örneğin, ne zaman bir kullanıcının istediği bir dosyayı açmaya **Dosya Aç** iletişim kutusu kullanıcıdan dosya adını almak için bir uygulama tarafından genellikle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="34cdb-345">Daha fazla bilgi için [iletişim kutularına genel bakış](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34cdb-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34cdb-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="34cdb-347">İletişim Kutularına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34cdb-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="34cdb-348">WPF Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="34cdb-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
