---
title: Gezintiye Genel Bakış
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
ms.openlocfilehash: 24b872fcf58db3ef0ef7d04165129804dc46d641
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364279"
---
# <a name="navigation-overview"></a>Gezintiye Genel Bakış

Windows Presentation Foundation (WPF), iki tür uygulama için kullanılabilen tarayıcı stili gezinmeyi destekler: tek başına uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Gezinti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için içerik paketlemek için <xref:System.Windows.Controls.Page> sınıfını sağlar. ' Yi kullanarak bir veya <xref:System.Windows.Controls.Page> kullanarak bir veya <xref:System.Windows.Navigation.NavigationService>programlı olarak bir ile diğerine gidebilirsiniz. <xref:System.Windows.Documents.Hyperlink> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], öğesinden gelen ve geri gitmek için kullanılan sayfaları hatırlamaları için günlüğü kullanır.

<xref:System.Windows.Controls.Page>,, ve Journal, tarafından [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]sunulan gezinti desteğinin çekirdeğini oluşturur. <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> Bu genel bakış, gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyalar, [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyalar ve nesneler için gezinti içeren gelişmiş gezinti desteğini kullanmadan önce bu özellikleri ayrıntılı olarak ele alır.

> [!NOTE]
> Bu konuda, "Browser" terimi, yalnızca şu anda ve Firefox içeren [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] uygulamaları barındırabilen tarayıcılara başvurur. Belirli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellikler yalnızca belirli bir tarayıcı tarafından desteklendiğinde, tarayıcı sürümüne başvurulur.

## <a name="navigation-in-wpf-applications"></a>WPF uygulamalarında gezinme

Bu konu, içindeki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temel gezinti özelliklerine genel bir bakış sağlar. Bu yetenekler [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], hem tek başına uygulamalar için hem de bu konu, bu konuda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]olan bağlamı içinde yer almaktadır.

> [!NOTE]
> Bu konu, nasıl derleme ve dağıtım [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]yapılacağını ele almaz. Hakkında [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).

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

İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].NET Framework nesneleri, özel nesneleri, numaralandırma değerlerini, kullanıcı denetimlerini, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyaları içeren çeşitli içerik türlerine gidebilirsiniz. Bununla birlikte, içerik paketlemeyi kullanmanın en yaygın ve uygun yolunun kullanarak <xref:System.Windows.Controls.Page>olduğunu fark edeceksiniz. Ayrıca, <xref:System.Windows.Controls.Page> görünüşlerinin geliştirilmesi ve geliştirmeyi basitleştirmek için gezintiye özgü özellikler uygular.

Kullanarak <xref:System.Windows.Controls.Page>, aşağıdaki gibi bir biçimlendirme kullanarak bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeriğe göre gezinebilir bir içerik sayfası uygulayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Biçimlendirme <xref:System.Windows.Controls.Page> içinde `Page` [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] uygulanan bir, kök öğesi olarak sahiptir ve ad alanı bildirimi gerektirir. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` Öğesi, gitmek ve göstermek istediğiniz içeriği içerir. Aşağıdaki biçimlendirmede gösterildiği gibi, `Page.Content` özellik öğesini ayarlayarak içerik eklersiniz.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content`yalnızca bir alt öğe içerebilir; Yukarıdaki örnekte, içerik tek bir dizedir, "Merhaba, sayfa!" Uygulamada, içeriğinizi eklemek ve oluşturmak için genellikle alt öğe (bkz. [Düzen](../advanced/layout.md)) olarak bir düzen denetimi kullanırsınız.

Bir `Page` öğenin alt öğeleri bir <xref:System.Windows.Controls.Page> ve içeriği olarak kabul edilir ve sonuç olarak açık `Page.Content` bildirimi kullanmanız gerekmez. Aşağıdaki biçimlendirme, önceki örneğe bildirime dayalı olarak eşdeğerdir.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

Bu durumda, `Page.Content` `Page` öğesinin alt öğeleriyle otomatik olarak ayarlanır. Daha fazla bilgi için bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).

Yalnızca <xref:System.Windows.Controls.Page> biçimlendirme, içerik görüntülemek için yararlıdır. Ancak, ayrıca <xref:System.Windows.Controls.Page> , kullanıcıların sayfayla etkileşime geçmesini sağlayan denetimleri görüntüleyebilir ve olayları işleyerek ve uygulama mantığını çağırarak kullanıcı etkileşimine yanıt verebilir. Etkileşimli <xref:System.Windows.Controls.Page> bir şekilde, aşağıdaki örnekte gösterildiği gibi biçimlendirme ve arka plan kod birleşimi kullanılarak uygulanır.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Biçimlendirme dosyası ve arka plan kod dosyasının birlikte çalışmasına izin vermek için aşağıdaki yapılandırma gereklidir:

- Biçimlendirme ' de, `Page` öğesi `x:Class` özniteliğini içermelidir. Uygulama `x:Class` oluşturulduğunda, biçimlendirme dosyasında bulunan ' dan <xref:System.Windows.Controls.Page> türetilmiş ve `x:Class` özniteliği tarafından belirtilen ada [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] sahip bir `partial` sınıf oluşturulmasına neden olur. Bu, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ) için bir ad alanı bildiriminin eklenmesini gerektirir. `partial` Oluşturulan`InitializeComponent`sınıf, olayları kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağırılır.

- Arka plan kod içinde, sınıf, biçimlendirme içindeki `partial` `x:Class` özniteliği tarafından belirtilen aynı ada sahip bir sınıf olmalıdır ve ' den <xref:System.Windows.Controls.Page>türetmelidir. Bu, arka plan kod dosyasının, uygulama oluşturulduğunda biçimlendirme dosyası için `partial` oluşturulan sınıfla ilişkilendirilmesini sağlar (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).

- Arka plan kod içinde, <xref:System.Windows.Controls.Page> sınıfının `InitializeComponent` yöntemini çağıran bir Oluşturucu uygulaması gerekir. `InitializeComponent`, biçimlendirme dosyasının oluşturulan `partial` sınıfı tarafından olayları kaydetmek ve biçimlendirmede tanımlanan özellikleri ayarlamak için uygulanır.

> [!NOTE]
> Kullanarak <xref:System.Windows.Controls.Page> [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] projenizeyenibireklediğinizde,herikibiçimlendirmevearkaplankodukullanılarakuygulanırveşuşekildebiçimlendirmevearkaplankoddosyalarıarasındakiilişkiyioluşturmak<xref:System.Windows.Controls.Page> için gerekli yapılandırmayı içerir burada açıklanmıştır.

' A <xref:System.Windows.Controls.Page>sahip olduktan sonra bu sayfaya gidebilirsiniz. Uygulamanın ilk gittiği adı <xref:System.Windows.Controls.Page> belirtmek için, Başlat <xref:System.Windows.Controls.Page>'ı yapılandırmanız gerekir.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Başlangıç sayfasını yapılandırma

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]bir tarayıcıda barındırılacak belirli bir uygulama altyapısı miktarı gerektirir. ' De [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], sınıfıgerekliuygulamaaltyapısınıkuranbiruygulamatanımınınparçasıdır(bkz.uygulamayönetiminegenelbakış).<xref:System.Windows.Application> [](application-management-overview.md)

