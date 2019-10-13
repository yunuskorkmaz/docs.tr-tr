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
ms.openlocfilehash: 874bc0b1b0ac38210569632dc3d21ed727ae26e4
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291650"
---
# <a name="navigation-overview"></a>Gezintiye Genel Bakış

Windows Presentation Foundation (WPF), iki tür uygulama için kullanılabilen tarayıcı stili gezinmeyi destekler: tek başına uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Gezinmede içerik paketlemek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Controls.Page> sınıfını sağlar. Bir <xref:System.Windows.Controls.Page> ' dan diğerine, <xref:System.Windows.Documents.Hyperlink> veya program aracılığıyla <xref:System.Windows.Navigation.NavigationService> kullanarak gidebilirsiniz. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' dan gelen ve geri gitmek için kullanılan sayfaları hatırlama günlüğünü kullanır.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService> ve günlük [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından sunulan gezinti desteğinin çekirdeğini oluşturur. Bu genel bakış, gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları, HTML dosyaları ve nesneler için gezinti içeren gelişmiş gezinti desteğini kullanmadan önce bu özellikleri ayrıntılı olarak ele alır.

> [!NOTE]
> Bu konuda, "Browser" terimi, şu anda Microsoft Internet Explorer ve Firefox içeren [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarını barındırabilen tarayıcılara başvurur. Belirli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellikleri yalnızca belirli bir tarayıcı tarafından desteklendiğinde tarayıcı sürümüne başvurulur.

## <a name="navigation-in-wpf-applications"></a>WPF uygulamalarında gezinme

Bu konu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' daki temel gezinti özelliklerine genel bir bakış sağlar. Bu yetenekler hem tek başına uygulamalar hem de [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için kullanılabilir, ancak bu konu, bu konuda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bağlamı içinde sunulur.

> [!NOTE]
> Bu konu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ' ın nasıl oluşturulduğunu ve dağıtılacağını ele almaz. @No__t-0 hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).

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

- [Özgü](#Cookies)

- [Yapılandırılmış gezinti](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Sayfa uygulama

@No__t-0 ' da, .NET Framework nesneleri, özel nesneler, sabit listesi değerleri, Kullanıcı denetimleri, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve HTML dosyaları içeren birkaç içerik türüne gidebilirsiniz. Ancak, <xref:System.Windows.Controls.Page> ' ı kullanarak içerik paketlemeyi kullanmanın en yaygın ve kolay yolunu bulabilirsiniz. Ayrıca, <xref:System.Windows.Controls.Page>, görünümünü iyileştirmek ve geliştirmeyi basitleştirmek için gezintiye özgü özellikler uygular.

@No__t-0 ' ı kullanarak, aşağıdaki gibi işaretlemeleri kullanarak, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeriğinin gezinebilir bir sayfasını bildirimli olarak uygulayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

@No__t-1 biçimlendirmesinde uygulanan <xref:System.Windows.Controls.Page>, kök öğesi olarak `Page` ' dir ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] @ no__t-4 ad alanı bildirimi gerektirir. @No__t-0 öğesi, gitmek ve göstermek istediğiniz içeriği içerir. Aşağıdaki biçimlendirmede gösterildiği gibi `Page.Content` özellik öğesini ayarlayarak içerik eklersiniz.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` yalnızca bir alt öğe içerebilir; Yukarıdaki örnekte, içerik tek bir dizedir, "Merhaba, sayfa!" Uygulamada, içeriğinizi eklemek ve oluşturmak için genellikle alt öğe (bkz. [Düzen](../advanced/layout.md)) olarak bir düzen denetimi kullanırsınız.

@No__t-0 öğesinin alt öğeleri, bir <xref:System.Windows.Controls.Page> ' in içeriği olduğu kabul edilir ve sonuç olarak, açık `Page.Content` bildirimini kullanmanız gerekmez. Aşağıdaki biçimlendirme, önceki örneğe bildirime dayalı olarak eşdeğerdir.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

Bu durumda, `Page.Content` `Page` öğesinin alt öğeleriyle otomatik olarak ayarlanır. Daha fazla bilgi için bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).

Yalnızca biçimlendirme <xref:System.Windows.Controls.Page> içerik görüntülemek için kullanışlıdır. Ancak, <xref:System.Windows.Controls.Page>, kullanıcıların sayfayla etkileşime geçmesini sağlayan denetimleri de görüntüleyebilir ve olayları işleyerek ve uygulama mantığını çağırarak kullanıcı etkileşimine yanıt verebilir. Etkileşimli <xref:System.Windows.Controls.Page>, aşağıdaki örnekte gösterildiği gibi, biçimlendirme ve arka plan kodu birleşimi kullanılarak uygulanır.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Biçimlendirme dosyası ve arka plan kod dosyasının birlikte çalışmasına izin vermek için aşağıdaki yapılandırma gereklidir:

- Biçimlendirme ' de `Page` öğesi `x:Class` özniteliğini içermelidir. Uygulama yapılandırıldığında, biçimlendirme dosyasında `x:Class` ' ı, Microsoft Build Engine 'in (MSBuild) <xref:System.Windows.Controls.Page> ' den türetilen ve `x:Class` özniteliğiyle belirtilen ada sahip bir `partial` sınıfı oluşturmasına neden olur. Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı bildiriminin eklenmesini gerektirir. Oluşturulan `partial` sınıfı, olayları kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağrılan `InitializeComponent` ' i uygular.

- Arka plan kod içinde, sınıf, biçimlendirme içindeki `x:Class` özniteliğiyle belirtilen aynı ada sahip `partial` sınıfı olmalıdır ve <xref:System.Windows.Controls.Page> ' den türetilmelidir. Bu, arka plan kod dosyasının, uygulama oluşturulduğunda biçimlendirme dosyası için oluşturulan `partial` sınıfıyla ilişkilendirilmesine izin verir (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).

- Arka plan kod içinde <xref:System.Windows.Controls.Page> sınıfı, `InitializeComponent` yöntemini çağıran bir Oluşturucu uygulamalıdır. `InitializeComponent`, olayları kaydetmek ve biçimlendirmede tanımlanan özellikleri ayarlamak için biçimlendirme dosyasının oluşturulan `partial` sınıfı tarafından uygulanır.

> [!NOTE]
> @No__t-1 kullanarak projenize yeni bir <xref:System.Windows.Controls.Page> eklediğinizde <xref:System.Windows.Controls.Page>, hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır ve burada açıklanan biçimlendirme ve arka plan kod dosyaları arasındaki ilişkiyi oluşturmak için gereken yapılandırmayı içerir.

@No__t-0 olduktan sonra bu sayfaya gidebilirsiniz. Bir uygulamanın gittiği ilk <xref:System.Windows.Controls.Page> ' ı belirtmek için, Start <xref:System.Windows.Controls.Page> ' i yapılandırmanız gerekir.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Başlangıç sayfasını yapılandırma

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bir tarayıcıda barındırılmak için belirli bir uygulama altyapısı miktarı gerektirir. @No__t-0 ' da, <xref:System.Windows.Application> sınıfı gerekli uygulama altyapısını kuran bir uygulama tanımının parçasıdır (bkz. [uygulama yönetimine genel bakış](application-management-overview.md)).

Bir uygulama tanımı, genellikle bir MSBuild @ no__t-0 öğesi olarak yapılandırılmış biçimlendirme dosyası ile hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır. @No__t-0 ' a yönelik bir uygulama tanımı aşağıda verilmiştir.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

@No__t-0, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] başlatıldığında otomatik olarak yüklenen <xref:System.Windows.Controls.Page> olan başlangıç <xref:System.Windows.Controls.Page> ' i belirtmek için uygulama tanımını kullanabilir. Bunu, istenen <xref:System.Windows.Controls.Page> için <xref:System.Windows.Application.StartupUri%2A> özelliğini [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] olarak ayarlayarak yapabilirsiniz.

> [!NOTE]
> Çoğu durumda, <xref:System.Windows.Controls.Page> bir uygulamayla derlenir veya bir uygulamayla birlikte dağıtılır. Bu gibi durumlarda, bir @no__t tanımlayan <xref:System.Windows.Controls.Page>, *paket* düzenine uygun bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] olan bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' dir. @No__t-0 paketi, [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)daha fazla ele alınmıştır. Ayrıca, aşağıda açıklanan http düzenini kullanarak içeriğe gidebilirsiniz.

Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Application.StartupUri%2A> ' ı biçimlendirme içinde bildirimli olarak ayarlayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

Bu örnekte, `StartupUri` özniteliği, giriş sayfası. xaml tanımlayan bir göreli paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ile ayarlanır. @No__t-0 başlatıldığında, giriş sayfası. xaml otomatik olarak gezilebilir ve görüntülenir. Bu, bir Web sunucusundan başlatılan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' ı gösteren aşağıdaki şekilde gösterilmiştir.

![XBAP sayfası](./media/navigation-overview/xbap-launched-from-a-web-server.png "Bu, bir Web SUNUCUSUNDAN başlatılan bir XBAP gösterir.")

> [!NOTE]
> @No__t-0 geliştirme ve dağıtımı hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md) ve [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konak penceresinin başlığını, genişliğini ve yüksekliğini yapılandırma

Önceki şekilden fark etmiş olduğunuz bir şey, hem tarayıcının hem de sekme bölmesinin başlığının, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] olması olabilir. Büyük olmasının yanı sıra başlık etkileyici veya bilgilendirici değildir. Bu nedenle, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliğini ayarlayarak başlığı değiştirmeniz için bir yol sunar. Ayrıca, sırasıyla <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A> ' i ayarlayarak tarayıcı penceresinin genişlik ve yüksekliğini yapılandırabilirsiniz.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A>, aşağıdaki örnekte gösterildiği gibi biçimlendirme içinde bildirimli olarak ayarlanabilir.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Sonuç aşağıdaki şekilde gösterilmiştir.

