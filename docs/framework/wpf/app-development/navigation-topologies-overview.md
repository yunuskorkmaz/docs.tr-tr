---
title: Gezinti Topolojilerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 8976ba7973e4f53022846b98c47d5613fd6ba158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557556"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="b012d-102">Gezinti Topolojilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b012d-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="b012d-103">Bu genel bakışta Gezinti topolojide tanıtılmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b012d-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="b012d-104">Örnekler ile üç ortak gezinti topolojisi daha sonra ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="b012d-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b012d-105">Bu konuyu okumadan önce yapılandırılmış Gezinti kavramı aşina olmalısınız [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfa işlevlerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b012d-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="b012d-106">Bu konuların ikisi hakkında daha fazla bilgi için bkz: [yapılandırılmış Gezinti genel bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b012d-106">For more information on both of these topics, see [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="b012d-107">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="b012d-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="b012d-108">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="b012d-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="b012d-109">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="b012d-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="b012d-110">Sabit doğrusal topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="b012d-111">Sabit hiyerarşik topoloji üzerinden dinamik Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="b012d-112">Dinamik olarak üretilen topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="b012d-113">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="b012d-113">Navigation Topologies</span></span>  
 <span data-ttu-id="b012d-114">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], gezinti genellikle sayfalarının oluşur (<xref:System.Windows.Controls.Page>) köprü ile (<xref:System.Windows.Documents.Hyperlink>) tıklatıldığında başka sayfalara gidin.</span><span class="sxs-lookup"><span data-stu-id="b012d-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="b012d-115">İçin gittiğinizde sayfaları tanımlanır [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (bkz [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="b012d-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="b012d-116">Sayfaları, köprüleri gösteren aşağıdaki basit örneği göz önünde bulundurun ve [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b012d-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="b012d-117">Bu sayfalar halinde düzenlenir bir *gezinti topolojisi* , yapısı, sayfalar arasında nasıl gidebilirsiniz tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b012d-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="b012d-118">Bir uygulamayı çalıştırırken bazıları yalnızca tanımlanabilir daha karmaşık topolojiler Gezinti gerekmesine rağmen bu belirli gezinti topolojisi basit senaryolarda uygundur.</span><span class="sxs-lookup"><span data-stu-id="b012d-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="b012d-119">Bu konuda üç ortak Gezinti topolojisini kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak üretilen*.</span><span class="sxs-lookup"><span data-stu-id="b012d-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="b012d-120">Her gezinti topolojisi sahip olan bir örneği ile gösterildiği bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki resimde gösterilen bir ister:</span><span class="sxs-lookup"><span data-stu-id="b012d-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="b012d-121">![Görev veri öğeleri sayfalarıyla](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="b012d-121">![Task pages with data items](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="b012d-122">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="b012d-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="b012d-123">Gezinti topolojileri iki geniş türü vardır:</span><span class="sxs-lookup"><span data-stu-id="b012d-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="b012d-124">**Sabit Topoloji**: derleme zamanında tanımlanan ve çalışma zamanında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="b012d-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="b012d-125">Sabit topolojiler, sabit bir dizi gezinmeyi doğrusal veya hiyerarşik sırada sayfaların için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b012d-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="b012d-126">**Dinamik topoloji**: kullanıcı, uygulama veya sistem toplanan giriş göre çalışma zamanında tanımlı.</span><span class="sxs-lookup"><span data-stu-id="b012d-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="b012d-127">Dinamik topolojiler, sayfalar farklı sıralarında gezildiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b012d-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="b012d-128">Sayfaları kullanarak gezinti topolojileri oluşturmak mümkün olsa da, geçirme ve bir topoloji sayfaları aracılığıyla veri döndürmek için destek basitleştirir ek destek sağladıkları için örnekler sayfa işlevlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b012d-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="b012d-129">Sabit doğrusal topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="b012d-130">Sabit doğrusal topoloji, sabit bir dizisinde gittiğinizde bir veya daha fazla sihirbaz sayfasına sahip bir sihirbaz yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="b012d-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="b012d-131">Aşağıdaki şekil üst düzey yapı ve sabit doğrusal topoloji sihirbazla akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b012d-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="b012d-132">![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="b012d-132">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="b012d-133">Sabit doğrusal topoloji üzerinde gezinme için tipik davranışlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b012d-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="b012d-134">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="b012d-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b012d-135">Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="b012d-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b012d-136">Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b012d-137">Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b012d-138">Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b012d-139">Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b012d-140">Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b012d-141">Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="b012d-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b012d-142">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b012d-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b012d-143">Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b012d-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b012d-144">Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="b012d-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="b012d-145">Sabit hiyerarşik topoloji üzerinden dinamik Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="b012d-146">Bazı uygulamalarda, sayfalar aşağıdaki resimde gösterildiği gibi iki veya daha fazla diğer sayfalara gezinti izin verin.</span><span class="sxs-lookup"><span data-stu-id="b012d-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="b012d-147">![Birden çok sayfaya gidebilir bir sayfa](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="b012d-147">![A page that can navigate to multiple pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="b012d-148">Bu yapı sabit hiyerarşik topoloji bilinir ve uygulama veya kullanıcı tarafından hangi hiyerarşinin geçirildiği sırası genellikle çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b012d-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="b012d-149">Çalışma zamanında, iki veya daha fazla başka sayfalara gezinme sağlar hiyerarşideki her bir sayfa gitmek için hangi sayfayı belirlemek için gereken verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="b012d-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="b012d-150">Aşağıdaki şekilde bir önceki şekle bağlı birkaç olası gezinti sıralarının gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b012d-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="b012d-151">![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="b012d-151">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="b012d-152">Sabit hiyerarşik bir yapı sayfalarında gittiğinizde sıra çalışma zamanında belirlenir olsa bile, kullanıcı deneyimi sabit doğrusal topoloji için kullanıcı deneyimi ile aynıdır:</span><span class="sxs-lookup"><span data-stu-id="b012d-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="b012d-153">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="b012d-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b012d-154">Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="b012d-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b012d-155">Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b012d-156">Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b012d-157">Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b012d-158">Günlük aracılığıyla geri dönerseniz kullanıcılar Gezinti sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="b012d-159">Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b012d-160">Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b012d-161">Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="b012d-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b012d-162">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b012d-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b012d-163">Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b012d-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b012d-164">Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="b012d-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="b012d-165">Dinamik olarak üretilen topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="b012d-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="b012d-166">Bazı uygulamalarda, iki veya daha fazla sayfa gittiğinizde sırası yalnızca çalışma zamanında kullanıcı, uygulama veya dış veri olup olmadığını tarafından belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="b012d-167">Aşağıdaki şekilde belirlenmemiş Gezinti dizisi ile sayfalar kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b012d-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="b012d-168">![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="b012d-168">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="b012d-169">Sonraki şekilde, çalışma zamanında kullanıcı tarafından seçilen bir gezinti dizisi gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b012d-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="b012d-170">![Gezinti diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="b012d-170">![Navigation diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="b012d-171">Gezinti dizisi dinamik olarak üretilen bir topoloji olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="b012d-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="b012d-172">Önceki topolojilerde olduğu gibi kullanıcı için diğer gezinti topolojileri ile kullanıcı deneyimi aynı gibidir:</span><span class="sxs-lookup"><span data-stu-id="b012d-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="b012d-173">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="b012d-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b012d-174">Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="b012d-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b012d-175">Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b012d-176">Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b012d-177">Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b012d-178">Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b012d-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b012d-179">Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b012d-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b012d-180">Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="b012d-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b012d-181">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b012d-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b012d-182">Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b012d-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b012d-183">Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="b012d-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b012d-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b012d-184">See Also</span></span>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [<span data-ttu-id="b012d-185">Yapılandırılmış Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b012d-185">Structured Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
