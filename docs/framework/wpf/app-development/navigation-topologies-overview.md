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
# <a name="navigation-topologies-overview"></a>Gezinti Topolojilerine Genel Bakış
<a name="introduction"></a>Bu genel bakışta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içindeki gezinti topolojilerine giriş sağlanır. Örneklerle birlikte üç ortak gezinti topolojisi daha sonra ele alınmıştır.  
  
> [!NOTE]
> Bu konuyu okumadan önce, sayfa işlevlerini kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yapılandırılmış gezinme kavramıyla ilgili bilgi sahibi olmanız gerekir. Bu konuların her ikisi hakkında daha fazla bilgi için bkz. [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md).  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Gezinti topolojileri](#Navigation_Topologies)  
  
- [Yapılandırılmış gezinti topolojileri](#Structured_Navigation_Topologies)  
  
- [Sabit doğrusal topoloji üzerinden gezinme](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Sabit hiyerarşik topoloji üzerinde dinamik gezinti](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Dinamik olarak oluşturulan bir topoloji üzerinden gezinme](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Gezinti topolojileri  
 @No__t_0, gezinti tipik olarak, tıklandığı zaman diğer sayfalara gitmek için köprüler (<xref:System.Windows.Documents.Hyperlink>) ile sayfalardan (<xref:System.Windows.Controls.Page>) oluşur. ' Ye gidildiği sayfalar Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) tarafından tanımlanır (bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md)). Sayfaları, köprüleri ve Tekdüzen Kaynak tanımlayıcılarını (URI) gösteren aşağıdaki basit örneği göz önünde bulundurun:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Bu sayfalar, yapısı sayfalar arasında nasıl gezindiğinize göre belirlenen bir *gezinti topolojisi* içinde düzenlenir. Bu özel gezinti topolojisi basit senaryolarda uygundur, ancak bazıları yalnızca bir uygulama çalışırken tanımlanabilseler de, daha karmaşık topolojiler gerektirebilir.  
  
 Bu konuda üç genel gezinti topolojisi ele alınmaktadır: *Sabit doğrusal*, *sabit hiyerarşik*ve *dinamik olarak üretilen*. Her gezinti topolojisi, aşağıdaki şekilde gösterildiği gibi bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olan bir örnekle gösterilmiştir:  
  
 ![Veri öğeleri ve gezinti düğmeleri içeren görev sayfaları.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Yapılandırılmış gezinti topolojileri  
 İki geniş gezinti topolojisi türü vardır:  
  
- **Sabit topoloji**: derleme zamanında tanımlanır ve çalışma zamanında değişmez. Sabit topolojiler, doğrusal veya hiyerarşik bir düzende sabit bir sayfa dizisi aracılığıyla gezinme için faydalıdır.  
  
- **Dinamik topoloji**: Kullanıcı, uygulama veya sistem tarafından toplanan girişe dayalı olarak çalışma zamanında tanımlanır. Dinamik topolojiler, sayfalar farklı dizilerle gezinilebilir olduğunda faydalıdır.  
  
 Sayfaları kullanarak gezinti topolojileri oluşturmak mümkün olsa da, örnekler, bir topolojinin sayfaları aracılığıyla veri geçirme ve döndürme desteğini kolaylaştıran ek destek sağladığından, örnek sayfa işlevlerini kullanır.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Sabit doğrusal topoloji üzerinden gezinme  
 Sabit bir doğrusal topoloji, sabit bir dizide gezindiği bir veya daha fazla sihirbaz sayfasına sahip olan bir sihirbazın yapısına benzer. Aşağıdaki şekilde, sabit bir doğrusal topolojiyle bir sihirbazın üst düzey yapısı ve akışı gösterilmektedir:  
  
 ![Sabit bir doğrusal topolojiyi gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Sabit bir doğrusal topoloji üzerinde gezinmek için tipik davranışlar şunları içerir:  
  
- Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme. Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir. Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.  
  
- Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.  
  
- Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.  
  
- Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Sabit hiyerarşik topoloji üzerinde dinamik gezinti  
 Bazı uygulamalarda, sayfalar aşağıdaki şekilde gösterildiği gibi iki veya daha fazla sayfaya gezinmesine izin verir: 
  
 ![Birden çok sayfaya gidebileceğiniz bir sayfayı gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Bu yapı sabit bir hiyerarşik topoloji olarak bilinir ve hiyerarşinin çapraz geçen sırası genellikle uygulama veya Kullanıcı tarafından çalışma zamanında belirlenir. Çalışma zamanında, hiyerarşideki iki veya daha fazla sayfaya gezinmesine izin veren her sayfa, hangi sayfanın ekleneceğini belirlemede gereken verileri toplar. Aşağıdaki şekilde, önceki şekle göre olası çeşitli gezinti dizilerinden biri gösterilmektedir:  
  
 ![Olası bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Sabit hiyerarşik bir yapıdaki sayfaların çalışma zamanında gezinmesine rağmen, Kullanıcı deneyimi sabit bir doğrusal topoloji için Kullanıcı deneyimiyle aynıdır:  
  
- Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme. Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir. Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.  
  
- Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.  
  
- Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar, günlük üzerinden geri gittiklerinde, gezinti sırasını değiştirebilir.  
  
- Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.  
  
- Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Dinamik olarak oluşturulan bir topoloji üzerinden gezinme  
 Bazı uygulamalarda, iki veya daha fazla sayfanın gezindiği sıra yalnızca çalışma zamanında, Kullanıcı, uygulama veya dış veriler tarafından belirlenebilir. Aşağıdaki şekilde, belirlenmemiş bir gezinti sırası olan bir sayfa kümesi gösterilmektedir:  
  
 ![Belirlenmemiş bir gezinti dizisine sahip bir sayfa kümesi.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Sonraki şekilde, çalışma zamanında Kullanıcı tarafından seçilen bir gezinti sırası gösterilmektedir:  
  
 ![Çalışma zamanında seçilen bir gezinti sırasını gösteren diyagram.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Gezinti sırası, dinamik olarak oluşturulan bir topoloji olarak bilinir. Diğer gezinti topolojilerinde olduğu gibi, Kullanıcı deneyimi, önceki topolojilerle aynı olur:  
  
- Çağıran sayfadan, Sihirbazı başlatan ve ilk sihirbaz sayfasına gezinen bir başlatıcı sayfasına gitme. Çağıran bir sayfa ilk sihirbaz sayfasını doğrudan çağırabileceğinizden, bir başlatıcı sayfası ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Less <xref:System.Windows.Navigation.PageFunction%601>) gerekli değildir. Ancak, bir başlatıcı sayfası kullanılması, özellikle başlatma karmaşık ise, sihirbaz başlatmasını kolaylaştırabilir.  
  
- Kullanıcılar, geri ve Ileri düğmelerini (veya köprüleri) kullanarak sayfalar arasında gezinebilirsiniz.  
  
- Kullanıcılar, günlüğü kullanarak sayfalar arasında gezinebilirler.  
  
- Kullanıcılar bir Iptal düğmesine basarak Sihirbazı herhangi bir sihirbaz sayfasından iptal edebilir.  
  
- Kullanıcılar son sihirbaz sayfasında son düğmesine basarak sihirbazı kabul edebilir.  
  
- Sihirbaz iptal edilirse, sihirbaz uygun bir sonuç döndürür ve herhangi bir veri döndürmez.  
  
- Bir Kullanıcı bir Sihirbazı kabul ediyorsa, sihirbaz uygun bir sonuç döndürür ve topladığı verileri döndürür.  
  
- Sihirbaz tamamlandığında (kabul edildiğinde veya iptal edildiğinde), sihirbazın içerdiği sayfalar günlükten kaldırılır. Bu, sihirbazın her örneğini yalıtılmış tutar, böylece potansiyel veri veya durum bozukluileri önlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Yapılandırılmış Gezintiye Genel Bakış](structured-navigation-overview.md)
