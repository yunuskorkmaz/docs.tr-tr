---
title: "Gönderilmiş Olaylara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22ce2611afa2a3b2b06b7d378479e5ffd2f744f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="routed-events-overview"></a>Gönderilmiş Olaylara Genel Bakış
Bu konu yönlendirilmiş olaylar kavramını açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Bu konuda, yönlendirilmiş olaylar terimleri tanımlar, açıklar öğeleri ağacıyla yönlendirilmiş yönlendirilmiş olayları nasıl yönlendirilmiş olaylar nasıl işleneceğini özetler ve kendi özel yönlendirilmiş olaylar oluşturmak nasıl tanıtır.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu temel bilgiye sahip olduğunuzu varsayar [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ve nesne odaklı programlama, hem de nasıl kavramı arasındaki ilişkileri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ağaç olarak kavramsallaştırılabileceği. Bu konudaki örnekleri takip etmek için ayrıca anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve nasıl yazıldığını çok temel bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları veya sayfaları. Daha fazla bilgi için bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) ve [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Yönlendirilmiş olay nedir?  
 Düşünebilirsiniz yönlendirilmiş olayları işlev ya da uygulama açısından ya da. Bazı kişiler birini veya diğer tanım daha kullanışlı çünkü her iki tanımları burada sunulur.  
  
 İşlev tanımı: yönlendirilmiş olay işleyicileri bir öğe ağacında birden çok dinleyici yerine yalnızca olayı nesneyi çağırabileceği olay türüdür.  
  
 Uygulama tanımı: yönlendirilmiş bir olaydır bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bir örneği tarafından yedeklenen olay <xref:System.Windows.RoutedEvent> sınıfı ve tarafından işlenen [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.  
  
 Tipik bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması birçok öğe içerir. Kod içinde oluşturulan ya da bildirilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], her bir öğe ağaç ilişkisindeki bu öğeleri yok. Olay yolu olay tanımı bağlı olarak iki yönlü birinde ilerleyebilir, ancak genellikle rota kaynak öğeden hareket eder ve "öğe ağacı köküne (genellikle bir sayfaya veya bir pencereyi) ulaşana kadar sonra Yukarı öğe ağacıyla köpürür". DHTML nesne modeliyle daha önce çalıştıysa bu kabarcıklanma kavramı size tanıdık olabilir.  
  
 Aşağıdaki basit öğe ağacını göz önünde bulundurun:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Bu öğe ağacı aşağıdakine benzer üretir:  
  
 ![Evet, Hayır ve İptal düğmeleri](../../../../docs/framework/wpf/advanced/media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 Kaynağı bu Basitleştirilmiş öğe ağacında bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay biridir <xref:System.Windows.Controls.Button> öğeleri ve hangisi <xref:System.Windows.Controls.Button> tıklandığını olay işleme fırsatına sahip ilk öğedir. Ancak bağlı hiçbir işleyici <xref:System.Windows.Controls.Button> olay yukarı çok Kabarcık sonra olayı'nda görür <xref:System.Windows.Controls.Button> olan öğe ağacında üst <xref:System.Windows.Controls.StackPanel>. Potansiyel olarak, olay balonları <xref:System.Windows.Controls.Border>ve daha sonra (gösterilmez) öğe ağacı sayfa kökünün ötesine.  
  
 Diğer bir deyişle, bu olay yolu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay:  
  
 Düğme StackPanel-->--> kenarlık-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Yönlendirilmiş olaylar için üst düzey senaryolar  
 Yönlendirilmiş olay kavramını motive senaryoları kısa bir özeti aşağıda verilmiştir ve tipik bir neden [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay bu senaryoları için yeterli değil:  
  
 **Denetim oluşturma ve saklama:** çeşitli denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin içerik modeli vardır. Örneğin, görüntüyü içine koyabilirsiniz bir <xref:System.Windows.Controls.Button>, düğmenin görsel ağaç etkili bir şekilde genişleten. Ancak, eklenen görüntünün bir düğme yanıt vermesine neden isabet sınama davranışını bölmeniz gerekir olmayan bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> içeriği, görüntünün teknik bir parçası olan pikseller üzerinde kullanıcı olsa bile.  
  
 **Tek işleyicinin ek noktaları:** içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], birçok öğeden geçirilen olayları işlemek için birden çok kez aynı işleyici eklemeniz gerekir. Yönlendirilmiş olaylar bu işleyici önceki örnekte gösterildiği gibi yalnızca bir kez eklemek etkinleştirmeniz ve işleyici mantığını nereden olay gerekirse geldiğini belirlemek için kullanın. Örneğin, bu işleyici daha önce gösterilen olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Sınıf işleme:** yönlendirilmiş olaylar sınıf tarafından tanımlanan statik bir işleyici izin verir. Bu sınıfı işleyici herhangi bir bağlı örnek işleyicileri için önce bir olay işleme fırsatına sahip.  
  
 **Yansıma olmadan bir olay başvuran:** belirli kod ve biçimlendirme teknikleri belirli bir olay tanımlamak için bir yol gerekir. Yönlendirilmiş olay oluşturur bir <xref:System.Windows.RoutedEvent> statik veya çalışma zamanı yansıması gerektirmeyen güvenilir olay tanımlaması tekniği sağlayan bir tanımlayıcı olarak alan.  
  
### <a name="how-routed-events-are-implemented"></a>Yönlendirilmiş olaylar nasıl uygulanır  
 Yönlendirilmiş olay bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bir örneği tarafından yedeklenen olay <xref:System.Windows.RoutedEvent> sınıfı ve kayıtlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. <xref:System.Windows.RoutedEvent> Kayıttan alınan örnek olarak korunur genellikle bir `public` `static` `readonly` alan kaydeder ve bu nedenle yönlendirilmiş olay "sahibi" sınıf üyesi. Aynı adlı bağlantı [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] (bazen "sarmalayıcı" olayı olarak adlandırılır) olay geçersiz kılınarak `add` ve `remove` uygulamaları için [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay. Normalde, `add` ve `remove` ekleme ve kaldırma olay işleyicileri için uygun dile özgü olay sözdizimini kullanan örtülü varsayılan olarak kalır. Yönlendirilmiş olay yedekleme ve bağlantı mekanizmasını nasıl bağımlılık özelliği kavramsal olarak benzer bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] tarafından yedeklenen özelliği <xref:System.Windows.DependencyProperty> sınıfı ve kayıtlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi.  
  
 Aşağıdaki örnek, özel bir bildirimi gösterir `Tap` kayıt ve riskini dahil olmak üzere, yönlendirilmiş olay <xref:System.Windows.RoutedEvent> tanımlayıcı alanı ve `add` ve `remove` uygulamaları için `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Yönlendirilmiş olay işleyicileri ve XAML  
 Kullanarak bir olay işleyicisi eklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay adı olay dinleyicisi olan öğe üzerinde bir özniteliği olarak bildirin. Özniteliğin değeri arka plan kod dosyasının kısmi sınıfında mevcut olmalıdır, uygulanan işleyici yöntemi adıdır.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Standart ekleme sözdizimi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay işleyicileri olduğundan yönlendirilmiş olay işleyicileri için aynı işleyicilere gerçekten eklediğiniz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] yönlendirilmiş olay uygulaması bulunan olay sarmalayıcı altında. Olay işleyicileri ekleme hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Yönlendirme stratejileri  
 Yönlendirilmiş üç yönlendirme stratejiler birini olayları kullanın:  
  
-   **Tırmanmasını:** olay kaynağı üzerindeki olay işleyicileri çağrılır. Yönlendirilmiş olay öğesi ağaç kök ulaşmasını kadar art arda üst öğeler için sonra yönlendirir. Yönlendirilmiş olayların çoğu kabarcıklanma yönlendirme stratejisi kullanın. Kabarcıklanma yönlendirilmiş olaylar genellikle ayrı denetimleri veya diğer kullanıcı Arabirimi öğeleri giriş veya durum değişiklikleri bildirmek için kullanılır.  
  
-   **Doğrudan:** yalnızca source öğesi yanıt işleyicileri çağırma fırsatı verilir. Bu ", üretim için" paraleldir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] olaylar için kullanır. Ancak, standart bir aksine [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay, yönlendirilmiş olaylar sınıf işlemeyi destekler doğrudan (ilerideki bölümde sınıf işleme açıklanmıştır) tarafından kullanılan ve <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger>.  
  
-   **Tünel oluşturma:** başlangıçta, olay işleyicileri öğesi ağaç kökü çağrılır. Yönlendirilmiş olay sonra art arda alt öğeleri (yönlendirilmiş olayı öğesi) yönlendirilmiş olay kaynağı olan düğüm öğe doğru yol boyunca yönlendir dolaşır. Tünel yönlendirilmiş olayları genellikle kullanılan veya birleştirme bir denetim için bir parçası olarak olaylar bileşik bölümlerinden kasıtlı olarak gizlenen veya tam denetime özgü olaylar değiştirilmiştir şekilde işlenmiş. İçinde sağlanan giriş olayları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle bir tünel/tırmanmasını çifti olarak uygulanan gelir. Tünel olayları da önizleme olayları olarak çiftleri için kullanılan bir adlandırma kuralı nedeniyle adlandırılır.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Yönlendirilmiş olayları neden kullanma?  
 Bir uygulama geliştiricisi olarak, her zaman bilmiyorsanız veya olay işleme yönlendirilmiş olay olarak uygulandığını verdiğiniz gerekmez. Yönlendirilmiş olaylar özel davranışa sahiptir, ancak bu davranışı burada tetiklenir olay öğesi olarak işleniyorsa büyük ölçüde görünmez olur.  
  
 Burada yönlendirilmiş olaylar güçlü olur, önerilen senaryoların herhangi biri kullanılmasıdır: bir ortak kök en yaygın işleyicileri tanımlama birleştirme kendi denetim veya kendi özel denetim sınıfınızı tanımlama.  
  
 Yönlendirilmiş olay dinleyicileri ve yönlendirilmiş olay kaynakları, hiyerarşilerinde yaygın bir olayı paylaşmak gerekmez. Tüm <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> herhangi bir yönlendirilmiş olay için bir olay dinleyicisi olabilir. Bu nedenle, çalışma boyunca kullanılabilir yönlendirilmiş olayların tam kümesini kullanabilirsiniz [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] "uygulama içindeki farklı öğelerin olay bilgisi alışverişi yapabildiği bir kavramsal arabirimi" olarak ayarlayın. Bu "arabirimi" kavramı yönlendirilmiş olaylar için özellikle girdi olayları için geçerlidir.  
  
 Olayı için olay verilerini her öğeye rotadaki perpetuated çünkü yönlendirilmiş olaylar öğe ağacı üzerinden iletişim kurmak için de kullanılabilir. Bir öğe şeyin olay verileri değiştirebilir ve bu değişiklik rotadaki sonraki öğeye kullanılabilir olacaktır.  
  
 Yönlendirme en boy dışındaki diğer iki nedeni vardır verilen herhangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay olarak gerçekleştirilen bir standart yerine yönlendirilmiş olay [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay. Kendi olaylarınızı uyguluyorsanız, bu ilkeler de düşünebilirsiniz:  
  
-   Belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil ve şablon özellikler gibi <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger> yönlendirilmiş olay olmada başvurulan olayı gerektirir. Bu, daha önce bahsedilen olay tanımlayıcısı senaryosudur.  
  
-   Yönlendirilmiş olay işleme mekanizması sınıf herhangi bir kayıtlı örnek işleyicileri onlara erişmeden önce yönlendirilmiş olayları işleme fırsatına sahip statik yöntemler yapabildiği belirtebilir bir sınıf destekler. Sınıfınıza örneğindeki bir olay işleme tarafından yanlışlıkla atlanması olamaz olay denetimli sınıfı davranışları zorunlu kılabilir denetim tasarımında çok kullanışlı olmasıdır.  
  
 Her yukarıdaki konuları, bu konunun ayrı bir bölümde ele alınmıştır.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Ekleme ve bir olay işleyicisi için yönlendirilmiş olay uygulama  
 Bir olay işleyicisi eklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], sadece olay adı bir öznitelik olarak bir öğe ekleyin ve aşağıdaki örnekteki gibi uygun bir temsilci uygulayan olay işleyicisi adı olarak öznitelik değerini ayarlayın.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor`işleyen kodu içeren uygulanmış işleyicinin adıdır <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. `b1SetColor`olarak aynı imzaya sahip olmalıdır <xref:System.Windows.RoutedEventHandler> olay işleyicisi temsilcisidir temsilci için <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. Tüm yönlendirilmiş olay işleyici temsilcileri ilk parametresi olduğu için olay işleyicisini eklenir ve ikinci parametre olaya ilişkin veriler belirtir öğesi belirtir.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler>temel yönlendirilmiş olay işleyicisi temsilcisidir. Özel olay verilerinin aktarılabilmesi özelleştirilmiş belirli denetimler veya senaryolar yönlendirilmiş olaylar için yönlendirilmiş olay işleyicileri için kullanılacak temsilcileri de daha özelleştirilmiş olabilirler. Örneğin, ortak bir giriş senaryosunda, işleyebilirsiniz bir <xref:System.Windows.UIElement.DragEnter> yönlendirilmiş olay. İşleyicinizi uygulamalıdır <xref:System.Windows.DragEventHandler> temsilci. En belirgin temsilciyi kullanarak da işleyebilirsiniz <xref:System.Windows.DragEventArgs> işleyici ve okuma <xref:System.Windows.DragEventArgs.Data%2A> sürükleme işleminin Pano yükünü içeren özellik.  
  
 Olay işleyici kullanarak bir öğe eklemek nasıl tam bir örnek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [yönlendirilmiş olayını işle](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
 Kod içinde oluşturulan bir uygulamada yönlendirilmiş olay işleyicisi ekleme basittir. Yönlendirilmiş olay işleyicileri her zaman bir yardımcı yöntem eklenebilir <xref:System.Windows.UIElement.AddHandler%2A> (için var olan yedekleme çağıran aynı yöntemi `add`.) Ancak, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olaylar genellikle yedekleme uygulamalarına sahiptir `add` ve `remove` dile özgü olay sözdizimi tarafından eklenecek yönlendirilmiş olaylar için işleyiciler izin mantığı daha sezgisel sözdizimi olduğu yardımcı yöntemi. Yardımcı yöntemi kullanım örneği verilmiştir:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 Sonraki örnekte gösterildiği [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] işleci sözdizimi ([!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] biraz farklı işlecinin sözdizimi başvurusunun kaldırılmasının kendi işleme nedeniyle oluşur):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Kodda bir olay işleyicisi ekleme örneği için bkz: [kullanarak bir olay işleyicisini eklemek](../../../../docs/framework/wpf/advanced/how-to-add-an-event-handler-using-code.md).  
  
 Kullanıyorsanız [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)], aynı zamanda `Handles` işleyicileri işleyici bildirimlerinin bir parçası eklemek için anahtar sözcüğü. Daha fazla bilgi için bkz: [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>İşlenmiş kavramı  
 Bir ortak olay verileri temel sınıfı, tüm yönlendirilmiş olaylar paylaşmak <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs>tanımlar <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği bir Boole değeri alır. Amacı <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği olan herhangi bir olay işleyicisini yönlendirilmiş olay olarak işaretlemek için yol boyunca etkinleştirmek için *ele*, değerini ayarlayarak <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true`. Yol boyunca tek bir öğede işleyici tarafından işlendikten sonra paylaşılan olay verileri, yol boyunca her dinleyicisi yeniden bildirilir.  
  
 Değeri <xref:System.Windows.RoutedEventArgs.Handled%2A> etkiler yönlendirilmiş olay bildirilen veya onu ilerledikçe işlenen nasıl yol boyunca daha fazla. Varsa <xref:System.Windows.RoutedEventArgs.Handled%2A> olan `true` olay verileri yönlendirilmiş olay ve diğer öğeler üzerinde bu yönlendirilmiş olayı dinlemek işleyicileri için genellikle artık bu belirli olay örneği için çağrılır. Bu işleyiciler için hem de bağlı geçerlidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve gibi dile özgü olay işleyicisi ek sözdizimleri tarafından eklenen işleyiciler için `+=` veya `Handles`. En yaygın işleyici senaryoları için bir olay ayarlanarak işlenmiş olarak işaretleme <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` "tünel yolu ya da kabarcıklanma yolunun, ayrıca rotadaki bir noktada sınıfı işleyici tarafından işlenen herhangi bir olayın da yönlendirmesini durdurur".  
  
 Ancak yapabildiği dinleyicileri hala çalışabilir işleyicileri yönlendirilmiş olaylarına yanıt olarak bir "handledEventsToo" mekanizması yoktur nerede <xref:System.Windows.RoutedEventArgs.Handled%2A> olan `true` olay verisi içinde. Diğer bir deyişle, olay yolu gerçekten işlenmiş olarak olay verisi işaretleyerek durdurulmaz. Yalnızca veya kod handledEventsToo mekanizmasını kullanabilirsiniz bir <xref:System.Windows.EventSetter>:  
  
-   Kodda, genel çalışan dile özgü olay sözdizimini kullanmak yerine [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayları, çağrı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yöntemi <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> işleyicinizi eklemek için. Değerini belirtin `handledEventsToo` olarak `true`.  
  
-   İçinde bir <xref:System.Windows.EventSetter>ayarlayın <xref:System.Windows.EventSetter.HandledEventsToo%2A> özniteliğini `true`.  
  
 Davranış yanı sıra, <xref:System.Windows.RoutedEventArgs.Handled%2A> durumunun yönlendirilmiş olaylar kavramını oluşturduğu <xref:System.Windows.RoutedEventArgs.Handled%2A> nasıl uygulamanızı tasarlayın ve olay işleyici kod yazmanız gerektiği için etkilere sahiptir. Kavramsallaştırabilirsiniz <xref:System.Windows.RoutedEventArgs.Handled%2A> yönlendirilmiş olaylar tarafından gösterilen basit bir protokol olarak. Tam olarak bu protocol kullanma, ancak nasıl yönelik kavramsal tasarım kadar olan değerini <xref:System.Windows.RoutedEventArgs.Handled%2A> kullanılması amaçlanmıştır aşağıdaki gibidir:  
  
-   Yönlendirilmiş olay işlenmiş olarak işaretlenmişse, o yol boyunca diğer öğeler tarafından yeniden yapılması gerekmez.  
  
-   Yönlendirilmiş olay işlenmiş olarak işaretlenmemiş sonra yol boyunca önceki diğer dinleyicileri bir işleyici veya olay verileri işlemek ve ayarlamak için kayıtlı seçerseniz olan işleyicileri kayıt ya da seçmiş olduğunuz <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true`. (Veya doğal geçerli dinleyici rota ilk noktanın mümkündür.) Geçerli dinleyici işleyicileri artık üç olası kurslar eylem vardır:  
  
    -   Hiç eylem yok; Olay işlenmemiş kalır ve olay sonraki dinleyiciye yönlendirir.  
  
    -   Olaya yanıt olarak kod yürütmek, ancak bulguyu gerçekleştirilecek eylem olay işlenmiş olarak işaretleme garanti etmeye önemli değildi. Sonraki dinleyiciye olay yollar.  
  
    -   Olaya yanıt olarak kodu yürütün. Olay gerçekleştirilecek eylemi işlenmiş olarak işaretleme garanti etmeye önemli olarak kabul edilen çünkü olay işleyicisine geçirilen verileri işlenmiş olarak işaretleyin. Olay hala yönelir sonraki dinleyiciye ancak ile <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` yalnızca kendi olay verileri içindeki `handledEventsToo` dinleyicileri sonraki işleyicileri çağırma fırsatına sahip.  
  
 Bu kavramsal tasarım daha önce bahsedilen yönlendirme davranışı tarafından desteklenir: önceki işleyici yol boyunca zatenayarlanmışolsabileçağrılanyönlendirilmişolaylariçinişleyicileriliştirmekdaha(mümkünolsabilekodveyastilleriçinde)güçtür<xref:System.Windows.RoutedEventArgs.Handled%2A>için `true`.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.RoutedEventArgs.Handled%2A>sınıfı işlenmesini yönlendirilmiş olayları ve olduğu zaman konusunda öneriler uygun yönlendirilmiş olay olarak işaretlemek için <xref:System.Windows.RoutedEventArgs.Handled%2A>, bkz: [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Uygulamalarda, yalnızca ortaya çıkan nesne üzerinde kabarcıklanma yönlendirilmiş olay işlemek ve her olayın yönlendirme özellikleriyle ilgili olmaması için oldukça yaygındır. Ancak, yine yönlendirilmiş olay öğesi ağacı başka bir öğe olasılığına yan etkileri engellemede engellemek için verileri, ayrıca, aynı yönlendirilmiş olay için bağlı bir işleyici sahiptir olay işlenmiş olarak işaretlemek için iyi bir uygulama olur.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Sınıf işleyicileri  
 Bazı şekilde türeyen bir sınıf tanımlıyorsanız, <xref:System.Windows.DependencyObject>, ayrıca tanımlayın ve sınıfınız bildirilen veya devralınmış olay üyesi olan yönlendirilmiş olay işleyicisi sınıfı ekleyin. Sınıf işleyicileri yönlendirilmiş olay yolunu içinde öğe örneğine eriştiğinde, bu sınıfın bir örneğine bağlı olan herhangi bir örnek dinleyici işleyicileri önce çağrılır.  
  
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleriniz yönlendirilmiş belirli olaylar için işleme devralınan sınıf. Bu yönlendirilmiş olay herhangi bir zamanda yükseltilmiş değil, ancak gerçekte işlenmiş sınıfı yapılıyor ve belirli teknikler kullanırsanız, yönlendirilmiş olay hala potansiyel olarak, örnek işleyicileri tarafından işlenebilir dış görünümü verebilir. Ayrıca, birçok temel sınıf ve denetim işleme sınıfı geçersiz kılmak için kullanılan sanal yöntemler kullanıma sunar. İstenmeyen sınıf işleme geçici çalışma konusunda ve özel bir sınıf içinde kendi sınıf tanımlama daha fazla bilgi için bkz: [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>WPF içindeki ekli olaylar  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dili de tanımlar adlı olay özel bir tür bir *ekli olayı*. Ekli olay rasgele bir öğe olarak belirli bir olay için bir işleyici eklemenize olanak tanır. Olay işleme öğesi değil tanımlayın veya ekli olay devralır ve ne olası olayı tetiklenmeden nesne ne de hedef işleme örneği tanımlayın veya gerekir aksi takdirde bu olay bir sınıf üyesi olarak "sahip".  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş sistemi ekli olaylar kapsamlı olarak kullanır. Ancak, bu ekli olayların neredeyse tüm temel öğeleri aracılığıyla iletilir. Giriş olayları sonra eşdeğer ekli olmayan yönlendirilmiş temel öğe sınıfı üyeleri olan olaylar gibi görünür. Örneğin, arka plandaki olay bağlı <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> daha kolayca herhangi verilen işlenebilir <xref:System.Windows.UIElement> kullanarak <xref:System.Windows.UIElement.MouseDown> üzerindeki <xref:System.Windows.UIElement> ekli olay sözdizimiyle baş yerine içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod.  
  
 İçindeki ekli olaylar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [bağlı olaylara genel bakış](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>XAML'de yetkili olay adları  
 Benzer başka bir sözdizimi kullanımı *typename*. *eventname* olay sözdizimi iliştirilmiş ancak kesinlikle bakıldığında ekli olay kullanımını alt öğeleri tarafından gerçekleştirilen yönlendirilmiş olaylar için işleyiciler taktığınızda değil. Ortak üst üye olarak ilgili yönlendirilmiş olay olmasa bile olay yönlendirmesi avantajlarından yararlanmak için ortak bir üst işleyicileri iliştirin. Bu örneği yeniden göz önünde bulundurun:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 İşleyici burada eklenir üst öğe dinleyicisi İşte bir <xref:System.Windows.Controls.StackPanel>. Ancak, bildirildi ve tarafından gerçekleştirilen yönlendirilmiş bir olay işleyicisi ekleme <xref:System.Windows.Controls.Button> sınıfı (<xref:System.Windows.Controls.Primitives.ButtonBase> aslında, ancak kullanılabilir <xref:System.Windows.Controls.Button> devralma yoluyla). <xref:System.Windows.Controls.Button>"olay, ancak herhangi bir ağa bağlanması herhangi bir yönlendirilmiş olay yönlendirilmiş olay sistem izinleri işleyicileri sahibi" <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> dinleyicileri için aksi bağlayamıyor örneği dinleyicisi bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay. Bu yetkili olay öznitelik adları için varsayılan xmlns ad alanı genellikle varsayılandır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns ad alanı, ancak ayrıca belirtebilirsiniz özel yönlendirilmiş olaylar için önekli ad alanları. Xmlns hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>WPF giriş olayları  
 İçerisinde yönlendirilmiş olayların sık bir uygulaması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] girdi olayları için bir platformdur. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tünel yönlendirilmiş adları "Önizleme" sözcüğüyle öneki kurala göre olaylar. Giriş olayları çiftler halinde kabarcıklanma olayı ve diğer tünel olayı olmak biriyle genellikle gelir. Örneğin, <xref:System.Windows.ContentElement.KeyDown> olay ve <xref:System.Windows.ContentElement.PreviewKeyDown> sahip aynı imza olay kabarcıklanma giriş olayı olmasıyla eski ile ve ikinci tünel giriş olayı. Bazen, giriş olaylarını yalnızca kabarcıklanma sürümü veya belki yalnızca doğrudan yönlendirilmiş sürümü yüklü. Belgelerde, yönlendirilmiş olay konuları bu tür yönlendirilmiş olaylar mevcutsa ve yönetilen başvuru sayfaları bölümlerde her yönlendirilmiş olay yönlendirme stratejisi açıklamak alternatif yönlendirme stratejileri benzer yönlendirilmiş olaylarla çapraz başvuru.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Böylece girişi, fare Düğme basma gibi tek bir kullanıcı eyleminden sırayla çiftinin her iki yönlendirilmiş olaylar oluşturacak çiftler halinde gelir giriş olaylarını uygulanır. İlk olarak, tünel olayı tetiklenir ve yolunu dolaşır. Daha sonra kabarcıklanma olayı tetiklenir ve yolunu dolaşır. İki olay tam anlamıyla çünkü aynı olay veri örneğini paylaşırlar <xref:System.Windows.UIElement.RaiseEvent%2A> kabarcıklanma olayını uygulayan sınıfa yöntem çağrısında tünel olayından olay verilerini dinler ve yeni oluşturulan olay içinde yeniden kullanır. Tünel olay işleyicileri ile dinleyicileri sahip yönlendirilmiş olayı işlenmiş işaretlemek için ilk fırsat (sınıf işleyicileri ilk olarak, daha sonra örnek işleyiciler). Bir öğenin tünel yol boyunca yönlendirilmiş olay işlenmiş olarak işaretlerse, zaten işlenen olay verileri kabarcıklanma olayı için gönderilir ve eşdeğeri giriş olaylarını tırmanmasını iliştirilen tipik işleyiciler çağrılmaz. Dış görünümleri işlenmiş kabarcıklanma olayı değil bile oluşturuldu gibi olacaktır. Bu işleme davranışı burada tüm isabet testi giriş olaylarını veya bileşik parçalarının yerine son denetiminiz tarafından bildirilecek giriş olaylarını odak tabanlı bağlı isteyebilirsiniz denetim birleştirmesini için yararlıdır. Son denetim öğesi birleştirme kökte yakındır ve bu nedenle öncelikle ve belki de bir "Bu yönlendirilmiş olayı denetimi yedekler kodun bir parçası daha fazla denetime özgü olay ile değiştirmek için" tünel olayını işle fırsat sınıfına sahip sınıf.  
  
 Giriş olayı works işlemesinin nasıl çizim, aşağıdaki giriş olayı örneği göz önünde bulundurun. Aşağıdaki ağaç çizimde, `leaf element #2` kaynağı, hem de bir `PreviewMouseDown` ve ardından bir `MouseDown` olay.  
  
 ![Olay yönlendirme diyagramı](../../../../docs/framework/wpf/advanced/media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Giriş olayı Tırmanmasını ve tünel oluşturma  
  
 Olay işleme sırasını aşağıdaki gibidir:  
  
1.  `PreviewMouseDown`(kök öğe üzerinde tünel).  
  
2.  `PreviewMouseDown`(Ara öğe #1 tünel).  
  
3.  `PreviewMouseDown`(kaynak öğe #2 Tünel).  
  
4.  `MouseDown`(kaynak öğe #2 kabarcık).  
  
5.  `MouseDown`(Ara öğe #1 kabarcık).  
  
6.  `MouseDown`(kök öğe üzerinde kabarcık).  
  
 Yönlendirilmiş olay işleyici temsilcisi iki nesne başvuru sağlar: olay ve burada işleyicinin çağrıldığı nesne yükseltilmiş nesne. İşleyicinin burada çağrıldığı nesnesi tarafından bildirilen nesnesidir `sender` parametresi. Burada olayın ilk oluşturulduğu nesne tarafından bildirilen <xref:System.Windows.RoutedEventArgs.Source%2A> olay verilerini bir özellik. Yönlendirilmiş olay hala oluşturulabilir ve bu durumda aynı nesne tarafından işlenen `sender` ve <xref:System.Windows.RoutedEventArgs.Source%2A> (Bu, adım 3 ve 4 olay işleme örneği listesindeki durumuyla) özdeş.  
  
 Tünel oluşturma ve tırmanmasını nedeniyle üst öğeler giriş olaylarını almasını nerede <xref:System.Windows.RoutedEventArgs.Source%2A> kendi alt öğelerini biridir. Kaynak öğenin ne olduğunu bilmeniz önemlidir, erişerek source öğesi tanımlayabilirsiniz <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği.  
  
 Genellikle, giriş olayı işaretlendikten sonra <xref:System.Windows.RoutedEventArgs.Handled%2A>, daha fazla işleyici çağrılamaz. Genellikle, giriş olaylarını bir işleyici giriş olayı anlamı, uygulamaya özgü mantıksal işlenmesini gideren çağrılır hemen işlenmiş olarak işaretlemeniz gerekir.  
  
 Özel durum hakkında genel bu bildirimi <xref:System.Windows.RoutedEventArgs.Handled%2A> durumudur kasıtlı olarak yoksaymak için kayıtlı olan olay işleyicileri giriş <xref:System.Windows.RoutedEventArgs.Handled%2A> olay verileri durumunu yol boyunca hala çağrıldığı. Daha fazla bilgi için bkz: [önizleme olayları](../../../../docs/framework/wpf/advanced/preview-events.md) veya [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Tünel oluşturma ve kabarcıklanma olayları ve sıralı arasında paylaşılan olay veri modeli ilk olayları tırmanmasını tünel oluşturma, genellikle tüm yönlendirilmiş olaylar için doğrudur bir kavram değildir. Davranış özellikle olduğunu seçilmesiyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olay çiftlerini oluşturmak ve bağlamak giriş aygıtları seçin. Giriş olaylarınızı uygulama Gelişmiş bir senaryo olsa da bu modeli, kendi giriş olaylarını izlemek de seçebilirsiniz.  
  
 Sınıf-genellikle bu denetim içinde belirli bir kullanıcı odaklı giriş olay anlamı tanımlayarak ve yeni bir olay oluşturma amacıyla giriş belirli olayları işlemesini belirli sınıfları seçin. Daha fazla bilgi için bkz: [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Giriş ve tipik uygulama senaryoları içinde giriş ve olayların nasıl etkileşim hakkında daha fazla bilgi için bkz: [giriş genel bakış](../../../../docs/framework/wpf/advanced/input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters ve EventTriggers  
 Önceden bildirilmiş dahil stillerinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay işlemesi biçimlendirmede sözdizimini kullanarak bir <xref:System.Windows.EventSetter>. Stil uygulandığında, başvurulan işleyici stilde örneğine eklenir. Bildirebilirsiniz bir <xref:System.Windows.EventSetter> yalnızca yönlendirilmiş olay için. Bir örnek verilmiştir. Unutmayın `b1SetColor` Burada başvurulan bir arka plan kod dosyasına yöntemidir.  
  
 [!code-xaml[EventOvwSupport#XAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Burada kazanılan avantajı stili, uygulamanızda herhangi bir düğmeye uygulanabilecek diğer bilgileri büyük bir bölümünü bulunma olasılığı olmasıdır ve <xref:System.Windows.EventSetter> bir parçası olması, stilini bile biçimlendirme düzeyinde kodu yeniden kullanma yükseltir. Ayrıca, bir <xref:System.Windows.EventSetter> yöntemi adlarını işleyicileri bir adım daha fazla genel uygulama ve sayfa biçimlendirme soyutlar.  
  
 Yönlendirilmiş olay ve animasyon özelliklerini bir araya getiren başka bir özel sözdizimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan bir <xref:System.Windows.EventTrigger>. İle <xref:System.Windows.EventSetter>, yalnızca yönlendirilmiş olaylar için kullanılabilir bir <xref:System.Windows.EventTrigger>. Genellikle, bir <xref:System.Windows.EventTrigger> bir stil bir parçası olarak bildirilmiş ancak bir <xref:System.Windows.EventTrigger> sayfa düzeyi öğelerde parçası olarak bildirilebilir <xref:System.Windows.FrameworkElement.Triggers%2A> koleksiyonu veya bir <xref:System.Windows.Controls.ControlTemplate>. Bir <xref:System.Windows.EventTrigger> belirtmenize olanak tanıyan bir <xref:System.Windows.Media.Animation.Storyboard> yönlendirilmiş olay, bir öğedeki yolunu eriştiğinde çalıştırmalarını bildirir bir <xref:System.Windows.EventTrigger> bu olay için. Avantajı, bir <xref:System.Windows.EventTrigger> yalnızca olay işleme ve başlayacak şekilde neden üzerinden olan mevcut bir film şeridi bir <xref:System.Windows.EventTrigger> film şeridi ve çalışma zamanı davranışını daha iyi denetim sunar. Daha fazla bilgi için bkz: [bir film şeridi sonra başlar denetlemek için olay tetikleyicileri kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Yönlendirilmiş olaylar hakkında daha fazla bilgi  
 Bu konuda, temel kavramları açıklayan ve kılavuz nasıl ve yanıtlamak için zaten yönlendirilmiş olaylar çeşitli temel öğeleri ve denetimleri olduğunda sunumu açısından yönlendirilmiş olaylar çoğunlukla anlatılmaktadır. Ancak, özel sınıfınızın desteğinin yanı sıra tüm gerekli, özelleştirilmiş olay veri sınıfları ve temsilciler gibi kendi yönlendirilmiş olay oluşturabilirsiniz. Yönlendirilmiş olay sahibi herhangi bir sınıf olabilir, ancak yönlendirilmiş olaylar tarafından gerçekleştirilen ve tarafından işlenen <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> faydalı olması için türetilmiş sınıfları. Özel olaylar hakkında daha fazla bilgi için bkz: [özel yönlendirilmiş olay oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.EventManager>  
 <xref:System.Windows.RoutedEvent>  
 <xref:System.Windows.RoutedEventArgs>  
 [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Zayıf Olay Desenleri](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)
