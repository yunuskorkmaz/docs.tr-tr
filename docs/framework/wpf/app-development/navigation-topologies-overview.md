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
ms.openlocfilehash: 16ce791c300c431b7349293d00648c881f97c372
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356786"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="ae38f-102">Gezinti Topolojilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae38f-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="ae38f-103">Bu genel bakış içindeki gezinti topolojilerine tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae38f-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="ae38f-104">Daha sonra örnek, üç genel gezinti topolojileri ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae38f-105">Bu konuda okumadan önce yapılandırılmış Gezinti kavramı bilmeniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfa işlevlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="ae38f-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="ae38f-106">Bu konu hem de daha fazla bilgi için bkz [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae38f-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="ae38f-107">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="ae38f-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="ae38f-108">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="ae38f-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="ae38f-109">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="ae38f-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="ae38f-110">Sabit doğrusal topoloji içinde gezinme</span><span class="sxs-lookup"><span data-stu-id="ae38f-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="ae38f-111">Sabit hiyerarşik topoloji üzerinde dinamik Gezinti</span><span class="sxs-lookup"><span data-stu-id="ae38f-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="ae38f-112">Dinamik olarak oluşturulan topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="ae38f-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="ae38f-113">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="ae38f-113">Navigation Topologies</span></span>  
 <span data-ttu-id="ae38f-114">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], gezinti, genellikle sayfaları oluşur (<xref:System.Windows.Controls.Page>) köprülerle (<xref:System.Windows.Documents.Hyperlink>) tıklandığında diğer sayfalara gidin.</span><span class="sxs-lookup"><span data-stu-id="ae38f-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="ae38f-115">İçin gitme sayfaları tanımlanır [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (bkz [paketi URI ' WPF'de](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="ae38f-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="ae38f-116">Sayfaları, köprüleri gösteren aşağıdaki basit örnekte göz önünde bulundurun ve [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ae38f-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="ae38f-117">Bu sayfalar halinde düzenlenir bir *gezinti topolojisi* yapısını sayfaları arasında nasıl gezinebileceğiniz tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="ae38f-118">Gezinti daha karmaşık topolojiler, bir uygulama çalıştırılırken bazıları yalnızca tanımlanabilir gerekmesine rağmen bu belirli Gezinti topoloji basit senaryo uygundur.</span><span class="sxs-lookup"><span data-stu-id="ae38f-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="ae38f-119">Bu konuda üç genel gezinti topolojileri kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak üretilen*.</span><span class="sxs-lookup"><span data-stu-id="ae38f-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="ae38f-120">Her Gezinti topolojisine sahip olan bir örnek gösterilmiştir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki şekilde gösterilen bir ister:</span><span class="sxs-lookup"><span data-stu-id="ae38f-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="ae38f-121">![Görev veri öğeleri sayfalarıyla](./media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="ae38f-121">![Task pages with data items](./media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="ae38f-122">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="ae38f-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="ae38f-123">Gezinti topolojilerine iki geniş türü vardır:</span><span class="sxs-lookup"><span data-stu-id="ae38f-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="ae38f-124">**Sabit Topoloji**: derleme zamanında tanımlanmış ve çalışma zamanında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="ae38f-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="ae38f-125">Sabit topolojiler, sabit bir dizi gezinmeyi doğrusal veya hiyerarşik sırayla sayfalar için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="ae38f-126">**Dinamik topoloji**: kullanıcı, uygulama veya sistem toplanan giriş göre çalışma zamanında tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="ae38f-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="ae38f-127">Dinamik topolojileri sayfaları farklı sıralarında geçtiğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="ae38f-128">Gezinti topolojilerine sayfalarını kullanarak oluşturmak mümkün olsa da, sağladıkları basitleştirir ve döndüren bir topoloji sayfalarına veri geçirme için destek ek destek için örnekleri sayfa işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae38f-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="ae38f-129">Sabit doğrusal topoloji içinde gezinme</span><span class="sxs-lookup"><span data-stu-id="ae38f-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="ae38f-130">Sabit doğrusal topoloji, sabit bir sırayla gitme bir veya daha fazla sihirbaz sayfasına sahip bir sihirbaz yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="ae38f-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="ae38f-131">Aşağıdaki şekilde bir sihirbazın sabit doğrusal topoloji ile akış ve üst düzey yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="ae38f-132">![Gezinti topoloji diyagramı](./media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="ae38f-132">![Navigation topology diagram](./media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="ae38f-133">Sabit doğrusal topoloji üzerinde gezinme için tipik davranışları şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="ae38f-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="ae38f-134">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="ae38f-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="ae38f-135">Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="ae38f-136">Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="ae38f-137">Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="ae38f-138">Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="ae38f-139">Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="ae38f-140">Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="ae38f-141">Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ae38f-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="ae38f-142">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae38f-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="ae38f-143">Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="ae38f-144">Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="ae38f-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="ae38f-145">Sabit hiyerarşik topoloji üzerinde dinamik Gezinti</span><span class="sxs-lookup"><span data-stu-id="ae38f-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="ae38f-146">Bazı uygulamalarda, sayfaları aşağıdaki resimde gösterildiği gibi iki veya daha fazla diğer sayfalarına yönelik gezinme olanak verir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="ae38f-147">![Birden çok sayfasına gidebilirsiniz bir sayfa](./media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="ae38f-147">![A page that can navigate to multiple pages](./media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="ae38f-148">Bu yapı sabit hiyerarşik topoloji bilinir ve uygulama veya kullanıcı tarafından hangi hiyerarşinin geçirildiği sırası genellikle çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="ae38f-149">Çalışma zamanında, iki veya daha fazla diğer sayfalarına yönelik gezinme sağlar hiyerarşide her sayfasına gitmek için hangi sayfa belirlemek için gereken verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="ae38f-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="ae38f-150">Aşağıdaki şekilde bir önceki şekle bağlı birkaç olası gezinti sıralarının gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="ae38f-151">![Gezinti topoloji diyagramı](./media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="ae38f-151">![Navigation topology diagram](./media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="ae38f-152">Sabit hiyerarşik bir yapıda sayfaları gitme sırasını çalışma zamanında belirlenir olsa bile, kullanıcı deneyimini sabit doğrusal topoloji için kullanıcı deneyimi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="ae38f-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="ae38f-153">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="ae38f-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="ae38f-154">Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="ae38f-155">Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="ae38f-156">Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="ae38f-157">Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="ae38f-158">Kullanıcıların gittikleri günlük aracılığıyla geri gezinti sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="ae38f-159">Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="ae38f-160">Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="ae38f-161">Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ae38f-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="ae38f-162">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae38f-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="ae38f-163">Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="ae38f-164">Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="ae38f-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="ae38f-165">Dinamik olarak oluşturulan topoloji üzerinde Gezinti</span><span class="sxs-lookup"><span data-stu-id="ae38f-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="ae38f-166">Bazı uygulamalarda, iki veya daha fazla sayfaya gitme sırasını yalnızca çalışma zamanında kullanıcı, uygulama veya dış veri olup olmadığını tarafından belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="ae38f-167">Aşağıdaki şekilde bir belirlenmemiş Gezinti diziyle sayfalar kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="ae38f-168">![Gezinti topoloji diyagramı](./media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="ae38f-168">![Navigation topology diagram](./media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="ae38f-169">Şekilde, çalışma zamanında kullanıcı tarafından seçilen bir gezinti sırasını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="ae38f-170">![Gezinti diyagramı](./media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="ae38f-170">![Navigation diagram](./media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="ae38f-171">Gezinti sırasında dinamik olarak oluşturulan topoloji bilinir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="ae38f-172">Önceki Topolojileri için olduğu gibi kullanıcının olarak başka gezinme topolojileri ile kullanıcı deneyimini aynıdır:</span><span class="sxs-lookup"><span data-stu-id="ae38f-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="ae38f-173">Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme.</span><span class="sxs-lookup"><span data-stu-id="ae38f-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="ae38f-174">Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="ae38f-175">Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="ae38f-176">Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="ae38f-177">Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="ae38f-178">Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="ae38f-179">Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="ae38f-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="ae38f-180">Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ae38f-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="ae38f-181">Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae38f-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="ae38f-182">Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ae38f-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="ae38f-183">Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.</span><span class="sxs-lookup"><span data-stu-id="ae38f-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae38f-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae38f-184">See also</span></span>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="ae38f-185">Yapılandırılmış Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae38f-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
