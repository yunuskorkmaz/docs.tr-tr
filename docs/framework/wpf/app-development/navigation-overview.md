---
title: Gezintiye Genel Bakış
description: Windows Presentation Foundation (WPF) ' de tek başına uygulamalarda ve XAML tarayıcı uygulamalarında kullanılan tarayıcı stili gezinme desteği hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621710"
---
# <a name="navigation-overview"></a>Gezintiye Genel Bakış

Windows Presentation Foundation (WPF), iki tür uygulamada kullanılabilen tarayıcı stili gezinmeyi destekler: tek başına uygulamalar ve XAML tarayıcı uygulamaları (XBAP). İçeriği gezinti için paketlemek için WPF <xref:System.Windows.Controls.Page> sınıfı sağlar. ' Yi kullanarak bir veya kullanarak bir <xref:System.Windows.Controls.Page> veya programlı olarak bir ile diğerine gidebilirsiniz <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> . WPF, ' den gelen ve geri gitmek için kullanılan sayfaları hatırlama günlüğünü kullanır.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Navigation.NavigationService> ve Journal, WPF tarafından sunulan gezinti desteğinin çekirdeğini oluşturur. Bu genel bakış [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , gevşek dosyalar, HTML dosyaları ve nesneler için gezinti içeren gelişmiş gezinti desteğini kapsamadan önce bu özellikleri ayrıntılı olarak araştırır.

> [!NOTE]
> Bu konuda, "Browser" terimi, şu anda Microsoft Internet Explorer ve Firefox içeren WPF uygulamalarını barındırabilen tarayıcılara başvurur. Belirli WPF özelliklerinin yalnızca belirli bir tarayıcı tarafından desteklendiği, tarayıcı sürümüne başvurulur.

## <a name="navigation-in-wpf-applications"></a>WPF uygulamalarında gezinme

Bu konu, WPF 'de anahtar gezinti özelliklerine genel bir bakış sağlar. Bu yetenekler hem tek başına uygulamalar hem de XBAP 'ler için kullanılabilir, ancak bu konu, bunları bir XBAP bağlamı içinde gösterir.

> [!NOTE]
> Bu konuda, XBAP oluşturma ve dağıtma konusu ele alınmaktadır. XBAP 'ler hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).

Bu bölümde, aşağıdaki gezinti yönleri açıklanmaktadır ve gösterilmektedir:

- [Sayfa uygulama](#CreatingAXAMLPage)

- [Başlangıç sayfasını yapılandırma](#Configuring_a_Start_Page)

- [Konak penceresinin başlığını, genişliğini ve yüksekliğini yapılandırma](#ConfiguringAXAMLPage)

- [Köprü gezintisi](#NavigatingBetweenXAMLPages)

- [Parça gezintisi](#FragmentNavigation)

- [Gezinti hizmeti](#NavigationService)

- [Gezinti hizmeti ile programlama yoluyla gezinme](#Programmatic_Navigation_with_the_Navigation_Service)

- [Gezinti ömrü](#Navigation_Lifetime)

- [Günlükle gezinti hatırlama](#NavigationHistory)

- [Sayfa ömrü ve günlüğü](#PageLifetime)

- [Içerik durumunu gezinti geçmişi ile koruma](#RetainingContentStateWithNavigationHistory)

- [Çerezler](#Cookies)

- [Yapılandırılmış gezinti](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Sayfa uygulama

WPF 'de .NET Framework nesneleri, özel nesneleri, numaralandırma değerlerini, kullanıcı denetimlerini, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve HTML dosyalarını içeren çeşitli içerik türlerine gidebilirsiniz. Bununla birlikte, içerik paketlemeyi kullanmanın en yaygın ve uygun yolunun kullanarak olduğunu fark edeceksiniz <xref:System.Windows.Controls.Page> . Ayrıca, <xref:System.Windows.Controls.Page> görünüşlerinin geliştirilmesi ve geliştirmeyi basitleştirmek için gezintiye özgü özellikler uygular.

Kullanarak <xref:System.Windows.Controls.Page> , [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki gibi bir biçimlendirme kullanarak bir içeriğe göre gezinebilir bir içerik sayfası uygulayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<xref:System.Windows.Controls.Page>Biçimlendirme içinde uygulanan bir, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` kök öğesi olarak sahıptır ve WPF XML ad alanı bildirimi gerektirir. `Page`Öğesi, gitmek ve göstermek istediğiniz içeriği içerir. `Page.Content`Aşağıdaki biçimlendirmede gösterildiği gibi, özellik öğesini ayarlayarak içerik eklersiniz.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content`yalnızca bir alt öğe içerebilir; Yukarıdaki örnekte, içerik tek bir dizedir, "Merhaba, sayfa!" Uygulamada, içeriğinizi eklemek ve oluşturmak için genellikle alt öğe (bkz. [Düzen](../advanced/layout.md)) olarak bir düzen denetimi kullanırsınız.

Bir öğenin alt öğeleri `Page` bir ve içeriği olarak kabul edilir <xref:System.Windows.Controls.Page> ve sonuç olarak açık bildirimi kullanmanız gerekmez `Page.Content` . Aşağıdaki biçimlendirme, önceki örneğe bildirime dayalı olarak eşdeğerdir.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

Bu durumda, `Page.Content` öğesinin alt öğeleriyle otomatik olarak ayarlanır `Page` . Daha fazla bilgi için bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).

Yalnızca biçimlendirme <xref:System.Windows.Controls.Page> , içerik görüntülemek için yararlıdır. Ancak, <xref:System.Windows.Controls.Page> Ayrıca, kullanıcıların sayfayla etkileşime geçmesini sağlayan denetimleri görüntüleyebilir ve olayları işleyerek ve uygulama mantığını çağırarak kullanıcı etkileşimine yanıt verebilir. Etkileşimli bir <xref:System.Windows.Controls.Page> şekilde, aşağıdaki örnekte gösterildiği gibi biçimlendirme ve arka plan kod birleşimi kullanılarak uygulanır.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Biçimlendirme dosyası ve arka plan kod dosyasının birlikte çalışmasına izin vermek için aşağıdaki yapılandırma gereklidir:

- Biçimlendirme ' de, `Page` öğesi `x:Class` özniteliğini içermelidir. Uygulama yapılandırıldığında, `x:Class` biçimlendirme dosyasında bulunması Microsoft Build Engine (MSBuild) ' `partial` den türetilen <xref:System.Windows.Controls.Page> ve özniteliği tarafından belirtilen adı içeren bir sınıf oluşturmasına neden olur `x:Class` . Bu, şema () için bir XML ad alanı bildiriminin eklenmesini gerektirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` . Oluşturulan `partial` sınıf `InitializeComponent` , olayları kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağırılır.

- Arka plan kod içinde, sınıf, `partial` biçimlendirme içindeki özniteliği tarafından belirtilen aynı ada sahip bir sınıf olmalıdır `x:Class` ve ' den türetmelidir <xref:System.Windows.Controls.Page> . Bu, arka plan kod dosyasının, `partial` uygulama oluşturulduğunda biçimlendirme dosyası için oluşturulan sınıfla ilişkilendirilmesini sağlar (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).

- Arka plan kod içinde, <xref:System.Windows.Controls.Page> sınıfının yöntemini çağıran bir Oluşturucu uygulaması gerekir `InitializeComponent` . `InitializeComponent`, biçimlendirme dosyasının oluşturulan `partial` sınıfı tarafından olayları kaydetmek ve biçimlendirmede tanımlanan özellikleri ayarlamak için uygulanır.

> [!NOTE]
> <xref:System.Windows.Controls.Page>Visual Studio kullanarak projenize yeni bir eklediğinizde, <xref:System.Windows.Controls.Page> her iki biçimlendirme ve arka plan kodu kullanılarak uygulanır ve burada açıklanan biçimlendirme ve arka plan kod dosyaları arasındaki ilişkiyi oluşturmak için gerekli yapılandırmayı içerir.

' A sahip olduktan sonra <xref:System.Windows.Controls.Page> Bu sayfaya gidebilirsiniz. Uygulamanın ilk gittiği adı belirtmek için <xref:System.Windows.Controls.Page> , Başlat 'ı yapılandırmanız gerekir <xref:System.Windows.Controls.Page> .

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Başlangıç sayfasını yapılandırma

XBAP 'ler bir tarayıcıda barındırılmak için belirli bir uygulama altyapısı miktarı gerektirir. WPF, <xref:System.Windows.Application> sınıf gerekli uygulama altyapısını kuran bir uygulama tanımının parçasıdır (bkz. [uygulama yönetimine genel bakış](application-management-overview.md)).

Bir uygulama tanımı, bir MSBuild öğesi olarak yapılandırılmış biçimlendirme dosyası ile hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır `ApplicationDefinition` . Aşağıda bir XBAP için uygulama tanımı verilmiştir.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

Bir XBAP, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> XBAP başlatıldığında otomatik olarak yüklenen bir başlangıcını belirtmek için uygulama tanımını kullanabilir. Bunu, <xref:System.Windows.Application.StartupUri%2A> özelliği, istenen için Tekdüzen Kaynak tanımlayıcısı (URI) ile ayarlayarak yapabilirsiniz <xref:System.Windows.Controls.Page> .

> [!NOTE]
> Çoğu durumda,, <xref:System.Windows.Controls.Page> bir uygulamayla derlenir veya bir uygulamayla birlikte dağıtılır. Bu gibi durumlarda, öğesini tanımlayan URI, <xref:System.Windows.Controls.Page> *paket* DÜZENINE uygun bir URI olan bir paket URI 'sidir. Paket URI 'Leri, [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)daha fazla ele alınmıştır. Ayrıca, aşağıda açıklanan http düzenini kullanarak içeriğe gidebilirsiniz.

<xref:System.Windows.Application.StartupUri%2A>Aşağıdaki örnekte gösterildiği gibi biçimlendirme içinde bildirimli olarak ayarlayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

Bu örnekte, özniteliği, `StartupUri` giriş sayfası. xaml tanımlayan göreli bir paket URI 'si ile ayarlanır. XBAP başlatıldığında, giriş sayfası. xaml otomatik olarak gezilebilir ve görüntülenir. Bu, bir Web sunucusundan başlatılan bir XBAP 'yi gösteren aşağıdaki şekilde gösterilmiştir.

![XBAP sayfası](./media/navigation-overview/xbap-launched-from-a-web-server.png "Bu, bir Web sunucusundan başlatılan bir XBAP gösterir.")

> [!NOTE]
> XBAP geliştirme ve dağıtımı hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md) ve [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konak penceresinin başlığını, genişliğini ve yüksekliğini yapılandırma

Önceki şekilden fark ettiğiniz bir şey, hem tarayıcının hem de sekme panelinin başlığının XBAP 'nin URI 'sidir. Büyük olmasının yanı sıra başlık etkileyici veya bilgilendirici değildir. Bu nedenle, <xref:System.Windows.Controls.Page> özelliği ayarlayarak başlığı değiştirmeniz için bir yol sunar <xref:System.Windows.Controls.Page.WindowTitle%2A> . Ayrıca, sırasıyla ve ayarlarını yaparak tarayıcı penceresinin genişlik ve yüksekliğini yapılandırabilirsiniz <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A> .

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A> Aşağıdaki örnekte gösterildiği gibi biçimlendirme içinde bildirimli olarak ayarlanabilir.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Sonuç aşağıdaki şekilde gösterilmiştir.

![Pencere başlığı, yükseklik, Genişlik](./media/navigation-overview/window-title-width-height.png "Bu, yapılandırabileceğiniz pencere başlığını, yüksekliğini ve genişliğini gösterir.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Köprü gezintisi

Tipik bir XBAP çeşitli sayfalar içerir. Bir sayfadan diğerine gitmenin en kolay yolu bir kullanmaktır <xref:System.Windows.Documents.Hyperlink> . <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> Aşağıdaki biçimlendirmede gösterilen öğesini kullanarak bildirimli olarak bir öğesine ekleyebilirsiniz `Hyperlink` .

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Bir `Hyperlink` öğesi şunları gerektirir:

- ' Nin, <xref:System.Windows.Controls.Page> özniteliği tarafından belirtildiği gibi, öğesine gitmek için paket URI 'si `NavigateUri` .

- Kullanıcının gezinti işlemini başlatmak için tıklatabilecek içerik (örneğin, metin ve görüntüler `Hyperlink` ) (öğenin içerebileceği içerik için bkz <xref:System.Windows.Documents.Hyperlink> .).

Aşağıdaki şekilde, öğesine sahip olan bir XBAP gösterilmektedir <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> .

![Köprü içeren sayfa](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Bu, Köprüsü olan bir sayfa içeren bir XBAP gösterir.")

İstediğiniz gibi, ' <xref:System.Windows.Documents.Hyperlink> ye TıKLAMAK XBAP 'ın <xref:System.Windows.Controls.Page> özniteliği tarafından tanımlanan öğesine gitmesini sağlar `NavigateUri` . Ayrıca, XBAP, <xref:System.Windows.Controls.Page> Internet Explorer 'Daki son sayfalar listesine bir giriş ekler. Bu, aşağıdaki şekilde gösterilmiştir.

![Geri ve Ileri düğmeleri](./media/navigation-overview/back-and-forward-navigation.png "Geri ve ileri düğmelerine gidin.")

Ayrıca, bir öğesinden diğerine gezinmeyi desteklemenin yanı <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> sıra parça gezintisini da destekler.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Parça gezintisi

*Parça gezintisi* , geçerli ya da diğeri içindeki bir içerik parçasına yönelik gezindir <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> . WPF 'de, içerik parçası, adlandırılmış bir öğe tarafından içerilen içeriktir. Adlandırılmış bir öğe, `Name` özniteliği ayarlanmış bir öğedir. Aşağıdaki biçimlendirme `TextBlock` bir içerik parçası içeren adlandırılmış bir öğeyi gösterir.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Bir <xref:System.Windows.Documents.Hyperlink> içerik parçasına gitmek için `NavigateUri` özniteliği şunları içermelidir:

- <xref:System.Windows.Controls.Page>Gidilecek içerik parçasının URI 'si.

- Bir "#" karakteri.

- <xref:System.Windows.Controls.Page>İçerik parçasını içeren içindeki öğesinin adı.

Bir parça URI 'SI aşağıdaki biçime sahiptir.

*PageUri* `#` *ElementName*

Aşağıda bir `Hyperlink` içerik parçasına gitmek için yapılandırılmış bir örneği gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Bu bölüm, WPF 'de varsayılan parça gezintisi uygulamasını açıklar. WPF ayrıca, kısmen olayını işlemeyi gerektiren kendi parça gezinti düzeninizi uygulamanıza olanak tanır <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> .

> [!IMPORTANT]
> Gevşek sayfalardaki parçalara gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ( [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` kök öğe olarak yalnızca biçimlendirme dosyaları), yalnızca sayfaların http aracılığıyla gözatılabilir olması durumunda olabilir.
>
> Ancak, gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa kendi parçalara gidebilir.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Gezinti hizmeti

<xref:System.Windows.Documents.Hyperlink>Bir kullanıcının belirli bir gezinmede gezinmeyi başlatmasına olanak sağlarken <xref:System.Windows.Controls.Page> , sayfanın bulunması ve indirilmesi işi sınıfı tarafından gerçekleştirilir <xref:System.Windows.Navigation.NavigationService> . Temelde, gibi <xref:System.Windows.Navigation.NavigationService> istemci kodu adına bir gezinti isteği işleme yeteneği sağlar <xref:System.Windows.Documents.Hyperlink> . Ayrıca, <xref:System.Windows.Navigation.NavigationService> bir gezinti isteğini izlemek ve etkili bir şekilde eğmek için daha yüksek düzeyde destek uygular.

Bir <xref:System.Windows.Documents.Hyperlink> tıklandığında, WPF <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Page> belirtilen paket URI 'sinde öğesini bulup indirmek için çağırır. İndirilen, <xref:System.Windows.Controls.Page> kök nesnesi indirilen bir örnek olan bir nesne ağacına dönüştürülür <xref:System.Windows.Controls.Page> . Kök nesneye bir başvuru, <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> özelliğinde depolanır. Gezindiği içeriğin paket URI 'SI <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliğinde depolanır, ancak <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> Bu, gezindiği son SAYFANıN paket URI 'sini depolar.

> [!NOTE]
> Bir WPF uygulamasının şu anda birden fazla etkin olması mümkündür <xref:System.Windows.Navigation.NavigationService> . Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Gezinti konakları](#Navigation_Hosts) bölümüne bakın.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Gezinti hizmeti ile programlama yoluyla gezinme

<xref:System.Windows.Navigation.NavigationService>Gezinmede biçimlendirme sırasında gezinme uygulanıp uygulanmadığı hakkında bilmeniz gerekmez <xref:System.Windows.Documents.Hyperlink> , çünkü sizin <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> adınıza kullanır. Yani, a 'nın doğrudan veya dolaylı üst öğesi <xref:System.Windows.Documents.Hyperlink> bir gezinti ana bilgisayarı (bkz. [gezinme Konakları](#Navigation_Hosts)), bir <xref:System.Windows.Documents.Hyperlink> Gezinti isteğini işlemek için gezinti konağının gezinti hizmetini bulup kullanabilirler.

Ancak, <xref:System.Windows.Navigation.NavigationService> aşağıdakiler de dahil olmak üzere doğrudan kullanmanız gerektiğinde durumlar vardır:

- Parametresiz bir Oluşturucu kullanarak bir örneği oluşturmanız gerektiğinde <xref:System.Windows.Controls.Page> .

- Üzerine geçmeden önce üzerinde Özellikler ayarlamanız gerekir <xref:System.Windows.Controls.Page> .

- <xref:System.Windows.Controls.Page>Gezilmesi gereken, yalnızca çalışma zamanında belirlenebilir.

Bu durumlarda, nesnenin yöntemini çağırarak programlı bir şekilde gezinmeyi başlatmak için kod yazmanız gerekir <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> . Bu, bir başvurusu almayı gerektirir <xref:System.Windows.Navigation.NavigationService> .

#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService 'e başvuru alma

[Gezinti konakları](#Navigation_Hosts) bölümünde ele alınan nedenlerden dolayı bir WPF uygulaması birden fazla olabilir <xref:System.Windows.Navigation.NavigationService> . Bu, kodunuzun, <xref:System.Windows.Navigation.NavigationService> genellikle geçerli olan olan bir ' ı bulmak için bir yol olması anlamına gelir <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> . Yöntemini çağırarak bir öğesine başvuru alabilirsiniz <xref:System.Windows.Navigation.NavigationService> `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> . <xref:System.Windows.Navigation.NavigationService>Belirli bir öğesine gidildiği için, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> yönteminin bağımsız değişkeni olarak öğesine bir başvuru geçirin <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> . Aşağıdaki kod, geçerli için nasıl alınacağını gösterir <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> .

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Bir için öğesini bulmak için bir kısayol olarak <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Page> özelliğini uygular <xref:System.Windows.Controls.Page.NavigationService%2A> . Bu, aşağıdaki örnekte gösterilir.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <xref:System.Windows.Controls.Page>Yalnızca olayını başlatan öğesine bir başvuru alabilir <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> .

#### <a name="programmatic-navigation-to-a-page-object"></a>Sayfa nesnesine programlama yoluyla gezinme

Aşağıdaki örnek, ile <xref:System.Windows.Navigation.NavigationService> programlı olarak bir öğesine gitmek için ' nin nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Page> . <xref:System.Windows.Controls.Page>Yalnızca tek, parametresiz bir Oluşturucu kullanılarak örneklendiği için programlı gezinme gereklidir. <xref:System.Windows.Controls.Page>Parametresiz oluşturucusu ile aşağıdaki biçimlendirme ve kodda gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> Parametresiz oluşturucusu ile öğesine gider, aşağıdaki biçimlendirme ve kodda gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

<xref:System.Windows.Documents.Hyperlink>Bu tıklatıldığında, eksik <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> oluşturucuyu kullanarak gezinmek ve yöntemi çağırmak için ' i örnekleyerek gezinti başlatılır <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> . <xref:System.Windows.Navigation.NavigationService.Navigate%2A><xref:System.Windows.Navigation.NavigationService>bir paket URI 'si yerine, gidilecek nesnenin başvurusunu kabul eder.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Paket URI 'SI ile programlama yoluyla gezinme

Program aracılığıyla bir paket URI 'SI oluşturmanız gerekiyorsa (örneğin, çalışma zamanında paket URI 'sini yalnızca belirleyebiliyorsanız), <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Geçerli sayfa yenileniyor

<xref:System.Windows.Controls.Page>Özelliği, özelliğinde depolanan paket URI 'si ile aynı paket URI 'sine sahipse indirilmez <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> . WPF 'yi geçerli sayfayı yeniden indirmeye zorlamak için <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi yöntemini çağırabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Gezinti ömrü

Gördüğünüz gibi, gezintiyi başlatmak için birçok yol vardır. Gezinti başlatıldığında ve gezinme devam ederken, tarafından uygulanan aşağıdaki olayları kullanarak gezintiyi izleyebilir ve etkileyebilirsiniz <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Yeni bir gezinti istendiğinde gerçekleşir. Gezinmeyi iptal etmek için kullanılabilir.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Bir indirme sırasında, gezinti ilerleme bilgileri sağlamak için düzenli aralıklarla gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Sayfa bulunduğunda ve indirildiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Gezinti durdurulduğunda (çağırarak <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ) veya geçerli bir gezinti sürerken yeni bir gezinti istendiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. İstenen içeriğe gidilirken bir hata ortaya çıktığında gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Gezinilmiş içerik yüklenip ayrıştırıldığında ve işlemeye başladıktan sonra gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Bir içerik parçasına Gezinti başladığında gerçekleşir, bu durum:

  - Hemen, istenen parça geçerli içeriktir.

  - Kaynak içerik yüklendikten sonra, istenen parça farklı içeriklerde yer alıyorsa.

Gezinti olayları aşağıdaki şekilde gösterilen sırayla oluşturulur.

![Sayfa gezintisi akış grafiği](./media/navigation-overview/order-of-navigation-events.png "Sayfa gezintisi olay akışı grafiği")

Genel olarak, <xref:System.Windows.Controls.Page> Bu olaylar konusunda endişe yoktur. Bir uygulamanın bunlarla ilgilenmesi daha olasıdır ve bu nedenle, bu olaylar sınıf tarafından da oluşturulur <xref:System.Windows.Application> :

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Her seferinde <xref:System.Windows.Navigation.NavigationService> bir olay ortaya geçirirse, <xref:System.Windows.Application> sınıf ilgili olayı oluşturur. <xref:System.Windows.Controls.Frame>ve <xref:System.Windows.Navigation.NavigationWindow> ilgili kapsamlarında gezintiyi algılamak için aynı olayları sunun.

Bazı durumlarda, <xref:System.Windows.Controls.Page> Bu olaylarla ilgileniyor olabilirsiniz. Örneğin, bir, <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> gezintiyi kendinden uzağa iptal edilip edilmeyeceğini tespit etmek için olayı işleyebilir. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Bir işleyiciyi bir gezinti olayı ile kaydettiğinizde <xref:System.Windows.Controls.Page> , önceki örnekte olduğu gibi, olay işleyicisinin kaydını da silmeniz gerekir. Bunu yapmazsanız, WPF gezintisinin günlüğü kullanarak gezintiyi hatırlıyor olması açısından yan etkileri olabilir <xref:System.Windows.Controls.Page> .

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Günlükle gezinti hatırlama

WPF, bir arka yığın ve bir ileri yığını olan sayfaları anımsamak için iki yığın kullanır. Geçerli <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> ya da var olan bir yeni ya da ileri ' ye gittiğinizde <xref:System.Windows.Controls.Page> , geçerli bir <xref:System.Windows.Controls.Page> *geri yığına*eklenir. Geçerli bir <xref:System.Windows.Controls.Page> öncekine geri gittiğinizde <xref:System.Windows.Controls.Page> , geçerli <xref:System.Windows.Controls.Page> olan *İleri yığına*eklenir. Arka yığın, ileri yığın ve bunları yönetme işlevleri, toplu olarak günlük olarak adlandırılır. Arka yığındaki her öğe ve ileri yığın, sınıfının bir örneğidir <xref:System.Windows.Navigation.JournalEntry> ve *günlük girdisi*olarak adlandırılır.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer 'da günlük gezinme

Kavramsal olarak, günlük, Internet Explorer 'daki **geri** ve **İleri** düğmeleriyle aynı şekilde çalışır. Bunlar aşağıdaki şekilde gösterilmiştir.

![Geri ve Ileri düğmeleri](./media/navigation-overview/back-and-forward-navigation.png "Geri ve ileri düğmelerine gidin.")

Internet Explorer tarafından barındırılan XBAP 'ler için WPF, günlüğü Internet Explorer 'ın gezintisine tümleştirir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bu, kullanıcıların Internet Explorer 'daki **geri**, **Ileri**ve **son sayfalar** düğmelerini kullanarak bir XBAP içindeki sayfalarda gezinmelerini sağlar.

> [!IMPORTANT]
> Internet Explorer 'da, bir Kullanıcı bir XBAP 'den uzağa ve geri gittiğinde, günlükte yalnızca canlı tutulmayan sayfaların günlük girişleri tutulur. Sayfaların canlı tutulması hakkında tartışma için, bu konunun ilerleyen kısımlarında [sayfa ömrü ve günlük](#PageLifetime) bölümüne bakın.

Varsayılan olarak, <xref:System.Windows.Controls.Page> Internet Explorer 'ın **son sayfalar** listesinde görünen her bir metın, için URI 'dir <xref:System.Windows.Controls.Page> . Çoğu durumda bu, kullanıcıya özellikle anlamlı değildir. Neyse ki, aşağıdaki seçeneklerden birini kullanarak metni değiştirebilirsiniz:

1. İliştirilmiş `JournalEntry.Name` öznitelik değeri.

2. `Page.Title`Öznitelik değeri.

3. `Page.WindowTitle`Geçerli için öznitelik değeri ve URI <xref:System.Windows.Controls.Page> .

4. Geçerli için URI <xref:System.Windows.Controls.Page> . (Varsayılan)

Seçeneklerin listelenme sırası, metni bulmak için öncelik sırasına göre eşleşir. Örneğin, `JournalEntry.Name` ayarlandıysa, diğer değerler yok sayılır.

Aşağıdaki örnek, `Page.Title` bir günlük girişi için görüntülenen metni değiştirmek için özniteliğini kullanır.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>WPF kullanarak günlükte gezinme

Bir Kullanıcı, Internet Explorer 'daki **geri**, **Ileri**ve **son sayfaları** kullanarak günlüğe gidebilse de, WPF tarafından sunulan hem bildirime dayalı hem de programlama mekanizmalarını kullanarak günlükte gezinebilirsiniz. Bunu yapmak için bir neden, sayfalarınızda özel gezinti 'leri sağlamaktır.

Tarafından sunulan gezinti komutlarını kullanarak bildirimli olarak günlük gezintisi desteği ekleyebilirsiniz <xref:System.Windows.Input.NavigationCommands> . Aşağıdaki örnek, gezinti komutunun nasıl kullanılacağını göstermektedir `BrowseBack` .

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Sınıfının aşağıdaki üyelerinden birini kullanarak günlüğe programlı bir şekilde gidebilirsiniz <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Günlük Ayrıca, bu konunun ilerleyen kısımlarında bulunan [Içerik durumunu gezinti geçmişiyle tutma](#RetainingContentStateWithNavigationHistory) bölümünde anlatıldığı gibi programlı bir şekilde yönetilebilir.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Sayfa ömrü ve günlüğü

Grafik, animasyon ve medya dahil zengin içerik içeren birden çok sayfalı bir XBAP düşünün. Özellikle video ve ses medyası kullanılıyorsa, bu gibi sayfalar için bellek ayak izi oldukça büyük olabilir. Bu tür bir XBAP, Journal 'ın gezindiği sayfaları "anımsar" olarak, büyük ve belirgin bir bellek miktarını hızla tüketebilir.

Bu nedenle, günlüğün varsayılan davranışı, <xref:System.Windows.Controls.Page> bir nesneye yönelik bir başvuru yerine her bir günlük girişinde meta verileri depolamadır <xref:System.Windows.Controls.Page> . Bir günlük girişi gezindiği zaman, <xref:System.Windows.Controls.Page> belirtilen yeni bir örneğini oluşturmak için meta verileri kullanılır <xref:System.Windows.Controls.Page> . Sonuç olarak, her bir <xref:System.Windows.Controls.Page> gezinerek aşağıdaki şekilde gösterilen yaşam süresi vardır.

![Sayfa ömrü](./media/navigation-overview/navigated-page-lifetime.png "Bu, bir sayfa gezindiği zaman ömrünü gösterir.")

Varsayılan günlük kaydı davranışının kullanılması bellek tüketimine kaydedebilse de, sayfa başına işleme performansı azaltılabilir; bir yeniden örnekleniyor <xref:System.Windows.Controls.Page> , özellikle çok sayıda içerik varsa zaman yoğunluğu olabilir. Günlükteki bir örneği tutmanız gerekiyorsa <xref:System.Windows.Controls.Page> , bunu yapmak için iki teknikte çizim yapabilirsiniz. İlk olarak, yöntemini çağırarak program aracılığıyla bir <xref:System.Windows.Controls.Page> nesneye gidebilirsiniz <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> .

İkinci olarak, WPF 'nin bir örneğini, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.KeepAlive%2A> özelliği olarak ayarlayarak `true` (varsayılan olarak `false` ) belirtebilirsiniz. Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Controls.Page.KeepAlive%2A> biçimlendirme içinde bildirimli olarak ayarlayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Etkin tutulan bir yaşam süresi, olmayan bir sunucudan daha çok <xref:System.Windows.Controls.Page> farklıdır. Canlı olarak tutulan bir ilk kez <xref:System.Windows.Controls.Page> , yalnızca <xref:System.Windows.Controls.Page> canlı tutulmayan bir gibi oluşturulur. Ancak, bir öğesinin bir örneği <xref:System.Windows.Controls.Page> günlüğe korunduğu için, günlükte kaldığı sürece hiçbir zaman yeniden örneklenemez. Sonuç olarak, bir ' ın <xref:System.Windows.Controls.Page> her gezinilişinde çağrılması gereken bir başlatma mantığı varsa <xref:System.Windows.Controls.Page> , onu oluşturucudan olay için bir işleyiciye taşımalısınız <xref:System.Windows.FrameworkElement.Loaded> . Aşağıdaki şekilde gösterildiği gibi, <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.FrameworkElement.Unloaded> olayları sırasıyla ve kaynağından her bir gezinilişinde, ve olayları yine de oluşturulur <xref:System.Windows.Controls.Page> .

![Yüklenen ve yüklenmeyen olaylar tetiklenir](./media/navigation-overview/loaded-and-unloaded-events.png "Yüklenen ve yüklenmeyen olaylar, bir sayfaya ve öğesinden gidildiği zaman tetiklenir.")

Bir, <xref:System.Windows.Controls.Page> etkin tutulmazsa, aşağıdakilerden birini yapmanız gerekmez:

- Bir başvuruyu veya bunun herhangi bir bölümünü saklayın.

- Olay işleyicilerini, tarafından uygulanmayan olaylarla kaydedin.

Bunlardan herhangi birini yapmak, <xref:System.Windows.Controls.Page> günlükten kaldırıldıktan sonra bile, bellekte bekletilmeye zorlayan başvurular oluşturur.

Genel olarak, <xref:System.Windows.Controls.Page> etkin tutmanın varsayılan davranışını tercih etmelisiniz <xref:System.Windows.Controls.Page> . Ancak, bu, sonraki bölümde ele alınan durum etkilerine sahiptir.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Içerik durumunu gezinti geçmişi ile koruma

Bir, <xref:System.Windows.Controls.Page> etkin tutulmazsa ve kullanıcıdan veri toplayacak denetimler içeriyorsa, bir kullanıcı tarafından uzaklaştığında ve geri gittiğinde verilere ne olur <xref:System.Windows.Controls.Page> ? Kullanıcı deneyimi perspektifinden, Kullanıcı daha önce girdikleri verileri görmeyi bekler. Ne yazık ki her bir gezinmede yeni bir örneği <xref:System.Windows.Controls.Page> oluşturulduğundan, verileri toplayan denetimler yeniden oluşturulur ve veriler kaybolur.

Neyse ki, günlük <xref:System.Windows.Controls.Page> Denetim verileri de dahil olmak üzere gezinmeler genelinde verileri hatırlama desteği sağlar. Özellikle, her biri için günlük girdisi, <xref:System.Windows.Controls.Page> ilişkili durum için geçici bir kapsayıcı olarak davranır <xref:System.Windows.Controls.Page> . Aşağıdaki adımlarda, ' den çıkıldığında bu desteğin nasıl kullanıldığı gösterilmektedir <xref:System.Windows.Controls.Page> :

1. Geçerli bir giriş <xref:System.Windows.Controls.Page> günlüğüne eklenir.

2. Durumu, <xref:System.Windows.Controls.Page> arka yığına eklenen bu sayfanın Günlük girdisiyle birlikte depolanır.

3. Yeni ' <xref:System.Windows.Controls.Page> ye gidildi.

Sayfaya <xref:System.Windows.Controls.Page> geri gidildiği zaman, günlük kullanılarak aşağıdaki adımlar gerçekleşir:

1. <xref:System.Windows.Controls.Page>(Arka yığındaki en üst günlük girdisi) örneği oluşturulur.

2. , <xref:System.Windows.Controls.Page> İçin günlük girdisiyle depolanan durumla yenilenir <xref:System.Windows.Controls.Page> .

3. , <xref:System.Windows.Controls.Page> Öğesine geri gidildi.

WPF, aşağıdaki denetimler bir üzerinde kullanıldığında otomatik olarak bu desteği kullanır <xref:System.Windows.Controls.Page> :

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

Bir <xref:System.Windows.Controls.Page> Bu denetimleri kullanıyorsa, bunlara girilen veriler, <xref:System.Windows.Controls.Page> aşağıdaki şekilde **sık kullanılan renkle** gösterildiği gibi, gezinmeler arasında hatırlanır <xref:System.Windows.Controls.ListBox> .

![Durumu hatırlayacağı denetimlerin bulunduğu sayfa](./media/navigation-overview/data-remembered-across-page-navigations.png "Girilen veriler sayfa gezginlerine göre hatırlanır.")

Bir <xref:System.Windows.Controls.Page> , önceki listede bulunanlar dışında bir denetim varsa veya durum özel nesnelerde depolandığında, günlüğün gezginler genelinde durumu anımsamasını sağlamak için kod yazmanız gerekir <xref:System.Windows.Controls.Page> .

Gezinmeler genelinde küçük bir durum parçalarını hatırlamanız gerekiyorsa <xref:System.Windows.Controls.Page> , <xref:System.Windows.DependencyProperty> <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> meta veri bayrağıyla yapılandırılan bağımlılık özelliklerini (bkz.) kullanabilirsiniz.

<xref:System.Windows.Controls.Page>Gezinmeler genelinde hatırlamanız gereken durum birden çok veri parçasına sahip olursa, eyaletinizi tek bir sınıfta kapsüllemek ve arabirimi uygulamak için daha az kod yoğunluğu sağlayabilirsiniz <xref:System.Windows.Navigation.IProvideCustomContentState> .

Tek tek bir için farklı durumlar arasında gezinmeniz gerekirse, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> ve ' yi kullanabilirsiniz <xref:System.Windows.Navigation.IProvideCustomContentState> <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> .

<a name="Cookies"></a>

### <a name="cookies"></a>Tanımlama bilgileri

WPF uygulamalarının verileri depolayabileceği diğer bir yöntem, ve yöntemleri kullanılarak oluşturulan, güncellenen ve silinen tanımlama bilgileriyle yapılır <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> . WPF 'de oluşturabileceğiniz tanımlama bilgileri, diğer Web uygulaması türlerinin kullandığı tanımlama bilgilerine sahiptir; tanımlama bilgileri, uygulama oturumları sırasında veya üzerinde bir istemci makinesinde bir uygulama tarafından depolanan rastgele veri parçalarından oluşur. Tanımlama bilgisi verileri genellikle aşağıdaki biçimde bir ad/değer çifti biçimini alır.

*Ad* `=` *Değer*

Veriler geçirildiğinde <xref:System.Windows.Application.SetCookie%2A> , <xref:System.Uri> tanımlama bilgisinin ayarlanması gereken konumun yanı sıra, bellek içinde bir tanımlama bilgisi oluşturulur ve yalnızca geçerli uygulama oturumunun süresi boyunca kullanılabilir. Bu tür tanımlama bilgisine *oturum tanımlama bilgisi*denir.

Bir tanımlama bilgisini uygulama oturumlarında depolamak için, aşağıdaki biçimi kullanarak tanımlama bilgisine bir sona erme tarihi eklenmelidir.

*Ad* `=` *Değer*`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Son kullanma tarihine sahip bir tanımlama bilgisi, tanımlama bilgisi süresi dolana kadar geçerli Windows yüklemesinin Temporary Internet Files klasöründe depolanır. Bu tür bir tanımlama bilgisi, uygulama oturumlarında devam ettiğinden *kalıcı tanımlama bilgisi* olarak bilinir.

Yöntemini çağırarak hem oturum hem de kalıcı tanımlama bilgilerini, <xref:System.Windows.Application.GetCookie%2A> <xref:System.Uri> tanımlama bilgisinin yöntemiyle ayarlandığı konumu geçirerek alırsınız <xref:System.Windows.Application.SetCookie%2A> .

Aşağıdakiler, WPF 'de tanımlama bilgilerinin desteklediği bazı yollardır:

- WPF tek başına uygulamaları ve XBAP 'ler, tanımlama bilgilerini oluşturup yönetebilir.

- Bir XBAP tarafından oluşturulan tanımlama bilgilerine tarayıcıdan erişilebilir.

- Aynı etki alanındaki XBAP 'ler tanımlama bilgilerini oluşturup paylaşabilir.

- Aynı etki alanındaki XBAP ve HTML sayfaları tanımlama bilgilerini oluşturup paylaşabilir.

- XBAP 'ler ve gevşek sayfalar Web istekleri yaparken tanımlama bilgileri gönderilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

- Hem üst düzey XBAP 'ler hem de IFRAME 'lerde barındırılan XBAP, tanımlama bilgilerine erişebilir.

- WPF 'de tanımlama bilgisi desteği, desteklenen tüm tarayıcılarda aynıdır.

- Internet Explorer 'da, tanımlama bilgileriyle ilgili olan P3P ilkesi, özellikle birinci taraf ve üçüncü taraf XBAP 'ler açısından WPF tarafından kabul edilir.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Yapılandırılmış gezinti

Verileri birinden diğerine geçirmeniz gerekirse <xref:System.Windows.Controls.Page> , verileri parametresiz bir oluşturucusuna bağımsız değişken olarak geçirebilirsiniz <xref:System.Windows.Controls.Page> . Bu tekniği kullanırsanız, canlı tutmanız gerektiğini unutmayın <xref:System.Windows.Controls.Page> ; Aksi takdirde, ' a bir sonraki sefer, <xref:System.Windows.Controls.Page> WPF <xref:System.Windows.Controls.Page> parametresiz oluşturucuyu kullanarak tarafından yeniden başlatılır.

Alternatif olarak, <xref:System.Windows.Controls.Page> geçirilmesi gereken verilerle ayarlanmış özellikleri de uygulayabilirsiniz. Bununla birlikte, <xref:System.Windows.Controls.Page> verilerin kendisine gezindiği bir şekilde geri iletilmesi gerektiğinde, şeyler karmaşık hale gelir <xref:System.Windows.Controls.Page> . Bu sorun, gezintinin <xref:System.Windows.Controls.Page> , ' den sonra geri döndürüldüğünden emin olmak için mekanizmaların yerel olarak desteklemediği bir sorundur. Temelde, gezinme çağrı/döndürme semantiğini desteklemez. Bu sorunu çözmek için WPF, <xref:System.Windows.Navigation.PageFunction%601> bir tarafından <xref:System.Windows.Controls.Page> öngörülebilir ve yapılandırılmış bir biçimde döndürüldüğünden emin olmak için kullanabileceğiniz sınıfı sağlar. Daha fazla bilgi için bkz. [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow sınıfı

Bu noktada, gezinilebilir içeriğe sahip uygulamalar oluşturmak için en büyük olasılıkla kullanabileceğiniz Gezinti hizmetlerinin gamutu olduğunu gördünüz. Bu hizmetler, XBAP 'ler ile sınırlı olmamakla birlikte, XBAP bağlamında ele alınmıştır. Modern işletim sistemleri ve Windows uygulamaları, tek başına uygulamalara tarayıcı stili gezinme eklemek için modern kullanıcıların tarayıcı deneyiminden yararlanır. Ortak örnekler şunlardır:

- **Sözcük eşanlamlılar sözlüğü**: kelime seçeneklerine gitme.

- **Dosya Gezgini**: dosya ve klasörlerde gezin.

- **Sihirbazlar**: karmaşık bir görevi, arasında gezinilemeyen birden çok sayfaya ayırma. Windows özelliklerinin eklenmesini ve kaldırılmasını işleyen Windows Bileşenleri Sihirbazı bir örnektir.

Tek başına uygulamalarınıza tarayıcı stili gezinme eklemek için <xref:System.Windows.Navigation.NavigationWindow> sınıfını kullanabilirsiniz. <xref:System.Windows.Navigation.NavigationWindow>' dan türetilir <xref:System.Windows.Window> ve bunu XBAP 'ın sağladığı gezinti için aynı desteğe genişletir. <xref:System.Windows.Navigation.NavigationWindow>Tek başına uygulamanızın ana penceresi veya iletişim kutusu gibi ikincil bir pencere olarak kullanabilirsiniz.

<xref:System.Windows.Navigation.NavigationWindow>, WPF 'de (,, vb.) en üst düzey sınıflarda olduğu gibi, bir <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> biçimlendirme ve arka plan kod birleşimini kullanın. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Bu kod <xref:System.Windows.Navigation.NavigationWindow> , açıldığında otomatik olarak bir <xref:System.Windows.Controls.Page> (Ana sayfa. xaml) öğesine giden bir oluşturur <xref:System.Windows.Navigation.NavigationWindow> . <xref:System.Windows.Navigation.NavigationWindow>Ana uygulama penceresuyorsa, öğesini `StartupUri` başlatmak için özniteliğini kullanabilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Aşağıdaki şekilde, <xref:System.Windows.Navigation.NavigationWindow> tek başına bir uygulamanın ana penceresi olarak gösterilir.

![Ana pencere](./media/navigation-overview/navigation-window-as-main-window.png "Ana pencere olarak gezinti penceresi")

Bu şekilde, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow> önceki örnekteki uygulama kodunda ayarlanmasa bile, ' ın bir başlığına sahip olduğunu görebilirsiniz. Bunun yerine, başlık <xref:System.Windows.Controls.Page.WindowTitle%2A> aşağıdaki kodda gösterilen özelliğini kullanarak ayarlanır.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

<xref:System.Windows.Controls.Page.WindowWidth%2A>Ve özelliklerinin ayarlanması <xref:System.Windows.Controls.Page.WindowHeight%2A> de ' nı etkiler <xref:System.Windows.Navigation.NavigationWindow> .

Genellikle, <xref:System.Windows.Navigation.NavigationWindow> davranışını veya görünümünü özelleştirmeniz gerektiğinde kendi uygulamanızı uygulamanız gerekir. Aksi takdirde, bir kısayolu kullanabilirsiniz. Tek başına bir uygulamada olarak bir öğesinin paket URI 'sini belirtirseniz, <xref:System.Windows.Controls.Page> <xref:System.Windows.Application.StartupUri%2A> <xref:System.Windows.Application> otomatik olarak bir için bir oluşturur <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> . Aşağıdaki biçimlendirmede bunun nasıl etkinleştirileceği gösterilmektedir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

İletişim kutusu gibi bir ikincil uygulama penceresinin olmasını istiyorsanız <xref:System.Windows.Navigation.NavigationWindow> , bu kodu açmak için aşağıdaki örnekteki kodu kullanabilirsiniz.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Aşağıdaki şekilde sonuç gösterilmektedir.

![İletişim kutusu](./media/navigation-overview/navigation-window-as-dialog-box.png "İletişim kutusu olarak gezinti penceresi")

Gördüğünüz gibi, <xref:System.Windows.Navigation.NavigationWindow> kullanıcıların günlükte gezinmesine izin veren Internet Explorer stili **geri** ve **İleri** düğmelerini görüntüler. Bu düğmeler, aşağıdaki şekilde gösterildiği gibi aynı kullanıcı deneyimini sağlar.

![NavigationWindow 'daki geri ve Ileri düğmeleri](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Gezinti penceresinde geri ve Ileri düğmeleri")

Sayfalarınız kendi günlük gezintisi desteğini ve Kullanıcı arabirimini sağladıysanız, özelliğinin değerini olarak ayarlayarak, tarafından görünen **geri** ve **İleri** düğmelerini gizleyebilirsiniz <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` .

Alternatif olarak, kendi öğesini değiştirmek için WPF 'de özelleştirme desteğini de kullanabilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> .

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame sınıfı

Hem tarayıcı hem de <xref:System.Windows.Navigation.NavigationWindow> gezinilebilir içerik barındıran Windows. Bazı durumlarda, uygulamalarda bir pencerenin tamamında barındırılması gerekmeyen içerikler vardır. Bunun yerine, bu içerik diğer içeriğin içinde barındırılır. Sınıfını kullanarak, gezinebilir içeriği diğer içeriklere ekleyebilirsiniz <xref:System.Windows.Controls.Frame> . <xref:System.Windows.Controls.Frame>, ve XBAP desteği sağlar <xref:System.Windows.Navigation.NavigationWindow> .

Aşağıdaki örnek <xref:System.Windows.Controls.Frame> öğesi kullanılarak bildirimli olarak öğesine nasıl ekleneceğini gösterir <xref:System.Windows.Controls.Page> `Frame` .

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Bu biçimlendirme, ' `Source` ın başlangıçta gideceği `Frame` bir paket URI 'si olan öğesinin özniteliğini ayarlar <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> . Aşağıdaki şekilde, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> birden çok sayfa arasında gezindiği olan bir XBAP gösterilmektedir.

![Birden çok sayfa arasında gezindiği çerçeve](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Bu, birden çok sayfa arasında bir çerçeve gezintisi gösterir.")

Yalnızca <xref:System.Windows.Controls.Frame> bir içeriğinin içinde kullanmak zorunda değilsiniz <xref:System.Windows.Controls.Page> . Ayrıca, a içeriğinin içinde barındırmak için de ortaktır <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> .

Varsayılan olarak, <xref:System.Windows.Controls.Frame> yalnızca kendi günlüğünü başka bir günlük yokluğunda kullanır. , <xref:System.Windows.Controls.Frame> Bir veya BIR XBAP içinde barındırılan içeriğin parçasıysa <xref:System.Windows.Navigation.NavigationWindow> , <xref:System.Windows.Controls.Frame> veya XBAP 'ye ait olan günlüğü kullanır <xref:System.Windows.Navigation.NavigationWindow> . Bazen, ancak <xref:System.Windows.Controls.Frame> kendi günlüğünden sorumlu olması gerekebilir. Bunun bir nedeni, tarafından barındırılan sayfalarda Journal gezintisine izin vermektedir <xref:System.Windows.Controls.Frame> . Bu, aşağıdaki şekilde gösterilmiştir.

![Çerçeve ve sayfa diyagramı](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Bu, bir çerçeve tarafından barındırılan sayfaların içindeki günlük gezintisini gösterir.")

Bu durumda, <xref:System.Windows.Controls.Frame> öğesinin özelliğini olarak ayarlayarak kendi günlüğünü kullanacak şekilde yapılandırabilirsiniz <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> . Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Aşağıdaki şekilde kendi günlüğünü kullanan bir içinde gezinmenin etkisi gösterilmektedir <xref:System.Windows.Controls.Frame> .

![Kendi günlüğünü kullanan bir çerçeve](./media/navigation-overview/frame-uses-its-own-journal.png "Bu, kendi günlüğünü kullanan bir çerçeve içinde gezinmenin etkisini gösterir.")

Günlük girişlerinin, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Internet Explorer yerine, üzerinde gezinerek gösterildiğine dikkat edin <xref:System.Windows.Controls.Frame> .

> [!NOTE]
> <xref:System.Windows.Controls.Frame>, Bir içinde barındırılan içeriğin parçasıysa <xref:System.Windows.Window> <xref:System.Windows.Controls.Frame> kendi günlüğünü kullanır ve sonuç olarak kendi gezinmesini görüntüler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

Kullanıcı deneyiminizin, <xref:System.Windows.Controls.Frame> gezinmeyi göstermeden kendi günlüğünü sağlaması gerekiyorsa, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' yi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olarak ayarlayarak gezinmeyi gizleyebilirsiniz <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> <xref:System.Windows.Visibility.Hidden> . Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Gezinti konakları

<xref:System.Windows.Controls.Frame>ve <xref:System.Windows.Navigation.NavigationWindow> , gezinti konakları olarak bilinen sınıflardır. *Gezinti ana bilgisayarı* , içeriğe gidebileceğiniz ve içeriği görüntüleyebilen bir sınıftır. Bunu gerçekleştirmek için, her bir gezinti ana bilgisayarı kendi <xref:System.Windows.Navigation.NavigationService> ve günlüğünü kullanır. Bir gezinti konağının temel yapımı aşağıdaki şekilde gösterilmiştir.

![Gezgin diyagramları](./media/navigation-overview/navigation-host-construction.png "Bir gezinti ana bilgisayarının temel yapımı")

Temelde, bu, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> bir XBAP 'nin tarayıcıda barındırılırken sağladığı gezinti desteğinin aynısını sağlamasına izin verir.

<xref:System.Windows.Navigation.NavigationService>Ve bir günlüğü kullanmanın yanı sıra, gezinti konakları, uygulayan aynı üyeleri uygular <xref:System.Windows.Navigation.NavigationService> . Bu, aşağıdaki şekilde gösterilmiştir.

![Bir çerçevedeki ve NavigationWindow içindeki bir günlük](./media/navigation-overview/navigation-window-and-frame.png "Gezinti penceresi ve çerçeve")

Bu, gezinti desteğini doğrudan bunlara karşı programbırakmanıza olanak tanır. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]' De barındırılan bir için özel bir gezinti sağlamanız gerekiyorsa bunu göz önünde bulundurabilir <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> . Ayrıca, her iki tür de (,) ve (,) dahil olmak üzere ek, gezintide ilgili Üyeler uygular, `BackStack` <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> Bu da <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> `ForwardStack` <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> arka yığında ve ileriye doğru yığındaki günlük girişlerini listeletmeniz sağlar.

Daha önce belirtildiği gibi, bir uygulama içinde birden çok günlük bulunabilir. Aşağıdaki şekilde, bunun gerçekleşene zaman gerçekleşebileceğinizi bir örnek verilmiştir.

![Bir uygulama içinde birden çok günlük](./media/navigation-overview/multiple-journals-in-one-application.png "Bu, bir uygulamada birden fazla günlük örneğine bir örnektir.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML sayfaları dışındaki Içeriğe gitme

Bu konu başlığı altında, <xref:System.Windows.Controls.Page> WPF 'nin çeşitli gezinti yeteneklerini göstermek için Pack XBAP 'ler kullanılmıştır. Ancak, bir <xref:System.Windows.Controls.Page> uygulamaya derlenen tek içerik türü değildir ve Pack XBAP, içeriği belirlemenin tek yolu değildir.

Bu bölümde gösterildiği gibi, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar, HTML dosyaları ve nesneler 'e de gidebilirsiniz.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Gevşek XAML dosyalarına gitme

Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya, aşağıdaki özelliklere sahip bir dosyadır:

- Yalnızca içerir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (yani, kod yok).

- Uygun bir ad alanı bildirimine sahiptir.

- . Xaml dosya adı uzantısına sahiptir.

Örneğin, gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya olan Person. xaml olarak depolanan aşağıdaki içeriği göz önünde bulundurun.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Dosyaya çift tıkladığınızda tarayıcı açılır ve ' a gider ve içeriği görüntüler. Bu, aşağıdaki şekilde gösterilmiştir.

![İçeriği Person. XAML dosyasında görüntüleme](./media/navigation-overview/contents-of-person-xaml-file.png "Person. XAML dosyasının içeriğini gösterir.")

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Aşağıdaki listeden gevşek bir dosya görüntüleyebilirsiniz:

- Yerel makinedeki, intranetteki veya Internet 'teki bir Web sitesi.

- Evrensel adlandırma kuralı (UNC) dosya paylaşma.

- Yerel disk.

Gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya tarayıcının sık kullanılanlarına eklenebilir veya tarayıcının giriş sayfası olabilir.

> [!NOTE]
> Gevşek sayfaları yayımlama ve başlatma hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

Gevşek bir sınırlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , yalnızca kısmi güvende çalışmak için güvenli olan içeriği barındırmanıza olanak sağlar. Örneğin, `Window` gevşek bir dosyanın kök öğesi olamaz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Çerçeve kullanarak HTML dosyalarına gitme

Tahmin edebileceğiniz gibi, HTML 'ye de gidebilirsiniz. Yalnızca http düzenini kullanan bir URI sağlamanız gerekir. Örneğin, aşağıdaki, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame> HTML sayfasına giden bir gösterir.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

HTML 'ye gitmek için özel izinler gerekir. Örneğin, Internet bölgesi kısmi güven güvenlik korumalı alanı ' nda çalışan bir XBAP 'den geziniyorsunuz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser denetimini kullanarak HTML dosyalarına gitme

<xref:System.Windows.Controls.WebBrowser>DENETIM HTML belgesi barındırma, gezinti ve betik/yönetilen kod birlikte çalışabilirliği destekler. Denetimle ilgili ayrıntılı bilgi için <xref:System.Windows.Controls.WebBrowser> bkz <xref:System.Windows.Controls.WebBrowser> ..

Benzer <xref:System.Windows.Controls.Frame> şekilde, HTML 'ye gidildiğinde <xref:System.Windows.Controls.WebBrowser> özel izinler gerekir. Örneğin, kısmi güven uygulamasından yalnızca kaynak sitesinde bulunan HTML 'ye gidebilirsiniz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Özel nesnelere gitme

Özel nesneler olarak depolanan verileriniz varsa, bu verileri görüntülemenin bir yolu, <xref:System.Windows.Controls.Page> Bu nesnelere bağlanan içeriğe sahip bir oluşturmak (bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md)). Yalnızca nesneleri görüntüleyen bir sayfanın tamamını oluşturmak için ek yüke gerek yoksa, bunun yerine doğrudan bunlara gidebilirsiniz.

`Person`Aşağıdaki kodda uygulanan sınıfı göz önünde bulundurun.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Bu sayfaya gitmek için <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi yöntemini çağırın.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Aşağıdaki şekilde sonuç gösterilmektedir.

![Bir sınıfa giden bir sayfa](./media/navigation-overview/page-navigates-to-an-object.png "Bu, bir nesnesine giden bir sayfa örneğidir.")

Bu şekilde, hiçbir şeyin yararlı görüntülendiğini görebilirsiniz. Aslında, görüntülenen değer `ToString` **kişi** nesnesi için yöntemin dönüş değeridir; varsayılan olarak, WPF 'in nesneyi temsil etmek için kullanabileceği tek değerdir. `ToString`Daha anlamlı bilgiler döndürmek için yöntemi geçersiz kılabilir, ancak yalnızca bir dize değeri olmaya devam eder. WPF 'in sunum özelliğinden yararlanan kullanabileceğiniz bir teknik, veri şablonu kullanmaktır. WPF 'nin belirli bir türdeki nesneyle ilişkilendirebileceğiniz bir veri şablonu uygulayabilirsiniz. Aşağıdaki kod, nesnesi için bir veri şablonu gösterir `Person` .

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Burada, veri şablonu, `Person` `x:Type` özniteliğinde biçimlendirme uzantısı kullanılarak türle ilişkilendirilir `DataType` . Veri şablonu daha sonra `TextBlock` öğeleri (bkz <xref:System.Windows.Controls.TextBlock> .) sınıfın özelliklerine bağlar `Person` . Aşağıdaki şekilde nesnesinin güncelleştirilmiş görünümü gösterilmektedir `Person` .

![Veri şablonu olan bir sınıfa gitme](./media/navigation-overview/navigating-to-a-class.png "Veri şablonu olan bir sınıfa gitme.")

Bu tekniğin avantajı, nesneleri uygulamanızda her yerde tutarlı bir şekilde göstermek için veri şablonunu yeniden kullanabilerek elde ettiğiniz tutardır.

Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Güvenlik

WPF gezinti desteği, XBAP 'lerin Internet üzerinden gezinmesine olanak sağlar ve uygulamaların üçüncü taraf içeriği barındıralmasına izin verir. Hem uygulama hem de kullanıcıların zararlı davranışlardan korunması için WPF, [güvenlik](../security-wpf.md) ve [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md)bölümünde ele alınan çeşitli güvenlik özellikleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Uygulama Yönetimine Genel Bakış](application-management-overview.md)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
- [Gezinti Topolojilerine Genel Bakış](navigation-topologies-overview.md)
- [Nasıl Yapılır Konuları](navigation-how-to-topics.md)
- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
