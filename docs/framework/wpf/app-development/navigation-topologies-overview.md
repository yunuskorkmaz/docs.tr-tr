---
title: "Gezinti Topolojilerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbe7fe80639537293413d8fb923033909a2451e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="navigation-topologies-overview"></a>Gezinti Topolojilerine Genel Bakış
<a name="introduction"></a>Bu genel bakışta Gezinti topolojide tanıtılmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Örnekler ile üç ortak gezinti topolojisi daha sonra ele alınmıştır.  
  
> [!NOTE]
>  Bu konuyu okumadan önce yapılandırılmış Gezinti kavramı aşina olmalısınız [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfa işlevlerini kullanarak. Bu konuların ikisi hakkında daha fazla bilgi için bkz: [yapılandırılmış Gezinti genel bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Gezinti topolojileri](#Navigation_Topologies)  
  
-   [Yapılandırılmış gezinti topolojileri](#Structured_Navigation_Topologies)  
  
-   [Sabit doğrusal topoloji üzerinde Gezinti](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Sabit hiyerarşik topoloji üzerinden dinamik Gezinti](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Dinamik olarak üretilen topoloji üzerinde Gezinti](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Gezinti topolojileri  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], gezinti genellikle sayfalarının oluşur (<xref:System.Windows.Controls.Page>) köprü ile (<xref:System.Windows.Documents.Hyperlink>) tıklatıldığında başka sayfalara gidin. İçin gittiğinizde sayfaları tanımlanır [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (bkz [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)). Sayfaları, köprüleri gösteren aşağıdaki basit örneği göz önünde bulundurun ve [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Bu sayfalar halinde düzenlenir bir *gezinti topolojisi* , yapısı, sayfalar arasında nasıl gidebilirsiniz tarafından belirlenir. Bir uygulamayı çalıştırırken bazıları yalnızca tanımlanabilir daha karmaşık topolojiler Gezinti gerekmesine rağmen bu belirli gezinti topolojisi basit senaryolarda uygundur.  
  
 Bu konuda üç ortak Gezinti topolojisini kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak üretilen*. Her gezinti topolojisi sahip olan bir örneği ile gösterildiği bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki resimde gösterilen bir ister:  
  
 ![Görev veri öğeleri sayfalarıyla](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Yapılandırılmış gezinti topolojileri  
 Gezinti topolojileri iki geniş türü vardır:  
  
-   **Sabit Topoloji**: derleme zamanında tanımlanan ve çalışma zamanında değiştirmez. Sabit topolojiler, sabit bir dizi gezinmeyi doğrusal veya hiyerarşik sırada sayfaların için yararlıdır.  
  
-   **Dinamik topoloji**: kullanıcı, uygulama veya sistem toplanan giriş göre çalışma zamanında tanımlı. Dinamik topolojiler, sayfalar farklı sıralarında gezildiğinde yararlıdır.  
  
 Sayfaları kullanarak gezinti topolojileri oluşturmak mümkün olsa da, geçirme ve bir topoloji sayfaları aracılığıyla veri döndürmek için destek basitleştirir ek destek sağladıkları için örnekler sayfa işlevlerini kullanır.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Sabit doğrusal topoloji üzerinde Gezinti  
 Sabit doğrusal topoloji, sabit bir dizisinde gittiğinizde bir veya daha fazla sihirbaz sayfasına sahip bir sihirbaz yapısına benzer. Aşağıdaki şekil üst düzey yapı ve sabit doğrusal topoloji sihirbazla akışını gösterir.  
  
 ![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 Sabit doğrusal topoloji üzerinde gezinme için tipik davranışlar şunlardır:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme. Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil. Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.  
  
-   Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.  
  
-   Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.  
  
-   Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.  
  
-   Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır. Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Sabit hiyerarşik topoloji üzerinden dinamik Gezinti  
 Bazı uygulamalarda, sayfalar aşağıdaki resimde gösterildiği gibi iki veya daha fazla diğer sayfalara gezinti izin verin.  
  
 ![Birden çok sayfaya gidebilir bir sayfa](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 Bu yapı sabit hiyerarşik topoloji bilinir ve uygulama veya kullanıcı tarafından hangi hiyerarşinin geçirildiği sırası genellikle çalışma zamanında belirlenir. Çalışma zamanında, iki veya daha fazla başka sayfalara gezinme sağlar hiyerarşideki her bir sayfa gitmek için hangi sayfayı belirlemek için gereken verileri toplar. Aşağıdaki şekilde bir önceki şekle bağlı birkaç olası gezinti sıralarının gösterilmektedir.  
  
 ![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 Sabit hiyerarşik bir yapı sayfalarında gittiğinizde sıra çalışma zamanında belirlenir olsa bile, kullanıcı deneyimi sabit doğrusal topoloji için kullanıcı deneyimi ile aynıdır:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme. Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil. Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.  
  
-   Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.  
  
-   Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.  
  
-   Günlük aracılığıyla geri dönerseniz kullanıcılar Gezinti sırasını değiştirebilirsiniz.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.  
  
-   Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.  
  
-   Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır. Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Dinamik olarak üretilen topoloji üzerinde Gezinti  
 Bazı uygulamalarda, iki veya daha fazla sayfa gittiğinizde sırası yalnızca çalışma zamanında kullanıcı, uygulama veya dış veri olup olmadığını tarafından belirlenebilir. Aşağıdaki şekilde belirlenmemiş Gezinti dizisi ile sayfalar kümesi gösterilmektedir.  
  
 ![Gezinti topoloji diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 Sonraki şekilde, çalışma zamanında kullanıcı tarafından seçilen bir gezinti dizisi gösterilmiştir.  
  
 ![Gezinti diyagramı](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 Gezinti dizisi dinamik olarak üretilen bir topoloji olarak bilinir. Önceki topolojilerde olduğu gibi kullanıcı için diğer gezinti topolojileri ile kullanıcı deneyimi aynı gibidir:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider başlatıcı sayfa gezinme. Başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sihirbaz sayfasını doğrudan çağırabilir miyim beri gerekli değil. Özellikle başlatma karmaşık ise başlatıcı sayfa kullanarak, ancak Sihirbazı'nı başlatma basitleştirebilirsiniz.  
  
-   Kullanıcılar, geri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilir.  
  
-   Kullanıcılar günlük kullanarak sayfalar arasında gezinebilir.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, Son düğmesine basarak son sihirbaz sayfasında Sihirbazı'nı kabul edebilir.  
  
-   Sihirbazı iptal ederseniz, sihirbaz uygun sonucu verir ve herhangi bir veri döndürmüyor.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun sonucu verir ve topladığı verileri döndürür.  
  
-   Sihirbaz (kabul veya iptal edildi) tamamlandığında, sihirbaz oluşur sayfalar günlükten kaldırılır. Bu, böylece olası veri veya durum bozuklukları önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Yapılandırılmış Gezintiye Genel Bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