![Pencere başlığı, yükseklik, Genişlik](./media/navigation-overview/window-title-width-height.png "Bu, yapılandırabileceğiniz pencere başlığını, yüksekliğini ve genişliğini gösterir.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Köprü gezintisi

Tipik bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] birçok sayfadan oluşur. Bir sayfadan diğerine gitmenin en kolay yolu <xref:System.Windows.Documents.Hyperlink> kullanmaktır. Aşağıdaki biçimlendirmede gösterilen `Hyperlink` öğesini kullanarak, bildirimli bir <xref:System.Windows.Documents.Hyperlink> ' a bir <xref:System.Windows.Controls.Page> öğesine ekleyebilirsiniz.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

@No__t-0 öğesi şunları gerektirir:

- @No__t-2 özniteliği tarafından belirtildiği gibi, gitmek için <xref:System.Windows.Controls.Page> ' in [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' dır.

- Kullanıcının, metin ve görüntüler gibi gezinti işlemini başlatmak için tıklabileceği içerik (`Hyperlink` öğesinin içerebileceği içerik için, bkz. <xref:System.Windows.Documents.Hyperlink>).

Aşağıdaki şekilde, <xref:System.Windows.Documents.Hyperlink> ' ye sahip bir <xref:System.Windows.Controls.Page> ile [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gösterilmektedir.

![Köprü Içeren sayfa](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Bu, Köprüsü olan bir sayfa içeren bir XBAP gösterir.")

Bekleneceğiniz gibi <xref:System.Windows.Documents.Hyperlink> ' a tıklamak, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' in `NavigateUri` özniteliği tarafından tanımlanan <xref:System.Windows.Controls.Page> ' ye gitmesini sağlar. Ayrıca, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], Internet Explorer 'daki son sayfalar listesine önceki <xref:System.Windows.Controls.Page> için bir giriş ekler. Bu, aşağıdaki şekilde gösterilmiştir.

![Geri]ve ileri düğmeleri geri(./media/navigation-overview/back-and-forward-navigation.png "ve ileri düğmeleriyle gezinir.")

Ayrıca, bir <xref:System.Windows.Controls.Page> ' dan diğerine gezinmeyi desteklemenin yanı sıra, <xref:System.Windows.Documents.Hyperlink> de parça gezintisini destekler.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Parça gezintisi

*Parça gezintisi* , geçerli <xref:System.Windows.Controls.Page> ya da başka bir <xref:System.Windows.Controls.Page> ' deki bir içerik parçasına yönelik gezindir. @No__t-0 ' da, içerik parçası, adlandırılmış bir öğe tarafından içerilen içeriktir. Adlandırılmış bir öğe, `Name` özniteliği ayarlanmış bir öğedir. Aşağıdaki biçimlendirme, bir içerik parçası içeren adlandırılmış bir `TextBlock` öğesi gösterir.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Bir @no__t için-0 ' a bir içerik parçasına gitmek için, `NavigateUri` özniteliği şunları içermelidir:

- @No__t-1 ' in [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' a gitmek için içerik parçadır.

- Bir "#" karakteri.

- @No__t-0 ' daki, içerik parçasını içeren öğenin adı.

@No__t-0 ' ın aşağıdaki biçimi vardır.

*PageUri* `#` *ElementName*

Aşağıda bir içerik parçasına gitmek üzere yapılandırılan `Hyperlink` ' ın bir örneği gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Bu bölüm [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' da varsayılan parça gezintisi uygulamasını açıklar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], Ayrıca, <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> olayının işlenmesini gerektiren kendi parça gezinti düzeninizi uygulamanıza olanak tanır.

> [!IMPORTANT]
> Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalarındaki parçalara gidebilirsiniz (kök öğe olarak yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] @no__t dosyaları), yalnızca sayfaların HTTP aracılığıyla gözatılabilir.
>
> Ancak, gevşek bir @no__t 0 sayfası kendi parçalara gidebilir.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Gezinti hizmeti

@No__t-0, bir kullanıcının belirli bir <xref:System.Windows.Controls.Page> ' e gezinti başlatmasına izin veriyorsa, sayfayı bulma ve indirme işi <xref:System.Windows.Navigation.NavigationService> sınıfı tarafından gerçekleştirilir. Temelde <xref:System.Windows.Navigation.NavigationService>, <xref:System.Windows.Documents.Hyperlink> gibi istemci kodu adına bir gezinti isteği işleme olanağı sağlar. Ayrıca, <xref:System.Windows.Navigation.NavigationService>, bir gezinti isteğini izlemek ve etkili bir şekilde eğmek için daha yüksek düzeyde destek uygular.