Bir uygulama tanımı genellikle, biçimlendirme dosyası bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` öğe olarak yapılandırıldığında hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır. Aşağıda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]için uygulama tanımıdır.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

, Başlatıldığında otomatik olarak yüklenen <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>birbaşlangıcınıbelirtmek içinuygulamatanımınıkullanabilir[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Bunu, <xref:System.Windows.Application.StartupUri%2A> [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] özelliği İstenen<xref:System.Windows.Controls.Page>için ile ayarlayarak yapabilirsiniz.

> [!NOTE]
> Çoğu durumda <xref:System.Windows.Controls.Page> ,, bir uygulamayla derlenir veya bir uygulamayla birlikte dağıtılır. Bu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] gibi durumlarda <xref:System.Windows.Controls.Page> , *paketi, paket* düzenine uyan bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]olan bir paketidir. Paket [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)daha fazla ele alınmıştır. Ayrıca, aşağıda açıklanan http düzenini kullanarak içeriğe gidebilirsiniz.

Aşağıdaki örnekte gösterildiği <xref:System.Windows.Application.StartupUri%2A> gibi biçimlendirme içinde bildirimli olarak ayarlayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

Bu örnekte, `StartupUri` özniteliği, giriş sayfası. xaml tanımlayan göreli bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paket ile ayarlanır. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Başlatıldığında, giriş sayfası. xaml otomatik olarak gösterilir ve görüntülenir. Bu, bir Web sunucusundan başlatılan ' ı gösteren [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aşağıdaki şekilde gösterilmiştir.

![XBAP sayfası](./media/navigation-overview/xbap-launched-from-a-web-server.png "Bu, bir Web sunucusundan başlatılan BIR XBAP gösterir.")

> [!NOTE]
> Geliştirme ve dağıtımı [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md) ve [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konak penceresinin başlığını, genişliğini ve yüksekliğini yapılandırma

Önceki şekilden fark ettiğiniz bir şey, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]hem tarayıcının hem de sekme panelinin başlığının için olduğu şeydir. Büyük olmasının yanı sıra başlık etkileyici veya bilgilendirici değildir. Bu nedenle, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği ayarlayarak başlığı değiştirmeniz için bir yol sunar. Ayrıca, sırasıyla ve <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A>ayarlarını yaparak tarayıcı penceresinin genişlik ve yüksekliğini yapılandırabilirsiniz.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> ve<xref:System.Windows.Controls.Page.WindowHeight%2A> aşağıdaki örnekte gösterildiği gibi biçimlendirme içinde bildirimli olarak ayarlanabilir.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Sonuç aşağıdaki şekilde gösterilmiştir.

![Pencere başlığı, yükseklik, Genişlik](./media/navigation-overview/window-title-width-height.png "Bu, yapılandırabileceğiniz pencere başlığını, yüksekliğini ve genişliğini gösterir.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Köprü gezintisi

Tipik [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olarak çeşitli sayfalar oluşur. Bir sayfadan diğerine gitmenin en kolay yolu bir <xref:System.Windows.Documents.Hyperlink>kullanmaktır. Aşağıdaki biçimlendirmede gösterilen <xref:System.Windows.Documents.Hyperlink> `Hyperlink` öğesini kullanarak bildirimli <xref:System.Windows.Controls.Page> olarak bir öğesine ekleyebilirsiniz.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Bir `Hyperlink` öğesi şunları gerektirir:

- Özniteliği tarafından <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] belirtildiğigibiöğesinegitmekiçinpaketi`NavigateUri` .

- Kullanıcının gezinti işlemini başlatmak için tıklatabilecek içerik (örneğin, metin ve görüntüler) ( `Hyperlink` öğenin içerebileceği içerik için bkz <xref:System.Windows.Documents.Hyperlink>.).

Aşağıdaki şekilde ' a sahip [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olan bir <xref:System.Windows.Controls.Page> ile <xref:System.Windows.Documents.Hyperlink>gösterilmektedir.

![Köprü Içeren sayfa](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Bu, Köprüsü olan bir sayfa içeren BIR XBAP gösterir.")

Bekleneceğiniz <xref:System.Windows.Documents.Hyperlink> gibi, öğesine tıkladığınızda [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] `NavigateUri` özniteliği tarafından tanımlanan öğesine <xref:System.Windows.Controls.Page> gitme izni verilir. Ayrıca, ' deki <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]son sayfalar listesi için bir giriş ekler.[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Bu, aşağıdaki şekilde gösterilmiştir.

![Geri ve ileri düğmeleri](./media/navigation-overview/back-and-forward-navigation.png "Geri ve ileri düğmelerine gidin.")

Ayrıca, <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> bir öğesinden diğerine gezinmeyi desteklemenin yanı sıra parça gezintisini da destekler.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Parça gezintisi

*Parça gezintisi* , geçerli <xref:System.Windows.Controls.Page> ya da diğeri <xref:System.Windows.Controls.Page>içindeki bir içerik parçasına yönelik gezindir. ' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]De, içerik parçası, adlandırılmış bir öğe tarafından içerilen içeriktir. Adlandırılmış bir öğe, `Name` özniteliği ayarlanmış bir öğedir. Aşağıdaki biçimlendirme bir içerik parçası içeren `TextBlock` adlandırılmış bir öğeyi gösterir.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Bir <xref:System.Windows.Documents.Hyperlink> içerik parçasına `NavigateUri` gitmek için özniteliği şunları içermelidir:

- [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] '<xref:System.Windows.Controls.Page> Nin gidilecek içerik parçası.

- Bir "#" karakteri.

- İçerik parçasını içeren içindeki öğesinin <xref:System.Windows.Controls.Page> adı.

Bir parçanın [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biçimi aşağıdaki biçimdedir.

*PageUri* `#` *ElementName*

Aşağıda bir içerik parçasına gitmek için yapılandırılmış `Hyperlink` bir örneği gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Bu bölümde, ' de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]varsayılan parça gezintisi uygulamasının açıklanmaktadır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Ayrıca, kısmen <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> olayını işlemeyi gerektiren kendi parça gezinti düzeninizi uygulamanıza olanak tanır.

> [!IMPORTANT]
> Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalardaki parçalara gidebilirsiniz (kök öğe `Page` olarak yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme dosyaları), yalnızca sayfaların üzerinden [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)]gözatılabilir durumunda olabilir.
>
> Ancak, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir sayfa kendi parçalara gidebilir.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Gezinti hizmeti

Bir <xref:System.Windows.Documents.Hyperlink> kullanıcının belirli <xref:System.Windows.Controls.Page>bir gezinmede gezinmeyi başlatmasına olanak sağlarken, <xref:System.Windows.Navigation.NavigationService> sayfanın bulunması ve indirilmesi işi sınıfı tarafından gerçekleştirilir. Temelde, gibi istemci kodu <xref:System.Windows.Documents.Hyperlink>adına bir gezinti isteği işleme yeteneği sağlar.<xref:System.Windows.Navigation.NavigationService> Ayrıca, <xref:System.Windows.Navigation.NavigationService> bir gezinti isteğini izlemek ve etkili bir şekilde eğmek için daha yüksek düzeyde destek uygular.

