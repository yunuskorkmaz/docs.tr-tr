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
ms.openlocfilehash: 826cfc0ea7f681e1f7cbe858008c24a4941f0e11
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335088"
---
# <a name="navigation-overview"></a>Gezintiye Genel Bakış
Windows Presentation Foundation (WPF), iki uygulama türünde de kullanılabilen tarayıcı stili gezintiyi destekler: tek başına uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Gezinti, paket içeriğine [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar <xref:System.Windows.Controls.Page> sınıfı. Diğerine gidebilirsiniz <xref:System.Windows.Controls.Page> diğerine bildirimli olarak, kullanarak bir <xref:System.Windows.Documents.Hyperlink>, kullanarak programlama yoluyla veya <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Günlük sayfadan çıkıldığında sayfaları unutmayın ve bunları geri gitmek için kullanır.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, ve günlük tarafından sunulan gezinti desteği setinin form [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu genel bakışta Gezinti gevşek içeren Gelişmiş gezinti desteği kapsayan önce bu özelliklerin ayrıntılı keşfediyor [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyaları ve nesneler.  
  
> [!NOTE]
>  Bu konu başlığında, "browser" terimi, barındırabilecek tarayıcılar ifade eder [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şu anda içeren uygulamalar, [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ve Firefox. Belirli durumlarda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellikler, yalnızca belirli bir tarayıcı tarafından desteklenir, tarayıcı sürümü başvuruda bulunulur.  

## <a name="navigation-in-wpf-applications"></a>WPF uygulamalarında Gezinti  
 Bu konu, içinde anahtar Gezinti özelliklerine genel bakış sağlar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu özellikler hem tek başına uygulamalar için kullanılabilir ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bunları bu konuda bağlamında sunar ancak bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Bu konuda, derlemek ve dağıtmak nasıl ele alınmamaktadır [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Daha fazla bilgi için [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bkz: [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).  
  
 Bu bölümde açıklanmaktadır ve gezinti şu yönlerini gösterir:  
  
-   [Bir sayfa uygulama](#CreatingAXAMLPage)  
  
-   [Başlangıç sayfası yapılandırma](#Configuring_a_Start_Page)  
  
-   [Ana pencerenin başlığı, genişlik ve yükseklik yapılandırma](#ConfiguringAXAMLPage)  
  
-   [Köprü Gezinti](#NavigatingBetweenXAMLPages)  
  
-   [Bölüm gezintisi](#FragmentNavigation)  
  
-   [Gezinti hizmeti](#NavigationService)  
  
-   [Programlı Gezinti Gezinti hizmeti](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Gezinti ömrü](#Navigation_Lifetime)  
  
-   [Günlük ile gezinti hatırlama](#NavigationHistory)  
  
-   [Sayfa ömrü ve günlük](#PageLifetime)  
  
-   [Gezinme geçmişi ile içerik durumu tutma](#RetainingContentStateWithNavigationHistory)  
  
-   [Tanımlama bilgileri](#Cookies)  
  
-   [Yapılandırılmış gezintiye](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Bir sayfa uygulama  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], .NET Framework nesneleri, özel nesneleri, sabit listesi değerleri, kullanıcı denetimleri dahil çeşitli içerik türleri gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyaları. Ancak, en yaygın ve kolay yolu için paket içeriğini kullanarak olduğunu fark edeceksiniz <xref:System.Windows.Controls.Page>. Ayrıca, <xref:System.Windows.Controls.Page> görünümlerini geliştirmek ve geliştirme işlemini basitleştirmek için Gezinti özgü özellikler uygular.  
  
 Kullanarak <xref:System.Windows.Controls.Page>, gezinebilir sayfası bildirimli olarak uygulayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme aşağıdaki gibi kullanarak içerik.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> içinde uygulanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sahip `Page` , kök öğesi olarak ve gerektiren [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ad alanı bildirimi. `Page` Gitmek ve görüntülemek için istediğiniz içerik öğesi içeriyor. Ayarlayarak içeriğinizi `Page.Content` aşağıdaki biçimlendirmede gösterildiği özellik öğesi.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` yalnızca bir alt öğe içerebilir; Önceki örnekte, tek bir içeriktir dize, "Hello, sayfa!" Uygulamada, genellikle alt öğesi bir Düzen denetimini kullanır (bkz [Düzen](../advanced/layout.md)) içerir ve içeriğinizi oluşturun.  
  
 Alt öğeleri bir `Page` öğenin içeriğini olacak şekilde değerlendirilir bir <xref:System.Windows.Controls.Page> ve sonuç olarak, açık kullanmanız gerekmez `Page.Content` bildirimi. Aşağıdaki biçimlendirme önceki örnekte bildirim temelli eşdeğeridir.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 Bu durumda, `Page.Content` alt öğeleri ile otomatik olarak ayarlanır `Page` öğesi. Daha fazla bilgi için [WPF içerik modeli](../controls/wpf-content-model.md).  
  
 Bir biçimlendirme yalnızca <xref:System.Windows.Controls.Page> içeriği görüntülemek için yararlıdır. Ancak, bir <xref:System.Windows.Controls.Page> sayfasıyla da etkileşime izin veren görüntü denetimleri de yapabilirsiniz ve kullanıcı etkileşimi olayları işleme ve uygulama mantığı çağırarak yanıtlayabilir. Etkileşimli <xref:System.Windows.Controls.Page> işaretleme ve kod arka plan, bir bileşimini kullanarak aşağıdaki örnekte gösterildiği gibi uygulanır.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 İşaretleme dosyasının ve birlikte çalışması için arka plan kod dosyasında, aşağıdaki yapılandırma izin vermek için gereklidir:  
  
-   Biçimlendirme içinde `Page` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulama oluşturulduğuna göre varlığını `x:Class` işaretlemede dosyası oluşturulmamasını [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] oluşturmak için bir `partial` türetilen sınıf <xref:System.Windows.Controls.Page> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu eklenmesini gerektiren bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildirimi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Oluşturulan `partial` sınıfının Implements `InitializeComponent`, hangi olayları kaydedin ve bu özellikleri ayarlamak için çağrılan biçimlendirme içinde uygulanır.  
  
-   Arka plan, kod sınıfı olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` biçimlendirme ve bu öznitelikte türetilmesi gereken <xref:System.Windows.Controls.Page>. Bu arka plan kod dosyası ile ilişkili olmasını sağlar `partial` uygulama oluşturulduğunda işaretleme dosyasının için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).  
  
-   Arka plan, kod içinde <xref:System.Windows.Controls.Page> sınıfı çağıran bir oluşturucu uygulanmalı `InitializeComponent` yöntemi. `InitializeComponent` uygulanan tarafından işaretleme dosyasının üretilmiş `partial` olaylarını kaydetmek ve biçimlendirme içinde tanımlanan özelliklerini ayarlamak için sınıf.  
  
> [!NOTE]
>  Yeni bir eklediğinizde <xref:System.Windows.Controls.Page> kullanarak proje [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> işaretleme ve kod arka plan, hem kullanılarak uygulanır ve işaretleme ve arka plan kod dosyaları arasındaki ilişki oluşturmak için gerekli yapılandırmayı içerir burada açıklanmıştır.  
  
 Sonra bir <xref:System.Windows.Controls.Page>, kendisine gidebilirsiniz. İlk belirtmek için <xref:System.Windows.Controls.Page> uygulamaya gider, başlangıç yapılandırmanız gereken <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Başlangıç sayfası yapılandırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] belirli bir miktarda bir tarayıcıda barındırılması için uygulama altyapısı gerektirir. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> sınıfı gerekli uygulama altyapısı kuran uygulama tanımı'nın bir parçasıdır (bkz [uygulama yönetimine genel bakış](application-management-overview.md)).  
  
 Uygulama tanımı olarak yapılandırılmış işaretleme dosyasının işaretleme ve kod arka plan, hem kullanarak genellikle uygulanan bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`ApplicationDefinition` öğesi. Bir uygulamanın tanımıdır aşağıdaki bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulama tanımına bir başlangıç belirtmek için kullanabilirsiniz <xref:System.Windows.Controls.Page>, olduğu <xref:System.Windows.Controls.Page> , otomatik olarak ne zaman yüklenen [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] başlatılır. Ayarlayarak bunu <xref:System.Windows.Application.StartupUri%2A> özelliğiyle [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] için istenen <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Çoğu durumda <xref:System.Windows.Controls.Page> içine derlenmiş olan veya bir uygulama ile dağıtılan. Bu gibi durumlarda, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] tanımlayan bir <xref:System.Windows.Controls.Page> bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], olduğu bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için uygun *paketi* düzeni. Paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] açıklanan daha ayrıntılı olarak [paketi URI ' WPF'de](pack-uris-in-wpf.md). Aşağıda açıklanan http Şeması kullanılarak içeriğe gidebilirsiniz.  
  
 Ayarlayabileceğiniz <xref:System.Windows.Application.StartupUri%2A> aşağıdaki örnekte gösterildiği gibi bildirimli olarak biçimlendirme içinde.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 Bu örnekte, `StartupUri` özniteliği ile göreli bir paketi ayarlanmış [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] HomePage.xaml tanımlar. Zaman [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olan başlatılan, HomePage.xaml otomatik olarak için gittiğinizde ve görüntülenir. Bu gösteren aşağıdaki şekilde tarafından gösterilen bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web sunucusundan başlatıldı.  
  
 ![XBAP sayfa](./media/navigation-overview/xbap-launched-from-a-web-server.png "bu bir Web sunucusundan başlatılan bir XBAP gösterir.")  
  
> [!NOTE]
>  Geliştirme ve dağıtımı ile ilgili daha fazla bilgi için [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bkz: [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md) ve [bir WPF uygulamasını dağıtma](deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Ana pencerenin başlığı, genişlik ve yükseklik yapılandırma  
 Bir şey önceki şekilden fark olan tarayıcı hem sekme bölmenin başlığı olduğunu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Uzun olmasının yanı sıra, etkileyici ve bilgilendirici başlığı. Bu nedenle, <xref:System.Windows.Controls.Page> ayarlayarak başlığını değiştirme bir yol sunar <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği. Ayrıca, genişlik ve yükseklik tarayıcı penceresinin ayarlayarak yapılandırabilirsiniz <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A>sırasıyla.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, ve <xref:System.Windows.Controls.Page.WindowHeight%2A> biçimlendirmesinde aşağıdaki örnekte gösterildiği gibi bildirimli olarak ayarlanabilir.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Sonuç, aşağıdaki şekilde gösterilir.  
  
 ![Pencere başlığı, yükseklik, genişlik](./media/navigation-overview/window-title-width-height.png "Bu pencere başlığı, yükseklik ve genişlik yapılandırabileceğiniz gösterir.")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Köprü Gezinti  
 Tipik bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] çeşitli sayfalar içerir. En basit yolu bir sayfadan diğerine giderler kullanmaktır bir <xref:System.Windows.Documents.Hyperlink>. Bildirimli olarak ekleyebileceğiniz bir <xref:System.Windows.Documents.Hyperlink> için bir <xref:System.Windows.Controls.Page> kullanarak `Hyperlink` öğesi, aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` öğesi aşağıdakileri gerektirir:  
  
-   Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , <xref:System.Windows.Controls.Page> , gitmek için belirtildiği gibi `NavigateUri` özniteliği.  
  
-   Bir kullanıcının metin ve görüntü gibi Gezinti başlatmak için tıklayabileceği içerik (içerik, `Hyperlink` öğesi içerir, bkz: <xref:System.Windows.Documents.Hyperlink>).  
  
 Aşağıdaki şekil gösterir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ile bir <xref:System.Windows.Controls.Page> olan bir <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Köprü sayfasıyla](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "bu köprü içeren bir sayfa ile bir XBAP gösterir.")  
  
 Beklediğiniz gibi tıklayarak <xref:System.Windows.Documents.Hyperlink> neden [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gitmek için <xref:System.Windows.Controls.Page> tarafından tanımlanan `NavigateUri` özniteliği. Ayrıca, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir giriş için önceki ekler <xref:System.Windows.Controls.Page> son sayfalar listesine [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Bu aşağıdaki şekilde gösterilmektedir.  
  
 ![Geri ve İleri düğmelerini](./media/navigation-overview/back-and-forward-navigation.png "geri ve İleri düğmelerini gidin.")  
  
 Birinden Gezintiyi Destekleme yanı sıra <xref:System.Windows.Controls.Page> diğerine <xref:System.Windows.Documents.Hyperlink> de destekler Gezinti parçası.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Bölüm gezintisi  
 *Gezinti parçalara* herhangi bir içerik parçasına Gezinti geçerli olduğu <xref:System.Windows.Controls.Page> veya başka bir <xref:System.Windows.Controls.Page>. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], içerik parçasına adlandırılmış bir öğe tarafından içerilen içeriktir. Sahip bir öğe adlandırılmış bir öğedir, `Name` öznitelik kümesi. Aşağıdaki biçimlendirme bir adlandırılmış gösterir `TextBlock` bir içerik parçası içeren öğe.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 İçin bir <xref:System.Windows.Documents.Hyperlink> bir içerik parçasına gidiş gitmek için `NavigateUri` öznitelik aşağıdakileri içerir:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , <xref:System.Windows.Controls.Page> Gitmek için içerik parçasına sahip.  
  
-   "#" Karakter.  
  
-   Öğede adını <xref:System.Windows.Controls.Page> içerik parçası içeren.  
  
 Bir parça [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki biçime sahiptir.  
  
 *PageURI* `#` *ElementName*  
  
 Aşağıdaki örneği gösterilmektedir. bir `Hyperlink` içerik parçaya gitmek için yapılandırılmış.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Bu bölümde, varsayılan parçasına Gezinti uygulamasında açıklanmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Ayrıca, kısmen gerektirip gerektirmediği kendi parça gezinme düzenini olanak tanır <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> olay.  
  
> [!IMPORTANT]
>  Gevşek parçalarında gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları (yalnızca işaretleme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ile dosyaları `Page` kök öğe olarak) aracılığıyla sayfaları yalnızca gözatılabilir varsa [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Ancak, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa için kendi parçaları gidebilirsiniz.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Gezinti hizmeti  
 Sırada <xref:System.Windows.Documents.Hyperlink> sağlayan belirli bir gezinti başlatmak bir kullanıcı <xref:System.Windows.Controls.Page>, bulma ve sayfa yükleme işlemlerini tarafından gerçekleştirilen <xref:System.Windows.Navigation.NavigationService> sınıfı. Aslında, <xref:System.Windows.Navigation.NavigationService> gibi istemci kodu adına bir gezinti isteği işleme yeteneği sağlar <xref:System.Windows.Documents.Hyperlink>. Ayrıca, <xref:System.Windows.Navigation.NavigationService> izleme ve gezinme isteği etkileyen üst düzey destek uygular.  
  
 Olduğunda bir <xref:System.Windows.Documents.Hyperlink> tıklandığında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çağrıları <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> bulmak ve indirmek için <xref:System.Windows.Controls.Page> belirtilen paket, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. İndirilen <xref:System.Windows.Controls.Page> , kök nesnesi indirilen örneği olan nesnelerin bir ağaca dönüştürülür <xref:System.Windows.Controls.Page>. Kök başvuru <xref:System.Windows.Controls.Page> nesne içinde depolandığı <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> özelliği. Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için çıkıldığında içeriği saklanır <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliği sırada <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> paketi depolar [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için çıkıldığında son sayfa için.  
  
> [!NOTE]
>  Mümkünse bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birden fazla etkin uygulamaya <xref:System.Windows.Navigation.NavigationService>. Daha fazla bilgi için [gezinti konakları](#Navigation_Hosts) bu konuda.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Programlı Gezinti Gezinti hizmeti  
 Hakkında bilmeniz gerekmez <xref:System.Windows.Navigation.NavigationService> Gezinti bildirimli olarak işaretleme kullanılarak uygulanmışsa <xref:System.Windows.Documents.Hyperlink>, çünkü <xref:System.Windows.Documents.Hyperlink> kullanan <xref:System.Windows.Navigation.NavigationService> sizin adınıza. Diğer bir deyişle ya da doğrudan veya dolaylı üst sürece bir <xref:System.Windows.Documents.Hyperlink> Gezinti ana bilgisayar (bkz [gezinti konakları](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> bulabilir ve işlemek için Gezinti konak Gezinti hizmeti mümkün olacaktır bir Gezinme isteği.  
  
 Ancak, bazı durumlarda kullanmanız gerekir <xref:System.Windows.Navigation.NavigationService> doğrudan, aşağıdakiler dahil:  
  
-   Örneği oluşturmak gerektiğinde bir <xref:System.Windows.Controls.Page> kullanarak varsayılan olmayan bir oluşturucu.  
  
-   Özellikleri ayarlamak gerektiğinde <xref:System.Windows.Controls.Page> önce bu sayfaya gidin.  
  
-   Zaman <xref:System.Windows.Controls.Page> için geçtiğiniz için yalnızca çalışma zamanında belirlenebileceği.  
  
 Bu durumda, program aracılığıyla gezinti çağırarak başlatmak için kod yazmanız gerekir. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi <xref:System.Windows.Navigation.NavigationService> nesne. Bir başvuru alma gerektiren bir <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService bir başvuru alma  
 Ele alınmaktadır nedeniyle [gezinti konakları](#Navigation_Hosts) bölümünde, bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama birden fazla olabilir <xref:System.Windows.Navigation.NavigationService>. Bu, kodunuzun bulmanın bir yolu gerektiği anlamına gelir. bir <xref:System.Windows.Navigation.NavigationService>, genellikle olduğu <xref:System.Windows.Navigation.NavigationService> geçerli çıkıldığında <xref:System.Windows.Controls.Page>. Bir başvuru almak bir <xref:System.Windows.Navigation.NavigationService> çağırarak `static`<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> yöntemi. Alınacak <xref:System.Windows.Navigation.NavigationService> belirli bir çıkıldığında <xref:System.Windows.Controls.Page>, başvuru geçirdiğiniz <xref:System.Windows.Controls.Page> bağımsız değişkeni olarak <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> yöntemi. Aşağıdaki kod nasıl alınacağı gösterilmiştir <xref:System.Windows.Navigation.NavigationService> geçerli <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Bulma için bir kısayol olarak <xref:System.Windows.Navigation.NavigationService> için bir <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> uygulayan <xref:System.Windows.Controls.Page.NavigationService%2A> özelliği. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> yalnızca bir başvuru almak kendi <xref:System.Windows.Navigation.NavigationService> olduğunda <xref:System.Windows.Controls.Page> başlatır <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Bir sayfa nesnesine programlı Gezinti  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Navigation.NavigationService> programlı olarak gitmek için bir <xref:System.Windows.Controls.Page>. Programlı gezinti, çünkü gereklidir <xref:System.Windows.Controls.Page> diğer bir deyişle geçtiğiniz için yalnızca oluşturulabilir tek, varsayılan olmayan bir oluşturucu kullanılarak. <xref:System.Windows.Controls.Page> Aşağıdaki işaretleme ve kod içinde varsayılan olmayan bir Oluşturucu ile gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> Varlıklardan için <xref:System.Windows.Controls.Page> aşağıdaki işaretleme ve kod içinde varsayılan olmayan bir Oluşturucu ile gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Zaman <xref:System.Windows.Documents.Hyperlink> bu <xref:System.Windows.Controls.Page> olan tıklattığında, gezinti tarafından örnekleme başlatılır <xref:System.Windows.Controls.Page> varsayılan olmayan oluşturucu kullanılarak ve çağırma gitmek için <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> nesnesine bir başvuru kabul eder, <xref:System.Windows.Navigation.NavigationService> yerine bir paket için gider [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Pack URI'si ile programlı Gezinti  
 Bir paketi oluşturmak ihtiyacınız varsa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programlı olarak (zaman yalnızca belirleyebilirsiniz paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında, örneğin), kullanabileceğiniz <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Geçerli sayfayı yenileyin  
 A <xref:System.Windows.Controls.Page> aynı paketi varsa indirilmez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi olarak [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] depolanan <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliği. Zorlamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçerli sayfayı yeniden yüklemek için çağırabilirsiniz <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Gezinti ömrü  
 Gördüğünüz gibi gezinti, başlatmak için birçok yolu vardır. Gezinti başlatılır ve gezinme işlemi devam ederken, izleyebilir ve tarafından uygulanan aşağıdaki olaylar kullanarak gezinti etkilemek <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>biçimindeki telefon numarasıdır. Yeni bir gezinti istendiğinde gerçekleşir. Gezinti iptal etmek için kullanılabilir.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>biçimindeki telefon numarasıdır. Gezinti durumu hakkında bilgi sağlamak için düzenli olarak indirme sırasında gerçekleşir.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>biçimindeki telefon numarasıdır. Sayfa bulunur ve indirilen gerçekleşir.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>biçimindeki telefon numarasıdır. Gezinti durdurulduğunda oluşur (çağırarak <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), veya ne zaman yeni bir gezinti istenen geçerli bir gezinti devam ederken.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>biçimindeki telefon numarasıdır. İstenen içeriğe gidilirken bir hata harekete geçirildiğinde gerçekleşir.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>biçimindeki telefon numarasıdır. İçin çıkıldığında içeriği yüklenir ve ayrıştırıldığında ve işleme başladı gerçekleşir.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>biçimindeki telefon numarasıdır. Hangi olur bir içerik parçasına Gezinti başladığında gerçekleşir:  
  
    -   Hemen geçerli içerikte istenen parçası ise.  
  
    -   Sonra istenen parça içinde farklı içerik ise kaynak içerik yüklendi.  
  
 Gezinme olayları, aşağıdaki şekilde gösterilen sırayla oluşturulur.  
  
 ![Sayfa gezintisi akış çizelgesi](./media/navigation-overview/order-of-navigation-events.png "sayfa gezintisi olay akış çizelgesi")  
  
 Genel olarak, bir <xref:System.Windows.Controls.Page> bu olaylar hakkında endişe değil. Bir uygulama ile ilgilidir ve bu nedenle, bu olaylar ayrıca tarafından oluşturulan daha büyük olasılıkla <xref:System.Windows.Application> sınıfı:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Her zaman <xref:System.Windows.Navigation.NavigationService> bir olay başlatır <xref:System.Windows.Application> sınıfı, karşılık gelen bir olay başlatır. <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> kendi ilgili kapsam içinde gezinme algılamak için aynı olayları sağlar.  
  
 Bazı durumlarda, bir <xref:System.Windows.Controls.Page> bu olayları ilginizi çekebilir. Örneğin, bir <xref:System.Windows.Controls.Page> işleyebilir <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> Gezinti uzağa kendisini iptal verilip verilmeyeceğini belirlemek için olay. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Bir gezinti olayından içeren bir işleyici kaydedin, bir <xref:System.Windows.Controls.Page>, önceki örnekte olduğu gibi olay işleyicisi de kaydını silmeniz gerekir. Aksi takdirde, nasıl gerçekleştireceğini yan etkileri olabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Gezinti hatırlar <xref:System.Windows.Controls.Page> günlük kullanarak gezinme.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Günlük ile gezinti hatırlama  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] unutmayın çıktığınız sayfalar için iki yığınları kullanır: geri yığını ve iletme yığını. Geçerli gittiğinizde <xref:System.Windows.Controls.Page> yeni bir <xref:System.Windows.Controls.Page> veya mevcut bir iletme <xref:System.Windows.Controls.Page>, geçerli <xref:System.Windows.Controls.Page> eklenir *geri yığın*. Geçerli gittiğinizde <xref:System.Windows.Controls.Page> geri için önceki <xref:System.Windows.Controls.Page>, geçerli <xref:System.Windows.Controls.Page> eklenir *iletme yığın*. Geri yığın, iletme yığını ve bunları yönetmek için gereken işlevleri topluca için günlük olarak adlandırılır. Her öğe, geri yığını ve iletme yığını örneğidir <xref:System.Windows.Navigation.JournalEntry> sınıfı ve şeklinde adlandırılan bir *günlük girdisi*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer günlüğünden gezinme  
 Kavramsal olarak, aynı günlük çalışır şekilde **geri** ve **İleri** içinde düğmeleri [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] yapın. Bunlar aşağıdaki şekilde gösterilir.  
  
 ![Geri ve İleri düğmelerini](./media/navigation-overview/back-and-forward-navigation.png "geri ve İleri düğmelerini gidin.")  
  
 İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] tarafından barındırılan [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] günlük Gezinti çubuğuna tümleşir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Bu sayfalarında gezinmek kullanıcılara bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kullanarak **geri**, **İleri**, ve **son sayfalar** içinde düğmeleri [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Günlük ile tümleşik olmayan [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] olduğu için aynı şekilde [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] veya Internet Explorer 8. Bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yedek Gezinti işler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], liste kutusundan bir kullanıcı gezinirken ve geri bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], yalnızca günlük girişlerini Canlı tutulan değil sayfaları için günlükte korunur. Sayfaları Canlı kalmasını hakkında daha fazla bilgi için bkz. [sayfa ömrü ve günlük](#PageLifetime) bu konuda.  
  
 Varsayılan olarak, her metin <xref:System.Windows.Controls.Page> , görünür **son sayfalar** listesi [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] olduğu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için <xref:System.Windows.Controls.Page>. Çoğu durumda, bu özellikle kullanıcıya anlamlı değildir. Neyse ki, aşağıdaki seçeneklerden birini kullanarak metin değiştirebilirsiniz:  
  
1. Ekli `JournalEntry.Name` öznitelik değeri.  
  
2. `Page.Title` Öznitelik değeri.  
  
3. `Page.WindowTitle` Öznitelik değeri ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] geçerli <xref:System.Windows.Controls.Page>.  
  
4. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Geçerli <xref:System.Windows.Controls.Page>. (Varsayılan)  
  
 Seçenekler listelendiği sırayı metni bulmak için öncelik sırası ile eşleşir. Örneğin, varsa `JournalEntry.Name` , diğer değerleri yok sayılır ayarlanmış.  
  
 Aşağıdaki örnekte `Page.Title` bir günlük girişi için görüntülenen metin değiştirmek için özniteliği.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>WPF kullanarak günlük gezinme  
 Bir kullanıcı kullanarak günlük gidebilirsiniz rağmen **geri**, **İleri**, ve **son sayfalar** içinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], her ikisini de kullanarak günlük da gidebilirsiniz tarafından sağlanan bildirim temelli ve programlı mekanizmaları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bunu yapmak için bir neden olan özel gezinti sağlamak [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sayfalarınızda.  
  
 Bildirimli olarak tarafından kullanıma sunulan Gezinti komutlarını kullanarak günlük gezinti desteği ekleyebilirsiniz <xref:System.Windows.Input.NavigationCommands>. Aşağıdaki örnek nasıl kullanılacağını gösterir `BrowseBack` Gezinti komutu.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Aşağıdaki üyeleri biri kullanılarak programlı olarak günlük gidebilirsiniz <xref:System.Windows.Navigation.NavigationService> sınıfı:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Günlük de anlatıldığı gibi program aracılığıyla yönetilebilir [Gezinme geçmişi ile istinat içerik durumunu](#RetainingContentStateWithNavigationHistory) bu konuda.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Sayfa ömrü ve günlük  
 Göz önünde bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Zengin içeriği içeren birkaç sayfalarıyla grafik, animasyon ve medya gibi. Bunlar gibi sayfaları için bellek Ayak izi, video ve ses medya özellikle kullanılması durumunda oldukça büyük olabilir. Günlük "taşınabilecek, bu tür olan sayfaları hatırlar koşuluyla," bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hızlı bir şekilde büyük ve belirgin bir bellek miktarıyla tüketebilir.  
  
 Bu nedenle, günlük varsayılan davranışını depolamaktır <xref:System.Windows.Controls.Page> meta veri başvurusu yerine, her günlük girdisi bir <xref:System.Windows.Controls.Page> nesne. Bir günlük girişi için gittiğinizde, kendi <xref:System.Windows.Controls.Page> belirtilen yeni bir örneğini oluşturmak için kullanılan meta veri <xref:System.Windows.Controls.Page>. Sonuç olarak, her <xref:System.Windows.Controls.Page> çıkıldığında aşağıdaki şekilde gösterilen ömre sahiptir.  
  
 ![Sayfa ömrü](./media/navigation-overview/navigated-page-lifetime.png "bu ne zaman bir sayfaya gitme yaşam süresini gösterir.")  
  
 Varsayılan olarak günlüğe kaydetme davranışını kullanarak bellek tüketimi kaydedebilirsiniz ancak sayfa başına işleme performansı azalabilir; reinstantiating bir <xref:System.Windows.Controls.Page> saati-yoğun, özellikle çok fazla içeriğe sahipse kullanılabilir. Silmemeniz gerekiyorsa bir <xref:System.Windows.Controls.Page> örneği günlük, bunu yapmak için iki teknik üzerinde çizebilirsiniz. İlk olarak, program aracılığıyla gidebilirsiniz bir <xref:System.Windows.Controls.Page> çağırarak <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi.  
  
 İkinci olarak, belirtebilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] örneğini korumak bir <xref:System.Windows.Controls.Page> ayarlayarak günlüğü <xref:System.Windows.Controls.Page.KeepAlive%2A> özelliğini `true` (varsayılan değer `false`). Aşağıdaki örnekte gösterildiği gibi ayarlayabilirsiniz <xref:System.Windows.Controls.Page.KeepAlive%2A> biçimlendirmede bildirimli olarak.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Yaşam süresi bir <xref:System.Windows.Controls.Page> diğer bir deyişle Canlı kalmasını olmayan bir farenizin farklıdır. İlk kez bir <xref:System.Windows.Controls.Page> tutulur, Canlı için görüntülendiği, tıpkı örneği bir <xref:System.Windows.Controls.Page> , değil tutulur tutma. Ancak, çünkü bir örneğini <xref:System.Windows.Controls.Page> korunur günlükte kaldığı sürece günlük, hiçbir zaman yeniden için örneği. Sonuç olarak, varsa bir <xref:System.Windows.Controls.Page> her çağrılması gereken başlatma mantığı varsa <xref:System.Windows.Controls.Page> görüntülendiği için bunu oluşturucudan işleyicisi içine taşımanız <xref:System.Windows.FrameworkElement.Loaded> olay. Aşağıdaki şekilde gösterildiği gibi <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.FrameworkElement.Unloaded> olayları her oluştuğunda bir <xref:System.Windows.Controls.Page> ve ondan, sırasıyla gitme.  
  
 ![Yüklenmiş ve yüklenmemiş olayları oluştuğunda zaman](./media/navigation-overview/loaded-and-unloaded-events.png "yüklenen ve yüklü olmayan olaylar oluştuğunda ve ondan bir sayfaya gitme olduğunda.")  
  
 Olduğunda bir <xref:System.Windows.Controls.Page> olduğu Canlı tutulur değil, aşağıdakilerden birini yapmanız gerektiğini değil:  
  
-   Bir başvuru veya herhangi bir bölümü Store.  
  
-   Olay işleyicileri tarafından uygulanmadı olaylarını kaydedin.  
  
 Bunlardan birini yapmak zorla başvuruları oluşturacaktır <xref:System.Windows.Controls.Page> günlükten bile kaldırıldıktan sonra bellekte saklanması gerekir.  
  
 Genel olarak, varsayılan tercih etmelisiniz <xref:System.Windows.Controls.Page> değil tutma davranışı bir <xref:System.Windows.Controls.Page> tutma. Ancak, sonraki bölümde açıklanan durum etkileri vardır.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Gezinme geçmişi ile içerik durumu tutma  
 Varsa bir <xref:System.Windows.Controls.Page> etkin tutulan bağlantıyı destekliyorsa, tutulamaz ve verileri bir kullanıcı UZAĞINIZDA giderse ve geri gerçekleşir kullanıcıdan veri toplamak denetimleri sahip <xref:System.Windows.Controls.Page>? Bir kullanıcı deneyimi açısından bakıldığında, kullanıcının daha önce girilen veri görmeyi beklemelisiniz. Ne yazık ki, çünkü yeni bir örneğini <xref:System.Windows.Controls.Page> her Gezinti toplanan verileri reinstantiated ve veriler kaybolur denetimleri oluşturulur.  
  
 Neyse ki, günlük veri arasında hatırlamak için destek sağlar <xref:System.Windows.Controls.Page> gezintiler denetim verileri dahil olmak üzere,. Özellikle, her günlük girdisi <xref:System.Windows.Controls.Page> ilişkili geçici bir kapsayıcı olarak davranır <xref:System.Windows.Controls.Page> durumu. Aşağıdaki adımlar, bu destek nasıl kullanıldığını özetlemektedir olduğunda bir <xref:System.Windows.Controls.Page> çıktığınız:  
  
1. Geçerli bir giriş <xref:System.Windows.Controls.Page> günlüğe eklenir.  
  
2. Durumunu <xref:System.Windows.Controls.Page> geri yığına eklenen bu sayfada, günlük girdisi ile birlikte saklanır.  
  
3. Yeni <xref:System.Windows.Controls.Page> için gitme.  
  
 Olduğunda sayfa <xref:System.Windows.Controls.Page> olduğu yerde günlüğünü kullanarak geçtiğiniz için aşağıdaki adımları uygulayın:  
  
1. <xref:System.Windows.Controls.Page> (Üst günlük girdisi geri yığın üzerinde) oluşturulur.  
  
2. <xref:System.Windows.Controls.Page> Günlük girdisi ile depolanan durumu yenilendiğini <xref:System.Windows.Controls.Page>.  
  
3. <xref:System.Windows.Controls.Page> Geri gitme.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bu destek aşağıdaki denetimleri üzerinde kullanıldığında otomatik olarak kullanan bir <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 Varsa bir <xref:System.Windows.Controls.Page> kullanır, bu denetimleri, içine girdiğiniz veriler arasında hatırlanır <xref:System.Windows.Controls.Page> tarafından gösterildiği şekilde gezintiler **sık kullanılan renk** <xref:System.Windows.Controls.ListBox> aşağıdaki şekilde.  
  
 ![Sayfa durumu unutmayın denetimlerle](./media/navigation-overview/data-remembered-across-page-navigations.png "girilen veriler arasında sayfa gezintiler anımsanacak.")  
  
 Olduğunda bir <xref:System.Windows.Controls.Page> denetimleri dışındaki yukarıdaki listede sahip veya bu duruma hatırlamak günlük neden için kod yazmanıza gerek durumu özel nesneleri depolandığında <xref:System.Windows.Controls.Page> gezintiler.  
  
 Küçük parçaları arasında durumu unutmayın gerekip gerekmediğini <xref:System.Windows.Controls.Page> gezintiler, bağımlılık özellikleri kullanabilirsiniz (bkz <xref:System.Windows.DependencyProperty>) ile yapılandırılmış <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> meta verileri bayrağı.  
  
 Durumu, sizin <xref:System.Windows.Controls.Page> gezintiler arasında unutmamak gerekir birden çok veri parçalarını oluşur, bu daha az kod Kullanımı Yoğun durumunuzu tek bir sınıf içinde kapsülleyebilir ve uygulamak için bulabilirsiniz <xref:System.Windows.Navigation.IProvideCustomContentState> arabirimi.  
  
 Tek bir çeşitli durumları arasında gezinmek ihtiyacınız varsa <xref:System.Windows.Controls.Page>, gelen gezinme olmadan <xref:System.Windows.Controls.Page> kendisini kullanabileceğiniz <xref:System.Windows.Navigation.IProvideCustomContentState> ve <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Tanımlama bilgileri  
 Başka bir şekilde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama veri depolamak oluşturulan tanımlama bilgileriyle güncelleştirilir ve kullanarak silinmiş <xref:System.Windows.Application.SetCookie%2A> ve <xref:System.Windows.Application.GetCookie%2A> yöntemleri. Oluşturabileceğiniz tanımlama bilgilerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] olan Web uygulamalarının diğer türleri aynı tanımlama bilgileri kullan; tanımlama bilgileridir rastgele parçalarını sırasında veya uygulama oturumları arasında uygulama istemci makinede tarafından depolanan verileri. Tanımlama bilgisi verisi, genellikle şu biçimde bir ad/değer çifti biçimi alır.  
  
 *Adı* `=` *değeri*  
  
 Ne zaman veri geçirildiğinde <xref:System.Windows.Application.SetCookie%2A>, birlikte <xref:System.Uri> tanımlama bilgisi ayarlanmalıdır konumu, bellek içi bir tanımlama bilgisi oluşturulur ve yalnızca geçerli uygulama oturumu süresi için kullanılabilir. Bu tür bir tanımlama bilgisi verilir bir *oturum tanımlama bilgisinin*.  
  
 Bir tanımlama bilgisi uygulama oturumları arasında depolamak için aşağıdaki biçimi kullanarak tanımlama bilgisine, sona erme tarihi eklenmesi gerekir.  
  
 *ADI* `=` *DEĞERİ* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Bir tanımlama bilgisi sona erme tarihi geçerli depolanan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] tanımlama bilgisi süresi dolana kadar yüklemenin Temporary Internet Files klasörü. Böyle bir tanımlama bilgisi olarak bilinen bir *kalıcı bir tanımlama bilgisi* çünkü bu uygulama oturumu arasında kalıcıdır.  
  
 Hem oturum hem de kalıcı tanımlama bilgileri çağırarak alma <xref:System.Windows.Application.GetCookie%2A> yöntemini <xref:System.Uri> nerede tanımlama bilgisi ayarlandığı ile konumun <xref:System.Windows.Application.SetCookie%2A> yöntemi.  
  
 Tanımlama bilgileri desteklenen yollarından bazıları verilmiştir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulamalar ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hem de oluşturabilir ve tanımlama bilgileri yönetebilirsiniz.  
  
-   Tarafından oluşturulan tanımlama bilgilerini bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tarayıcıdan erişilebilir.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] aynı etki alanından oluşturabilir ve tanımlama bilgilerini paylaşma.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] aynı etki alanında sayfalarından oluşturabilir ve tanımlama bilgileri paylaşın.  
  
-   Tanımlama bilgilerini gönderilen zaman [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları, Web istekleri olun.  
  
-   Hem üst düzey [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] barındırılan IFRAMES tanımlama bilgilerine erişebilir.  
  
-   Tanımlama bilgisi desteği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tüm desteklenen tarayıcılar için aynıdır.  
  
-   İçinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], tanımlama bilgilerini ilgilidir P3P ilkesini dikkate alınır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], özellikle birinci taraf ve üçüncü taraf göre [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Yapılandırılmış gezintiye  
 Bir veri iletmek gerekiyorsa <xref:System.Windows.Controls.Page> diğerine veri bağımsız değişken olarak bir varsayılan olmayan oluşturucusuna geçirebilirsiniz <xref:System.Windows.Controls.Page>. Bu yöntemi kullanırsanız, tutmalısınız Not <xref:System.Windows.Controls.Page> için gidin, sonraki açışınızda, canlı; <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yeniden başlattığına <xref:System.Windows.Controls.Page> varsayılan oluşturucuyu kullanarak.  
  
 Alternatif olarak, <xref:System.Windows.Controls.Page> geçilmesi gereken veri kümesi özellikleri uygulayabilir. Şeyler haline zor, ancak, bir <xref:System.Windows.Controls.Page> geçirilecek veriler tekrar <xref:System.Windows.Controls.Page> , geçtiğiniz için. Gezinti yerel olarak mekanizmaları, güvence altına almak için desteklemediğini sorun bir <xref:System.Windows.Controls.Page> sayfadan çıkıldığında sonra penceresine döndürülürsünüz. Esas olarak, gezinti çağrı/return'e semantiği desteklemiyor. Bu sorunu çözmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar <xref:System.Windows.Navigation.PageFunction%601> emin olmak için kullanabileceğiniz sınıfı bir <xref:System.Windows.Controls.Page> öngörülebilir ve yapılandırılmış biçimde döndürülür. Daha fazla bilgi için [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow sınıfı  
 Bu noktada, gezinebilir içeriğe sahip uygulamalar oluşturmak üzere kullanmak en olası gezinti Hizmetleri genişliğine gördünüz. Bu hizmetler bağlamında ele alınan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], sınırlı değildir ancak [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Modern işletim sistemi ve Windows uygulamaları modern kullanıcıların tarayıcı stili gezintiyi tek başına uygulamalarda eklemesine tarayıcı deneyimini yararlanın. Ortak örnekleri şunlardır:  
  
-   **Word eş anlamlılar**: Word Seçenekleri gidin.  
  
-   **Dosya Gezgini**: Dosya ve klasörleri gidin.  
  
-   **Sihirbazlar**: Karmaşık bir görev arasında gittiğinizde, birden çok sayfalarıyla bölmek. Windows özellikleri ekleme ve kaldırma işleme Windows Bileşenleri Sihirbazı'nı bir örnektir.  
  
 Tarayıcı stili gezintiyi tek başına uygulamalarınıza eklemek için kullanabileceğiniz <xref:System.Windows.Navigation.NavigationWindow> sınıfı. <xref:System.Windows.Navigation.NavigationWindow> öğesinden türetilen <xref:System.Windows.Window> ve onu aynı desteğiyle Gezinti genişleten [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sağlayın. Kullanabileceğiniz <xref:System.Windows.Navigation.NavigationWindow> bir iletişim kutusu gibi ikincil bir pencere olarak veya tek başına uygulamanızın her iki ana penceresi.  
  
 Uygulamak için bir <xref:System.Windows.Navigation.NavigationWindow>, çoğu düzey sınıflar olarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, vb.), biçimlendirme ve arka plan kod kullanın. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Bu kod oluşturur bir <xref:System.Windows.Navigation.NavigationWindow> , otomatik olarak gider bir <xref:System.Windows.Controls.Page> (HomePage.xaml) olduğunda <xref:System.Windows.Navigation.NavigationWindow> açılır. Varsa <xref:System.Windows.Navigation.NavigationWindow> ana uygulama penceresi kullanabileceğiniz `StartupUri` başlatmak için özniteliği. Bu, aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Aşağıdaki şekil gösterir <xref:System.Windows.Navigation.NavigationWindow> tek başına uygulama ana penceresi olarak.  
  
 ![Ana pencere](./media/navigation-overview/navigation-window-as-main-window.png "ana pencereyi olarak Gezinti penceresi")  
  
 Şekilden gördüğünüz gibi <xref:System.Windows.Navigation.NavigationWindow> ayarlanmış değildi olsa bile bir başlık sahip <xref:System.Windows.Navigation.NavigationWindow> önceki örnekten uygulama kodu. Bunun yerine, başlığı kullanılarak ayarlanabilir <xref:System.Windows.Controls.Page.WindowTitle%2A> aşağıdaki kodda gösterilen özelliği.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Ayarı <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A> özellikleri de etkiler <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Genellikle, kendi uygulamanız <xref:System.Windows.Navigation.NavigationWindow> davranışını veya görünümünü özelleştirmek gerektiğinde. Hiçbiri yoksa bir kısayolu kullanabilirsiniz. Paketi belirtirseniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , bir <xref:System.Windows.Controls.Page> olarak <xref:System.Windows.Application.StartupUri%2A> tek başına uygulamadaki <xref:System.Windows.Application> otomatik olarak oluşturur bir <xref:System.Windows.Navigation.NavigationWindow> konağa <xref:System.Windows.Controls.Page>. Aşağıdaki biçimlendirme, bunu etkinleştirmek gösterilmektedir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Bir ikincil uygulama penceresi gibi bir iletişim kutusu olarak isteyip istemediğinizi bir <xref:System.Windows.Navigation.NavigationWindow>, açmak için aşağıdaki örnek kodu kullanabilirsiniz.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Aşağıdaki şekilde sonucu gösterir.  
  
 ![Bir iletişim kutusu](./media/navigation-overview/navigation-window-as-dialog-box.png "Gezinti penceresinde bir iletişim kutusu")  
  
 Gördüğünüz gibi <xref:System.Windows.Navigation.NavigationWindow> görüntüler [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-style **geri** ve **İleri** günlük gitmek kullanıcıların düğmeleri. Bu düğmeler, aşağıdaki resimde gösterildiği gibi aynı kullanıcı deneyimi sağlar.  
  
 ![Geri ve İleri düğmelerini NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "geri ve İleri düğmelerini Gezinti penceresinde")  
  
 Sayfalarınızı kendi günlük gezinti desteği ve UI sağlarsanız, gizleyebilirsiniz **geri** ve **İleri** düğme tarafından görüntülenen <xref:System.Windows.Navigation.NavigationWindow> değerini ayarlayarak <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> özelliği`false`.  
  
 Alternatif olarak, özelleştirme desteği kullanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] değiştirilecek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , <xref:System.Windows.Navigation.NavigationWindow> kendisi.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Çerçeve sınıfı  
 Her iki tarayıcı ve <xref:System.Windows.Navigation.NavigationWindow> gezilebilir içeriği barındırmak dizisidir. Bazı durumlarda, uygulamalar, pencerenin tamamını tarafından barındırılması gerekmez içeriğe sahip. Bunun yerine, bu içeriğin diğer içerik içinde barındırılması. Kullanarak diğer içeriğinize gezilebilir içerik ekleyebilirsiniz <xref:System.Windows.Controls.Frame> sınıfı. <xref:System.Windows.Controls.Frame> olarak aynı destekler <xref:System.Windows.Navigation.NavigationWindow> ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.Windows.Controls.Frame> için bir <xref:System.Windows.Controls.Page> kullanarak bildirimli olarak `Frame` öğesi.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Bu işaretleme ayarlar `Source` özniteliği `Frame` öğesi bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Frame> başlangıçta gitmek. Aşağıdaki şekil gösterir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ile bir <xref:System.Windows.Controls.Page> olan bir <xref:System.Windows.Controls.Frame> çeşitli sayfalar arasında çıkıldığında.  
  
 ![Birden çok sayfa arasında gezinen bir çerçeve](./media/navigation-overview/frame-navigation-between-multiple-pages.png "bu birden çok sayfalar arasında gezintiyi gösterir.")  
  
 Yalnızca kullanmak zorunda değilsiniz <xref:System.Windows.Controls.Frame> içeriğini içinde bir <xref:System.Windows.Controls.Page>. Ayrıca barındırmak yaygın bir <xref:System.Windows.Controls.Frame> içeriğini içinde bir <xref:System.Windows.Window>.  
  
 Varsayılan olarak, <xref:System.Windows.Controls.Frame> yalnızca başka bir günlük olmaması durumunda kendi günlüğünü kullanır. Varsa bir <xref:System.Windows.Controls.Frame> içinde barındırılan içerik parçası olan bir <xref:System.Windows.Navigation.NavigationWindow> veya bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> ait günlük kullanan <xref:System.Windows.Navigation.NavigationWindow> veya [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Bazı durumlarda, yine de bir <xref:System.Windows.Controls.Frame> kendi günlüğü için sorumlu gerekebilir. Bunu yapmak için bir neden olan tarafından barındırılan sayfaları içinde günlük gezinme izin vermek için bir <xref:System.Windows.Controls.Frame>. Bu, aşağıdaki şekilde gösterilmiştir.  
  
 ![Çerçeve ve sayfa diyagramı](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "bu sayfa bir çerçeve tarafından barındırılan içinde günlük gezinme gösterir.")  
  
 Bu durumda, yapılandırabileceğiniz <xref:System.Windows.Controls.Frame> kendi günlük ayarlayarak kullanılacak <xref:System.Windows.Controls.Frame.JournalOwnership%2A> özelliği <xref:System.Windows.Controls.Frame> için <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Bu, aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 Aşağıdaki şekil içinde gezinme etkisini gösterir bir <xref:System.Windows.Controls.Frame> , kendi günlüğünü kullanır.  
  
 ![Kendi günlüğünü kullanan bir çerçeve](./media/navigation-overview/frame-uses-its-own-journal.png "bu kendi günlüğünü kullanan bir çerçeve içinde gezinme etkisini gösterir.")  
  
 Günlük girişlerini Gezinti tarafından gösterilen bildirim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde <xref:System.Windows.Controls.Frame>, yerine göre [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Varsa bir <xref:System.Windows.Controls.Frame> barındırılan içerik parçası olan bir <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> kendi günlüğünü kullanır ve sonuç olarak, kendi gezinme görüntüler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Kullanıcı deneyiminizi gerektiriyorsa bir <xref:System.Windows.Controls.Frame> Gezinti göstermeden kendi günlük sağlamak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], gezinti gizleyebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ayarlayarak <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> için <xref:System.Windows.Visibility.Hidden>. Bu, aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Gezinti konakları  
 <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> gezinti konakları olarak bilinen sınıflardır. A *Gezinti konak* gidin ve içeriği görüntülemek, bir sınıftır. Bunu yapmak için her Gezinti konağın kendi kullanan <xref:System.Windows.Navigation.NavigationService> ve günlük. Bir gezinti konak temel oluşumu, aşağıdaki şekilde gösterilir.  
  
 ![Gezgin diyagramları](./media/navigation-overview/navigation-host-construction.png "Gezinti konak temel yapımı")  
  
 Aslında, böylece <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.Frame> aynı sağlamak için gezinti desteği bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tarayıcıda barındırıldığında sağlar.  
  
 Kullanarak yanı sıra <xref:System.Windows.Navigation.NavigationService> ve bir günlük gezinti konakları aynı üyelere uygulamak, <xref:System.Windows.Navigation.NavigationService> uygular. Bu, aşağıdaki şekilde gösterilmiştir.  
  
 ![Bir günlük bir çerçeve ve NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Gezinti penceresinde ve çerçeve")  
  
 Bu, program Gezinti destek doğrudan bunlara karşı sağlar. Özel bir gezinti sağlamak gerekirse bu düşünebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için bir <xref:System.Windows.Controls.Frame> barındırılan bir <xref:System.Windows.Window>. Ayrıca, her iki türü de dahil olmak üzere, ek gezinti ilgili, üyeleri uygulamak `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) ve `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), günlük girişlerini geri listeleme izin yığın ve yığın, sırasıyla iletebilir.  
  
 Daha önce bahsedildiği gibi birden fazla günlük bir uygulama içinde bulunabilir. Bunun ortaya çıkabileceği aşağıdaki şekilde bir örnek sağlar.  
  
 ![Bir uygulama içinde birden çok günlük](./media/navigation-overview/multiple-journals-in-one-application.png "bu bir uygulamada birden fazla günlük örneğidir.")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML sayfaları dışında içerik gezinme  
 Bu konu, boyunca <xref:System.Windows.Controls.Page> ve paketi [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] çeşitli Gezinti özelliklerini göstermek için kullanılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ancak, bir <xref:System.Windows.Controls.Page> diğer bir deyişle tek tür için çıkıldığında İçerik Paketi ve bir uygulamaya derlenmiş değil [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içeriğini belirlemek için tek yolu değil.  
  
 Bu bölümde gösterildiği gibi ayrıca için gevşek gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] dosyaları ve nesneler.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Gevşek XAML dosyaları için gezinme  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki özelliklere sahip bir dosya dosyasıdır:  
  
-   Yalnızca içeren [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (diğer bir deyişle, hiçbir kod).  
  
-   Uygun ad alanı bildirimi sahiptir.  
  
-   .Xaml dosya adı uzantısına sahiptir.  
  
 Örneğin, gevşek depolanan aşağıdaki içeriğe göz önünde bulundurun [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Person.xaml dosyası.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Dosyayı çift tıkladığınızda tarayıcı açılır ve gider ve içeriğini görüntüler. Bu aşağıdaki şekilde gösterilmektedir.  
  
 ![İçeriği görüntüleme Person.XAML dosyasındaki](./media/navigation-overview/contents-of-person-xaml-file.png "Person.XAML dosyanın içeriğini gösterir.")  
  
 Gevşek görüntüleyebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki dosyasından:  
  
-   Yerel makine, intranet veya Internet üzerinde bir Web sitesi.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] dosya paylaşımı.  
  
-   Yerel disk.  
  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya tarayıcı Sık Kullanılanlara eklenebilir veya tarayıcının giriş sayfası.  
  
> [!NOTE]
>  Yayımlama ve gevşek başlatma hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları bkz [bir WPF uygulamasını dağıtma](deploying-a-wpf-application-wpf.md).  
  
 Gevşek ilgili tek sınırlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olduğundan, yalnızca kısmi güvende çalıştırmak güvenli içerik barındırabilirsiniz. Örneğin, `Window` gevşek kök öğe olamaz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Daha fazla bilgi için [WPF kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>HTML dosyaları çerçevesi kullanarak gezinme  
 Bekleyebileceğiniz gibi ayrıca gidebilirsiniz [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Yalnızca sağlamanız gereken bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , http düzeni kullanır. Örneğin, aşağıdaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gösteren bir <xref:System.Windows.Controls.Frame> varlıklardan için bir [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] sayfası.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Gezinme [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] özel izinler gerektirir. Örneğin, gelen gidilemiyor bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Internet bölgesi kısmi güven güvenliği korumalı alanında çalışıyor. Daha fazla bilgi için [WPF kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser denetimi kullanarak, HTML dosyaları gezinme  
 <xref:System.Windows.Controls.WebBrowser> Denetim destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] belge barındırma, gezinti ve komut dosyası ve yönetilen kod birlikte çalışabilirliği. Ayrıntılı bilgi için ilgili <xref:System.Windows.Controls.WebBrowser> denetlemek için bkz: <xref:System.Windows.Controls.WebBrowser>.  
  
 Gibi <xref:System.Windows.Controls.Frame>, gezinme için [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kullanarak <xref:System.Windows.Controls.WebBrowser> özel izinler gerektirir. Örneğin, bir kısmi güven uygulamasından yalnızca gezinebileceğiniz [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitede bulunan. Daha fazla bilgi için [WPF kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Özel nesneler için gezinme  
 Özel nesneler olarak depolanan veriler varsa, bu verileri görüntülemek için bir yol oluşturmak için olan bir <xref:System.Windows.Controls.Page> bu nesnelerle ilişkili içeriğe sahip (bkz [Data Binding Overview](../data/data-binding-overview.md)). Yalnızca nesneleri görüntülemek için bir sayfanın tamamını oluşturma ek yükü gerekmiyorsa, kendilerine doğrudan yerine gidebilirsiniz.  
  
 Göz önünde bulundurun `Person` aşağıdaki kodda uygulanır sınıfı.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Gitmek için çağrı <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Aşağıdaki şekilde sonucu gösterir.  
  
 ![Bir sınıfa giden bir sayfa](./media/navigation-overview/page-navigates-to-an-object.png "nesneye ızgaranın sayfasının bir örnek.")  
  
 Bu şekilden faydalı bir şey görüntülendiğini görebilirsiniz. Aslında, görüntülenen değer dönüş değeri `ToString` yöntemi **kişi** nesne; varsayılan olarak, bu yalnızca, değer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesneyi göstermek için kullanabilirsiniz. Geçersiz kılma `ToString` devam eder ancak daha anlamlı bilgiler döndürmek için yöntemi yalnızca bir dize değeri olmalıdır. Sunu yeteneklerini yararlanır kullanabileceğiniz bir teknik [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri şablonu kullanmaktır. Veri şablonu uygulayabilirsiniz, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belli bir türdeki bir nesne ile ilişkilendirebilirsiniz. Aşağıdaki kod, bir veri şablonu göstermektedir `Person` nesne.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Burada, veri şablonu ile ilişkili `Person` kullanarak türü `x:Type` işaretleme uzantısı'nda `DataType` özniteliği. Veri şablonu ardından bağlar `TextBlock` öğeleri (bkz <xref:System.Windows.Controls.TextBlock>) özelliklerine `Person` sınıfı. Güncelleştirilmiş görünümü, aşağıdaki şekilde gösterilmiştir `Person` nesne.  
  
 ![Veri şablonu bir sınıfa gezinme](./media/navigation-overview/navigating-to-a-class.png "veri şablonu bir sınıfa gezinme.")  
  
 Bu teknik bir avantajı, tutarlılık, nesnelerinizi tutarlı bir şekilde herhangi bir uygulamada görüntülemek için veri şablonunu yeniden erişebildiklerinden elde edin.  
  
 Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Gezinti desteği sağlayan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için Internet ve onu arasında çıkıldığında için üçüncü taraf içeriği barındırmak için uygulamalar sağlar. Hem uygulamalar hem de kullanıcılar zararlı bir davranış, korunacak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çeşitli içinde açıklanan güvenlik özellikleri sağlar [güvenlik](../security-wpf.md) ve [WPF kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Uygulama Yönetimine Genel Bakış](application-management-overview.md)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
- [Gezinti Topolojilerine Genel Bakış](navigation-topologies-overview.md)
- [Nasıl Yapılır Konuları](navigation-how-to-topics.md)
- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
