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
ms.openlocfilehash: 5d9b09085ed8057f53cae9f9177682b01e698f6d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580715"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="00796-102">Gezinti Topolojilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00796-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="00796-103">Bu genel bakışta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içindeki gezinti topolojilerine giriş sağlanır.</span><span class="sxs-lookup"><span data-stu-id="00796-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="00796-104">Örneklerle birlikte üç ortak gezinti topolojisi daha sonra ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="00796-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00796-105">Bu konuyu okumadan önce, sayfa işlevlerini kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yapılandırılmış gezinme kavramıyla ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00796-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="00796-106">Bu konuların her ikisi hakkında daha fazla bilgi için bkz. [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00796-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="00796-107">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="00796-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="00796-108">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="00796-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="00796-109">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="00796-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="00796-110">Sabit doğrusal topoloji üzerinden gezinme</span><span class="sxs-lookup"><span data-stu-id="00796-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="00796-111">Sabit hiyerarşik topoloji üzerinde dinamik gezinti</span><span class="sxs-lookup"><span data-stu-id="00796-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="00796-112">Dinamik olarak oluşturulan bir topoloji üzerinden gezinme</span><span class="sxs-lookup"><span data-stu-id="00796-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="00796-113">Gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="00796-113">Navigation Topologies</span></span>  
 <span data-ttu-id="00796-114">@No__t_0, gezinti tipik olarak, tıklandığı zaman diğer sayfalara gitmek için köprüler (<xref:System.Windows.Documents.Hyperlink>) ile sayfalardan (<xref:System.Windows.Controls.Page>) oluşur.</span><span class="sxs-lookup"><span data-stu-id="00796-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="00796-115">' Ye gidildiği sayfalar Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) tarafından tanımlanır (bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="00796-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="00796-116">Sayfaları, köprüleri ve Tekdüzen Kaynak tanımlayıcılarını (URI) gösteren aşağıdaki basit örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="00796-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="00796-117">Bu sayfalar, yapısı sayfalar arasında nasıl gezindiğinize göre belirlenen bir *gezinti topolojisi* içinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="00796-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="00796-118">Bu özel gezinti topolojisi basit senaryolarda uygundur, ancak bazıları yalnızca bir uygulama çalışırken tanımlanabilseler de, daha karmaşık topolojiler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="00796-119">Bu konuda üç genel gezinti topolojisi ele alınmaktadır: *Sabit doğrusal*, *sabit hiyerarşik*ve *dinamik olarak üretilen*.</span><span class="sxs-lookup"><span data-stu-id="00796-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="00796-120">Her gezinti topolojisi, aşağıdaki şekilde gösterildiği gibi bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olan bir örnekle gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00796-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Veri öğeleri ve gezinti düğmeleri içeren görev sayfaları.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="00796-122">Yapılandırılmış gezinti topolojileri</span><span class="sxs-lookup"><span data-stu-id="00796-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="00796-123">İki geniş gezinti topolojisi türü vardır:</span><span class="sxs-lookup"><span data-stu-id="00796-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="00796-124">**Sabit topoloji**: derleme zamanında tanımlanır ve çalışma zamanında değişmez.</span><span class="sxs-lookup"><span data-stu-id="00796-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="00796-125">Sabit topolojiler, doğrusal veya hiyerarşik bir düzende sabit bir sayfa dizisi aracılığıyla gezinme için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="00796-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="00796-126">**Dinamik topoloji**: Kullanıcı, uygulama veya sistem tarafından toplanan girişe dayalı olarak çalışma zamanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="00796-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="00796-127">Dinamik topolojiler, sayfalar farklı dizilerle gezinilebilir olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="00796-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="00796-128">Sayfaları kullanarak gezinti topolojileri oluşturmak mümkün olsa da, örnekler, bir topolojinin sayfaları aracılığıyla veri geçirme ve döndürme desteğini kolaylaştıran ek destek sağladığından, örnek sayfa işlevlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="00796-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="00796-129">Sabit doğrusal topoloji üzerinden gezinme</span><span class="sxs-lookup"><span data-stu-id="00796-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="00796-130">Sabit bir doğrusal topoloji, sabit bir dizide gezindiği bir veya daha fazla sihirbaz sayfasına sahip olan bir sihirbazın yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="00796-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="00796-131">Aşağıdaki şekilde, sabit bir doğrusal topolojiyle bir sihirbazın üst düzey yapısı ve akışı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00796-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Sabit bir doğrusal topolojiyi gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="00796-133">Sabit bir doğrusal topoloji üzerinde gezinmek için tipik davranışlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="00796-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="00796-134">Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme.</span><span class="sxs-lookup"><span data-stu-id="00796-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="00796-135">Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="00796-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="00796-136">Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="00796-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="00796-137">Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00796-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="00796-138">Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="00796-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="00796-139">Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="00796-140">Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="00796-141">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="00796-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="00796-142">Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00796-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="00796-143">Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="00796-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="00796-144">Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.</span><span class="sxs-lookup"><span data-stu-id="00796-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="00796-145">Sabit hiyerarşik topoloji üzerinde dinamik gezinti</span><span class="sxs-lookup"><span data-stu-id="00796-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="00796-146">Bazı uygulamalarda, sayfalar aşağıdaki şekilde gösterildiği gibi iki veya daha fazla sayfaya gezinmesine izin verir:</span><span class="sxs-lookup"><span data-stu-id="00796-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span> 
  
 ![Birden çok sayfaya gidebileceğiniz bir sayfayı gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="00796-148">Bu yapı sabit bir hiyerarşik topoloji olarak bilinir ve hiyerarşinin çapraz geçen sırası genellikle uygulama veya Kullanıcı tarafından çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="00796-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="00796-149">Çalışma zamanında, hiyerarşideki iki veya daha fazla sayfaya gezinmesine izin veren her sayfa, hangi sayfanın ekleneceğini belirlemede gereken verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="00796-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="00796-150">Aşağıdaki şekilde, önceki şekle göre olası çeşitli gezinti dizilerinden biri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00796-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Olası bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="00796-152">Sabit hiyerarşik bir yapıdaki sayfaların çalışma zamanında gezinmesine rağmen, Kullanıcı deneyimi sabit bir doğrusal topoloji için Kullanıcı deneyimiyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="00796-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="00796-153">Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme.</span><span class="sxs-lookup"><span data-stu-id="00796-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="00796-154">Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="00796-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="00796-155">Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="00796-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="00796-156">Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00796-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="00796-157">Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="00796-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="00796-158">Kullanıcılar, günlük üzerinden geri gittiklerinde, gezinti sırasını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="00796-159">Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="00796-160">Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="00796-161">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="00796-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="00796-162">Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00796-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="00796-163">Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="00796-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="00796-164">Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.</span><span class="sxs-lookup"><span data-stu-id="00796-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="00796-165">Dinamik olarak oluşturulan bir topoloji üzerinden gezinme</span><span class="sxs-lookup"><span data-stu-id="00796-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="00796-166">Bazı uygulamalarda, iki veya daha fazla sayfanın gezindiği sıra yalnızca çalışma zamanında, Kullanıcı, uygulama veya dış veriler tarafından belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="00796-167">Aşağıdaki şekilde, belirlenmemiş bir gezinti sırası olan bir sayfa kümesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00796-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Belirlenmemiş bir gezinti dizisine sahip bir sayfa kümesi.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="00796-169">Sonraki şekilde, çalışma zamanında Kullanıcı tarafından seçilen bir gezinti sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00796-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Çalışma zamanında seçilen bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="00796-171">Gezinti sırası, dinamik olarak oluşturulan bir topoloji olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="00796-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="00796-172">Diğer gezinti topolojilerinde olduğu gibi, Kullanıcı deneyimi, önceki topolojilerle aynı olur:</span><span class="sxs-lookup"><span data-stu-id="00796-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="00796-173">Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme.</span><span class="sxs-lookup"><span data-stu-id="00796-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="00796-174">Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="00796-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="00796-175">Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="00796-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="00796-176">Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00796-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="00796-177">Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="00796-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="00796-178">Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="00796-179">Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="00796-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="00796-180">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="00796-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="00796-181">Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00796-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="00796-182">Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="00796-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="00796-183">Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.</span><span class="sxs-lookup"><span data-stu-id="00796-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00796-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00796-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="00796-185">Yapılandırılmış Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00796-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