Bir <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> tıklandığında,<xref:System.Windows.Controls.Page> belirtilen paketin yerini[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]bulmak ve indirmek için çağırır.[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] İndirilen <xref:System.Windows.Controls.Page> , kök nesnesi indirilen <xref:System.Windows.Controls.Page>bir örnek olan bir nesne ağacına dönüştürülür. Kök <xref:System.Windows.Controls.Page> nesneye bir başvuru, <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> özelliğinde depolanır. Gezindiği [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] içerik paketi <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliğinde depolanır, ancak <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> bu, gezindiği son sayfanın paketini [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] depolar.

> [!NOTE]
> Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamanın Şu anda birden fazla etkin <xref:System.Windows.Navigation.NavigationService>olması mümkündür. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Gezinti konakları](#Navigation_Hosts) bölümüne bakın.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Gezinti hizmeti ile programlama yoluyla gezinme

Gezinmede <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> biçimlendirme sırasında gezinme uygulanıp uygulanmadığı hakkında bilmeniz gerekmez ,çünküsizinadınızakullanır.<xref:System.Windows.Documents.Hyperlink> Yani, a <xref:System.Windows.Documents.Hyperlink> 'nın doğrudan veya dolaylı üst öğesi bir gezinti ana bilgisayarı (bkz. [gezinme Konakları](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> bir gezinti isteğini işlemek için gezinti konağının gezinti hizmetini bulup kullanabilirler.

Ancak, aşağıdakiler de dahil olmak üzere doğrudan kullanmanız <xref:System.Windows.Navigation.NavigationService> gerektiğinde durumlar vardır:

- Parametresiz bir Oluşturucu kullanarak bir <xref:System.Windows.Controls.Page> örneği oluşturmanız gerektiğinde.

- Üzerine <xref:System.Windows.Controls.Page> geçmeden önce üzerinde Özellikler ayarlamanız gerekir.

- Gezilmesi <xref:System.Windows.Controls.Page> gereken, yalnızca çalışma zamanında belirlenebilir.

Bu durumlarda, <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> nesnenin yöntemini çağırarak programlı bir şekilde gezinmeyi başlatmak için kod yazmanız gerekir. Bu, bir <xref:System.Windows.Navigation.NavigationService>başvurusu almayı gerektirir.

#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService 'e başvuru alma

[Gezinti konakları](#Navigation_Hosts) bölümünde ele alınan nedenlerden dolayı bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama birden fazla <xref:System.Windows.Navigation.NavigationService>olabilir. Bu, kodunuzun, <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Navigation.NavigationService> genellikle geçerli <xref:System.Windows.Controls.Page>olan olan bir ' ı bulmak için bir yol olması anlamına gelir. <xref:System.Windows.Navigation.NavigationService> Yöntemini`static`çağırarakbiröğesine başvurualabilirsiniz.<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> Belirli bir öğesine gidildiği için, <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> yönteminin bağımsız değişkeni <xref:System.Windows.Controls.Page> olarak öğesine bir başvuru geçirin. <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> Aşağıdaki kod, geçerli <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page>için nasıl alınacağını gösterir.

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Bir <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> için öğesini bulmak için bir kısayol olarak, özelliğini uygular. <xref:System.Windows.Controls.Page> Bu, aşağıdaki örnekte gösterilir.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Yalnızca olayını başlatan <xref:System.Windows.Navigation.NavigationService> öğesine bir başvuru alabilir. <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Controls.Page>

#### <a name="programmatic-navigation-to-a-page-object"></a>Sayfa nesnesine programlama yoluyla gezinme

Aşağıdaki örnek, <xref:System.Windows.Navigation.NavigationService> ile programlı olarak bir <xref:System.Windows.Controls.Page>öğesine gitmek için ' nin nasıl kullanılacağını gösterir. Yalnızca tek, parametresiz bir Oluşturucu <xref:System.Windows.Controls.Page> kullanılarak örneklendiği için programlı gezinme gereklidir. Parametresiz <xref:System.Windows.Controls.Page> Oluşturucusu ile aşağıdaki biçimlendirme ve kodda gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Parametresiz oluşturucusu <xref:System.Windows.Controls.Page> ile öğesine gider, aşağıdaki biçimlendirme ve kodda gösterilmiştir. <xref:System.Windows.Controls.Page>

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Bu tıklatıldığında, eksik oluşturucuyu kullanarak gezinmek ve <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi çağırmak <xref:System.Windows.Controls.Page> için ' i örnekleyerek gezinti başlatılır. <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService.Navigate%2A>bir paket <xref:System.Windows.Navigation.NavigationService> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]yerine gezinme nesnesine bir başvuru kabul eder.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Paket URI 'SI ile programlama yoluyla gezinme

Program aracılığıyla bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oluşturmanız gerekiyorsa (örneğin, paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında belirleyebilmeniz için) <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Geçerli sayfa yenileniyor

Özelliği, özelliğinde depolanan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketle aynı paketine sahipse indirilmez. <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> Geçerli sayfayı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yeniden indirmeyi zorlamak için aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Gezinti ömrü

Gördüğünüz gibi, gezintiyi başlatmak için birçok yol vardır. Gezinti başlatıldığında ve gezinme devam ederken, tarafından <xref:System.Windows.Navigation.NavigationService>uygulanan aşağıdaki olayları kullanarak gezintiyi izleyebilir ve etkileyebilirsiniz:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Yeni bir gezinti istendiğinde gerçekleşir. Gezinmeyi iptal etmek için kullanılabilir.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Bir indirme sırasında, gezinti ilerleme bilgileri sağlamak için düzenli aralıklarla gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Sayfa bulunduğunda ve indirildiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Gezinti durdurulduğunda (çağırarak <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>) veya geçerli bir gezinti sürerken yeni bir gezinti istendiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. İstenen içeriğe gidilirken bir hata ortaya çıktığında gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Gezinilmiş içerik yüklenip ayrıştırıldığında ve işlemeye başladıktan sonra gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Bir içerik parçasına Gezinti başladığında gerçekleşir, bu durum:

  - Hemen, istenen parça geçerli içeriktir.

  - Kaynak içerik yüklendikten sonra, istenen parça farklı içeriklerde yer alıyorsa.

Gezinti olayları aşağıdaki şekilde gösterilen sırayla oluşturulur.

![Sayfa gezintisi akış grafiği](./media/navigation-overview/order-of-navigation-events.png "Sayfa gezintisi olay akışı grafiği")

Genel olarak, <xref:System.Windows.Controls.Page> bu olaylar konusunda endişe yoktur. Bir uygulamanın bunlarla ilgilenmesi daha olasıdır ve bu nedenle, bu olaylar <xref:System.Windows.Application> sınıf tarafından da oluşturulur:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Her seferinde <xref:System.Windows.Navigation.NavigationService> bir olay ortaya geçirirse <xref:System.Windows.Application> , sınıf ilgili olayı oluşturur. <xref:System.Windows.Controls.Frame>ve <xref:System.Windows.Navigation.NavigationWindow> ilgili kapsamlarında gezintiyi algılamak için aynı olayları sunun.

Bazı durumlarda, <xref:System.Windows.Controls.Page> bu olaylarla ilgileniyor olabilirsiniz. Örneğin, bir <xref:System.Windows.Controls.Page> , gezintiyi kendinden uzağa <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> iptal edilip edilmeyeceğini tespit etmek için olayı işleyebilir. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Bir işleyiciyi bir <xref:System.Windows.Controls.Page>gezinti olayı ile kaydettiğinizde, önceki örnekte olduğu gibi, olay işleyicisinin kaydını da silmeniz gerekir. Aksi takdirde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Controls.Page> gezinme 'nin günlüğü kullanarak gezinmesine göre yan etkileri olabilir.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Günlükle gezinti hatırlama

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir arka yığın ve bir ileri yığını olan sayfaları anımsamak için iki yığın kullanır: Geçerli <xref:System.Windows.Controls.Page> ya da var olan <xref:System.Windows.Controls.Page>bir yeni <xref:System.Windows.Controls.Page> ya da ileri ' ye gittiğinizde, geçerli <xref:System.Windows.Controls.Page> bir *geri yığına*eklenir. Geçerli <xref:System.Windows.Controls.Page> bir öncekine <xref:System.Windows.Controls.Page>geri gittiğinizde, geçerli <xref:System.Windows.Controls.Page> olan *İleri yığına*eklenir. Arka yığın, ileri yığın ve bunları yönetme işlevleri, toplu olarak günlük olarak adlandırılır. Arka yığındaki her öğe ve ileri yığın, <xref:System.Windows.Navigation.JournalEntry> sınıfının bir örneğidir ve *günlük girdisi*olarak adlandırılır.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer 'da günlük gezinme

Kavramsal olarak, günlük, **geri** ve **İleri** düğmeleriyle [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] aynı şekilde çalışır. Bunlar aşağıdaki şekilde gösterilmiştir.

![Geri ve ileri düğmeleri](./media/navigation-overview/back-and-forward-navigation.png "Geri ve ileri düğmelerine gidin.")

Tarafından [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] barındırılan[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] günlüğü uygulamasının gezintisinetümleştirir.[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] Bu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , kullanıcıların içindeki   arka,ilerivesonsayfalardüğmelerinikullanaraksayfalardagezinmelerini[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]sağlar  . Günlük, [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] veya Internet Explorer 8 [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] ile aynı şekilde tümleştirilmiştir. Bunun yerine [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , ikame bir gezinti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]oluşturur.

> [!IMPORTANT]
> ' [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]De, bir Kullanıcı bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]veya ' a geri geçtiğinde, yalnızca canlı tutulmayan sayfalara ait günlük girişleri tutulur. Sayfaların canlı tutulması hakkında tartışma için, bu konunun ilerleyen kısımlarında [sayfa ömrü ve günlük](#PageLifetime) bölümüne bakın.

Varsayılan olarak, <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] **en son sayfalar** listesinde görünen her bir metin için <xref:System.Windows.Controls.Page>' dır. Çoğu durumda bu, kullanıcıya özellikle anlamlı değildir. Neyse ki, aşağıdaki seçeneklerden birini kullanarak metni değiştirebilirsiniz:

1. İliştirilmiş `JournalEntry.Name` öznitelik değeri.

2. `Page.Title` Öznitelik değeri.

3. `Page.WindowTitle` Öznitelik değeri[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ve geçerli <xref:System.Windows.Controls.Page>.

4. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] İçin geçerli<xref:System.Windows.Controls.Page>. (Varsayılan)

Seçeneklerin listelenme sırası, metni bulmak için öncelik sırasına göre eşleşir. Örneğin, `JournalEntry.Name` ayarlandıysa, diğer değerler yok sayılır.

Aşağıdaki örnek, bir günlük `Page.Title` girişi için görüntülenen metni değiştirmek için özniteliğini kullanır.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>WPF kullanarak günlükte gezinme

Bir kullanıcı içinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]geri, **İleri**ve **son sayfaları** kullanarak günlükte gezinse de, hem bildirim temelli hem de tarafından sunulan programlama mekanizmalarını kullanarak günlükte gezinebilirsiniz. Bunun bir nedeni, sayfalarınızda özel gezinti [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sağlamaktır.

Tarafından <xref:System.Windows.Input.NavigationCommands>sunulan gezinti komutlarını kullanarak bildirimli olarak günlük gezintisi desteği ekleyebilirsiniz. Aşağıdaki örnek, `BrowseBack` gezinti komutunun nasıl kullanılacağını göstermektedir.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

<xref:System.Windows.Navigation.NavigationService> Sınıfının aşağıdaki üyelerinden birini kullanarak günlüğe programlı bir şekilde gidebilirsiniz:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Günlük Ayrıca, bu konunun ilerleyen kısımlarında bulunan [Içerik durumunu gezinti geçmişiyle tutma](#RetainingContentStateWithNavigationHistory) bölümünde anlatıldığı gibi programlı bir şekilde yönetilebilir.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Sayfa ömrü ve günlüğü

[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Grafik, animasyon ve medya dahil zengin içerik içeren çeşitli sayfalarla düşünün. Özellikle video ve ses medyası kullanılıyorsa, bu gibi sayfalar için bellek ayak izi oldukça büyük olabilir. Günlük "anımsar" olarak işaretlenmiş olan sayfaları (örneğin [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ,) büyük ve belirgin bir bellek miktarını hızla tüketebilir.

Bu nedenle, günlüğün varsayılan davranışı, bir nesneye yönelik bir başvuru yerine <xref:System.Windows.Controls.Page> her bir <xref:System.Windows.Controls.Page> günlük girişinde meta verileri depolamadır. Bir günlük girişi gezindiği zaman, <xref:System.Windows.Controls.Page> belirtilen <xref:System.Windows.Controls.Page>yeni bir örneğini oluşturmak için meta verileri kullanılır. Sonuç olarak, her <xref:System.Windows.Controls.Page> bir gezinerek aşağıdaki şekilde gösterilen yaşam süresi vardır.

![Sayfa ömrü](./media/navigation-overview/navigated-page-lifetime.png "Bu, bir sayfa gezindiği zaman ömrünü gösterir.")

Varsayılan günlük kaydı davranışının kullanılması bellek tüketimine kaydedebilse de, sayfa başına işleme performansı azaltılabilir; bir <xref:System.Windows.Controls.Page> yeniden örnekleniyor, özellikle çok sayıda içerik varsa zaman yoğunluğu olabilir. Günlükteki bir <xref:System.Windows.Controls.Page> örneği tutmanız gerekiyorsa, bunu yapmak için iki teknikte çizim yapabilirsiniz. İlk olarak, <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini çağırarak program aracılığıyla bir <xref:System.Windows.Controls.Page> nesneye gidebilirsiniz.

İkinci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] olarak, <xref:System.Windows.Controls.Page.KeepAlive%2A> özelliğini (varsayılan `true` <xref:System.Windows.Controls.Page>)olarakayarlayarak günlüktebirörneğinitutmayıbelirtebilirsiniz`false`. Aşağıdaki örnekte gösterildiği gibi, biçimlendirme içinde bildirimli olarak ayarlayabilirsiniz <xref:System.Windows.Controls.Page.KeepAlive%2A> .

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Etkin tutulan bir yaşam <xref:System.Windows.Controls.Page> süresi, olmayan bir sunucudan daha çok farklıdır. Canlı olarak tutulan bir <xref:System.Windows.Controls.Page> ilk kez, yalnızca canlı tutulmayan bir <xref:System.Windows.Controls.Page> gibi oluşturulur. Ancak, bir öğesinin <xref:System.Windows.Controls.Page> bir örneği günlüğe korunduğu için, günlükte kaldığı sürece hiçbir zaman yeniden örneklenemez. Sonuç olarak, bir <xref:System.Windows.Controls.Page> ' ın her <xref:System.Windows.Controls.Page> gezinilişinde çağrılması gereken bir başlatma mantığı varsa, onu oluşturucudan <xref:System.Windows.FrameworkElement.Loaded> olay için bir işleyiciye taşımalısınız. Aşağıdaki şekilde <xref:System.Windows.FrameworkElement.Loaded> gösterildiği gibi, ve olayları sırasıyla ve <xref:System.Windows.FrameworkElement.Unloaded> kaynağından her bir <xref:System.Windows.Controls.Page> gezinilişinde, ve olayları yine de oluşturulur.

![Yüklenen ve yüklenmeyen olaylar tetiklenir](./media/navigation-overview/loaded-and-unloaded-events.png "Yüklenen ve yüklenmeyen olaylar, bir sayfaya ve öğesinden gidildiği zaman tetiklenir.")

Bir <xref:System.Windows.Controls.Page> , etkin tutulmazsa, aşağıdakilerden birini yapmanız gerekmez:

- Bir başvuruyu veya bunun herhangi bir bölümünü saklayın.

- Olay işleyicilerini, tarafından uygulanmayan olaylarla kaydedin.

Bunlardan herhangi birini yapmak, günlükten kaldırıldıktan sonra bile, <xref:System.Windows.Controls.Page> bellekte bekletilmeye zorlayan başvurular oluşturur.

Genel olarak, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> etkin tutmanın varsayılan davranışını tercih etmelisiniz. Ancak, bu, sonraki bölümde ele alınan durum etkilerine sahiptir.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Içerik durumunu gezinti geçmişi ile koruma

Bir <xref:System.Windows.Controls.Page> , etkin tutulmazsa ve kullanıcıdan veri toplayacak denetimler içeriyorsa, bir kullanıcı tarafından uzaklaştığında ve geri <xref:System.Windows.Controls.Page>gittiğinde verilere ne olur? Kullanıcı deneyimi perspektifinden, Kullanıcı daha önce girdikleri verileri görmeyi bekler. Ne yazık ki her bir gezinmede yeni <xref:System.Windows.Controls.Page> bir örneği oluşturulduğundan, verileri toplayan denetimler yeniden oluşturulur ve veriler kaybolur.

Neyse ki, günlük denetim verileri de dahil olmak üzere <xref:System.Windows.Controls.Page> gezinmeler genelinde verileri hatırlama desteği sağlar. Özellikle, her biri <xref:System.Windows.Controls.Page> için günlük girdisi, ilişkili <xref:System.Windows.Controls.Page> durum için geçici bir kapsayıcı olarak davranır. Aşağıdaki adımlarda, ' den çıkıldığında bu desteğin nasıl kullanıldığı <xref:System.Windows.Controls.Page> gösterilmektedir:

1. Geçerli <xref:System.Windows.Controls.Page> bir giriş günlüğüne eklenir.

2. Durumu <xref:System.Windows.Controls.Page> , arka yığına eklenen bu sayfanın Günlük girdisiyle birlikte depolanır.

3. Yeni <xref:System.Windows.Controls.Page> ' ye gidildi.

Sayfaya <xref:System.Windows.Controls.Page> geri gidildiği zaman, günlük kullanılarak aşağıdaki adımlar gerçekleşir:

1. <xref:System.Windows.Controls.Page> (Arka yığındaki en üst günlük girdisi) örneği oluşturulur.

2. , İçin günlük girdisiyle depolanan durumla yenilenir. <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>

3. , <xref:System.Windows.Controls.Page> Öğesine geri gidildi.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Aşağıdaki denetimler bir <xref:System.Windows.Controls.Page>üzerinde kullanıldığında otomatik olarak bu desteği kullanır:

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

Bir <xref:System.Windows.Controls.Page> bu denetimleri kullanıyorsa, bunlara girilen veriler, aşağıdaki şekilde **sık kullanılan renkle** <xref:System.Windows.Controls.ListBox> gösterildiği gibi, gezinmeler arasında <xref:System.Windows.Controls.Page> hatırlanır.

![Durumu hatırlayacağı denetimlerin bulunduğu sayfa](./media/navigation-overview/data-remembered-across-page-navigations.png "Girilen veriler sayfa gezginlerine göre hatırlanır.")

Bir, <xref:System.Windows.Controls.Page> önceki listede bulunanlar dışında bir denetim varsa veya durum özel nesnelerde depolandığında, günlüğün gezginler genelinde <xref:System.Windows.Controls.Page> durumu anımsamasını sağlamak için kod yazmanız gerekir.

Gezinmeler genelinde <xref:System.Windows.Controls.Page> küçük bir durum parçalarını hatırlamanız gerekiyorsa, <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> meta veri bayrağıyla yapılandırılan bağımlılık özelliklerini (bkz <xref:System.Windows.DependencyProperty>.) kullanabilirsiniz.

Gezinmeler genelinde hatırlamanız <xref:System.Windows.Controls.Page> gereken durum birden çok veri parçasına sahip olursa, eyaletinizi tek bir sınıfta kapsüllemek ve <xref:System.Windows.Navigation.IProvideCustomContentState> arabirimi uygulamak için daha az kod yoğunluğu sağlayabilirsiniz.

Tek tek <xref:System.Windows.Controls.Page>bir için <xref:System.Windows.Controls.Page> farklı durumlar arasında gezinmeniz gerekirse, ve <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>' yi kullanabilirsiniz <xref:System.Windows.Navigation.IProvideCustomContentState> .

<a name="Cookies"></a>

### <a name="cookies"></a>Özgü

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Uygulamalar, <xref:System.Windows.Application.SetCookie%2A> ve<xref:System.Windows.Application.GetCookie%2A> yöntemleri kullanılarak oluşturulan, güncellenen ve silinen tanımlama bilgileriyle veri depolayabilen diğer bir yoldur. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturabileceğiniz tanımlama bilgileri, diğer Web uygulamalarının kullandığı tanımlama bilgilerine sahiptir; tanımlama bilgileri, uygulama oturumları sırasında veya üzerinde bir istemci makinesinde bir uygulama tarafından depolanan rastgele veri parçalarından oluşur. Tanımlama bilgisi verileri genellikle aşağıdaki biçimde bir ad/değer çifti biçimini alır.

*Ad* `=` *Değer*

Veriler geçirildiğinde <xref:System.Windows.Application.SetCookie%2A>, tanımlama bilgisinin ayarlanması gereken konumun yanı sıra <xref:System.Uri> , bellek içinde bir tanımlama bilgisi oluşturulur ve yalnızca geçerli uygulama oturumunun süresi boyunca kullanılabilir. Bu tür tanımlama bilgisine *oturum tanımlama bilgisi*denir.

Bir tanımlama bilgisini uygulama oturumlarında depolamak için, aşağıdaki biçimi kullanarak tanımlama bilgisine bir sona erme tarihi eklenmelidir.

*AD* `=` *DEĞER*`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Sona erme tarihi olan bir tanımlama bilgisi, tanımlama bilgisi süresi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] dolana kadar geçerli yüklemenin Temporary Internet Files klasöründe depolanır. Bu tür bir tanımlama bilgisi, uygulama oturumlarında devam ettiğinden *kalıcı tanımlama bilgisi* olarak bilinir.

<xref:System.Windows.Application.GetCookie%2A> Yöntemini çağırarak hem oturum hem de kalıcı tanımlama bilgilerini, <xref:System.Windows.Application.SetCookie%2A> tanımlama bilgisinin yöntemiyle ayarlandığı <xref:System.Uri> konumu geçirerek alırsınız.

Tanımlama bilgilerinin desteklenme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]yöntemlerinden bazıları aşağıda verilmiştir:

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tek başına uygulamalar [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] , tanımlama bilgilerini oluşturup yönetebilir.

- Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tarafından oluşturulan tanımlama bilgilerine tarayıcıdan erişilebilir.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]aynı etki alanından, tanımlama bilgilerini oluşturup paylaşabilir.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]aynı etki alanındaki sayfalar, tanımlama bilgilerini oluşturup paylaşabilir. [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]

- Tanımlama bilgileri, ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalar Web istekleri yaparken gönderilir.

- Hem üst düzey [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hem de iframe 'ler içinde barındırılan tanımlama bilgilerine erişebilir.

- İçindeki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tanımlama bilgisi desteği, desteklenen tüm tarayıcılarda aynıdır.

- ' [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]De, özellikle birinci tarafa ve üçüncü tarafa [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]göre, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tanımlama bilgileriyle ilgili P3P ilkesi tarafından kabul edilir.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Yapılandırılmış gezinti

Verileri birinden <xref:System.Windows.Controls.Page> diğerine geçirmeniz gerekirse, verileri parametresiz bir oluşturucusuna <xref:System.Windows.Controls.Page>bağımsız değişken olarak geçirebilirsiniz. Bu tekniği kullanırsanız <xref:System.Windows.Controls.Page> , canlı tutmanız gerektiğini unutmayın; Aksi takdirde, ' a bir sonraki gittiğiniz <xref:System.Windows.Controls.Page>zaman parametresiz oluşturucuyu kullanarak öğesini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yeniden başlatır <xref:System.Windows.Controls.Page> .

Alternatif olarak, <xref:System.Windows.Controls.Page> geçirilmesi gereken verilerle ayarlanmış özellikleri de uygulayabilirsiniz. Bununla birlikte, verilerin kendisine gezindiği bir <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> şekilde geri iletilmesi gerektiğinde, şeyler karmaşık hale gelir. Bu sorun, gezintinin, ' den sonra geri döndürüldüğünden emin olmak için <xref:System.Windows.Controls.Page> mekanizmaların yerel olarak desteklemediği bir sorundur. Temelde, gezinme çağrı/döndürme semantiğini desteklemez. Bu sorunu çözmek için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir <xref:System.Windows.Navigation.PageFunction%601> <xref:System.Windows.Controls.Page> sınıfının öngörülebilir ve yapılandırılmış bir biçimde döndürüldüğünden emin olmak için kullanabileceğiniz sınıfı sağlar. Daha fazla bilgi için bkz. [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow sınıfı

Bu noktada, gezinilebilir içeriğe sahip uygulamalar oluşturmak için en büyük olasılıkla kullanabileceğiniz Gezinti hizmetlerinin gamutu olduğunu gördünüz. Bunlarla sınırlı olmadıkları halde [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bu hizmetler bağlamında ele alınmıştır. [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Modern işletim sistemleri ve Windows uygulamaları, tek başına uygulamalara tarayıcı stili gezinme eklemek için modern kullanıcıların tarayıcı deneyiminden yararlanır. Ortak örnekler şunlardır:

- **Sözcük eşanlamlılar sözlüğü**: Word seçimlerine gidin.

- **Dosya Gezgini**: Dosya ve klasörlerde gezin.

- **Sihirbazlar**: Karmaşık bir görevi, arasında gezinilemeyen birden çok sayfaya ayırma. Windows özelliklerinin eklenmesini ve kaldırılmasını işleyen Windows Bileşenleri Sihirbazı bir örnektir.

Tek başına uygulamalarınıza tarayıcı stili gezinme eklemek için <xref:System.Windows.Navigation.NavigationWindow> sınıfını kullanabilirsiniz. <xref:System.Windows.Navigation.NavigationWindow>' dan <xref:System.Windows.Window> türetilir ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sağlayan gezinti için aynı desteğe genişletir. Tek başına uygulamanızın <xref:System.Windows.Navigation.NavigationWindow> ana penceresi veya iletişim kutusu gibi ikincil bir pencere olarak kullanabilirsiniz.

Bir <xref:System.Windows.Navigation.NavigationWindow>öğesini uygulamak için ( [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Window> ,<xref:System.Windows.Controls.Page>, vb.) ' de en üst düzey sınıflarda olduğu gibi, biçimlendirme ve arka plan kod birleşimini kullanırsınız. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Bu kod, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> açıldığında<xref:System.Windows.Navigation.NavigationWindow> otomatik olarak bir (Ana sayfa. xaml) öğesine giden bir oluşturur. Ana uygulama penceresuyorsa, öğesini başlatmak için `StartupUri` özniteliğini kullanabilirsiniz. <xref:System.Windows.Navigation.NavigationWindow> Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Aşağıdaki şekilde, <xref:System.Windows.Navigation.NavigationWindow> tek başına bir uygulamanın ana penceresi olarak gösterilir.

![Ana pencere](./media/navigation-overview/navigation-window-as-main-window.png "Ana pencere olarak gezinti penceresi")

Bu şekilde, önceki örnekteki <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow> uygulama kodunda ayarlanmasa bile, ' ın bir başlığına sahip olduğunu görebilirsiniz. Bunun yerine, başlık aşağıdaki kodda gösterilen <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliğini kullanarak ayarlanır.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Ve özelliklerinin ayarlanması <xref:System.Windows.Controls.Page.WindowHeight%2A> de ' nı etkiler <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Controls.Page.WindowWidth%2A>

Genellikle, davranışını veya görünümünü özelleştirmeniz <xref:System.Windows.Navigation.NavigationWindow> gerektiğinde kendi uygulamanızı uygulamanız gerekir. Aksi takdirde, bir kısayolu kullanabilirsiniz. Tek [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başına bir <xref:System.Windows.Application.StartupUri%2A> <xref:System.Windows.Controls.Page> uygulamadabirolan<xref:System.Windows.Navigation.NavigationWindow> paketini belirtirseniz, otomatikolarakbirolarakbiroluşturur.<xref:System.Windows.Controls.Page> <xref:System.Windows.Application> Aşağıdaki biçimlendirmede bunun nasıl etkinleştirileceği gösterilmektedir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

İletişim kutusu gibi bir ikincil uygulama penceresinin olmasını <xref:System.Windows.Navigation.NavigationWindow>istiyorsanız, bu kodu açmak için aşağıdaki örnekteki kodu kullanabilirsiniz.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Aşağıdaki şekilde sonuç gösterilmektedir.

![İletişim kutusu](./media/navigation-overview/navigation-window-as-dialog-box.png "İletişim kutusu olarak gezinti penceresi")

Görebileceğiniz gibi, <xref:System.Windows.Navigation.NavigationWindow> kullanıcıların günlükte gezinmesini sağlayan ekran [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]stili **geri** ve **İleri** düğmelerini de görüntüleyebilirsiniz. Bu düğmeler, aşağıdaki şekilde gösterildiği gibi aynı kullanıcı deneyimini sağlar.

![NavigationWindow 'Daki geri ve ileri düğmeleri](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Gezinti penceresinde geri ve ileri düğmeleri")

Sayfalarınız kendi günlük gezintisi desteğini ve Kullanıcı arabirimini sağladıysanız, <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> özelliğinin değerini olarak `false`ayarlayarak, tarafından <xref:System.Windows.Navigation.NavigationWindow> görünen **geri** ve **İleri** düğmelerini gizleyebilirsiniz.

Alternatif olarak, ' ın ' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nin <xref:System.Windows.Navigation.NavigationWindow> yerini değiştirmek için içindeki özelleştirme desteğini de kullanabilirsiniz.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame sınıfı

Hem tarayıcı <xref:System.Windows.Navigation.NavigationWindow> hem de gezinilebilir içerik barındıran Windows. Bazı durumlarda, uygulamalarda bir pencerenin tamamında barındırılması gerekmeyen içerikler vardır. Bunun yerine, bu içerik diğer içeriğin içinde barındırılır. <xref:System.Windows.Controls.Frame> Sınıfını kullanarak, gezinebilir içeriği diğer içeriklere ekleyebilirsiniz. <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow> ve ile [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]aynı desteği sağlar.

Aşağıdaki örnek <xref:System.Windows.Controls.Frame> öğesi`Frame` kullanılarak <xref:System.Windows.Controls.Page> bildirimli olarak öğesine nasıl ekleneceğini gösterir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Bu biçimlendirme `Frame` öğesi, `Source` ilk olarak öğesine gitmeniz <xref:System.Windows.Controls.Frame> gereken için <xref:System.Windows.Controls.Page> bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketiyle birlikte öğesinin özniteliğini ayarlar. Aşağıdaki şekilde, birden çok [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] sayfa arasında <xref:System.Windows.Controls.Page> gezindiği bir <xref:System.Windows.Controls.Frame> ile içeren bir ile gösterilmektedir.

![Birden çok sayfa arasında gezindiği çerçeve](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Bu, birden çok sayfa arasında bir çerçeve gezintisi gösterir.")

Yalnızca bir <xref:System.Windows.Controls.Frame> <xref:System.Windows.Controls.Page>içeriğinin içinde kullanmak zorunda değilsiniz. Ayrıca, a içeriğinin <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>içinde barındırmak için de ortaktır.

Varsayılan olarak, <xref:System.Windows.Controls.Frame> yalnızca kendi günlüğünü başka bir günlük yokluğunda kullanır. <xref:System.Windows.Controls.Frame> ,Ya<xref:System.Windows.Navigation.NavigationWindow> da <xref:System.Windows.Controls.Frame> 'de[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]barındırılan içeriğin parçasıysa, veya'aaitolangünlüğükullanır.<xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Bazen, ancak <xref:System.Windows.Controls.Frame> kendi günlüğünden sorumlu olması gerekebilir. Bunun bir nedeni, tarafından <xref:System.Windows.Controls.Frame>barındırılan sayfalarda Journal gezintisine izin vermektedir. Bu, aşağıdaki şekilde gösterilmiştir.

![Çerçeve ve sayfa diyagramı](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Bu, bir çerçeve tarafından barındırılan sayfaların içindeki günlük gezintisini gösterir.")

<xref:System.Windows.Controls.Frame> Bu durumda, öğesinin <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> özelliğini olarak<xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>ayarlayarak kendi günlüğünü kullanacak şekilde yapılandırabilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Aşağıdaki şekilde kendi günlüğünü kullanan bir <xref:System.Windows.Controls.Frame> içinde gezinmenin etkisi gösterilmektedir.

![Kendi günlüğünü kullanan bir çerçeve](./media/navigation-overview/frame-uses-its-own-journal.png "Bu, kendi günlüğünü kullanan bir çerçeve içinde gezinmenin etkisini gösterir.")

Günlük girişlerinin, tarafından [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]değil ' de gezinme tarafından gösterildiğine dikkat edin.

> [!NOTE]
> <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], Bir<xref:System.Windows.Controls.Frame> içinde barındırılan içeriğin parçasıysa kendi günlüğünü kullanır ve sonuç olarak <xref:System.Windows.Window>kendi gezinmesini görüntüler.

<xref:System.Windows.Controls.Frame> Kullanıcı deneyiminizin <xref:System.Windows.Visibility.Hidden>, gezinmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]göstermeden kendi günlüğünü sağlaması gerekiyorsa, ' yi <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> olarak ayarlayarak gezinmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gizleyebilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Gezinti konakları

<xref:System.Windows.Controls.Frame>ve <xref:System.Windows.Navigation.NavigationWindow> , gezinti konakları olarak bilinen sınıflardır. *Gezinti ana bilgisayarı* , içeriğe gidebileceğiniz ve içeriği görüntüleyebilen bir sınıftır. Bunu gerçekleştirmek için, her bir gezinti ana bilgisayarı kendi <xref:System.Windows.Navigation.NavigationService> ve günlüğünü kullanır. Bir gezinti konağının temel yapımı aşağıdaki şekilde gösterilmiştir.

![Gezgin diyagramları](./media/navigation-overview/navigation-host-construction.png "Bir gezinti ana bilgisayarının temel yapımı")

Temelde, bu <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> , tarayıcıda barındırılırken [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] sağladığı aynı gezinti desteğini sağlar.

Ve bir <xref:System.Windows.Navigation.NavigationService> günlüğü kullanmanın yanı sıra, gezinti konakları, <xref:System.Windows.Navigation.NavigationService> uygulayan aynı üyeleri uygular. Bu, aşağıdaki şekilde gösterilmiştir.

Bir ![çerçevedeki ve NavigationWindow Içindeki bir günlük](./media/navigation-overview/navigation-window-and-frame.png "Gezinti penceresi ve çerçeve")

Bu, gezinti desteğini doğrudan bunlara karşı programbırakmanıza olanak tanır. ' De [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame>barındırılanbir için özel bir gezinti sağlamanız gerekiyorsa bunu göz önünde bulundurabilir. <xref:System.Windows.Window> Ayrıca, her iki tür `BackStack` de (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) ve (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>) dahil olmak üzere ek `ForwardStack` , gezinti ile ilgili Üyeler uygular ve bu da günlük girdilerini arka planda listeleyebileceğiniz sırasıyla yığın ve ileri yığın.

Daha önce belirtildiği gibi, bir uygulama içinde birden çok günlük bulunabilir. Aşağıdaki şekilde, bunun gerçekleşene zaman gerçekleşebileceğinizi bir örnek verilmiştir.

![Bir uygulama Içinde birden çok günlük](./media/navigation-overview/multiple-journals-in-one-application.png "Bu, bir uygulamada birden fazla günlük örneğine bir örnektir.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML sayfaları dışındaki Içeriğe gitme

Bu konu başlığı altında <xref:System.Windows.Controls.Page> , ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] çeşitli gezinti yeteneklerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]göstermek için paketi kullanılmıştır. Ancak, <xref:System.Windows.Controls.Page> bir uygulamaya derlenen tek içerik türü değildir ve paket [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içeriği belirlemenin tek yolu değildir.

Bu bölümde gösterildiği gibi, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] dosyalar ve nesneler 'e de gidebilirsiniz.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Gevşek XAML dosyalarına gitme

Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya, aşağıdaki özelliklere sahip bir dosyadır:

- Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerir (yani, kod yok).

- Uygun bir ad alanı bildirimine sahiptir.

- . Xaml dosya adı uzantısına sahiptir.

Örneğin, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir dosya olan Person. xaml olarak depolanan aşağıdaki içeriği göz önünde bulundurun.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Dosyaya çift tıkladığınızda tarayıcı açılır ve ' a gider ve içeriği görüntüler. Bu, aşağıdaki şekilde gösterilmiştir.

![Içeriği Person. xaml dosyasında görüntüleme](./media/navigation-overview/contents-of-person-xaml-file.png "Person. xaml dosyasının Içeriğini gösterir.")

Aşağıdaki listeden gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir dosya görüntüleyebilirsiniz:

- Yerel makinedeki, intranetteki veya Internet 'teki bir Web sitesi.

- Bir [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] dosya paylaşma.

- Yerel disk.

Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir dosya tarayıcının sık kullanılanlarına eklenebilir veya tarayıcının giriş sayfası olabilir.

> [!NOTE]
> Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yayımlama ve başlatma hakkında daha fazla bilgi için bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir sınırlama, yalnızca kısmi güvende çalışmak için güvenli olan içeriği barındırmanıza olanak sağlar. Örneğin, `Window` gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir dosyanın kök öğesi olamaz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Çerçeve kullanarak HTML dosyalarına gitme

Tahmin edebileceğiniz gibi, ' ye [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]de gidebilirsiniz. Yalnızca http düzenini kullanan bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sağlamanız gerekir. Örneğin, aşağıda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] sayfaya giden bir <xref:System.Windows.Controls.Frame> sayfa görüntülenir.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

' A gitme özel izinler gerektirir.[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] Örneğin, Internet bölgesi kısmi güven güvenlik korumalı [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] alanı ' nda çalıştırılan bir bilgisayardan geziniyorsunuz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser denetimini kullanarak HTML dosyalarına gitme

Denetim belge barındırma, gezinti ve betik/yönetilen kod birlikte çalışabilirliğini destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. <xref:System.Windows.Controls.WebBrowser> <xref:System.Windows.Controls.WebBrowser> Denetimle ilgili ayrıntılı bilgi için bkz <xref:System.Windows.Controls.WebBrowser>.

Benzer <xref:System.Windows.Controls.Frame>şekilde [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] , kullanmaya<xref:System.Windows.Controls.WebBrowser> gitme özel izinler gerektirir. Örneğin, kısmi güven uygulamasından yalnızca [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitesinde bulunan ' a gidebilirsiniz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Özel nesnelere gitme

Özel nesneler olarak depolanan verileriniz varsa, bu verileri görüntülemenin bir yolu, bu nesnelere bağlanan içeriğe sahip bir <xref:System.Windows.Controls.Page> oluşturmak (bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md)). Yalnızca nesneleri görüntüleyen bir sayfanın tamamını oluşturmak için ek yüke gerek yoksa, bunun yerine doğrudan bunlara gidebilirsiniz.

Aşağıdaki kodda uygulanan sınıfı göz önünde bulundurun. `Person`

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Bu sayfaya gitmek için aşağıdaki kodda gösterildiği gibi <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> yöntemini çağırın.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Aşağıdaki şekilde sonuç gösterilmektedir.

![Bir sınıfa giden bir sayfa](./media/navigation-overview/page-navigates-to-an-object.png "Bu, bir nesnesine giden bir sayfa örneğidir.")

Bu şekilde, hiçbir şeyin yararlı görüntülendiğini görebilirsiniz. Aslında, görüntülenen değer `ToString` **kişi** nesnesi için yöntemin dönüş değeridir; varsayılan olarak, bu, nesnenizin temsil edilebilmesi için kullanılabilecek tek değerdir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] . Daha anlamlı bilgiler döndürmek `ToString` için yöntemi geçersiz kılabilir, ancak yalnızca bir dize değeri olmaya devam eder. ' Nin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sunum özelliğinden faydalanan bir teknik, veri şablonu kullanmaktır. Belirli bir türdeki nesneyle [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ilişkilendirebileceğiniz bir veri şablonu uygulayabilirsiniz. Aşağıdaki kod, `Person` nesnesi için bir veri şablonu gösterir.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Burada, veri şablonu, `Person` `DataType` özniteliğinde `x:Type` biçimlendirme uzantısı kullanılarak türle ilişkilendirilir. Veri şablonu daha sonra öğeleri `TextBlock` (bkz <xref:System.Windows.Controls.TextBlock>.) `Person` sınıfın özelliklerine bağlar. Aşağıdaki şekilde `Person` nesnesinin güncelleştirilmiş görünümü gösterilmektedir.

![Veri şablonu olan bir sınıfa gitme](./media/navigation-overview/navigating-to-a-class.png "Veri şablonu olan bir sınıfa gitme.")

Bu tekniğin avantajı, nesneleri uygulamanızda her yerde tutarlı bir şekilde göstermek için veri şablonunu yeniden kullanabilerek elde ettiğiniz tutardır.

Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Güvenlik

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]gezinti desteği Internet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] üzerinden gezinmesine izin verir ve uygulamaların üçüncü taraf içeriği barındıralmasına izin verir. Hem uygulama hem de kullanıcıların zararlı davranışlardan korunması için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , [güvenlik](../security-wpf.md) ve [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md)bölümünde ele alınan çeşitli güvenlik özellikleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Uygulama Yönetimine Genel Bakış](application-management-overview.md)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
- [Gezinti Topolojilerine Genel Bakış](navigation-topologies-overview.md)
- [Nasıl Yapılır Konuları](navigation-how-to-topics.md)
- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
