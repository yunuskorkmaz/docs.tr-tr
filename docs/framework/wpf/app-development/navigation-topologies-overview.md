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
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174205"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="025bb-102">Gezinti Topolojilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="025bb-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="025bb-103">Bu genel bakış, WPF'deki gezinme topolojilerine giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="025bb-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="025bb-104">Üç ortak navigasyon topolojisi, örnekleri ile, daha sonra tartışılır.</span><span class="sxs-lookup"><span data-stu-id="025bb-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="025bb-105">Bu konuyu okumadan önce, sayfa işlevlerini kullanarak WPF yapılandırılmış gezinme kavramına aşina olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="025bb-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="025bb-106">Bu konuların her ikisi hakkında daha fazla bilgi için [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="025bb-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="025bb-107">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="025bb-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="025bb-108">Navigasyon Topolojileri</span><span class="sxs-lookup"><span data-stu-id="025bb-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="025bb-109">Yapılandırılmış Navigasyon Topolojileri</span><span class="sxs-lookup"><span data-stu-id="025bb-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="025bb-110">Sabit Doğrusal Topoloji üzerinde gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="025bb-111">Sabit Hiyerarşik Topoloji Üzerinde Dinamik Gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="025bb-112">Dinamik Olarak Oluşturulan Topoloji Üzerinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="025bb-113">Navigasyon Topolojileri</span><span class="sxs-lookup"><span data-stu-id="025bb-113">Navigation Topologies</span></span>  
 <span data-ttu-id="025bb-114">WPF'de gezinme genellikle tıklatıldığında<xref:System.Windows.Controls.Page>diğer sayfalara<xref:System.Windows.Documents.Hyperlink>yönlendiren köprülere sahip sayfalardan () oluşur.</span><span class="sxs-lookup"><span data-stu-id="025bb-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="025bb-115">Gezinmek üzere yönlendirilen sayfalar, tek düzen kaynak tanımlayıcıları (URI' ler) tarafından tanımlanır (bkz. [WPF'deki Paket URI'leri).](pack-uris-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="025bb-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="025bb-116">Sayfaları, köprüleri ve tek düzen kaynak tanımlayıcılarını (UrI'ler) gösteren aşağıdaki basit örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="025bb-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="025bb-117">Bu sayfalar, yapısı sayfalar arasında nasıl gezinebileceğinize göre belirlenen bir *gezinti topolojisinde* düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="025bb-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="025bb-118">Bu özel navigasyon topolojisi basit senaryolarda uygundur, ancak navigasyon daha karmaşık topolojiler gerektirebilir ve bunların bazıları yalnızca bir uygulama çalışırken tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="025bb-119">Bu konu üç ortak navigasyon topolojisi kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak oluşturulan*.</span><span class="sxs-lookup"><span data-stu-id="025bb-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="025bb-120">Her navigasyon topolojisi, aşağıdaki şekilde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gösterilene benzer bir örneğe sahip bir örnekle gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="025bb-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Veri öğeleri ve gezinme düğmeleri ile görev sayfaları.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="025bb-122">Yapılandırılmış Navigasyon Topolojileri</span><span class="sxs-lookup"><span data-stu-id="025bb-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="025bb-123">Navigasyon topolojilerinin iki geniş türü vardır:</span><span class="sxs-lookup"><span data-stu-id="025bb-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="025bb-124">**Sabit Topoloji**: derleme zamanında tanımlanır ve çalışma zamanında değişmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="025bb-125">Sabit topolojiler, doğrusal veya hiyerarşik bir sırada sabit bir sayfa dizisinde gezinmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="025bb-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="025bb-126">**Dinamik Topoloji**: kullanıcıdan, uygulamadan veya sistemden toplanan girdiye göre çalışma zamanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="025bb-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="025bb-127">Dinamik topolojiler, sayfalar farklı dizilerde gezinildiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="025bb-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="025bb-128">Sayfaları kullanarak gezinme topolojileri oluşturmak mümkün olsa da, örnekler sayfa işlevlerini kullanır, çünkü bir topolojinin sayfaları üzerinden veri geçişi ve döndürülme desteği için desteği kolaylaştıran ek destek sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="025bb-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="025bb-129">Sabit Doğrusal Topoloji üzerinde gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="025bb-130">Sabit doğrusal topoloji, sabit bir sırada gezinen bir veya daha fazla sihirbaz sayfası olan bir sihirbazın yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="025bb-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="025bb-131">Aşağıdaki şekil, sabit doğrusal topolojiye sahip bir sihirbazın üst düzey yapısını ve akışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="025bb-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Sabit doğrusal topolojiyi gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="025bb-133">Sabit doğrusal bir topolojide gezinmek için tipik davranışlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="025bb-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="025bb-134">Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme.</span><span class="sxs-lookup"><span data-stu-id="025bb-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="025bb-135">Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="025bb-136">Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="025bb-137">Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="025bb-138">Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="025bb-139">Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="025bb-140">Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="025bb-141">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="025bb-142">Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="025bb-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="025bb-143">Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="025bb-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="025bb-144">Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.</span><span class="sxs-lookup"><span data-stu-id="025bb-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="025bb-145">Sabit Hiyerarşik Topoloji Üzerinde Dinamik Gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="025bb-146">Bazı uygulamalarda, sayfalar aşağıdaki şekilde gösterildiği gibi iki veya daha fazla başka sayfaya gezinmeye izin verir:</span><span class="sxs-lookup"><span data-stu-id="025bb-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![Birden çok sayfaya gidebilecek bir sayfayı gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="025bb-148">Bu yapı sabit hiyerarşik topoloji olarak bilinir ve hiyerarşinin geçiş sırası genellikle çalışma zamanında uygulama veya kullanıcı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="025bb-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="025bb-149">Çalışma zamanında, hiyerarşideki iki veya daha fazla diğer sayfaya gezinmeye izin veren her sayfa, hangi sayfaya gidileni belirlemek için gereken verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="025bb-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="025bb-150">Aşağıdaki şekil, önceki şeme göre birkaç olası gezinme dizisinden birini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="025bb-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Olası bir gezinme sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="025bb-152">Sabit hiyerarşik yapıdaki sayfaların gezinme sırası çalışma zamanında belirlense de, kullanıcı deneyimi sabit doğrusal bir topoloji için kullanıcı deneyimiyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="025bb-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="025bb-153">Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme.</span><span class="sxs-lookup"><span data-stu-id="025bb-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="025bb-154">Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="025bb-155">Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="025bb-156">Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="025bb-157">Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="025bb-158">Kullanıcılar günlükte geri gezindiklerinde gezinme sırasını değiştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="025bb-159">Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="025bb-160">Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="025bb-161">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="025bb-162">Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="025bb-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="025bb-163">Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="025bb-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="025bb-164">Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.</span><span class="sxs-lookup"><span data-stu-id="025bb-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="025bb-165">Dinamik Olarak Oluşturulan Topoloji Üzerinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="025bb-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="025bb-166">Bazı uygulamalarda, iki veya daha fazla sayfanın gezinildiği sıra, kullanıcı, uygulama veya dış veri tarafından yalnızca çalışma zamanında belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="025bb-167">Aşağıdaki şekil, belirsiz gezinme sıralı bir sayfa kümesini gösterir:</span><span class="sxs-lookup"><span data-stu-id="025bb-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Belirsiz gezinme sırasını olan bir sayfa kümesi.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="025bb-169">Bir sonraki şekil, kullanıcı tarafından çalışma zamanında seçilen bir gezinti dizisini gösterir:</span><span class="sxs-lookup"><span data-stu-id="025bb-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Çalışma zamanında seçilen bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="025bb-171">Navigasyon sırası dinamik olarak oluşturulan topoloji olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="025bb-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="025bb-172">Kullanıcı için, diğer navigasyon topolojilerinde olduğu gibi, kullanıcı deneyimi önceki topolojiler için olduğu gibi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="025bb-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="025bb-173">Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme.</span><span class="sxs-lookup"><span data-stu-id="025bb-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="025bb-174">Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="025bb-175">Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="025bb-176">Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="025bb-177">Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="025bb-178">Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="025bb-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="025bb-179">Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.</span><span class="sxs-lookup"><span data-stu-id="025bb-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="025bb-180">Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="025bb-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="025bb-181">Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="025bb-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="025bb-182">Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="025bb-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="025bb-183">Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.</span><span class="sxs-lookup"><span data-stu-id="025bb-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025bb-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="025bb-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="025bb-185">Yapılandırılmış Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="025bb-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