@No__t-0 ' a tıklandığında, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' i @no__t, belirtilen Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' @no__t bulmak ve indirmek için-2 ' yi çağırır. İndirilen <xref:System.Windows.Controls.Page>, kök nesnesi indirilen <xref:System.Windows.Controls.Page> ' in bir örneği olan bir nesne ağacına dönüştürülür. Kök <xref:System.Windows.Controls.Page> nesnesine bir başvuru <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> özelliğinde depolanır. @No__t-0 paketi, gezindiği içerik için <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliğinde depolanır, ancak <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> paketi, gezindiği son sayfa için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' ü depolar.

> [!NOTE]
> @No__t-0 uygulamasının birden fazla etkin <xref:System.Windows.Navigation.NavigationService> ' e sahip olması mümkündür. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Gezinti konakları](#Navigation_Hosts) bölümüne bakın.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Gezinti hizmeti ile programlama yoluyla gezinme

@No__t-2, sizin adınıza <xref:System.Windows.Navigation.NavigationService> ' ü kullandığından, gezinme, <xref:System.Windows.Documents.Hyperlink> kullanılarak biçimlendirme içinde bildirimli olarak uygulanırsa <xref:System.Windows.Navigation.NavigationService> hakkında bilmeniz gerekmez. Yani, bir <xref:System.Windows.Documents.Hyperlink> ' ın doğrudan veya dolaylı üst öğesi bir gezinti ana bilgisayarı olduğu sürece (bkz. [Gezinti konakları](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> ' yi bir gezinti isteğini işlemek için gezinti konağının gezinti hizmetini bulabilir ve kullanabilir.

Ancak, aşağıdakiler de dahil olmak üzere <xref:System.Windows.Navigation.NavigationService> kullanmanız gerektiğinde durumlar vardır:

- Parametresiz bir Oluşturucu kullanarak <xref:System.Windows.Controls.Page> örneğini oluşturmanız gerektiğinde.

- @No__t-0 ' da, bu sayfaya geçmeden önce özellikleri ayarlamanız gerekir.

- Gezinilmesi gereken <xref:System.Windows.Controls.Page> yalnızca çalışma zamanında belirlenebilir.

Bu durumlarda, <xref:System.Windows.Navigation.NavigationService> nesnesinin <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemini çağırarak programlı olarak gezinmeyi başlatmak için kod yazmanız gerekir. @No__t-0 ' a başvuru almayı gerektirir.

#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService 'e başvuru alma

[Gezinti konakları](#Navigation_Hosts) bölümünde ele alınan nedenlerle [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir uygulama birden fazla <xref:System.Windows.Navigation.NavigationService> ' ye sahip olabilir. Bu, kodunuzun <xref:System.Windows.Navigation.NavigationService> ' ı bulmak için bir yönteme ihtiyaç duymasıdır. Bu, genellikle geçerli <xref:System.Windows.Controls.Page> ' ye gidildiği <xref:System.Windows.Navigation.NavigationService> ' dir. @No__t-1 @ no__t-2 yöntemini çağırarak <xref:System.Windows.Navigation.NavigationService> ' a bir başvuru alabilirsiniz. Belirli bir <xref:System.Windows.Controls.Page> ' e gezindiği <xref:System.Windows.Navigation.NavigationService> ' ı almak için, <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> yönteminin bağımsız değişkeni olarak <xref:System.Windows.Controls.Page> ' ye bir başvuru geçirirsiniz. Aşağıdaki kod, geçerli <xref:System.Windows.Controls.Page> için <xref:System.Windows.Navigation.NavigationService> ' ın nasıl alınacağını gösterir.

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Bir <xref:System.Windows.Controls.Page> için @no__t bulmak için bir kısayol olarak, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> özelliğini uygular. Bu, aşağıdaki örnekte gösterilmiştir.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> @No__t-0 ' ın yalnızca <xref:System.Windows.Navigation.NavigationService> ' e bir başvuru alabilir <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> olayını oluşturur.

#### <a name="programmatic-navigation-to-a-page-object"></a>Sayfa nesnesine programlama yoluyla gezinme

Aşağıdaki örnek, bir <xref:System.Windows.Controls.Page> ' e programlı olarak gitmek için <xref:System.Windows.Navigation.NavigationService> ' nın nasıl kullanılacağını gösterir. Programlı gezinme gereklidir çünkü gezinmekte olan <xref:System.Windows.Controls.Page> yalnızca tek, parametresiz bir Oluşturucu kullanılarak örneklenebilir. Parametresiz oluşturucuya sahip <xref:System.Windows.Controls.Page>, aşağıdaki biçimlendirme ve kodda gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Parametresiz oluşturucusu ile <xref:System.Windows.Controls.Page> ' e giden <xref:System.Windows.Controls.Page>, aşağıdaki biçimlendirme ve kodda gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Bu <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> ' a tıklandığında, eksik Oluşturucuyu kullanmak ve <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini çağırmak için <xref:System.Windows.Controls.Page> ' yi örnekleyerek gezinti başlatılır. <xref:System.Windows.Navigation.NavigationService.Navigate%2A>, bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerine <xref:System.Windows.Navigation.NavigationService> ' e gidecektir nesnesine bir başvuru kabul eder.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Paket URI 'SI ile programlama yoluyla gezinme

Program aracılığıyla @no__t bir paket oluşturmanız gerekiyorsa (örneğin, çalışma zamanında yalnızca [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketini belirleyebiliyorsanız) <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bu, aşağıdaki örnekte gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Geçerli sayfa yenileniyor

@No__t-0, <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliğinde saklanan Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ile aynı Pack @no__t sahip değilse indirilmez. @No__t zorlamak için-0 geçerli sayfayı yeniden indirmek için aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Gezinti ömrü

Gördüğünüz gibi, gezintiyi başlatmak için birçok yol vardır. Gezinti başlatıldığında ve gezinme devam ederken, <xref:System.Windows.Navigation.NavigationService> tarafından uygulanan aşağıdaki olayları kullanarak gezintiyi izleyebilir ve etkileyebilirsiniz:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Yeni bir gezinti istendiğinde gerçekleşir. Gezinmeyi iptal etmek için kullanılabilir.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Bir indirme sırasında, gezinti ilerleme bilgileri sağlamak için düzenli aralıklarla gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Sayfa bulunduğunda ve indirildiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Gezinti durdurulduğunda (<xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ' ı çağırarak) veya geçerli bir gezinti sürerken yeni bir gezinti istendiğinde gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. İstenen içeriğe gidilirken bir hata ortaya çıktığında gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Gezinilmiş içerik yüklenip ayrıştırıldığında ve işlemeye başladıktan sonra gerçekleşir.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Bir içerik parçasına Gezinti başladığında gerçekleşir, bu durum:

  - Hemen, istenen parça geçerli içeriktir.

  - Kaynak içerik yüklendikten sonra, istenen parça farklı içeriklerde yer alıyorsa.

Gezinti olayları aşağıdaki şekilde gösterilen sırayla oluşturulur.

![Sayfa gezintisi akış grafiği](./media/navigation-overview/order-of-navigation-events.png "sayfa gezintisi olay akışı grafiği")

Genel olarak, <xref:System.Windows.Controls.Page> bu olaylar hakkında endişe vermez. Bir uygulamanın bunlarla ilgilenmesi daha olasıdır ve bu nedenle, bu olaylar <xref:System.Windows.Application> sınıfı tarafından da oluşturulur:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Her <xref:System.Windows.Navigation.NavigationService> bir olay harekete geçirirse, <xref:System.Windows.Application> sınıfı ilgili olayı başlatır. <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow>, ilgili kapsamları içinde gezinmeyi algılamak için aynı olayları sunar.

Bazı durumlarda, bu olaylarla ilgili bir <xref:System.Windows.Controls.Page> olabilir. Örneğin, bir <xref:System.Windows.Controls.Page> ' ın kendisinden bir gezintinin iptal edilip edilmeyeceğini tespit etmek için <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> olayı işleyebilir. Bu, aşağıdaki örnekte gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Bir işleyiciyi bir <xref:System.Windows.Controls.Page> ' dan bir gezinti olayı ile kaydedersiniz, önceki örnekte olduğu gibi, olay işleyicisinin de kaydını kaldırmanız gerekir. Bunu yapmazsanız, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gezintisinin günlüğü kullanarak <xref:System.Windows.Controls.Page> gezinmeyi hatırlıyor olması bakımından yan etkileri olabilir.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Günlükle gezinti hatırlama

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], gezinmekte olduğunuz sayfaları anımsamak için iki yığın kullanır: bir arka yığın ve bir ileri yığın. Geçerli <xref:System.Windows.Controls.Page> ' dan yeni bir <xref:System.Windows.Controls.Page> ' e gittiğinizde veya varolan bir <xref:System.Windows.Controls.Page> ' ye ilettiğinizde, geçerli <xref:System.Windows.Controls.Page> *arka yığına*eklenir. Geçerli <xref:System.Windows.Controls.Page> ' dan önceki <xref:System.Windows.Controls.Page> ' e gittiğinizde, geçerli <xref:System.Windows.Controls.Page> *İleri yığına*eklenir. Arka yığın, ileri yığın ve bunları yönetme işlevleri, toplu olarak günlük olarak adlandırılır. Arka yığındaki her öğe ve ileri yığın, <xref:System.Windows.Navigation.JournalEntry> sınıfının bir örneğidir ve *günlük girdisi*olarak adlandırılır.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer 'da günlük gezinme

Kavramsal olarak, günlük, Internet Explorer 'daki **geri** ve **İleri** düğmeleriyle aynı şekilde çalışır. Bunlar aşağıdaki şekilde gösterilmiştir.

![Geri]ve ileri düğmeleri geri(./media/navigation-overview/back-and-forward-navigation.png "ve ileri düğmeleriyle gezinir.")

Internet Explorer tarafından barındırılan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], Internet Explorer 'ın gezinti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' ye tıklayarak günlüğü tümleştirir. Bu, kullanıcıların Internet Explorer 'daki **geri**, **Ileri**ve **son sayfalar** düğmelerini kullanarak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' daki sayfalarda gezinmelerini sağlar.

> [!IMPORTANT]
> Internet Explorer 'da, bir Kullanıcı [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' dan uzaklaştığında ve yalnızca canlı tutulmayan sayfalara ait günlük girişleri tutulur. Sayfaların canlı tutulması hakkında tartışma için, bu konunun ilerleyen kısımlarında [sayfa ömrü ve günlük](#PageLifetime) bölümüne bakın.

Varsayılan olarak, Internet Explorer 'ın **son sayfalar** listesinde görünen her bir @no__t için metin, <xref:System.Windows.Controls.Page> için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ' dir. Çoğu durumda bu, kullanıcıya özellikle anlamlı değildir. Neyse ki, aşağıdaki seçeneklerden birini kullanarak metni değiştirebilirsiniz:

1. İliştirilmiş `JournalEntry.Name` özniteliği değeri.

2. @No__t-0 özniteliği değeri.

3. @No__t-0 öznitelik değeri ve geçerli <xref:System.Windows.Controls.Page> için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

4. Geçerli <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Varsayılanını

Seçeneklerin listelenme sırası, metni bulmak için öncelik sırasına göre eşleşir. Örneğin, `JournalEntry.Name` ayarlanmışsa, diğer değerler yoksayılır.

Aşağıdaki örnek, bir günlük girişi için görüntülenen metni değiştirmek üzere `Page.Title` özniteliğini kullanır.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>WPF kullanarak günlükte gezinme

Bir Kullanıcı Internet Explorer 'daki **geri**, **Ileri**ve **son sayfaları** kullanarak günlükte gezinse de, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından sunulan hem bildirime dayalı hem de programlı mekanizmaların kullanıldığı günlükte da gezinebilirsiniz. Bunu yapmak için bir neden, sayfalarınızda özel gezinti 'leri sağlamaktır.

@No__t-0 tarafından sunulan gezinti komutlarını kullanarak bildirimli olarak günlük gezinti desteği ekleyebilirsiniz. Aşağıdaki örnek `BrowseBack` gezinti komutunun nasıl kullanılacağını gösterir.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

@No__t-0 sınıfının aşağıdaki üyelerinden birini kullanarak günlüğe programlı bir şekilde gidebilirsiniz:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Günlük Ayrıca, bu konunun ilerleyen kısımlarında bulunan [Içerik durumunu gezinti geçmişiyle tutma](#RetainingContentStateWithNavigationHistory) bölümünde anlatıldığı gibi programlı bir şekilde yönetilebilir.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Sayfa ömrü ve günlüğü

Grafik, animasyon ve medya dahil zengin içerik içeren birkaç sayfalı [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] düşünün. Özellikle video ve ses medyası kullanılıyorsa, bu gibi sayfalar için bellek ayak izi oldukça büyük olabilir. Günlük "anımsar" olarak işaretlenmiş olan sayfaları (örneğin, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]), büyük ve belirgin bir bellek miktarını hızla tüketebilir.

Bu nedenle, günlüğün varsayılan davranışı, <xref:System.Windows.Controls.Page> nesnesine bir başvuru yerine her günlük girişinde <xref:System.Windows.Controls.Page> meta verileri depolamadır. Bir günlük girişi gezindiği zaman, <xref:System.Windows.Controls.Page> meta verisi belirtilen <xref:System.Windows.Controls.Page> ' in yeni bir örneğini oluşturmak için kullanılır. Sonuç olarak, gezindiği her @no__t 0 ' ın ömrü aşağıdaki şekilde gösterilmiştir.

![Sayfa ömrü](./media/navigation-overview/navigated-page-lifetime.png "Bu, bir sayfa gezindiği zaman ömrünü gösterir.")

Varsayılan günlük kaydı davranışının kullanılması bellek tüketimine kaydedebilse de, sayfa başına işleme performansı azaltılabilir; @no__t yeniden örnekleniyor-0, özellikle çok sayıda içerik varsa zaman yoğunluğu olabilir. Günlükte <xref:System.Windows.Controls.Page> örneğini tutmanız gerekiyorsa, bunu yapmak için iki teknikte çizim yapabilirsiniz. İlk olarak, <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemini çağırarak program aracılığıyla <xref:System.Windows.Controls.Page> nesnesine gidebilirsiniz.

İkinci olarak, <xref:System.Windows.Controls.Page.KeepAlive%2A> özelliğini `true` (varsayılan değer `false`) olarak ayarlayarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' ın günlükte <xref:System.Windows.Controls.Page> örneğini korumasını belirtebilirsiniz. Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Controls.Page.KeepAlive%2A> ' ı biçimlendirmeye bildirimli olarak ayarlayabilirsiniz.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Etkin tutulan <xref:System.Windows.Controls.Page> yaşam süresi, olmayan bir sunucudan daha çok farklıdır. Canlı tutulan bir <xref:System.Windows.Controls.Page> ' a gidildiği zaman, etkin olmayan bir <xref:System.Windows.Controls.Page> gibi oluşturulur. Ancak, <xref:System.Windows.Controls.Page> ' ın bir örneği günlüğe korunduğu için, günlükte kaldığı sürece hiçbir zaman yeniden örneklenemez. Sonuç olarak, bir @no__t 0 ' ın her gezin@no__t ilişinde çağrılması gereken başlatma mantığı varsa, bunu oluşturucudan <xref:System.Windows.FrameworkElement.Loaded> olayı için bir işleyiciye taşımalısınız. Aşağıdaki şekilde gösterildiği gibi, <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.FrameworkElement.Unloaded> olayları sırasıyla bir <xref:System.Windows.Controls.Page> ' ye gidildiği her seferinde de oluşturulur.

![Yüklenen ve yüklenmeyen olaylar başlatıldığında](./media/navigation-overview/loaded-and-unloaded-events.png "yüklendi ve bir sayfaya gidildiği zaman kaldırılan olaylar tetiklenir.")

@No__t-0 etkin tutulmazsa, aşağıdakilerden birini yapmanız gerekmez:

- Bir başvuruyu veya bunun herhangi bir bölümünü saklayın.

- Olay işleyicilerini, tarafından uygulanmayan olaylarla kaydedin.

Bunlardan herhangi birini yapmak, <xref:System.Windows.Controls.Page> ' ı bellekten kaldırıldıktan sonra bile bellekte bekletilmeye zorlayan başvurular oluşturur.

Genel olarak, @no__t 1 ' in etkin tutulması için varsayılan <xref:System.Windows.Controls.Page> davranışını tercih etmelisiniz. Ancak, bu, sonraki bölümde ele alınan durum etkilerine sahiptir.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Içerik durumunu gezinti geçmişi ile koruma

Bir <xref:System.Windows.Controls.Page> etkin tutulmazsa ve kullanıcıdan veri toplayacak denetimler içeriyorsa, bir Kullanıcı <xref:System.Windows.Controls.Page> ' den uzaklaştığında verilere ne olur? Kullanıcı deneyimi perspektifinden, Kullanıcı daha önce girdikleri verileri görmeyi bekler. Ne yazık ki, her bir gezintide <xref:System.Windows.Controls.Page> ' ın yeni bir örneği oluşturulduğundan, verilerin toplandığı denetimlerin yeniden oluşturulması ve verilerin kaybolması.

Neyse ki günlük, Denetim verileri de dahil olmak üzere <xref:System.Windows.Controls.Page> gezginlerinin genelinde verileri hatırlama desteği sağlar. Özellikle, her bir @no__t için günlük girdisi, ilişkili <xref:System.Windows.Controls.Page> durumu için geçici bir kapsayıcı görevi görür. Aşağıdaki adımlar, <xref:System.Windows.Controls.Page> ' dan gezindiği zaman bu desteğin nasıl kullanıldığını özetler:

1. Geçerli <xref:System.Windows.Controls.Page> girişi günlüğe eklenir.

2. @No__t-0 ' ın durumu, arka yığına eklenen Bu sayfa için günlük girdisiyle birlikte depolanır.

3. Yeni <xref:System.Windows.Controls.Page> ' a gidildi.

@No__t-0 sayfası geri gezinirken, günlük kullanılarak aşağıdaki adımlar gerçekleştirilir:

1. @No__t-0 (arka yığındaki en üst günlük girdisi) örneği oluşturulur.

2. @No__t-0, <xref:System.Windows.Controls.Page> için günlük girdisiyle depolanan durumla yenilenir.

3. @No__t-0 ' a geri gezinilebilir.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], aşağıdaki denetimler <xref:System.Windows.Controls.Page> ' de kullanıldığında otomatik olarak bu desteği kullanır:

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

@No__t-0 bu denetimleri kullanıyorsa, bunlara girilen veriler, aşağıdaki şekilde **sık kullanılan renk**<xref:System.Windows.Controls.ListBox> ' te gösterildiği gibi, <xref:System.Windows.Controls.Page> gezginlerine göre hatırlanır.

Girilen ![durum verilerini hatırlayacağı denetimlerin bulunduğu sayfa](./media/navigation-overview/data-remembered-across-page-navigations.png ", sayfa gezginlerine göre hatırlanır.")

@No__t-0 ' ın önceki listede bulunanlar dışında bir denetim varsa veya durum özel nesnelerde depolandığında, günlüğün <xref:System.Windows.Controls.Page> gezginlerinin durumunu anımsamasını sağlamak için kod yazmanız gerekir.

@No__t-0 gezginlerinin tamamında küçük bir durum parçalarını hatırlamanız gerekiyorsa, <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> meta verileri bayrağıyla yapılandırılan bağımlılık özelliklerini (bkz. <xref:System.Windows.DependencyProperty>) kullanabilirsiniz.

@No__t-0 ' ın gezinmeler genelinde hatırlamaları gereken durum birden çok veri parçasına sahip olursa, eyaletinizi tek bir sınıfta kapsüllemek ve <xref:System.Windows.Navigation.IProvideCustomContentState> arabirimini uygulamak için daha az kod yoğunluğu sağlayabilirsiniz.

Tek bir @no__t, <xref:System.Windows.Controls.Page> ' den ilerlemeden farklı durumlardan birine gitmeniz gerekiyorsa, <xref:System.Windows.Navigation.IProvideCustomContentState> ve <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> ' ü kullanabilirsiniz.

<a name="Cookies"></a>

### <a name="cookies"></a>Özgü

@No__t-0 uygulamalarının verileri depolayabileceği diğer bir yöntem, <xref:System.Windows.Application.SetCookie%2A> ve <xref:System.Windows.Application.GetCookie%2A> yöntemleri kullanılarak oluşturulan, güncellenen ve silinen tanımlama bilgileriyle yapılır. @No__t-0 ' da oluşturabileceğiniz tanımlama bilgileri, diğer Web uygulaması türleri tarafından kullanılan tanımlama bilgilerine sahip olabilir; tanımlama bilgileri, uygulama oturumları sırasında veya üzerinde bir istemci makinesinde bir uygulama tarafından depolanan rastgele veri parçalarından oluşur. Tanımlama bilgisi verileri genellikle aşağıdaki biçimde bir ad/değer çifti biçimini alır.

*Ad* `=` *değeri*

Veriler <xref:System.Windows.Application.SetCookie%2A> ' a geçirildiğinde, tanımlama bilgisinin ayarlanması gereken konumun <xref:System.Uri> ' i ile birlikte, bellek içinde bir tanımlama bilgisi oluşturulur ve yalnızca geçerli uygulama oturumunun süresi boyunca kullanılabilir. Bu tür tanımlama bilgisine *oturum tanımlama bilgisi*denir.

Bir tanımlama bilgisini uygulama oturumlarında depolamak için, aşağıdaki biçimi kullanarak tanımlama bilgisine bir sona erme tarihi eklenmelidir.

*Ad* `=` *değer* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Son kullanma tarihine sahip bir tanımlama bilgisi, tanımlama bilgisi süresi dolana kadar geçerli Windows yüklemesinin Temporary Internet Files klasöründe depolanır. Bu tür bir tanımlama bilgisi, uygulama oturumlarında devam ettiğinden *kalıcı tanımlama bilgisi* olarak bilinir.

@No__t-0 yöntemini çağırarak hem oturum hem de kalıcı tanımlama bilgilerini, tanımlama bilgisinin <xref:System.Windows.Application.SetCookie%2A> yöntemiyle ayarlandığı konumun <xref:System.Uri> geçirerek elde edersiniz.

@No__t-0 ' da tanımlama bilgilerinin desteklenme yöntemlerinden bazıları aşağıda verilmiştir:

- @no__t-tek başına uygulamalar ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], tanımlama bilgilerini oluşturup yönetebilir.

- @No__t-0 tarafından oluşturulan tanımlama bilgilerine tarayıcıdan erişilebilir.

- aynı etki alanındaki [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] tanımlama bilgilerini oluşturup paylaşabilir.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve aynı etki alanındaki HTML sayfaları tanımlama bilgilerini oluşturup paylaşabilir.

- @No__t-0 ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları Web istekleri yaparken tanımlama bilgileri gönderilir.

- IFRAME 'ler içinde barındırılan üst düzey [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], tanımlama bilgilerine erişebilir.

- @No__t-0 ' daki tanımlama bilgisi desteği desteklenen tüm tarayıcılarda aynıdır.

- Internet Explorer 'da, tanımlama bilgileriyle ilgili P3P ilkesi, özellikle birinci taraf ve üçüncü taraf [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ' e göre [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından kabul edilir.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Yapılandırılmış gezinti

Bir <xref:System.Windows.Controls.Page> ' dan diğerine veri geçirmeniz gerekiyorsa, verileri bağımsız değişken olarak <xref:System.Windows.Controls.Page> ' in parametresiz oluşturucusuna geçirebilirsiniz. Bu tekniği kullanırsanız, <xref:System.Windows.Controls.Page> canlı tutmanız gerektiğini unutmayın; Aksi takdirde, <xref:System.Windows.Controls.Page> ' e bir sonraki sefer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], parametresiz oluşturucuyu kullanarak <xref:System.Windows.Controls.Page> ' ü yeniden başlatır.

Alternatif olarak, <xref:System.Windows.Controls.Page> ' ı, geçirilmesi gereken verilerle ayarlanmış özellikleri uygulayabilir. Ancak, <xref:System.Windows.Controls.Page> ' ın verileri kendisine gidildiği <xref:System.Windows.Controls.Page> ' e geçirmesi gerektiğinde bu şeyler karmaşık hale gelir. Bu sorun, gezinmeden sonra <xref:System.Windows.Controls.Page> ' ın geri döndürüldüğünden emin olmak için gezinmede mekanizmaların yerel olarak desteklemediği bir sorundur. Temelde, gezinme çağrı/döndürme semantiğini desteklemez. Bu sorunu çözmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Controls.Page> ' nin öngörülebilir ve yapılandırılmış bir biçimde döndürüldüğünden emin olmak için kullanabileceğiniz <xref:System.Windows.Navigation.PageFunction%601> sınıfını sağlar. Daha fazla bilgi için bkz. [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow sınıfı

Bu noktada, gezinilebilir içeriğe sahip uygulamalar oluşturmak için en büyük olasılıkla kullanabileceğiniz Gezinti hizmetlerinin gamutu olduğunu gördünüz. Bu hizmetler, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ile sınırlı olmamakla birlikte [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] bağlamında tartışılır. Modern işletim sistemleri ve Windows uygulamaları, tek başına uygulamalara tarayıcı stili gezinme eklemek için modern kullanıcıların tarayıcı deneyiminden yararlanır. Ortak örnekler şunlardır:

- **Sözcük eşanlamlılar sözlüğü**: kelime seçeneklerine gitme.

- **Dosya Gezgini**: dosya ve klasörlerde gezin.

- **Sihirbazlar**: karmaşık bir görevi, arasında gezinilemeyen birden çok sayfaya ayırma. Windows özelliklerinin eklenmesini ve kaldırılmasını işleyen Windows Bileşenleri Sihirbazı bir örnektir.

Tek başına uygulamalarınıza tarayıcı stili gezinme eklemek için <xref:System.Windows.Navigation.NavigationWindow> sınıfını kullanabilirsiniz. <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Window> ' den türetilir ve bunu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sağlayan gezinti için aynı desteğe genişletir. @No__t-0 ' i tek başına uygulamanızın ana penceresi veya iletişim kutusu gibi ikincil bir pencere olarak kullanabilirsiniz.

@No__t-0 ' ı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' deki en üst düzey sınıfların (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page> vb.) uygulamak için, biçimlendirme ve arka plan kod birleşimini kullanırsınız. Bu, aşağıdaki örnekte gösterilmiştir.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Bu kod, <xref:System.Windows.Navigation.NavigationWindow> açıldığında otomatik olarak bir <xref:System.Windows.Controls.Page> (Ana sayfa. xaml) öğesine giden <xref:System.Windows.Navigation.NavigationWindow> oluşturur. @No__t-0 ana uygulama penceresuyorsa, bu özniteliği başlatmak için `StartupUri` özniteliğini kullanabilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Aşağıdaki şekilde, tek başına bir uygulamanın ana penceresi olarak <xref:System.Windows.Navigation.NavigationWindow> gösterilmektedir.

Ana pencere olarak ![ana]pencere(./media/navigation-overview/navigation-window-as-main-window.png "Gezinti penceresi")

Bu şekilde, <xref:System.Windows.Navigation.NavigationWindow> ' ın bir başlık olduğunu görebilirsiniz. Bu, önceki örnekteki <xref:System.Windows.Navigation.NavigationWindow> uygulama kodunda ayarlanmamış olsa da olabilir. Bunun yerine, başlık, aşağıdaki kodda gösterilen <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği kullanılarak ayarlanır.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

@No__t-0 ve <xref:System.Windows.Controls.Page.WindowHeight%2A> özelliklerinin ayarlanması ayrıca <xref:System.Windows.Navigation.NavigationWindow> ' i de etkiler.

Genellikle kendi davranışını veya görünümünü özelleştirmeniz gerektiğinde kendi @no__t (0) uygulayın. Aksi takdirde, bir kısayolu kullanabilirsiniz. Tek başına bir uygulamada <xref:System.Windows.Application.StartupUri%2A> olarak bir <xref:System.Windows.Controls.Page> paketi @no__t belirtirseniz, <xref:System.Windows.Application> ' ü @no__t barındırmak için otomatik olarak bir <xref:System.Windows.Navigation.NavigationWindow> oluşturur. Aşağıdaki biçimlendirmede bunun nasıl etkinleştirileceği gösterilmektedir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

İletişim kutusu gibi bir ikincil uygulama penceresinin <xref:System.Windows.Navigation.NavigationWindow> olmasını istiyorsanız, aşağıdaki örnekteki kodu kullanarak açabilirsiniz.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Aşağıdaki şekilde sonuç gösterilmektedir.

İletişim kutusu olarak ![bir iletişim kutusu](./media/navigation-overview/navigation-window-as-dialog-box.png "Gezinti penceresi")

Gördüğünüz gibi, <xref:System.Windows.Navigation.NavigationWindow>, kullanıcıların günlükte gezinmesine izin veren Internet Explorer stili **geri** ve **İleri** düğmelerini görüntüler. Bu düğmeler, aşağıdaki şekilde gösterildiği gibi aynı kullanıcı deneyimini sağlar.

(./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Gezinti penceresindeki NavigationWindow geri ve ileri düğmelerine") ![geri ve ileri düğmeleri]

Sayfalarınız kendi günlük gezintisi desteğini ve Kullanıcı arabirimini sağladıysanız, <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> özelliğinin değerini `false` olarak ayarlayarak, <xref:System.Windows.Navigation.NavigationWindow> ' i tarafından görüntülenmiş **geri** ve **İleri** düğmelerini gizleyebilirsiniz.

Alternatif olarak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' daki özelleştirme desteğini kullanarak <xref:System.Windows.Navigation.NavigationWindow> ' nin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' i değiştirebilirsiniz.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame sınıfı

Hem tarayıcı hem de <xref:System.Windows.Navigation.NavigationWindow>, gezinebilir içeriği barındıran Windows ' dır. Bazı durumlarda, uygulamalarda bir pencerenin tamamında barındırılması gerekmeyen içerikler vardır. Bunun yerine, bu içerik diğer içeriğin içinde barındırılır. @No__t-0 sınıfını kullanarak diğer içeriklere gezinebilir içerik ekleyebilirsiniz. <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow> ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ile aynı desteği sağlar.

Aşağıdaki örnek, `Frame` öğesini kullanarak <xref:System.Windows.Controls.Frame> ' a <xref:System.Windows.Controls.Page> ' e nasıl ekleneceğini gösterir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Bu biçimlendirme, <xref:System.Windows.Controls.Frame> ' ün ilk olarak gezindiği <xref:System.Windows.Controls.Page> için `Frame` öğesinin `Source` özniteliğini bir paketiyle ayarlar [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Aşağıdaki şekilde, birkaç sayfa arasında gezindiği <xref:System.Windows.Controls.Frame> ' a sahip bir <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gösterilmektedir.

Birden ![çok sayfa arasında gezindiği bir çerçeve bu,](./media/navigation-overview/frame-navigation-between-multiple-pages.png "birden çok sayfa arasında bir çerçeve gezintisi gösterir.")

Yalnızca bir <xref:System.Windows.Controls.Page> içeriğinin içinde <xref:System.Windows.Controls.Frame> kullanmanız gerekmez. Ayrıca, bir <xref:System.Windows.Window> içeriğinin içinde <xref:System.Windows.Controls.Frame> barındırmak için de ortaktır.

Varsayılan olarak, <xref:System.Windows.Controls.Frame> yalnızca başka bir günlük yokluğunda kendi günlüğünü kullanır. @No__t-0 ' ı bir <xref:System.Windows.Navigation.NavigationWindow> veya [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' de barındırılan içeriğin parçasıysa, <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow> veya [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' e ait günlüğü kullanır. Bazen, <xref:System.Windows.Controls.Frame> ' ın kendi günlüğünden sorumlu olması gerekebilir. Bunun bir nedeni, <xref:System.Windows.Controls.Frame> tarafından barındırılan sayfalarda günlük gezintisine izin vermektedir. Bu, aşağıdaki şekilde gösterilmiştir.

![Çerçeve ve sayfa diyagramı bu,](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "bir çerçeve tarafından barındırılan sayfaların içindeki günlük gezintisini gösterir.")

Bu durumda, <xref:System.Windows.Controls.Frame> ' ı <xref:System.Windows.Controls.Frame> ' nin <xref:System.Windows.Controls.Frame.JournalOwnership%2A> özelliğini <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> ' e ayarlayarak kendi günlüğünü kullanacak şekilde yapılandırabilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Aşağıdaki şekilde, kendi günlüğünü kullanan bir <xref:System.Windows.Controls.Frame> içinde gezinmenin etkisi gösterilmektedir.

Kendi ![günlüğünü kullanan bir çerçeve](./media/navigation-overview/frame-uses-its-own-journal.png "Bu, kendi günlüğünü kullanan bir çerçeve içinde gezinmenin etkisini gösterir.")

Günlük girişlerinin, Internet Explorer yerine <xref:System.Windows.Controls.Frame> ' de gezinti @no__t gösterildiğini unutmayın.

> [!NOTE]
> @No__t-0, bir <xref:System.Windows.Window> ' de barındırılan içeriğin parçasıysa, <xref:System.Windows.Controls.Frame> kendi günlüğünü kullanır ve sonuç olarak kendi gezinti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' ü görüntüler.

Kullanıcı deneyiminizin bir <xref:System.Windows.Controls.Frame> ' ı, gezinti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' i göstermeden kendi günlüğünü sağlaması gerekiyorsa, <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> ' i <xref:System.Windows.Visibility.Hidden> ' e ayarlayarak gezinti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' yi gizleyebilirsiniz. Bu, aşağıdaki biçimlendirmede gösterilmiştir.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Gezinti konakları

<xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow>, gezinti konakları olarak bilinen sınıflardır. *Gezinti ana bilgisayarı* , içeriğe gidebileceğiniz ve içeriği görüntüleyebilen bir sınıftır. Bunu gerçekleştirmek için, her bir gezinti ana bilgisayarı kendi <xref:System.Windows.Navigation.NavigationService> ve günlüğünü kullanır. Bir gezinti konağının temel yapımı aşağıdaki şekilde gösterilmiştir.

![Gezgin diyagramlarını](./media/navigation-overview/navigation-host-construction.png "bir gezinti ana bilgisayarının temel yapımı")

Temelde bu, <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.Frame> ' i, tarayıcıda barındırıldığı [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' nin sunduğu aynı gezinti desteğini sağlamasına izin verir.

@No__t-0 ve bir günlük kullanmanın yanı sıra, gezinti konakları <xref:System.Windows.Navigation.NavigationService> ' i uygulayan aynı üyeleri uygular. Bu, aşağıdaki şekilde gösterilmiştir.

Bir ![çerçevedeki ve NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "gezinme penceresinde ve çerçevede") bulunan bir günlük

Bu, gezinti desteğini doğrudan bunlara karşı programbırakmanıza olanak tanır. @No__t-2 ' de barındırılan bir <xref:System.Windows.Controls.Frame> için özel bir gezinti @no__t sağlamanız gerekiyorsa bunu göz önünde bulundurabilir. Ayrıca, her iki tür de `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) ve `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>) dahil olmak üzere ek, gezintide ilgili Üyeler uygular. Bu, sırasıyla arka yığında ve sarma yığınında bulunan günlük girişlerini listeletmanızı sağlar.

Daha önce belirtildiği gibi, bir uygulama içinde birden çok günlük bulunabilir. Aşağıdaki şekilde, bunun gerçekleşene zaman gerçekleşebileceğinizi bir örnek verilmiştir.

![Bir uygulama Içinde birden çok](./media/navigation-overview/multiple-journals-in-one-application.png "günlük bu, bir uygulamada birden fazla günlüğe ait bir örnektir.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML sayfaları dışındaki Içeriğe gitme

Bu konu boyunca <xref:System.Windows.Controls.Page> ve Pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' nin çeşitli gezinti özelliklerini göstermek için kullanılmıştır. Ancak, bir uygulamaya derlenen <xref:System.Windows.Controls.Page> ' a gezinilebilen tek içerik türü değildir ve Pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ' i içerik belirlemenin tek yolu değildir.

Bu bölümde gösterildiği gibi, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalarına, HTML dosyalarına ve nesnelerine de gidebilirsiniz.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Gevşek XAML dosyalarına gitme

Gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası, aşağıdaki özelliklere sahip bir dosyadır:

- Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (yani, kod yok) içerir.

- Uygun bir ad alanı bildirimine sahiptir.

- . Xaml dosya adı uzantısına sahiptir.

Örneğin, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası, kişi. xaml olarak depolanan aşağıdaki içeriği göz önünde bulundurun.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Dosyaya çift tıkladığınızda tarayıcı açılır ve ' a gider ve içeriği görüntüler. Bu, aşağıdaki şekilde gösterilmiştir.

![Person. xaml dosyasında Içeriğin gösterilmesi],(./media/navigation-overview/contents-of-person-xaml-file.png "Person. xaml dosyasının içeriğini gösterir.")

Aşağıdaki listeden gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası görüntüleyebilirsiniz:

- Yerel makinedeki, intranetteki veya Internet 'teki bir Web sitesi.

- Evrensel adlandırma kuralı (UNC) dosya paylaşma.

- Yerel disk.

Gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası tarayıcının sık kullanılanlarına eklenebilir veya tarayıcının giriş sayfası olabilir.

> [!NOTE]
> Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yayımlama ve başlatma hakkında daha fazla bilgi için bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).

Gevşek @no__t ile ilgili bir sınırlama-0, yalnızca kısmi güvende çalıştırmak için güvenli olan içeriği barındırmanıza olanak sağlar. Örneğin, `Window`, gevşek bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasının kök öğesi olamaz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Çerçeve kullanarak HTML dosyalarına gitme

Tahmin edebileceğiniz gibi, HTML 'ye de gidebilirsiniz. Yalnızca http düzenini kullanan bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sağlamanız gerekir. Örneğin, aşağıdaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], HTML sayfasına giden bir <xref:System.Windows.Controls.Frame> gösterir.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

HTML 'ye gitmek için özel izinler gerekir. Örneğin, Internet bölgesi kısmi güven güvenlik alanı ' nda çalışan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' dan geziniyorsunuz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser denetimini kullanarak HTML dosyalarına gitme

@No__t-0 denetimi HTML belgesi barındırma, gezinti ve betik/yönetilen kod birlikte çalışabilirliği destekler. @No__t-0 denetimiyle ilgili ayrıntılı bilgi için bkz. <xref:System.Windows.Controls.WebBrowser>.

@No__t-0 gibi <xref:System.Windows.Controls.WebBrowser> kullanılarak HTML 'ye gitmek özel izinler gerektirir. Örneğin, kısmi güven uygulamasından yalnızca kaynak sitesinde bulunan HTML 'ye gidebilirsiniz. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Özel nesnelere gitme

Özel nesneler olarak depolanan verileriniz varsa, bu verileri görüntülemenin bir yolu, bu nesnelere bağlanan içeriğe sahip bir <xref:System.Windows.Controls.Page> oluşturmaktır (bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md)). Yalnızca nesneleri görüntüleyen bir sayfanın tamamını oluşturmak için ek yüke gerek yoksa, bunun yerine doğrudan bunlara gidebilirsiniz.

Aşağıdaki kodda uygulanan `Person` sınıfını göz önünde bulundurun.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Bu sayfaya gitmek için aşağıdaki kodda gösterildiği gibi <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> yöntemini çağırın.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Aşağıdaki şekilde sonuç gösterilmektedir.

Bir sınıfa giden bir ![sayfa](./media/navigation-overview/page-navigates-to-an-object.png ", bir nesneye giden bir sayfa örneğidir.")

Bu şekilde, hiçbir şeyin yararlı görüntülendiğini görebilirsiniz. Aslında, görüntülenen değer, **kişi** nesnesi için `ToString` yönteminin dönüş değeridir; Varsayılan olarak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ' nin nesneniz temsil etmek için kullanabileceği tek değerdir. Daha anlamlı bilgiler döndürmek için `ToString` yöntemini geçersiz kılabilirsiniz, ancak yalnızca bir dize değeri olmaya devam eder. @No__t-0 ' ın sunum olanaklarından faydalanan bir teknik, veri şablonu kullanmaktır. @No__t-0 ' ın belirli bir türdeki nesneyle ilişkilendirebileceğiniz bir veri şablonu uygulayabilirsiniz. Aşağıdaki kod `Person` nesnesi için bir veri şablonu gösterir.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Burada, veri şablonu `DataType` özniteliğinde `x:Type` biçimlendirme uzantısı kullanılarak `Person` türüyle ilişkilendirilir. Daha sonra veri şablonu `TextBlock` öğelerini (bkz. <xref:System.Windows.Controls.TextBlock>) `Person` sınıfının özelliklerine bağlar. Aşağıdaki şekilde `Person` nesnesinin güncelleştirilmiş görünümü gösterilmektedir.

Veri şablonu olan bir sınıfa ![gezinerek](./media/navigation-overview/navigating-to-a-class.png "veri şablonu") olan bir sınıfa gitme.

Bu tekniğin avantajı, nesneleri uygulamanızda her yerde tutarlı bir şekilde göstermek için veri şablonunu yeniden kullanabilerek elde ettiğiniz tutardır.

Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Güvenlik

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gezinti desteği, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ' i Internet üzerinden gezinmesine olanak tanır ve uygulamaların üçüncü taraf içeriği barındıralmasına izin verir. Her iki uygulamayı ve kullanıcıyı zararlı davranışlara karşı korumak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], [güvenlik](../security-wpf.md) ve [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md)bölümünde ele alınan çeşitli güvenlik özellikleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Uygulama yönetimine genel bakış](application-management-overview.md)
- [WPF 'de paket URI 'Leri](pack-uris-in-wpf.md)
- [Yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md)
- [Gezinti topolojilerine genel bakış](navigation-topologies-overview.md)
- [Nasıl yapılır konuları](navigation-how-to-topics.md)
- [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md)
