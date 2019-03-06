---
title: Gönderilmiş Olaylara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: b0db690bfd1a0cabf3060067ea23cf01acf3251d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379217"
---
# <a name="routed-events-overview"></a>Gönderilmiş Olaylara Genel Bakış
Bu konuda yönlendirilmiş olaylar kavramını açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Konu yönlendirilmiş olaylar terminolojisini, açıklar yönlendirilmiş olaylar öğe ağacındaki yönlendirilir nasıl nasıl işleyeceğinizi özetler ve kendi özel gönderilmiş olay oluşturma kullanıma sunar.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu temel bilgiye sahip olduğunuzu varsayar [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ve nesne yönelimli programlama, hem de nasıl kavramını arasındaki ilişkileri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ağaç olarak kavramsallaştırılabileceği. Bu konudaki örnekleri izlemek için de anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve çok temel yazma ne yapılacağını bildiğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar veya sayfaları. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md) ve [XAML genel bakış (WPF)](xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Gönderilmiş bir olayı nedir?  
 Düşünebilirsiniz yönlendirilmiş olayları ya da işlev ya da uygulama açısından. Bazı kişiler birini veya diğer tanım daha kullanışlı çünkü her iki tanımları burada gösterilir.  
  
 İşlev tanımı: Yönlendirilmiş olay işleyicileri olayı tetikleyen nesne yerine bir öğe ağacında birden çok dinleyici çağırabilirsiniz olay türüdür.  
  
 Uygulama tanımı: Yönlendirilmiş olay bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] örneği tarafından desteklenen olay <xref:System.Windows.RoutedEvent> sınıfı ve tarafından işlenen [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.  
  
 Tipik bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması birçok öğe içerir. Kod içinde oluşturulan ya da bildirilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bu öğeleri bir öğe ağacı ilişki birbirine mevcut. Olay tanımı bağlı olarak iki yönlü birinde olay rotada seyahat etmek, ancak genellikle rota kaynak öğeden hareket eder ve "öğesi ağaç kökü (genellikle bir sayfası veya pencere) ulaşana kadar ardından yukarı öğesi ağacı ile Balonlar". DHTML nesne modeli ile daha önce çalıştıysa tırmanma bu kavramı size tanıdık gelebilir.  
  
 Aşağıdaki basit öğe ağacında göz önünde bulundurun:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Bu öğe ağacı aşağıdaki gibi üretir:  
  
 ![Evet, Hayır ve İptal düğmeleri](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 Bu Basitleştirilmiş öğe ağacında, kaynağı bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay biridir <xref:System.Windows.Controls.Button> öğeleri ve hangisi <xref:System.Windows.Controls.Button> tıklandığını olay işleme fırsatına sahip ilk öğedir. Ancak bağlı hiçbir işleyici <xref:System.Windows.Controls.Button> olayı, olay için yukarı doğru Kabarcık sonra davranır <xref:System.Windows.Controls.Button> olan öğe ağacında üst <xref:System.Windows.Controls.StackPanel>. Büyük olasılıkla olay baloncuklar için <xref:System.Windows.Controls.Border>ve daha sonra ötesine sayfa kök öğe ağacında (gösterilmemiştir).  
  
 Diğer bir deyişle, bu olay yolu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay:  
  
 Düğme StackPanel-->--> kenarlık-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Yönlendirilmiş olaylar için üst düzey senaryoları  
 Yönlendirilmiş olay kavramını motive senaryolara kısa bir özeti aşağıda verilmiştir ve tipik bir neden [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay bu senaryolar için yeterli değil:  
  
 **Denetim oluşturma ve saklama:** Çeşitli denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin içerik modeli vardır. Örneğin, görüntüyü içine yerleştirebilirsiniz bir <xref:System.Windows.Controls.Button>, düğmenin görsel ağacı etkili bir şekilde genişleten. Ancak, eklenen görüntü yanıt vermek bir düğme neden isabet sınaması davranışı bozmamalıdır bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> içeriği, görüntüsü teknik bir parçası olan piksel kullanıcı tıkladığında olsa bile.  
  
 **Tek işleyicinin ek noktaları:** İçinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], birden çok öğeden geçirilen olayları işlemek üzere birden çok kez aynı işleyiciyi eklemek gerekir. Yönlendirilmiş olaylar bu işleyici, yalnızca bir kez, önceki örnekte gösterildiği eklemek etkinleştirmeniz ve işleyici mantığını nereden olay gerekirse geldiğini belirlemek için kullanın. Örneğin, bu daha önce gösterilen işleyicisi olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Sınıf işlemesi:** Olayları izin sınıfı tarafından tanımlanan statik bir işleyici yönlendirilir. Bu sınıfı işleyici herhangi bir bağlı örnek işleyicileri için önce bir olay işleme fırsatına sahiptir.  
  
 **Yansıma olmadan bir olay başvuruyor:** Belirli kod ve biçimlendirme teknikleri, belirli bir olayı belirlemek için bir yol gerekir. Gönderilmiş bir olay oluşturur bir <xref:System.Windows.RoutedEvent> statik veya çalışma zamanı yansıma gerektirmeyen güvenilir olay kimliği tekniği sağlayan bir tanımlayıcı olarak alan.  
  
### <a name="how-routed-events-are-implemented"></a>Yönlendirilmiş olaylar nasıl uygulanır  
 Yönlendirilmiş olay bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] örneği tarafından desteklenen olay <xref:System.Windows.RoutedEvent> sınıfı ve kayıtlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. <xref:System.Windows.RoutedEvent> Kayıttan alınan örnek olarak korunduğunda genellikle bir `public` `static` `readonly` alan kaydeder ve bu nedenle yönlendirilmiş olay "sahip" sınıf üyesi. Aynı adlı bağlantı [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] (bazen "sarmalayıcı" olayı olarak adlandırılır) olayını geçersiz kılınarak `add` ve `remove` uygulamaları [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay. Normalde, `add` ve `remove` ekleme ve kaldırma olay işleyicileri için dile özgü olay uygun sözdizimini kullanan örtülü varsayılan olarak kalır. Yönlendirilmiş olay yedekleme ve bağlantı mekanizması nasıl bir bağımlılık özelliği kavramsal olarak benzer bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] güçlendirilmiştir özelliği <xref:System.Windows.DependencyProperty> sınıfı ve kayıtlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi.  
  
 Aşağıdaki örnek, özel bir bildirimi gösterir `Tap` kaydı ve riskini de dahil olmak üzere, yönlendirilmiş olay <xref:System.Windows.RoutedEvent> tanımlayıcı alanı ve `add` ve `remove` uygulamaları `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Yönlendirilmiş olay işleyicileri ve XAML  
 Kullanarak bir olay işleyicisi eklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay adının bir olay dinleyicisi olan öğe üzerinde bir özniteliği olarak bildirin. Özniteliğin değeri arka plan kod dosyasının kısmi class içinde bulunmalıdır uygulanan işleyicisi yönteminiz adıdır.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Standart ekleme söz dizimi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay işleyicileri olduğundan yönlendirilmiş olay işleyicileri için aynı işleyicilerini gerçekten eklemekte olduğunuz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] yönlendirilmiş olay uygulaması olan olay sarmalayıcı altında. Olay işleyicileri ekleme hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [XAML genel bakış (WPF)](xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Stratejilerini yönlendirme  
 Üç yönlendirme stratejisi birini olayları kullanın yönlendirilir:  
  
-   **Tırmanma:** Olay işleyicileri olay kaynağı üzerinde çağrılır. Yönlendirilmiş olayı öğesi ağaç kökü ulaşana kadar art arda gelen üst öğelere ardından yönlendirir. En yönlendirilmiş olaylar, tırmanma yönlendirme stratejisi kullanın. Tırmanma yönlendirilmiş olaylar, genellikle ayrı denetimleri veya diğer kullanıcı Arabirimi öğeleri giriş durum değişikliklerini bildirmek için kullanılır.  
  
-   **Doğrudan:** Yalnızca kaynak öğenin kendisinin yanıt işleyicilerini çağırma fırsatı verilir. Bu ", üretim için" benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] için olayları kullanır. Ancak, standart bir aksine [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay doğrudan yönlendirilmiş olaylar sınıfı işlemeyi destekler (gelecek bölümde sınıfı işleme açıklanmıştır) ve tarafından kullanılan <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger>.  
  
-   **Tünel oluşturma:** Başlangıçta, olay işleyicileri öğesi ağaç kökünde çağrılır. Yönlendirilmiş olay sonra art arda gelen alt öğeleri düğüm öğe yönlendirilmiş olay kaynağı (yönlendirilmiş olayı öğesi) doğru yol boyunca düzeninden rotayı dolaşır. Tünel yönlendirilmiş olaylar genellikle kullanılan veya birleştirme bir denetim için bir parçası olarak bileşik parçalarından olayları kasıtlı olarak gizlenen veya tam denetime özgü olaylar yerine şekilde işlenir. İçinde sağlanan giriş olayları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle bir tünel/tırmanma çift olarak uygulanan gelir. Tünel olayları da önizleme olayları çiftleri için kullanılan bir adlandırma kuralı nedeniyle adlandırılır.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Yönlendirilmiş olaylar niçin kullanılır?  
 Bir uygulama geliştiricisi olarak, her zaman bilmek veya işlemekte olduğunuz olay gönderilmiş bir olay uygulandığını dikkate gerekmez. Yönlendirilmiş olaylar özel davranışa sahiptir, ancak bu öğe üzerinde bir olay oluşturulduğu işleniyorsa büyük ölçüde görünmez bir davranıştır.  
  
 Önerilen senaryolardan birini kullanıyorsanız burada yönlendirilmiş olaylar güçlü hale olduğu: ortak bir kök en yaygın işleyicileri tanımlama birleştirme kendi denetiminizi veya kendi özel denetimi sınıfını tanımlama.  
  
 Yönlendirilmiş olay dinleyicileri ve yönlendirilmiş olay kaynakları hiyerarşilerini ortak bir olayı paylaşmak gerekmez. Tüm <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> gönderilmiş bir olay için bir olay dinleyicisi olabilir. Bu nedenle, yönlendirilmiş olaylar çalışma boyunca kullanılabilir tam kümesini kullanabileceğiniz [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] "uygulama içindeki farklı öğelerin olay bilgi alışverişi verebileceğiniz bir kavramsal arabirimi" ayarlayın. Yönlendirilmiş olaylar için bu "arabirim" kavramı, giriş olayları için özellikle geçerlidir.  
  
 Olay verileri olayın rota içindeki her öğeyi perpetuated çünkü yönlendirilmiş olaylar öğesi ağacı ile iletişim kurmak için de kullanılabilir. Bir öğe bir şey olay verileri değiştirebilir ve bu değişiklik rota sonraki öğe için kullanılabilir hale gelir.  
  
 Yönlendirme en boy dışındaki diğer iki nedeni vardır verilen herhangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay yerine standart bir gönderilmiş bir olay olarak uygulanmasını [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay. Kendi olaylarınızı uyguluyorsanız, bu ilkelere dikkate almanız gerekebilir:  
  
-   Belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil ve şablon oluşturma özellikleri gibi <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger> başvurulan olayı yönlendirilmiş olay olmasını gerektirir. Bu, daha önce bahsedilen olay tanımlayıcısı senaryodur.  
  
-   Yönlendirilmiş olaylar işleme mekanizması sınıfı, tüm kayıtlı örnek işleyicileri erişebilmeniz için önce yönlendirilmiş olaylar işleme fırsatına sahip statik yöntemler yapabildiği belirtebilirsiniz bir sınıf destekler. Sınıfınıza örneği üzerinde bir olay işleme tarafından yanlışlıkla atlanması olamaz olay temelli sınıf davranışlarını zorunlu kılabilir denetim tasarımında, çok kullanışlı olmasıdır.  
  
 Her yukarıdaki konuları, bu konunun ayrı bir bölümde ele alınmıştır.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Ekleme ve bir olay işleyicisi için gönderilmiş bir olayı uygulama  
 Bir olay işleyicisi eklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], sadece bir öğeye bir öznitelik olarak olay adı ekleyerek, öznitelik değeri aşağıdaki örnekte olduğu gibi uygun bir temsilci uygulayan bir olay işleyicisi adı olarak ayarlayın.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` işleyen kodu içeren uygulanan işleyici adı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. `b1SetColor` aynı imzaya sahip olmalıdır <xref:System.Windows.RoutedEventHandler> olay işleyici temsilcisini olan bir temsilci için <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. Tüm yönlendirilmiş olay işleyici temsilcilerini ilk parametresi, olay işleyicisi eklenir ve ikinci parametre olaya ilişkin veriler belirtir öğesi belirtir.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler> temel yönlendirilmiş olay işleyicisi temsilcisidir. Böylece bunlar özelleştirilmiş olay veri iletebilir özelleştirilmiş belirli denetimler veya senaryoları yönlendirilmiş olaylar için yönlendirilmiş olay işleyicilerinde temsilcileri ayrıca daha özelleştirilmiş olabilirler. Örneğin, ortak bir giriş senaryosunda, işleyebilir bir <xref:System.Windows.UIElement.DragEnter> yönlendirilmiş olay. İşleyicinizi uygulamalıdır <xref:System.Windows.DragEventHandler> temsilci. En belirgin temsilci kullanarak, işleyebileceği <xref:System.Windows.DragEventArgs> işleyicisi ve okuma <xref:System.Windows.DragEventArgs.Data%2A> sürükleme işleminin Pano yükünü içeren özellik.  
  
 Bir olay işleyicisi kullanarak bir öğe eklemek tam bir örnek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [bir yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).  
  
 Kod içinde oluşturulan bir uygulamada gönderilmiş bir olay işleyicisi eklemek oldukça basittir. Yönlendirilmiş olay işleyicileri her zaman bir yardımcı yöntem aracılığıyla eklenecek <xref:System.Windows.UIElement.AddHandler%2A> (var olan yedekleme için çağıran yöntemin olduğu `add`.) Ancak, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olaylar genellikle sahip yedekleme uygulamalarına `add` ve `remove` bir dile özgü olay sözdizimi tarafından eklenecek yönlendirilmiş olaylar için işleyiciler izin mantığı daha sezgisel sözdizimi olduğu yardımcı yöntemi. Yardımcı yöntemi kullanım örneği verilmiştir:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 Sonraki örnekte gösterildiği C# işleci sözdizimini (Visual Basic sahip biraz farklı işleci söz dizimi başvurusunun kaldırılması, işleme nedeniyle):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Kodda bir olay işleyicisi ekleme örneği için bkz. [kullanarak bir olay işleyicisini eklemek](how-to-add-an-event-handler-using-code.md).  
  
 Visual Basic kullanıyorsanız, ayrıca kullanabileceğiniz `Handles` işleyici bildirimlerinin bir parçası olarak işleyicileri eklemek için anahtar sözcüğü. Daha fazla bilgi için [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>İşlenmiş kavramı  
 Bir ortak olay verileri temel sınıfı, tüm yönlendirilmiş olaylar paylaşmak <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> tanımlar <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği bir Boole değeri alır. Amacı <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliktir yönlendirilmiş olay olarak işaretlemek için yol boyunca herhangi bir olay işleyici etkinleştirmek için *işlenen*, değerini ayarlayarak <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true`. Bir öğe yol boyunca işleyici tarafından işlendikten sonra paylaşılan bir olay verileri, yol boyunca her dinleyici için yeniden bildirilir.  
  
 Değerini <xref:System.Windows.RoutedEventArgs.Handled%2A> etkiler gönderilmiş bir olay rapor ya da bunu ilerledikçe işlenen nasıl yol boyunca daha fazla. Varsa <xref:System.Windows.RoutedEventArgs.Handled%2A> olduğu `true` olay verileri gönderilmiş bir olay ve diğer öğelerde bu yönlendirilmiş olayı dinleyen işleyicileri için genellikle artık bu belirli olay örneği için çağrılmaz. Bu işleyiciler için hem de bağlı geçerlidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve gibi dile özgü olay işleyicisi ek sözdizimleri tarafından eklenen işleyiciler için `+=` veya `Handles`. En yaygın işleyici senaryoları için bir olay ayarlayarak işlenmiş olarak işaretleme <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` "tünel yolu ya da tırmanma bir rota için ve ayrıca bir noktasında rota sınıfı işleyici tarafından işlenir herhangi bir olay için yönlendirmeyi durdurur".  
  
 Ancak, yapabildiği dinleyicileri yine de çalıştırabilir işleyicileri yönlendirilmiş olaylara yanıt olarak bir "handledEventsToo" mekanizması yoktur burada <xref:System.Windows.RoutedEventArgs.Handled%2A> olduğu `true` olay veri. Diğer bir deyişle, olay yolu tamamen olay verileri işlenmiş olarak işaretleme durdurulmaz. HandledEventsToo mekanizması kod ya da yalnızca kullanabilen bir <xref:System.Windows.EventSetter>:  
  
-   Kodda, çalışan bir dile özgü olay söz dizimi genel kullanmak yerine [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayları çağırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yöntemi <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> işleyicinizi eklemek için. Değerini belirtmek `handledEventsToo` olarak `true`.  
  
-   İçinde bir <xref:System.Windows.EventSetter>ayarlayın <xref:System.Windows.EventSetter.HandledEventsToo%2A> özniteliğini `true`.  
  
 Davranış yanı sıra, <xref:System.Windows.RoutedEventArgs.Handled%2A> durumu üretir yönlendirilmiş olaylar kavramı <xref:System.Windows.RoutedEventArgs.Handled%2A> , uygulamanızı tasarlayın ve bunları nasıl olay işleyicisi kodu yazmak için olası etkilere sahiptir. Kavramsallaştırmak <xref:System.Windows.RoutedEventArgs.Handled%2A> yönlendirilmiş olaylar tarafından gösterilen basit bir protokol olarak. Tam olarak bu protokolü kullanma, ancak nasıl kavramsal tasarımı kadar olan değerini <xref:System.Windows.RoutedEventArgs.Handled%2A> kullanılmaya yönelik aşağıdaki gibidir:  
  
-   Yönlendirilmiş olay işlenmiş olarak işaretlenmişse, onu yeniden o yol boyunca diğer öğeleri tarafından ele alınması gerekmez.  
  
-   Yönlendirilmiş olay işlenmiş olarak işaretlenmemiş sonra yol boyunca önceki diğer dinleyicilere eylemleri bir işleyici veya olay verileri işlemek ve ayarlamak için kayıtlı seçtiğiniz olan işleyicileri kayıt ya da seçmiş olduğunuz <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true`. (Veya doğal olarak geçerli dinleyici rotadaki ilk noktası olabilir.) Geçerli dinleyici işleyicileri, artık eylemi üç olası kurslarımız vardır:  
  
    -   Hiç eylem yok; olay işlenmeden kalır ve olay sonraki dinleyiciye yönlendirir.  
  
    -   Olay yanıt kodu yürütün, ancak bulguyu gerçekleştirilecek eylemi olayı işlenmiş olarak işaretleme garanti altına almak için önemli değil. Sonraki dinleyicisi olay yollar.  
  
    -   Olaya yanıt olarak bir kod yürütün. Olay gerçekleştirilecek eylemi işlenmiş olarak işaretleme garanti altına almak için önemli kabul edilen olduğundan olay işleyicisine geçirilen verileri işlenmiş olarak işaretler. Olay hala yönlendiren sonraki dinleyicisi ancak ile <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` yalnızca kendi olay verilerinde `handledEventsToo` dinleyicileri, işleyicileri daha çağrılacak şansınız vardır.  
  
 Kavramsal bu tasarım, daha önce bahsedilen yönlendirme davranışı tarafından desteklenir: bir önceki işleyici yol boyunca zatenayarlanmışolsabileçağrılanyönlendirilmişolaylariçinişleyicilereklemekdahazor,(halamümkünolsadakodveyastilleri)olduğu<xref:System.Windows.RoutedEventArgs.Handled%2A>için `true`.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.RoutedEventArgs.Handled%2A>sınıfı işlenmesini yönlendirilmiş olayları ve uygun olduğunda ilgili öneriler gönderilmiş bir olay olarak işaretlemek için <xref:System.Windows.RoutedEventArgs.Handled%2A>, bkz: [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](marking-routed-events-as-handled-and-class-handling.md).  
  
 Uygulamalar, yalnızca ortaya çıkan nesne tırmanma yönlendirilmiş olayı işleme ve hiç olay yönlendirme özellikleriyle ilgili olmaması için oldukça yaygındır. Ancak, yine de yönlendirilmiş olay veri öğesi ağacın başka bir öğe ihtimale beklenmedik yan etkileri önlemek için Ayrıca, aynı yönlendirilmiş olay için bağlı bir işleyici olması durumunda işlenmiş olarak işaretlemek için iyi bir uygulamadır.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Sınıf işleyicileri  
 Bazı şekilde türeyen bir sınıf tanımlıyorsanız, <xref:System.Windows.DependencyObject>, ayrıca tanımlayabilir ve sınıfınızın olayı, bildirilmiş veya devralınan bir üyesi olan gönderilmiş bir olay işleyicisi sınıfı ekleyin. Sınıf işleyicileri gönderilmiş bir olayı öğesi örneği yolunu eriştiğinde, söz konusu sınıfın bir örneğine eklenen herhangi bir örnek dinleyici işleyicileri önce çağrılır.  
  
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri, devralınan sınıf belirli yönlendirilmiş olaylar için işleme sahiptir. Bu yönlendirilmiş olayı hiç gerçekleşmedi, ancak gerçekte işlenen sınıfı yapılıyor ve belirli teknikler kullanırsanız yönlendirilmiş olay hala olası örneği İşleyicileriniz tarafından işlenebilen dışa doğru görünümünü verebilir. Ayrıca, birçok temel sınıf ve denetim işleme sınıfı geçersiz kılmak için kullanılan sanal yöntemler kullanıma sunar. İstenmeyen sınıfı işleme etrafında çalışma konusunda ve kendi sınıf özel bir sınıf içinde işleme daha fazla bilgi için bkz: [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>WPF içinde ekli olaylar  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dil de olay olarak adlandırılan özel bir tür tanımlar bir *ekli olay*. Ekli olay belirli bir olay işleyicisi için rastgele bir öğe eklemenize olanak tanır. Olay işleme öğesi değil tanımlayın veya ekli olay devralır ve ne potansiyel olarak olayı tetiklenmeden nesne ya da hedef işleme örneği tanımlayın veya gerekir aksi takdirde bu olay bir sınıf üyesi olarak "sahibi".  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş sistemi ekli olaylar kapsamlı olarak kullanır. Ancak, neredeyse tüm iliştirilmiş bu olayların temel öğeler iletilir. Giriş olayları, ardından eşdeğer bağlı olmayan yönlendirilmiş temel öğe sınıfının üyesi olan olaylar gibi görünür. Ekli olay temel alınan örneği için <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> daha kolayca verilen herhangi işlenebilir <xref:System.Windows.UIElement> kullanarak <xref:System.Windows.UIElement.MouseDown> üzerindeki <xref:System.Windows.UIElement> ekli olay söz dizimi ile baş yerine içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod.  
  
 Ekli olaylar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [iliştirilmiş olaylara genel bakış](attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>XAML içinde yetkili olay adları  
 Benzer başka bir sözdizimi kullanımı *typename*. *eventname* olay sözdizimi bağlı, ancak NET olarak söylemek gerekirse bir ekli olay kullanımı için alt öğeler tarafından başlatılan yönlendirilmiş olaylara işleyiciler eklediğinizde değil. Ortak üst ilgili yönlendirilmiş olay üyesi olmasa bile olay yönlendirme, avantajından yararlanmak için ortak bir üst işleyicileri ekleyin. Bu örnek yeniden göz önünde bulundurun:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 İşte, işleyici eklendi burada üst öğe dinleyicisi bir <xref:System.Windows.Controls.StackPanel>. Ancak, bildirildi ve tarafından gerçekleştirilen gönderilmiş bir olay işleyicisi ekleme <xref:System.Windows.Controls.Button> sınıfı (<xref:System.Windows.Controls.Primitives.ButtonBase> aslında, ancak kullanılabilir <xref:System.Windows.Controls.Button> devralma yoluyla). <xref:System.Windows.Controls.Button> "olay ancak yönlendirilmiş olay sistem izinleri işleyicileri herhangi birine bağlı tüm yönlendirilmiş olay için sahip" <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> dinleyicileri için Aksi takdirde paylaşılmasıdır örneği dinleyicisi bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay. Bu tam olay öznitelik adları için varsayılan xmlns ad alanı genellikle varsayılandır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns ad alanı, ancak önekli ad alanları için özel yönlendirilmiş olaylar belirtebilirsiniz. Xmlns hakkında daha fazla bilgi için bkz: [XAML ad alanları ve WPF XAML Namespace eşleme](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>WPF giriş olayları  
 Yönlendirilmiş olaylar içinde sık bir uygulaması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olayları için bir platformdur. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tünel adları kurala göre "Preview" sözcüğü öneki olayları yönlendirilmiş. Giriş olayları çiftler halinde, tırmanma olay ve diğer tünel olayı olan biriyle genellikle gelir. Örneğin, <xref:System.Windows.ContentElement.KeyDown> olay ve <xref:System.Windows.ContentElement.PreviewKeyDown> olay tırmanma giriş olayı olan önceki ile aynı imzaya sahip ve ikinci tünel giriş olayı. Bazen, giriş olayları yalnızca tırmanma sürümü veya belki de yalnızca doğrudan yönlendirilmiş sürümü gerekir. Belgelerde, yönlendirilmiş olay konuları böyle yönlendirilmiş olaylar varsa ve her yönlendirilmiş olay yönlendirme stratejisini yönetilen başvuru sayfalarına bölümlerde açıklamak alternatif stratejilerini yönlendirme ile benzer yönlendirilmiş olaylar çapraz başvuru.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çiftler halinde gelen giriş olayları, böylece bir fare düğmesine basma gibi bir giriş tek kullanıcı eyleminden sırayla çiftinin her iki yönlendirilmiş olaylar oluşturacak uygulanır. İlk olarak, tünel olayı tetiklenir ve yolunu dolaşır. Ardından tırmanma olay tetiklenir ve yolunu dolaşır. İki olay tam anlamıyla çünkü aynı olay verileri örneği paylaşma <xref:System.Windows.UIElement.RaiseEvent%2A> tırmanma olayı oluşturan uygulayan sınıfa yöntem çağrısında tünel olayı olay verileri dinler ve yeni oluşturulan olay içinde kullanır. Dinleyicileri tünel olay işleyicileri ile işlenen yönlendirilmiş olay işaretlemek için ilk şansınız vardır (sınıf işleyicileri ilk olarak, daha sonra örnek işleyiciler). Tünel yol boyunca bir öğe yönlendirilmiş olay işlenmiş olarak işaretlenmiş, tırmanma olayı için olay zaten işlenmiş veriler gönderilir ve tipik işleyicileri için giriş olayları tırmanma eşdeğer bağlı çağrılmaz. Dışa doğru olması için işlenen tırmanma olay değil bile yükseltildikten gibi olacaktır. Bu işleme davranışını giriş olayları veya bileşik parçalarının yerine, son denetim tarafından bildirilecek giriş olaylarını odak tabanlı tüm isabet sınaması göre isteyebileceğiniz denetim birleştirme için kullanışlıdır. Son denetim öğesi kök dizininde birleştirme yakındır ve bu nedenle ilk ve belki de bir "yönlendirilmiş olay denetimi yedekler kodun bir parçası bir daha özel denetim olayı ile değiştirmek için" tünel olayı işleme fırsatına sınıfına sahip sınıf.  
  
 Giriş olayı works işlemesinin nasıl bir çizim, aşağıdaki giriş olayı örneği göz önünde bulundurun. Aşağıdaki ağaç çizimde gösterilen `leaf element #2` kaynağı hem de bir `PreviewMouseDown` ve ardından bir `MouseDown` olay.  
  
 ![Olay yönlendirme diyagramı](./media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Giriş olayı Tırmanma ve tünel oluşturma  
  
 Olay işleme sırası aşağıdaki gibidir:  
  
1.  `PreviewMouseDown` (kök öğe üzerinde tünel).  
  
2.  `PreviewMouseDown` (#1 Ara öğede tünel).  
  
3.  `PreviewMouseDown` (kaynak öğesinde #2 Tünel).  
  
4.  `MouseDown` (kaynak öğesinde #2 kabarcık).  
  
5.  `MouseDown` (#1 Ara öğede kabarcık).  
  
6.  `MouseDown` (Kök öğede kabarcık).  
  
 Yönlendirilmiş olay işleyici temsilcisini iki nesne başvuru sağlar: olay ve burada işleyicinin çağrıldığı nesnesi başlatan nesne. İşleyicinin burada çağrıldığı nesnesi tarafından bildirilen nesnesidir `sender` parametresi. Burada olayın ilk oluşturulduğu nesnesi tarafından bildirilen <xref:System.Windows.RoutedEventArgs.Source%2A> olay verilerini bir özellik. Yönlendirilmiş olay yine de yükseltilmiş ve bu durumda aynı nesne tarafından işlenen `sender` ve <xref:System.Windows.RoutedEventArgs.Source%2A> özdeş olan (Bu, adım 3 ve 4 olay işleme örneği listesindeki çalışmasıyla).  
  
 Tünel oluşturma ve tırmanma nedeniyle üst öğe giriş olaylarını almak burada <xref:System.Windows.RoutedEventArgs.Source%2A> bunların alt öğeleri biridir. Kaynak öğesi ne olduğunu bilmeniz önemlidir, erişerek kaynak öğesi tanımlayabilirsiniz <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği.  
  
 Genellikle, giriş olayı işaretlendikten sonra <xref:System.Windows.RoutedEventArgs.Handled%2A>, daha fazla işleyici çağrılamaz. Genellikle, giriş olayları, uygulamaya özgü mantıksal işleme giriş olayın anlamını ele alan bir işleyici çağrılmadan hemen sonra işlenmiş olarak işaretlemeniz gerekir.  
  
 Özel durum hakkındaki bu genel ifadenin <xref:System.Windows.RoutedEventArgs.Handled%2A> durumunda kasıtlı olarak yoksaymak için kayıtlı olay işleyicileri giriş <xref:System.Windows.RoutedEventArgs.Handled%2A> olay verileri durumunu yol boyunca hala çağrıldığı. Daha fazla bilgi için [önizleme olayları](preview-events.md) veya [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](marking-routed-events-as-handled-and-class-handling.md).  
  
 Tünel oluşturma ve tırmanma olayları ve sıralı arasında paylaşılan bir olay veri modeline ilk sonra olayları tırmanma tünel oluşturma, genellikle tüm yönlendirilmiş olaylar için true olan bir kavram değildir. Davranış özellikle olduğunu seçilmesiyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olayı çiftlerini oluşturmak ve bağlamak giriş cihazları seçin. Uygulama kendi giriş olayları Gelişmiş bir senaryodur ancak bu modeli, kendi giriş olaylarını izlemek de seçebilirsiniz.  
  
 Belirli sınıfları, tanıtıcı sınıfı bu denetim içinde belirli bir kullanıcı temelli giriş olayı anlamı tanımlayarak ve yeni bir olay oluşturma amacıyla genellikle giriş belirli olaylar seçin. Daha fazla bilgi için [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](marking-routed-events-as-handled-and-class-handling.md).  
  
 Giriş ve giriş ve olayların tipik uygulama senaryolarında nasıl etkileşim hakkında daha fazla bilgi için bkz. [girişe genel bakış](input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters ve EventTriggers  
 Önceden bildirilmiş dahil stillerinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay işlemesi biçimlendirmede sözdizimini kullanarak bir <xref:System.Windows.EventSetter>. Stilin uygulandığı zaman, başvurulan işleyicisi stil uygulanmış bir örneğine eklenir. Bildirebilirsiniz bir <xref:System.Windows.EventSetter> yalnızca yönlendirilmiş olay için. Bir örnek verilmiştir. Unutmayın `b1SetColor` Burada başvurulan bir arka plan kod dosyasında yöntemidir.  
  
 [!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Burada elde edilen avantajı stili, uygulamanızda herhangi bir düğmeye uygulanabilecek diğer bilgileri büyük ölçüde bulunma olasılığı olmasıdır ve <xref:System.Windows.EventSetter> parçası olması o stilin bile biçimlendirme düzeyinde kod yeniden kullanımını yükseltir. Ayrıca, bir <xref:System.Windows.EventSetter> işleyicileri bir adım daha genel uygulama ve sayfa biçimlendirmeyi yöntem adlarını soyutlar.  
  
 Yönlendirilmiş olay ve animasyon özelliklerini bir araya getiren başka bir özel sözdizimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olduğu bir <xref:System.Windows.EventTrigger>. Olduğu gibi <xref:System.Windows.EventSetter>, yalnızca yönlendirilmiş olaylar için kullanılabilir bir <xref:System.Windows.EventTrigger>. Genellikle, bir <xref:System.Windows.EventTrigger> stili bir parçası olarak bildirilmiş ancak bir <xref:System.Windows.EventTrigger> sayfa düzeyi öğelerde kapsamında bildirilebilir <xref:System.Windows.FrameworkElement.Triggers%2A> koleksiyonuna veya bir <xref:System.Windows.Controls.ControlTemplate>. Bir <xref:System.Windows.EventTrigger> belirtmenize olanak tanıyan bir <xref:System.Windows.Media.Animation.Storyboard> gönderilmiş bir olay, bir öğedeki yolunu eriştiğinde çalıştırmaları bildirdiğini bir <xref:System.Windows.EventTrigger> bu olay için. Avantajı, bir <xref:System.Windows.EventTrigger> yalnızca olay işleme ve başlatmak bu neden üzerinden olan mevcut bir görsel taslağı bir <xref:System.Windows.EventTrigger> film şeridini ve çalışma zamanı davranışını üzerinde daha fazla denetim sağlar. Daha fazla bilgi için [bir film şeridini denetlemek için olay tetikleyicileri kullanma](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Yönlendirilmiş olaylar hakkında daha fazla bilgi  
 Bu konuda, temel kavramları açıklayan ve yönergeler konusunda ve yanıtlamak için zaten yönlendirilmiş olaylar çeşitli temel öğeler ve denetimlerin olduğunda sunan perspektifinden yönlendirilmiş olaylar çoğunlukla anlatılmaktadır. Ancak, tüm gerekli desteğiyle birlikte, özel olay veri sınıfları ve temsilciler gibi özel sınıfınıza kendi yönlendirilmiş olay oluşturabilirsiniz. Yönlendirilmiş olay sahibi herhangi bir sınıf olabilir, ancak yönlendirilmiş olaylar tarafından gerçekleştirilen ve tarafından işlenen <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> faydalı olması için türetilmiş sınıflar. Özel olaylar hakkında daha fazla bilgi için bkz. [özel yönlendirilmiş olay oluşturma](how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Girişe Genel Bakış](input-overview.md)
- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [WPF İçinde Ağaçlar](trees-in-wpf.md)
- [Zayıf Olay Desenleri](weak-event-patterns.md)
