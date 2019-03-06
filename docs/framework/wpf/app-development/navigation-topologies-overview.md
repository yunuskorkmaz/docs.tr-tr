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
# <a name="navigation-topologies-overview"></a>Gezinti Topolojilerine Genel Bakış
<a name="introduction"></a> Bu genel bakış içindeki gezinti topolojilerine tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Daha sonra örnek, üç genel gezinti topolojileri ele alınmıştır.  
  
> [!NOTE]
>  Bu konuda okumadan önce yapılandırılmış Gezinti kavramı bilmeniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfa işlevlerini kullanma. Bu konu hem de daha fazla bilgi için bkz [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Gezinti topolojileri](#Navigation_Topologies)  
  
-   [Yapılandırılmış gezinti topolojileri](#Structured_Navigation_Topologies)  
  
-   [Sabit doğrusal topoloji içinde gezinme](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Sabit hiyerarşik topoloji üzerinde dinamik Gezinti](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Dinamik olarak oluşturulan topoloji üzerinde Gezinti](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Gezinti topolojileri  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], gezinti, genellikle sayfaları oluşur (<xref:System.Windows.Controls.Page>) köprülerle (<xref:System.Windows.Documents.Hyperlink>) tıklandığında diğer sayfalara gidin. İçin gitme sayfaları tanımlanır [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (bkz [paketi URI ' WPF'de](pack-uris-in-wpf.md)). Sayfaları, köprüleri gösteren aşağıdaki basit örnekte göz önünde bulundurun ve [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Bu sayfalar halinde düzenlenir bir *gezinti topolojisi* yapısını sayfaları arasında nasıl gezinebileceğiniz tarafından belirlenir. Gezinti daha karmaşık topolojiler, bir uygulama çalıştırılırken bazıları yalnızca tanımlanabilir gerekmesine rağmen bu belirli Gezinti topoloji basit senaryo uygundur.  
  
 Bu konuda üç genel gezinti topolojileri kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak üretilen*. Her Gezinti topolojisine sahip olan bir örnek gösterilmiştir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki şekilde gösterilen bir ister:  
  
 ![Görev veri öğeleri sayfalarıyla](./media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Yapılandırılmış gezinti topolojileri  
 Gezinti topolojilerine iki geniş türü vardır:  
  
-   **Sabit Topoloji**: derleme zamanında tanımlanmış ve çalışma zamanında değiştirmez. Sabit topolojiler, sabit bir dizi gezinmeyi doğrusal veya hiyerarşik sırayla sayfalar için kullanışlıdır.  
  
-   **Dinamik topoloji**: kullanıcı, uygulama veya sistem toplanan giriş göre çalışma zamanında tanımlanmış. Dinamik topolojileri sayfaları farklı sıralarında geçtiğiniz yararlıdır.  
  
 Gezinti topolojilerine sayfalarını kullanarak oluşturmak mümkün olsa da, sağladıkları basitleştirir ve döndüren bir topoloji sayfalarına veri geçirme için destek ek destek için örnekleri sayfa işlevlerini kullanın.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Sabit doğrusal topoloji içinde gezinme  
 Sabit doğrusal topoloji, sabit bir sırayla gitme bir veya daha fazla sihirbaz sayfasına sahip bir sihirbaz yapısına benzer. Aşağıdaki şekilde bir sihirbazın sabit doğrusal topoloji ile akış ve üst düzey yapısını gösterir.  
  
 ![Gezinti topoloji diyagramı](./media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 Sabit doğrusal topoloji üzerinde gezinme için tipik davranışları şunları içerir:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme. Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir. Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.  
  
-   Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.  
  
-   Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
-   Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır. Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Sabit hiyerarşik topoloji üzerinde dinamik Gezinti  
 Bazı uygulamalarda, sayfaları aşağıdaki resimde gösterildiği gibi iki veya daha fazla diğer sayfalarına yönelik gezinme olanak verir.  
  
 ![Birden çok sayfasına gidebilirsiniz bir sayfa](./media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 Bu yapı sabit hiyerarşik topoloji bilinir ve uygulama veya kullanıcı tarafından hangi hiyerarşinin geçirildiği sırası genellikle çalışma zamanında belirlenir. Çalışma zamanında, iki veya daha fazla diğer sayfalarına yönelik gezinme sağlar hiyerarşide her sayfasına gitmek için hangi sayfa belirlemek için gereken verileri toplar. Aşağıdaki şekilde bir önceki şekle bağlı birkaç olası gezinti sıralarının gösterilmektedir.  
  
 ![Gezinti topoloji diyagramı](./media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 Sabit hiyerarşik bir yapıda sayfaları gitme sırasını çalışma zamanında belirlenir olsa bile, kullanıcı deneyimini sabit doğrusal topoloji için kullanıcı deneyimi aynıdır:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme. Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir. Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.  
  
-   Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcıların gittikleri günlük aracılığıyla geri gezinti sırasını değiştirebilirsiniz.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.  
  
-   Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
-   Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır. Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Dinamik olarak oluşturulan topoloji üzerinde Gezinti  
 Bazı uygulamalarda, iki veya daha fazla sayfaya gitme sırasını yalnızca çalışma zamanında kullanıcı, uygulama veya dış veri olup olmadığını tarafından belirlenebilir. Aşağıdaki şekilde bir belirlenmemiş Gezinti diziyle sayfalar kümesi gösterilmektedir.  
  
 ![Gezinti topoloji diyagramı](./media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 Şekilde, çalışma zamanında kullanıcı tarafından seçilen bir gezinti sırasını gösterilmektedir.  
  
 ![Gezinti diyagramı](./media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 Gezinti sırasında dinamik olarak oluşturulan topoloji bilinir. Önceki Topolojileri için olduğu gibi kullanıcının olarak başka gezinme topolojileri ile kullanıcı deneyimini aynıdır:  
  
-   Arama sayfasından Sihirbazı'nı başlatır ve ilk sihirbaz sayfasına gider bir Başlatıcısı sayfa gezinme. Bir başlatıcı sayfa (bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-daha az <xref:System.Windows.Navigation.PageFunction%601>) arama sayfası ilk sayfasında doğrudan çağırabildiğinden gerekli değildir. Özellikle başlatma karmaşık ise bir Başlatıcısı sayfasını kullanarak, ancak Sihirbazı başlatma basitleştirebilir.  
  
-   Kullanıcılar geri ve İleri düğmelerini (veya köprüler) kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcılar, günlük kullanarak sayfalar arasında gezinebilirsiniz.  
  
-   Kullanıcılar, iptal düğmesine basarak herhangi bir sihirbaz sayfasında Sihirbazı iptal edebilirsiniz.  
  
-   Kullanıcılar, sihirbaz son sihirbaz sayfasında son düğmesine basarak kabul edebilir.  
  
-   Sihirbazı iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
-   Bir kullanıcı bir Sihirbazı'nı kabul ederse, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
-   Sihirbazı'nı (kabul edildi veya iptal edildi) tamamlandıktan sonra sihirbaz oluşur sayfaları günlükten kaldırılır. Bu, böylece olası verileri veya durumu anomalileri önleme yalıtılmış, sihirbaz her bir örneğini saklar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
