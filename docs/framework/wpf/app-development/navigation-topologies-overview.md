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
# <a name="navigation-topologies-overview"></a>Gezinti Topolojilerine Genel Bakış
<a name="introduction"></a>Bu genel bakış, WPF'deki gezinme topolojilerine giriş sağlar. Üç ortak navigasyon topolojisi, örnekleri ile, daha sonra tartışılır.  
  
> [!NOTE]
> Bu konuyu okumadan önce, sayfa işlevlerini kullanarak WPF yapılandırılmış gezinme kavramına aşina olmalısınız. Bu konuların her ikisi hakkında daha fazla bilgi için [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)bölümüne bakın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Navigasyon Topolojileri](#Navigation_Topologies)  
  
- [Yapılandırılmış Navigasyon Topolojileri](#Structured_Navigation_Topologies)  
  
- [Sabit Doğrusal Topoloji üzerinde gezinme](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Sabit Hiyerarşik Topoloji Üzerinde Dinamik Gezinme](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Dinamik Olarak Oluşturulan Topoloji Üzerinde Gezinme](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a>Navigasyon Topolojileri  
 WPF'de gezinme genellikle tıklatıldığında<xref:System.Windows.Controls.Page>diğer sayfalara<xref:System.Windows.Documents.Hyperlink>yönlendiren köprülere sahip sayfalardan () oluşur. Gezinmek üzere yönlendirilen sayfalar, tek düzen kaynak tanımlayıcıları (URI' ler) tarafından tanımlanır (bkz. [WPF'deki Paket URI'leri).](pack-uris-in-wpf.md) Sayfaları, köprüleri ve tek düzen kaynak tanımlayıcılarını (UrI'ler) gösteren aşağıdaki basit örneği göz önünde bulundurun:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Bu sayfalar, yapısı sayfalar arasında nasıl gezinebileceğinize göre belirlenen bir *gezinti topolojisinde* düzenlenir. Bu özel navigasyon topolojisi basit senaryolarda uygundur, ancak navigasyon daha karmaşık topolojiler gerektirebilir ve bunların bazıları yalnızca bir uygulama çalışırken tanımlanabilir.  
  
 Bu konu üç ortak navigasyon topolojisi kapsar: *sabit doğrusal*, *sabit hiyerarşik*, ve *dinamik olarak oluşturulan*. Her navigasyon topolojisi, aşağıdaki şekilde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gösterilene benzer bir örneğe sahip bir örnekle gösterilmiştir:  
  
 ![Veri öğeleri ve gezinme düğmeleri ile görev sayfaları.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a>Yapılandırılmış Navigasyon Topolojileri  
 Navigasyon topolojilerinin iki geniş türü vardır:  
  
- **Sabit Topoloji**: derleme zamanında tanımlanır ve çalışma zamanında değişmez. Sabit topolojiler, doğrusal veya hiyerarşik bir sırada sabit bir sayfa dizisinde gezinmek için yararlıdır.  
  
- **Dinamik Topoloji**: kullanıcıdan, uygulamadan veya sistemden toplanan girdiye göre çalışma zamanında tanımlanır. Dinamik topolojiler, sayfalar farklı dizilerde gezinildiğinde kullanışlıdır.  
  
 Sayfaları kullanarak gezinme topolojileri oluşturmak mümkün olsa da, örnekler sayfa işlevlerini kullanır, çünkü bir topolojinin sayfaları üzerinden veri geçişi ve döndürülme desteği için desteği kolaylaştıran ek destek sağlarlar.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a>Sabit Doğrusal Topoloji üzerinde gezinme  
 Sabit doğrusal topoloji, sabit bir sırada gezinen bir veya daha fazla sihirbaz sayfası olan bir sihirbazın yapısına benzer. Aşağıdaki şekil, sabit doğrusal topolojiye sahip bir sihirbazın üst düzey yapısını ve akışını gösterir:  
  
 ![Sabit doğrusal topolojiyi gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Sabit doğrusal bir topolojide gezinmek için tipik davranışlar şunlardır:  
  
- Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme. Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez. Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.  
  
- Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.  
  
- Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
- Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Sabit Hiyerarşik Topoloji Üzerinde Dinamik Gezinme  
 Bazı uygulamalarda, sayfalar aşağıdaki şekilde gösterildiği gibi iki veya daha fazla başka sayfaya gezinmeye izin verir:
  
 ![Birden çok sayfaya gidebilecek bir sayfayı gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Bu yapı sabit hiyerarşik topoloji olarak bilinir ve hiyerarşinin geçiş sırası genellikle çalışma zamanında uygulama veya kullanıcı tarafından belirlenir. Çalışma zamanında, hiyerarşideki iki veya daha fazla diğer sayfaya gezinmeye izin veren her sayfa, hangi sayfaya gidileni belirlemek için gereken verileri toplar. Aşağıdaki şekil, önceki şeme göre birkaç olası gezinme dizisinden birini göstermektedir:  
  
 ![Olası bir gezinme sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Sabit hiyerarşik yapıdaki sayfaların gezinme sırası çalışma zamanında belirlense de, kullanıcı deneyimi sabit doğrusal bir topoloji için kullanıcı deneyimiyle aynıdır:  
  
- Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme. Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez. Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.  
  
- Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.  
  
- Kullanıcılar günlükte geri gezindiklerinde gezinme sırasını değiştirebilirler.  
  
- Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
- Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a>Dinamik Olarak Oluşturulan Topoloji Üzerinde Gezinme  
 Bazı uygulamalarda, iki veya daha fazla sayfanın gezinildiği sıra, kullanıcı, uygulama veya dış veri tarafından yalnızca çalışma zamanında belirlenebilir. Aşağıdaki şekil, belirsiz gezinme sıralı bir sayfa kümesini gösterir:  
  
 ![Belirsiz gezinme sırasını olan bir sayfa kümesi.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Bir sonraki şekil, kullanıcı tarafından çalışma zamanında seçilen bir gezinti dizisini gösterir:  
  
 ![Çalışma zamanında seçilen bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Navigasyon sırası dinamik olarak oluşturulan topoloji olarak bilinir. Kullanıcı için, diğer navigasyon topolojilerinde olduğu gibi, kullanıcı deneyimi önceki topolojiler için olduğu gibi aynıdır:  
  
- Arama sayfasından sihirbazı başlatan ve ilk sihirbaz sayfasına yönlendiren başlatıcı sayfasına gezinme. Bir arama sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ilk <xref:System.Windows.Navigation.PageFunction%601>sihirbaz sayfasını doğrudan arayabildiği için başlatıcı sayfası (a-az) gerekmez. Ancak, başlatıcı sayfası kullanmak, özellikle başlatma karmaşıksa sihirbaz ın başlatılmasını basitleştirebilir.  
  
- Kullanıcılar, İleri ve İleri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar günlüğü kullanarak sayfalar arasında gezinebilir.  
  
- Kullanıcılar, İptal düğmesine basarak sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasındaki sihirbazı Bitiş düğmesine basarak kabul edebilirler.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç verir ve herhangi bir veri döndürmez.  
  
- Kullanıcı bir sihirbaz kabul ederse, sihirbaz uygun bir sonucu döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edilen veya iptal edilen), sihirbazın oluşturduğu sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini izole eder ve böylece olası verilerden veya durum anormalliklerinden kaçınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
