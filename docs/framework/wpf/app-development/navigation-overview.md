---
title: Gezintiye Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 69
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c84c5742fcbb0d1554bd6fc379fc44f3b9cb055
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="navigation-overview"></a>Gezintiye Genel Bakış
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] iki tür uygulamalarda kullanılabilir tarayıcısı stilinde Gezinti destekler: tek başına uygulamaları ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Gezinme, paket içeriği için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar <xref:System.Windows.Controls.Page> sınıfı. Birinden gidebilirsiniz <xref:System.Windows.Controls.Page> diğerine bildirimli olarak, kullanarak bir <xref:System.Windows.Documents.Hyperlink>, veya kullanarak programlı olarak <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Günlük sayfadan çıkıldığında sayfaları unutmayın ve bunları geri gitmek için kullanır.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, ve günlük form tarafından sunulan gezinti desteği çekirdek [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu genel bakışta gezinme gevşek içeren Gelişmiş gezinti desteği kapsayan önce bu özellikleri ayrıntılı araştırır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyaları ve nesneleri.  
  
> [!NOTE]
>  Bu konuda, "tarayıcı" terimi barındırabilen tarayıcılar başvuruyor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şu anda içeren uygulamalar [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ve Firefox. Belirli durumlarda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellikler, yalnızca belirli bir tarayıcı tarafından desteklenir, tarayıcı sürümü için denir.  
   
     
## <a name="navigation-in-wpf-applications"></a>WPF uygulamalarında Gezinti  
 Bu konu içinde anahtar Gezinti özelliklerine genel bakış sağlar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu özelliklerin her iki tek başına uygulamaları için kullanılabilir ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bu konuda bunları bağlamında sunar ancak bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Bu konuda oluşturmak ve dağıtmak nasıl ele alınmamaktadır [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Daha fazla bilgi için [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 Bu bölümde açıklar ve gezinti şu yönlerini gösterir:  
  
-   [Bir sayfa uygulama](#CreatingAXAMLPage)  
  
-   [Başlangıç sayfası yapılandırma](#Configuring_a_Start_Page)  
  
-   [Konak penceresinin başlık, genişlik ve yükseklik yapılandırma](#ConfiguringAXAMLPage)  
  
-   [Köprü gezinme](#NavigatingBetweenXAMLPages)  
  
-   [Bölüm gezintisi](#FragmentNavigation)  
  
-   [Gezinti hizmeti](#NavigationService)  
  
-   [Gezinti hizmetiyle programlı Gezinti](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Gezinti yaşam süresi](#Navigation_Lifetime)  
  
-   [Gezinti günlüğüyle anımsama](#NavigationHistory)  
  
-   [Sayfa ömrü ve günlük](#PageLifetime)  
  
-   [İçerik durumu Gezinme geçmişi ile koruma](#RetainingContentStateWithNavigationHistory)  
  
-   [Tanımlama bilgileri](#Cookies)  
  
-   [Yapılandırılmış Gezinti](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Bir sayfa uygulama  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], .NET Framework nesneleri, özel nesneleri, numaralandırma değerlerinin, kullanıcı denetimleri içeren çeşitli içerik türleri gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] dosyaları. Ancak, en yaygın ve uygun paket içeriğini şekilde kullanarak olduğunu fark edeceksiniz <xref:System.Windows.Controls.Page>. Ayrıca, <xref:System.Windows.Controls.Page> görünümlerini geliştirmek ve geliştirme basitleştirmek için Gezinti özgü özellikler uygular.  
  
 Kullanarak <xref:System.Windows.Controls.Page>, gezinebilir sayfası bildirimli olarak uygulayabileceğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme aşağıdaki gibi kullanarak içerik.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> içinde uygulanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sahip `Page` , kök öğesi olarak ve gerektirir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ad alanı bildirimi. `Page` Öğesi gidin ve görüntülemek istediğiniz içerik bulunuyor. Ayarlayarak içeriğinizi `Page.Content` aşağıdaki biçimlendirmede gösterildiği gibi özellik öğesi.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` yalnızca bir alt öğe içerebilir; Önceki örnekte, tek bir içeriktir dize, "Hello, sayfa!" Uygulamada, genellikle alt öğesi olarak düzen denetimi kullanır (bkz [düzeni](../../../../docs/framework/wpf/advanced/layout.md)) içerir ve içeriğinizi oluşturun.  
  
 Alt öğelerinin bir `Page` öğesi içeriği olarak değerlendirilir bir <xref:System.Windows.Controls.Page> ve sonuç olarak, açıkça kullanmanız gerekmez `Page.Content` bildirimi. Aşağıdaki biçimlendirmede önceki örnekte bildirim temelli eşdeğeridir.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 Bu durumda, `Page.Content` ile alt öğelerini otomatik olarak ayarlanır `Page` öğesi. Daha fazla bilgi için bkz: [WPF içerik modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
 Salt biçimlendirme <xref:System.Windows.Controls.Page> içeriği görüntülemek için yararlıdır. Ancak, bir <xref:System.Windows.Controls.Page> için kullanıcı etkileşimi olayları işleme ve uygulama mantığını çağırma yanıtlayabilir ve ayrıca kullanıcıların sayfa ile etkileşime girmesine izin görüntü denetimleri kullanabilirsiniz. Etkileşimli bir <xref:System.Windows.Controls.Page> biçimlendirme ve arka plan kod, bir bileşimini kullanarak aşağıdaki örnekte gösterildiği gibi uygulanır.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Biçimlendirme dosyası ve arka plan kodu dosyanın birlikte çalışabilmesi için aşağıdaki yapılandırma izin vermek için gereklidir:  
  
-   Biçimlendirme içinde `Page` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulaması oluşturulur, varlığını `x:Class` biçimlendirmede dosya neden olan [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] oluşturmak için bir `partial` öğesinden türetilen sınıf <xref:System.Windows.Controls.Page> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu eklenmesini gerektirir bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildiriminin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Oluşturulan `partial` uygulayan sınıf `InitializeComponent`, olayları kaydetmek ve özelliklerini ayarlamak için çağırıldığı biçimlendirme içinde uygulanır.  
  
-   Kod arkasında, sınıf olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` biçimlendirme ve bu içinde öznitelik öğesinden türetilmelidir <xref:System.Windows.Controls.Page>. Bu arka plan kodu ile ilişkili dosyaya verir `partial` uygulama yapılandırıldığında biçimlendirme dosyası için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   Kod arka plan, <xref:System.Windows.Controls.Page> sınıfı, çağıran bir oluşturucu uygulanmalı `InitializeComponent` yöntemi. `InitializeComponent` uygulanan dosya biçimlendirme tarafından oluşturulan `partial` olaylarını kaydetmek ve biçimlendirme içinde tanımlanan özelliklerini ayarlamak için sınıf.  
  
> [!NOTE]
>  Yeni bir eklediğinizde <xref:System.Windows.Controls.Page> kullanarak proje için [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> biçimlendirme ve arka plan kodu, kullanılarak uygulanır ve işaretleme ve arka plan kod dosyaları arasındaki ilişki oluşturmak için gerekli yapılandırmayı içerir burada açıklanmıştır.  
  
 Bulduktan sonra bir <xref:System.Windows.Controls.Page>, kendisine gidebilirsiniz. İlk belirtmek için <xref:System.Windows.Controls.Page> uygulamaya gider, başlangıç yapılandırmanız gereken <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Başlangıç sayfası yapılandırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] belirli bir miktarda bir tarayıcıda barındırılması için uygulama altyapısı gerektirir. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> sınıfı gerekli uygulama altyapısı kuran uygulama tanımını bir parçasıdır (bkz [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
 Uygulama tanımı, genellikle olarak yapılandırılan biçimlendirme dosyayla biçimlendirme ve arka plan kodu, kullanılarak uygulanır bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` öğesi. Bir uygulama tanımıdır aşağıdaki bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kendi uygulama tanımını bir başlangıç belirtmek için kullanabilirsiniz <xref:System.Windows.Controls.Page>, olduğu <xref:System.Windows.Controls.Page> , otomatik olarak ne zaman yüklendi [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] başlatılır. Ayarlayarak bunu <xref:System.Windows.Application.StartupUri%2A> özelliğiyle [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] istenen için <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Çoğu durumda, <xref:System.Windows.Controls.Page> içine derlenmiş veya bir uygulama ile dağıtılır. Bu durumda, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] tanımlayan bir <xref:System.Windows.Controls.Page> bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], olduğu bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için uygun *paketi* düzeni. Paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ele alınan daha ayrıntılı olarak [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md). Aşağıda açıklanan http düzenini kullanarak içerik de gidebilirsiniz.  
  
 Ayarlayabileceğiniz <xref:System.Windows.Application.StartupUri%2A> aşağıdaki örnekte gösterildiği gibi bildirimli olarak biçimlendirme içinde.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 Bu örnekte, `StartupUri` özniteliği göreli paketiyle ayarlanmış [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] HomePage.xaml tanımlar. Zaman [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olan başlatılan, HomePage.xaml otomatik olarak için gittiğinizde ve görüntülenir. Bu gösteren aşağıdaki şekilde tarafından gösterilen bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web sunucusundan başlatılmış.  
  
 ![XBAP sayfası](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure9.png "NavigationOverviewFigure9")  
  
> [!NOTE]
>  Geliştirilmesi ve dağıtımı hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md) ve [WPF uygulaması dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Konak penceresinin başlık, genişlik ve yükseklik yapılandırma  
 Önceki rakamdan fark bir şey. tarayıcı ve sekmesini paneli başlığı olduğunu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Uzun olmasının yanı sıra, çekici ne bilgilendirici başlığı. Bu nedenle, <xref:System.Windows.Controls.Page> ayarlayarak başlığını değiştirmek bir yol sunar <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği. Ayrıca, genişlik ve yükseklik tarayıcı penceresinin ayarlayarak yapılandırabileceğiniz <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A>sırasıyla.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, ve <xref:System.Windows.Controls.Page.WindowHeight%2A> biçimlendirme, aşağıdaki örnekte gösterildiği gibi bildirimli olarak ayarlanabilir.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Sonuç aşağıdaki çizimde gösterilmiştir.  
  
 ![Pencere başlığı, yüksekliği, genişliği](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure2.png "NavigationOverviewFigure2")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Köprü gezinme  
 Tipik bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] birkaç sayfa oluşur. Bir sayfadan diğerine gitmek için en basit yolu kullanmaktır bir <xref:System.Windows.Documents.Hyperlink>. Bildirimli olarak ekleyebileceğiniz bir <xref:System.Windows.Documents.Hyperlink> için bir <xref:System.Windows.Controls.Page> kullanarak `Hyperlink` aşağıdaki biçimlendirmede gösterilen öğesi.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` öğesi aşağıdakileri gerektirir:  
  
-   Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , <xref:System.Windows.Controls.Page> , gitmek için belirtildiği gibi `NavigateUri` özniteliği.  
  
-   Bir kullanıcının metin ve resimler gibi Gezinti başlatmak için tıklatabileceği içerik (içerik için `Hyperlink` öğesi içermediğinden, bkz: <xref:System.Windows.Documents.Hyperlink>).  
  
 Aşağıdaki şekil gösterir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ile bir <xref:System.Windows.Controls.Page> olan bir <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Köprü sayfasıyla](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure3.png "NavigationOverviewFigure3")  
  
 Beklediğiniz gibi tıklatarak <xref:System.Windows.Documents.Hyperlink> neden [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gitmek için <xref:System.Windows.Controls.Page> tarafından tanımlanan `NavigateUri` özniteliği. Ayrıca, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir girdi için önceki ekler <xref:System.Windows.Controls.Page> son sayfalar listesine [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Bu aşağıdaki şekilde gösterilir.  
  
 ![Geri ve İleri düğmelerini](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Birinden Gezintiyi Destekleme yanı sıra <xref:System.Windows.Controls.Page> diğerine <xref:System.Windows.Documents.Hyperlink> de destekler Gezinti parçalara.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Bölüm gezintisi  
 *Parçalara Gezinti* gezinti ya da içerik parçadaki için geçerli olan <xref:System.Windows.Controls.Page> veya başka bir <xref:System.Windows.Controls.Page>. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], içerik parça adlı bir öğe tarafından içerilen içeriktir. Adlandırılmış bir öğesi olan bir öğedir kendi `Name` öznitelik kümesi. Aşağıdaki biçimlendirmede adlandırılmış gösterir `TextBlock` içerik parça içeren öğe.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 İçin bir <xref:System.Windows.Documents.Hyperlink> içerik parçaya gitmek için `NavigateUri` özniteliği şunları içermelidir:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , <xref:System.Windows.Controls.Page> Gitmek için içerik parça ile.  
  
-   "#" Karakter.  
  
-   Öğede adını <xref:System.Windows.Controls.Page> içerik parça içerir.  
  
 Bir parça [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki biçime sahiptir.  
  
 *PageURI* `#` *ElementName*  
  
 Aşağıdaki örneği gösterilmektedir bir `Hyperlink` içerik parçaya gitmek için yapılandırılmış.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Bu bölümde varsayılan parça Gezinti uygulamasında açıklanmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Ayrıca, kısmen işleme gerektiren kendi parça Gezinti uygulamaz olanak tanır <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> olay.  
  
> [!IMPORTANT]
>  Gevşek parçalanma gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları (yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ile dosyaları `Page` kök öğesi olarak) aracılığıyla sayfaları yalnızca gözatılabilir varsa [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Ancak, gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa kendi parçada gidin.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Gezinti hizmeti  
 Sırada <xref:System.Windows.Documents.Hyperlink> belirli bir gezinti başlatmak bir kullanıcının <xref:System.Windows.Controls.Page>, bulma ve sayfa yükleme işlemlerini tarafından gerçekleştirilen <xref:System.Windows.Navigation.NavigationService> sınıfı. Esas olarak, <xref:System.Windows.Navigation.NavigationService> gibi istemci kodu adına bir gezinti isteği işleme yeteneği sağlar <xref:System.Windows.Documents.Hyperlink>. Ayrıca, <xref:System.Windows.Navigation.NavigationService> izleme ve bir gezinti isteği etkileyen daha yüksek düzeyli destek uygular.  
  
 Zaman bir <xref:System.Windows.Documents.Hyperlink> tıklandığında, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çağrıları <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> bulup indirmek için <xref:System.Windows.Controls.Page> belirtilen paket adresindeki [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. İndirilen <xref:System.Windows.Controls.Page> , kök nesnesi bir örneğidir indirilen nesne ağacına dönüştürülür <xref:System.Windows.Controls.Page>. Kök başvuru <xref:System.Windows.Controls.Page> nesne depolanır <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> özelliği. Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için ilk içeriği içinde depolanan için <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliği, sırada <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> paketi depolar [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için gittiğinizde son sayfası.  
  
> [!NOTE]
>  Mümkünse bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birden fazla etkin olmasını uygulama <xref:System.Windows.Navigation.NavigationService>. Daha fazla bilgi için bkz: [gezinti konakları](#Navigation_Hosts) bu konuda daha sonra.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Gezinti hizmetiyle programlı Gezinti  
 Hakkında bilmek zorunda değilsiniz <xref:System.Windows.Navigation.NavigationService> Gezinti bildirimli olarak işaretleme kullanarak uygulanmışsa <xref:System.Windows.Documents.Hyperlink>, çünkü <xref:System.Windows.Documents.Hyperlink> kullanan <xref:System.Windows.Navigation.NavigationService> sizin adınıza. Yani ya da doğrudan veya dolaylı üst sürece bir <xref:System.Windows.Documents.Hyperlink> Gezinti ana bilgisayar (bkz [gezinti konakları](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> bulabilir ve işlemek için Gezinti ana bilgisayarın Gezinti hizmet kuramaz bir Gezinti isteği.  
  
 Ancak, bazı durumlarda kullanmanız gerektiğinde <xref:System.Windows.Navigation.NavigationService> doğrudan, aşağıdakiler dahil:  
  
-   Örneği oluşturmak gerektiğinde bir <xref:System.Windows.Controls.Page> varsayılan olmayan bir Oluşturucu kullanarak.  
  
-   Özelliklerini ayarlamak gerektiğinde <xref:System.Windows.Controls.Page> önce kendisine gidin.  
  
-   Zaman <xref:System.Windows.Controls.Page> için gittiğinizde yalnızca çalışma zamanında belirlenebilir olduğunu.  
  
 Bu durumlarda çağırarak Gezinti programlı olarak başlatmak için kod yazmanız gerekir. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi <xref:System.Windows.Navigation.NavigationService> nesnesi. Bir başvuru alma gerektiren bir <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Bir başvuru NavigationService alma  
 Ele alınmaktadır nedeniyle [gezinti konakları](#Navigation_Hosts) bölümünde, bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama birden fazla olabilir <xref:System.Windows.Navigation.NavigationService>. Kodunuzu bulmak için bir yola ihtiyaç duyar yani bir <xref:System.Windows.Navigation.NavigationService>, genellikle olduğu <xref:System.Windows.Navigation.NavigationService> geçerli gittiğinizde <xref:System.Windows.Controls.Page>. Bir başvuru alabileceğiniz bir <xref:System.Windows.Navigation.NavigationService> çağırarak `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> yöntemi. Alınacak <xref:System.Windows.Navigation.NavigationService> belirli bir gittiğinizde <xref:System.Windows.Controls.Page>, başvuru geçirdiğiniz <xref:System.Windows.Controls.Page> bağımsız değişkeni olarak <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> yöntemi. Aşağıdaki kodu nasıl alınacağını gösterir <xref:System.Windows.Navigation.NavigationService> geçerli <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Bulma için bir kısayol olarak <xref:System.Windows.Navigation.NavigationService> için bir <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> uygulayan <xref:System.Windows.Controls.Page.NavigationService%2A> özelliği. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> yalnızca başvuru alabilir, <xref:System.Windows.Navigation.NavigationService> zaman <xref:System.Windows.Controls.Page> başlatır <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Bir sayfa nesnesine programlı Gezinti  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Navigation.NavigationService> program aracılığıyla gitmek için bir <xref:System.Windows.Controls.Page>. Programlı gezinti, çünkü gereklidir <xref:System.Windows.Controls.Page> diğer bir deyişle için gittiğinizde yalnızca oluşturulabilir, varsayılan olmayan tek Oluşturucusu kullanarak. <xref:System.Windows.Controls.Page> Varsayılan olmayan Oluşturucu ile aşağıdaki biçimlendirme ve kodun gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> Varlıklardan için <xref:System.Windows.Controls.Page> varsayılan olmayan Oluşturucu ile aşağıdaki biçimlendirme ve kodun gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Zaman <xref:System.Windows.Documents.Hyperlink> bu <xref:System.Windows.Controls.Page> olan tıklandığında, gezinti örneği tarafından başlatılan <xref:System.Windows.Controls.Page> varsayılan olmayan Oluşturucu kullanarak ve çağırma gitmek için <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> Nesne başvuru kabul eder, <xref:System.Windows.Navigation.NavigationService> , bir paketi yerine gideceği [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Bir paketi URI programlı gezinme  
 Bir paketi oluşturmak ihtiyacınız varsa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] program aracılığıyla (zaman yalnızca belirleyebilirsiniz paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında, örneğin), kullanabileceğiniz <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Geçerli sayfayı yenilemeyi  
 A <xref:System.Windows.Controls.Page> aynı paketi varsa indirilmez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi olarak [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] içinde depolanan <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> özelliği. Zorlamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçerli sayfayı yeniden yüklemek için çağırabilirsiniz <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Gezinti yaşam süresi  
 Gördüğünüz gibi gezinme, başlatmak için birçok yolu vardır. Gezinti başlatıldığında ve gezinme işlemi devam ederken, izlemek ve tarafından uygulanan aşağıdaki olaylar kullanarak gezinti etkilemek olduğunda <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Yeni bir gezinti istendiğinde oluşur. Gezinti iptal etmek için kullanılabilir.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Gezinti ilerleme durumu bilgileri sağlamak için düzenli aralıklarla bir yükleme sırasında oluşur.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Sayfa bulunan ve indirilen oluşur.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Gezinti durdurulduğunda oluşur (çağırarak <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), veya ne zaman yeni bir gezinti istenen geçerli bir gezinti sürerken.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. İstenen içerik gezinirken bir hata ortaya çıktığında oluşur.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. İçin ilk içeriği yüklenen ayrıştırılmış ve işleme başladıktan oluşur.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Bir içerik parça gezinme başladığında, olur oluşur:  
  
    -   Hemen istenen parça geçerli içerikte ise.  
  
    -   İstenen parça farklı içeriği ise kaynak içerik yüklendikten sonra.  
  
 Aşağıdaki şekilde gösterilen sırada Gezinti olaylar oluşturulur.  
  
 ![Sayfa gezintisi akış çizelgesi](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure11.png "NavigationOverviewFigure11")  
  
 Genel olarak, bir <xref:System.Windows.Controls.Page> bu olaylar hakkında ilgili değildir. Bir uygulama bunlarla ilgili olduğu ve bu nedenle, bu olaylar ayrıca tarafından başlatılan büyük olasılıkla <xref:System.Windows.Application> sınıfı:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Her zaman <xref:System.Windows.Navigation.NavigationService> bir olay başlatır <xref:System.Windows.Application> sınıfı, karşılık gelen olay başlatır. <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> kendi ilgili kapsamlarında Gezinti algılamak için aynı olayları sunar.  
  
 Bazı durumlarda, bir <xref:System.Windows.Controls.Page> bu olayları ilginizi çekebilir. Örneğin, bir <xref:System.Windows.Controls.Page> işleyebilirsiniz <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> kendisini çıktığınızda gezinme iptal gerekip gerekmediğini belirlemek için olay. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Gezinti olayından bir işleyici kaydolduğunuzda, bir <xref:System.Windows.Controls.Page>, önceki örnekte olduğu gibi olay işleyicisi ayrıca kayıttan çıkarmanız gerekir. Bunu yapmazsanız, nasıl göre yan etkileri olabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Gezinti hatırlıyor <xref:System.Windows.Controls.Page> günlüğünü kullanarak gezinti.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Gezinti günlüğüyle anımsama  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gelen gittiğiniz sayfaları anımsaması iki yığınları kullanır: geri yığını ve bir iletme yığını. Geçerli gidin zaman <xref:System.Windows.Controls.Page> yeni bir <xref:System.Windows.Controls.Page> veya varolan bir iletme <xref:System.Windows.Controls.Page>, geçerli <xref:System.Windows.Controls.Page> eklenen *geri yığını*. Geçerli gidin zaman <xref:System.Windows.Controls.Page> dön önceki <xref:System.Windows.Controls.Page>, geçerli <xref:System.Windows.Controls.Page> eklenen *iletme yığını*. Geri yığını, iletme yığını ve bunları yönetmek için işlevselliği topluca için günlük olarak bilinir. Her öğe geri yığını ve iletme yığını örneğidir <xref:System.Windows.Navigation.JournalEntry> sınıfı ve olarak adlandırılır bir *günlük girdisi*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer günlüğünden gezinme  
 Kavramsal olarak, günlük aynı çalışır biçimi **geri** ve **İleri** içinde düğmeleri [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] yapın. Bunlar aşağıdaki çizimde gösterilmektedir.  
  
 ![Geri ve İleri düğmelerini](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] tarafından barındırılan [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] günlük gezintinin tümleştirir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Bu sayfalarında gezinmek kullanıcılara bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kullanarak **geri**, **İleri**, ve **son sayfalar** içinde düğmeleri [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Günlük içine tümleştirilmiştir değil [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] olduğu için aynı şekilde [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] veya Internet Explorer 8. Bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir yedek Gezinti işler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], bir kullanıcı merkezden gittiğinde daha sonra tekrar bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], yalnızca günlük girişlerini Canlı tutulan değil sayfalar için günlükte korunur. Sayfaları canlı tutma hakkında daha fazla bilgi için bkz: [sayfa ömrü ve günlük](#PageLifetime) bu konuda daha sonra.  
  
 Varsayılan olarak, her metin <xref:System.Windows.Controls.Page> , görünür **son sayfalar** listesi [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] olan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için <xref:System.Windows.Controls.Page>. Çoğu durumda, bu kullanıcı için özellikle anlamlı değildir. Neyse ki, aşağıdaki seçeneklerden birini kullanarak metin değiştirebilirsiniz:  
  
1.  Ekli `JournalEntry.Name` öznitelik değeri.  
  
2.  `Page.Title` Öznitelik değeri.  
  
3.  `Page.WindowTitle` Öznitelik değeri ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] geçerli <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Geçerli <xref:System.Windows.Controls.Page>. (Varsayılan)  
  
 Metin bulma için öncelik sırasını seçenekleri listelenmiş görevlerin sırası eşleşir. Örneğin, varsa `JournalEntry.Name` , diğer değerleri yoksayılır ayarlanmadı.  
  
 Aşağıdaki örnek kullanır `Page.Title` özniteliği için bir günlük girdisi görüntülenen metni değiştirin.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>WPF kullanarak günlük gezinme  
 Bir kullanıcı kullanarak günlük gidebilirsiniz rağmen **geri**, **İleri**, ve **son sayfalar** içinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], her ikisini de kullanarak günlük de gidebilirsiniz tarafından sağlanan bildirim temelli ve programlama mekanizmaları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bunu yapmak için bir neden olan özel gezinti sağlamak için [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sayfalarınızı içinde.  
  
 Tarafından sunulan Gezinti komutlarını kullanarak, günlük gezinti desteği bildirimli olarak ekleyebilirsiniz <xref:System.Windows.Input.NavigationCommands>. Aşağıdaki örnekte nasıl kullanılacağı ortaya `BrowseBack` Gezinti komutu.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Aşağıdaki üyeleri birini kullanarak, günlük program aracılığıyla gezinebilirsiniz <xref:System.Windows.Navigation.NavigationService> sınıfı:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Günlük de anlatıldığı gibi program aracılığıyla yönetilebilir [istinat içerik Gezinme geçmişi durumuyla](#RetainingContentStateWithNavigationHistory) bu konuda daha sonra.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Sayfa ömrü ve günlük  
 Göz önünde bulundurun bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Zengin içeriği içeren birkaç sayfalarıyla grafikleri, animasyonları ve medya gibi. Bu gibi sayfalar için bellek alanını özellikle video ve ses medya kullanılıyorsa oldukça büyük olabilir. Günlük "gittiğinizde için bu tür kaldırılmış sayfaları hatırlıyor o" bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hızlı bir şekilde büyük ve belirgin bir bellek miktarı tüketebilir.  
  
 Bu nedenle, günlük varsayılan davranışını depolamaktır <xref:System.Windows.Controls.Page> başvuru yerine her günlük girdisi meta verileri bir <xref:System.Windows.Controls.Page> nesnesi. Bir günlük girişi için gittiğinizde, kendi <xref:System.Windows.Controls.Page> yeni bir örneğini belirtilen oluşturmak için kullanılan meta veri <xref:System.Windows.Controls.Page>. Sonuç olarak, her <xref:System.Windows.Controls.Page> gittiğinizde aşağıdaki şekilde gösterilen kullanım ömrü vardır.  
  
 ![Sayfa ömrü](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure10.PNG "NavigationOverviewFigure10")  
  
 Varsayılan olarak günlüğe kaydetme davranışını kullanarak bellek tüketimi kaydedebilirsiniz rağmen sayfa başına işleme performansı azalabilir; reinstantiating bir <xref:System.Windows.Controls.Page> zaman özellikle çok miktarda içerik varsa, yoğun olabilir. Silmemeniz gerekiyorsa bir <xref:System.Windows.Controls.Page> örneği günlüğü'nde, bunu yapmak için iki teknikleri hakkında çizebilirsiniz. İlk olarak, program aracılığıyla gidebilirsiniz bir <xref:System.Windows.Controls.Page> çağırarak nesne <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> yöntemi.  
  
 İkinci olarak, belirtebilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] örneğini korumak bir <xref:System.Windows.Controls.Page> ayarlayarak günlüğündeki <xref:System.Windows.Controls.Page.KeepAlive%2A> özelliğine `true` (varsayılan `false`). Aşağıdaki örnekte gösterildiği gibi ayarlayabileceğiniz <xref:System.Windows.Controls.Page.KeepAlive%2A> bildirimli olarak biçimlendirmede.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Yaşam süresi bir <xref:System.Windows.Controls.Page> yani canlı tutulur olmayan bir dilden çok az farklıdır. İlk kez bir <xref:System.Windows.Controls.Page> , tutulur Canlı için görüntülendiği, tıpkı örneği bir <xref:System.Windows.Controls.Page> , değil tutulur tutma. Ancak, çünkü örneği <xref:System.Windows.Controls.Page> tutulur günlükte kaldığı sürece günlük, hiçbir zaman yeniden için örneği. Sonuç olarak, varsa bir <xref:System.Windows.Controls.Page> her seferinde çağrılması gereken başlatma mantığı varsa <xref:System.Windows.Controls.Page> gittiğinizde için bunu oluşturucudan işleyicisi içine taşımanız <xref:System.Windows.FrameworkElement.Loaded> olay. Aşağıdaki şekilde gösterildiği gibi <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.FrameworkElement.Unloaded> olayları her zaman yükseltilmiş bir <xref:System.Windows.Controls.Page> ve ondan, sırasıyla gittiğinizde.  
  
 ![Yüklenen ve yüklenmeyen olaylar başlatıldığında](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure17.png "NavigationOverviewFigure17")  
  
 Zaman bir <xref:System.Windows.Controls.Page> olan Canlı tutulur değil, aşağıdakilerden birini yapmalısınız değil:  
  
-   Bir başvuru veya herhangi bir kısmını depolar.  
  
-   Olay işleyicileri tarafından uygulanmaz olaylar ile kaydedin.  
  
 Bunlardan yapılması zorla başvuruları oluşturacak <xref:System.Windows.Controls.Page> bile günlükten kaldırıldıktan sonra bellekte tutulacak.  
  
 Genel olarak, varsayılan tercih etmelisiniz <xref:System.Windows.Controls.Page> değil tutmayı davranışı bir <xref:System.Windows.Controls.Page> tutma. Ancak, bu sonraki bölümde açıklanan durumu etkilere sahiptir.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>İçerik durumu Gezinme geçmişi ile koruma  
 Varsa bir <xref:System.Windows.Controls.Page> canlı, tutulur değil ve verileri bir kullanıcı merkezden giderse ve geri olanlar kullanıcıdan veri toplamak denetimleri olan <xref:System.Windows.Controls.Page>? Bir kullanıcı deneyimi açısından bakıldığında, daha önce girilmiş verileri görmek kullanıcıya beklemeniz gerekir. Ne yazık ki, çünkü yeni bir örneğini <xref:System.Windows.Controls.Page> her Gezinti toplanan verileri reinstantiated ve veriler kaybolur denetimleri oluşturulur.  
  
 Neyse ki, günlük arasında verileri hatırlamak için destek sağlar <xref:System.Windows.Controls.Page> denetim verileri de dahil olmak üzere gezintilerini. Özellikle, günlük girdisi her <xref:System.Windows.Controls.Page> ilişkili için geçici bir kapsayıcı olarak davranır <xref:System.Windows.Controls.Page> durumu. Aşağıdaki adımlar bu destek nasıl kullanıldığını anahat olduğunda bir <xref:System.Windows.Controls.Page> sayfadan çıkıldığında:  
  
1.  Geçerli bir giriş <xref:System.Windows.Controls.Page> günlüğe eklenir.  
  
2.  Durumu <xref:System.Windows.Controls.Page> geri yığınına eklenen bu sayfa için günlük girdisi ile birlikte saklanır.  
  
3.  Yeni <xref:System.Windows.Controls.Page> için gittiğinizde.  
  
 Zaman sayfa <xref:System.Windows.Controls.Page> olan günlük kullanarak geri için gittiğinizde yerine aşağıdaki adımları uygulayın:  
  
1.  <xref:System.Windows.Controls.Page> (Üst günlük girdisi geri yığında) örneği.  
  
2.  <xref:System.Windows.Controls.Page> Günlük girdisi ile depolanmış durumuna yenilendiğini <xref:System.Windows.Controls.Page>.  
  
3.  <xref:System.Windows.Controls.Page> Geri gittiğinizde.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki denetimleri üzerinde kullanıldığında bu destek otomatik olarak kullanan bir <xref:System.Windows.Controls.Page>:  
  
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
  
 Varsa bir <xref:System.Windows.Controls.Page> kullanır, bu denetimleri, bunların içine girdiğiniz veriler arasında hatırlanır <xref:System.Windows.Controls.Page> tarafından gösterildiği gibi gezintilerini **sık kullanılan rengi** <xref:System.Windows.Controls.ListBox> aşağıdaki şekilde.  
  
 ![Sayfa durumu unutmayın denetimleri ile](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure13.png "NavigationOverviewFigure13")  
  
 Zaman bir <xref:System.Windows.Controls.Page> denetimleri yukarıdaki listede olanlar dışında olan veya durum özel nesneleri depolandığında durumu arasında anımsaması günlük neden için kod yazmanız gerekir <xref:System.Windows.Controls.Page> gezintilerini.  
  
 Arasında küçük durumlarından unutmayın gerekip gerekmediğini <xref:System.Windows.Controls.Page> gezintilerini, bağımlılık özellikleri kullanabilirsiniz (bkz <xref:System.Windows.DependencyProperty>) ile yapılandırılmış <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> meta veri bayrağı.  
  
 Durumu, <xref:System.Windows.Controls.Page> gezinmeler arasında anımsaması gereken birden çok veri parçalarını oluşur, bu daha az kod, tek bir sınıf durumda kapsüllemek ve uygulama için yoğun bulabilirsiniz <xref:System.Windows.Navigation.IProvideCustomContentState> arabirimi.  
  
 Tek bir çeşitli durumları arasında gezinmek ihtiyacınız varsa <xref:System.Windows.Controls.Page>, gelen gezinme olmadan <xref:System.Windows.Controls.Page> kendisini kullanabileceğiniz <xref:System.Windows.Navigation.IProvideCustomContentState> ve <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Tanımlama bilgileri  
 Başka bir yolla bu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama verilerini depolamak oluşturulan tanımlama bilgileriyle güncelleştirilene ve kullanarak silinmiş <xref:System.Windows.Application.SetCookie%2A> ve <xref:System.Windows.Application.GetCookie%2A> yöntemleri. Oluşturabileceğiniz tanımlama bilgilerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Web uygulamalarının diğer türleri aynı tanımlama bilgilerini kullanır; tanımlama bilgileridir sırasında veya uygulama oturumları arasında bir istemci makine üzerinde bir uygulama tarafından depolanan veriler rasgele parça. Tanımlama bilgisi verileri genellikle şu biçimde bir ad/değer çifti biçiminde alır.  
  
 *Ad* `=` *değeri*  
  
 Ne zaman veri iletilir <xref:System.Windows.Application.SetCookie%2A>, birlikte <xref:System.Uri> tanımlama bilgisinin ayarlanmalıdır konumu, bellek içi bir tanımlama bilgisi oluşturulur ve yalnızca oturum süresi boyunca geçerli uygulama için kullanılabilir. Bu tür bir tanımlama bilgisi olarak adlandırılır bir *oturum tanımlama bilgisi*.  
  
 Uygulama oturumları arasında bir tanımlama bilgisi depolamak için bir sona erme tarihi aşağıdaki biçimi kullanarak tanımlama bilgisine eklenmesi gerekir.  
  
 *AD* `=` *DEĞERİ* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Bir tanımlama bilgisi ile bir sona erme tarihi geçerli depolanan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] tanımlama bilgisinin süresinin kadar yüklemenin geçici Internet dosyaları klasörünün. Böyle bir tanımlama bilgisi olarak bilinen bir *kalıcı bir tanımlama bilgisi* uygulama oturumları arasında devam ederse olduğundan.  
  
 Oturum ve kalıcı tanımlama bilgileri çağırarak alma <xref:System.Windows.Application.GetCookie%2A> geçirme yöntemi <xref:System.Uri> burada tanımlama bilgisi ayarlandığı ile konumunun <xref:System.Windows.Application.SetCookie%2A> yöntemi.  
  
 Bazı tanımlama bilgileri desteklenen yolla verilmiştir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bağımsız uygulamalar ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] her ikisi de oluşturabilir ve tanımlama bilgileri yönetebilirsiniz.  
  
-   Tarafından oluşturulan tanımlama bilgilerini bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tarayıcıdan erişilebilir.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] aynı etki alanından oluşturabilir ve tanımlama bilgileri paylaşabilirsiniz.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] aynı etki alanında sayfalarından oluşturmak ve paylaşmak tanımlama bilgileri.  
  
-   Tanımlama bilgilerini gönderilen zaman [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları Web istekleri olun.  
  
-   Her ikisi de en üst düzey [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] barındırılan IFRAMES tanımlama bilgilerine erişebilir.  
  
-   Tanımlama bilgisi desteği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tüm desteklenen tarayıcılar için aynıdır.  
  
-   İçinde [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], tanımlama bilgilerini ilgilidir P3P ilke dikkate alınır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], özellikle birinci taraf ve üçüncü taraf göre [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Yapılandırılmış Gezinti  
 Bir veri iletmek gerekiyorsa <xref:System.Windows.Controls.Page> diğerine veri bağımsız değişken olarak bir varsayılan olmayan oluşturucuya geçirebilirsiniz <xref:System.Windows.Controls.Page>. Bu yöntemi kullanırsanız, tutmalısınız Not <xref:System.Windows.Controls.Page> Canlı; değilse, sonraki açışınızda, gitmeniz <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reinstantiates <xref:System.Windows.Controls.Page> varsayılan oluşturucu kullanarak.  
  
 Alternatif olarak, <xref:System.Windows.Controls.Page> geçirilmesi gereken veri kümesi özellikleri uygulayabilirsiniz. Şeyler hale beceri gerektiren, ancak, bir <xref:System.Windows.Controls.Page> geçirmek için veri geri <xref:System.Windows.Controls.Page> , gittiğinizde için. Gezinti yerel mekanizmaları, güvence altına almak için desteklemediğini sorunudur bir <xref:System.Windows.Controls.Page> sayfadan çıkıldığında sonra döndürülürsünüz. Esas olarak, gezinti çağrı/return semantiği desteklemiyor. Bu sorunu çözmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar <xref:System.Windows.Navigation.PageFunction%601> emin olmak için kullanabileceğiniz sınıfı bir <xref:System.Windows.Controls.Page> tahmin edilebilir ve yapılandırılmış bir şekilde döndürülür. Daha fazla bilgi için bkz: [yapılandırılmış Gezinti genel bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow sınıfı  
 Bu noktada, gezinebilir içeriğe uygulamaları oluşturmak için kullanmak en olası gezinti Hizmetleri gam gördünüz. Bu hizmetleri bağlamında ele alınan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bunlarla sınırlı değildir ancak [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Modern işletim sistemi ve Windows uygulamalarını tek başına uygulamalara tarayıcısı stilinde Gezinti eklemenizi modern kullanıcı tarayıcı deneyimini yararlanın. Ortak örnekler:  
  
-   **Word eş anlamlılar sözlüğü**: word seçenekleri gidin.  
  
-   **Dosya Gezgini**: dosya ve klasörleri gidin.  
  
-   **Sihirbazlar**: karmaşık bir görev arasında gittiğinizde birden çok sayfa içine bölmek. Windows özellikleri ekleme ve kaldırma işleme Windows Bileşenleri Sihirbazı'nı örneğidir.  
  
 Tek başına uygulamalarınıza tarayıcısı stilinde Gezinti birleştirmek için kullanabileceğiniz <xref:System.Windows.Navigation.NavigationWindow> sınıfı. <xref:System.Windows.Navigation.NavigationWindow> türetilen <xref:System.Windows.Window> ve onu Gezinti aynı desteğiyle genişleten [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sağlayın. Kullanabileceğiniz <xref:System.Windows.Navigation.NavigationWindow> ya da ana penceresinde, tek başına uygulamanızın veya bir iletişim kutusu gibi ikincil bir pencere olarak.  
  
 Uygulamak için bir <xref:System.Windows.Navigation.NavigationWindow>, en üst düzey sınıflar olarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, vb.), biçimlendirme ve arka plan kodu bileşimini kullanın. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Bu kod oluşturur bir <xref:System.Windows.Navigation.NavigationWindow> otomatik olarak varlıklardan için bir <xref:System.Windows.Controls.Page> (HomePage.xaml) olduğunda <xref:System.Windows.Navigation.NavigationWindow> açılır. Varsa <xref:System.Windows.Navigation.NavigationWindow> ana uygulama penceresi kullanabileceğiniz `StartupUri` özniteliği başlatın. Bu aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Aşağıdaki şekil gösterir <xref:System.Windows.Navigation.NavigationWindow> bağımsız uygulama ana penceresinde olarak.  
  
 ![Bir ana penceresi](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure18.png "NavigationOverviewFigure18")  
  
 Rakamdan görebilirsiniz <xref:System.Windows.Navigation.NavigationWindow> ayarlanmış değildi olsa bile bir başlığa sahip <xref:System.Windows.Navigation.NavigationWindow> önceki örnekten uygulama kodu. Bunun yerine, başlık kullanılarak ayarlanır <xref:System.Windows.Controls.Page.WindowTitle%2A> aşağıdaki kodda gösterildiği özelliği.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Ayarı <xref:System.Windows.Controls.Page.WindowWidth%2A> ve <xref:System.Windows.Controls.Page.WindowHeight%2A> özellikleri de etkiler <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Genellikle, kendi uygulamanız <xref:System.Windows.Navigation.NavigationWindow> davranışını veya görünümünü özelleştirmek gerektiğinde. Hiçbiri yoksa bir kısayolu kullanabilirsiniz. Paketi belirtirseniz, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , bir <xref:System.Windows.Controls.Page> olarak <xref:System.Windows.Application.StartupUri%2A> bir tek başına uygulamasında <xref:System.Windows.Application> otomatik olarak oluşturur bir <xref:System.Windows.Navigation.NavigationWindow> ana bilgisayara <xref:System.Windows.Controls.Page>. Aşağıdaki biçimlendirmede bunu etkinleştirmek nasıl gösterir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Bir ikincil uygulama penceresi olması için bir iletişim kutusu gibi isteyip istemediğinizi bir <xref:System.Windows.Navigation.NavigationWindow>, açmak için aşağıdaki örnekte kodu kullanabilirsiniz.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Aşağıdaki şekil sonucu gösterir.  
  
 ![Bir iletişim kutusu](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure19.png "NavigationOverviewFigure19")  
  
 Gördüğünüz gibi <xref:System.Windows.Navigation.NavigationWindow> görüntüler [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-stil **geri** ve **İleri** günlük gitmek kullanıcıların düğmeler. Bu düğme, aşağıdaki çizimde gösterildiği gibi aynı kullanıcı deneyimini sağlar.  
  
 ![Geri ve İleri düğmelerini NavigationWindow içinde](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure20.png "NavigationOverviewFigure20")  
  
 Sayfalarınızın kendi günlük gezinti desteği ve UI sağlarsanız, gizleyebilirsiniz **geri** ve **İleri** tarafından görüntülenen düğmeleri <xref:System.Windows.Navigation.NavigationWindow> değerini ayarlayarak <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> özelliği`false`.  
  
 Alternatif olarak, özelleştirme desteği kullanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] değiştirmek için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , <xref:System.Windows.Navigation.NavigationWindow> kendisi.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Çerçeve sınıfı  
 Her iki tarayıcı ve <xref:System.Windows.Navigation.NavigationWindow> windows gezinebilir içeriği barındırmak şunlardır. Bazı durumlarda, uygulamaların tüm pencere tarafından barındırılan gerekmez içeriğe sahip. Bunun yerine, bu tür içeriği içindeki diğer içeriği barındırılması. Kullanarak diğer içeriği gezinebilir içeriğe ekleyebilirsiniz <xref:System.Windows.Controls.Frame> sınıfı. <xref:System.Windows.Controls.Frame> aynı desteği sağlar <xref:System.Windows.Navigation.NavigationWindow> ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.Windows.Controls.Frame> için bir <xref:System.Windows.Controls.Page> kullanarak bildirimli olarak `Frame` öğesi.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Bu biçimlendirme ayarlar `Source` özniteliği `Frame` bir paketi öğesiyle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Frame> başlangıçta gitmek. Aşağıdaki şekil gösterir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ile bir <xref:System.Windows.Controls.Page> olan bir <xref:System.Windows.Controls.Frame> birkaç sayfaları arasında gittiğinizde.  
  
 ![Birden çok sayfa arasında gezinen bir çerçeve](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure5.png "NavigationOverviewFigure5")  
  
 Yalnızca kullanmak zorunda değilsiniz <xref:System.Windows.Controls.Frame> içeriğini içinde bir <xref:System.Windows.Controls.Page>. Da barındırmak için ortak bir <xref:System.Windows.Controls.Frame> içeriğini içinde bir <xref:System.Windows.Window>.  
  
 Varsayılan olarak, <xref:System.Windows.Controls.Frame> yalnızca başka bir günlük olmaması durumunda kendi günlüğünü kullanır. Varsa bir <xref:System.Windows.Controls.Frame> içinde ya da barındırılan içerik parçası olan bir <xref:System.Windows.Navigation.NavigationWindow> veya bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> ait günlük kullanan <xref:System.Windows.Navigation.NavigationWindow> veya [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Bazı durumlarda, yine de bir <xref:System.Windows.Controls.Frame> için kendi günlük sorumlu olması gerekebilir. Bunu yapmak için bir neden olan günlük Gezinti tarafından barındırılan sayfalar içinde izin vermek için bir <xref:System.Windows.Controls.Frame>. Bu aşağıdaki şekilde gösterilmiştir.  
  
 ![Çerçeve ve sayfa diyagramı](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure7.png "NavigationOverviewFigure7")  
  
 Bu durumda, yapılandırabileceğiniz <xref:System.Windows.Controls.Frame> ayarlayarak kendi günlük kullanılacak <xref:System.Windows.Controls.Frame.JournalOwnership%2A> özelliği <xref:System.Windows.Controls.Frame> için <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Bu aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 İçinde gezinme etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.Frame> kendi günlüğünü kullanır.  
  
 ![Kendi günlüğünü kullanan bir çerçeve](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure8.png "NavigationOverviewFigure8")  
  
 Günlük girişlerini Gezinti tarafından gösterilen bildirim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde <xref:System.Windows.Controls.Frame>, yerine göre [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Varsa bir <xref:System.Windows.Controls.Frame> içinde barındırılan içerik parçası olan bir <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> kendi günlük kullanır ve sonuç olarak, kendi gezinti görüntüler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Kullanıcı deneyiminiz gerektiriyorsa bir <xref:System.Windows.Controls.Frame> Gezinti göstermeden kendi günlük sağlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], gezinti gizleyebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ayarlayarak <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> için <xref:System.Windows.Visibility.Hidden>. Bu aşağıdaki biçimlendirmede gösterilir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Gezinti konakları  
 <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> gezinti konakları olarak bilinen sınıflarıdır. A *Gezinti konak* gidin ve içeriği görüntüle bir sınıftır. Bunu başarmak için her Gezinti konağın kendi kullandığı <xref:System.Windows.Navigation.NavigationService> ve günlük. Bir gezinme konak temel yapımı aşağıdaki şekilde gösterilir.  
  
 ![Gezgin diyagramları](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure15.png "NavigationOverviewFigure15")  
  
 Esas olarak, böylece <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.Frame> aynı sağlamak için gezinti desteği bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tarayıcıda barındırıldığında sağlar.  
  
 Kullanarak yanı sıra <xref:System.Windows.Navigation.NavigationService> ve bir günlük gezinti konakları aynı üyelerini uygulama, <xref:System.Windows.Navigation.NavigationService> uygular. Bu aşağıdaki şekilde gösterilmiştir.  
  
 ![Bir günlük bir çerçeve ve NavigationWindow](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure24.png "NaivgationOverviewFigure24")  
  
 Bu, program gezinti desteği doğrudan bunlara karşı olanak tanır. Özel bir gezinti sağlamak ihtiyacınız varsa, düşünebileceğiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için bir <xref:System.Windows.Controls.Frame> içinde barındırılan bir <xref:System.Windows.Window>. Ayrıca, her iki türü de dahil olmak üzere, ek, gezinti ilgili üyeleri uygulamak `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) ve `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), günlük girişlerini arka listeleme ver yığın ve yığını, sırasıyla iletebilir.  
  
 Daha önce belirtildiği gibi birden fazla günlük bir uygulama içinde bulunabilir. Bu durum, aşağıdaki şekilde gösteren bir örnek sağlar.  
  
 ![Bir uygulama içinde birden çok günlük](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure25.png "NaivgationOverviewFigure25")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML sayfaları dışında içeriğe gezinme  
 Bu konu, boyunca <xref:System.Windows.Controls.Page> ve paketi [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] çeşitli Gezinti özellikleri göstermek için kullanılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ancak, bir <xref:System.Windows.Controls.Page> diğer bir deyişle bir uygulamayı derlenmiş için ilk içeriği ve paketi türü değil [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içeriğini belirlemek için tek yolu değil.  
  
 Bu bölüm gösterir şekilde de için gevşek gidebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] dosyaları ve nesneleri.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Gevşek XAML dosyaları gezinme  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki özelliklere sahip bir dosya bir dosyadır:  
  
-   Yalnızca içeren [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (diğer bir deyişle, hiçbir kodu).  
  
-   Uygun ad alanı bildiriminin sahiptir.  
  
-   .Xaml dosya adı uzantısına sahiptir.  
  
 Örneğin, gevşek depolanan aşağıdaki içeriğe göz önünde bulundurun [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya, Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Dosyayı çift tıklatın, tarayıcı açar ve gider ve içeriği görüntüler. Bu aşağıdaki şekilde gösterilir.  
  
 ![İçeriği görüntüleme Person.XAML dosyasında](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure21.png "NavigationOverviewFigure21")  
  
 Gevşek görüntüleyebilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki dosyasından:  
  
-   Yerel makine, intranet veya Internet üzerindeki bir Web sitesi.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] dosya paylaşımı.  
  
-   Yerel disk.  
  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya tarayıcının Kullanılanlara eklenebilir veya tarayıcının giriş sayfası.  
  
> [!NOTE]
>  Yayımlama ve gevşek başlatma hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları, bkz: [WPF uygulaması dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
 Gevşek göre bir sınırlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kısmi güvende çalıştırmanın güvenli olduğunu içeriği yalnızca barındırabilir olduğu. Örneğin, `Window` gevşek kök öğesi olamaz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>HTML dosyaları çerçevesi kullanarak gezinme  
 Beklediğiniz gibi de gidebilirsiniz [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Sağlamak yeterlidir bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] http düzenini kullanır. Örneğin, aşağıdaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gösteren bir <xref:System.Windows.Controls.Frame> varlıklardan için bir [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] sayfası.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Gezinme [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] özel izinler gerektirir. Örneğin, gelen gidemezsiniz bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Internet bölgesi kısmi güven güvenlik korumalı alanda çalışır. Daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser denetimi kullanarak HTML dosyaları için gezinme  
 <xref:System.Windows.Controls.WebBrowser> Kontrol destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] belge barındırma, gezinti ve komut dosyası ve yönetilen kod birlikte çalışabilirlik. Ayrıntılı bilgi için ilgili <xref:System.Windows.Controls.WebBrowser> denetlemek için bkz: <xref:System.Windows.Controls.WebBrowser>.  
  
 Gibi <xref:System.Windows.Controls.Frame>, gezinme için [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kullanarak <xref:System.Windows.Controls.WebBrowser> özel izinler gerektirir. Örneğin, bir kısmi güven uygulamasından, yalnızca gidebilirsiniz [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitede bulunan. Daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Özel nesneler için gezinme  
 Özel nesneler olarak depolanan verileri varsa, bu verileri görüntülemek için bir yol oluşturmaktır bir <xref:System.Windows.Controls.Page> bu nesnelerle ilişkili içerikle (bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)). Yalnızca nesneleri görüntülemek için sayfanın tamamını oluşturma yükünü gerekmiyorsa, kendilerine doğrudan yerine gidebilirsiniz.  
  
 Göz önünde bulundurun `Person` aşağıdaki kodda uygulanır sınıfı.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Gitmek için arama <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Aşağıdaki şekil sonucu gösterir.  
  
 ![Bir sınıfa giden bir sayfa](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure22.png "NavigationOverviewFigure22")  
  
 Bu rakamdan faydalı bir şey görüntülendiğini görebilirsiniz. Aslında, görüntülenen değer dönüş değeri `ToString` yöntemi **kişi** ; nesnesinin varsayılan olarak, bu yalnızca, değer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesnenizin temsil etmek için kullanabilirsiniz. Geçersiz kılma `ToString` devam eder ancak daha anlamlı bilgileri döndürmek için yöntemi yalnızca bir dize değeri olmalıdır. Sunu yeteneklerini yararlanan bir tekniği kullanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri şablonu kullanmaktır. Veri şablonu uygulayabilirsiniz, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belirli bir türdeki bir nesne ile ilişkilendirebilirsiniz. Aşağıdaki kod veri şablonu gösterir `Person` nesnesi.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Burada, veri şablonu ilişkili olduğu `Person` kullanarak türü `x:Type` biçimlendirme uzantısı'nda `DataType` özniteliği. Veri şablonu sonra bağlar `TextBlock` öğeleri (bkz <xref:System.Windows.Controls.TextBlock>) özelliklerini `Person` sınıfı. Güncelleştirilmiş görünümünü aşağıdaki şekilde gösterilmiştir `Person` nesnesi.  
  
 ![Bir veri şablona sahip bir sınıfa gezinme](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure23.png "NavigationOverviewFigure23")  
  
 Bu teknik bir avantajı tutarlılık olduğu nesnelerinizi tutarlı bir şekilde herhangi bir yere, uygulamanızda görüntülenecek veri şablonu yeniden erişebildiklerinden elde.  
  
 Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Gezinti desteği sağlayan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için Internet ve onu arasında gittiğinizde için üçüncü taraf içeriği barındırmak uygulamaları sağlar. Uygulamaların ve kullanıcıların zararlı davranışından korumak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içinde açıklanan güvenlik özellikleri çeşitli sağlayan [güvenlik](../../../../docs/framework/wpf/security-wpf.md) ve [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Application.SetCookie%2A>  
 <xref:System.Windows.Application.GetCookie%2A>  
 [Uygulama Yönetimine Genel Bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [WPF İçinde URI'leri Paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Yapılandırılmış Gezintiye Genel Bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)  
 [Gezinti Topolojilerine Genel Bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/app-development/navigation-how-to-topics.md)  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
