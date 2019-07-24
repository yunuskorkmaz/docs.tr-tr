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
ms.openlocfilehash: 24fa283ec0c1fef2023845df0a05c3f1ebf5df06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400757"
---
# <a name="routed-events-overview"></a>Gönderilmiş Olaylara Genel Bakış

Bu konu, içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yönlendirilmiş olay kavramını açıklar. Bu konu, yönlendirilmiş olay terminolojisini tanımlar, yönlendirilmiş olayların bir öğe ağacı aracılığıyla nasıl yönlendirildiğini açıklar, yönlendirilmiş olayları nasıl işleyeceğinizi özetler ve kendi özel yönlendirilmiş olaylarınızı oluşturmayı tanıtır.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Önkoşullar

Bu konu başlığı altında, ortak dil çalışma zamanı (CLR) ve nesne odaklı programlama hakkında temel bilgiye sahip olduğunuz ve öğeler arasındaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ilişkilerin bir ağaç olarak nasıl anlaılabileceği kavramı varsayılmaktadır. Bu konudaki örnekleri izlemek için, ayrıca çok basit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların veya sayfaların nasıl yazılacağını anlamanız ve bilmeniz gerekir. Daha fazla bilgi için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md) Uygulamam ve [xaml 'ye Genel Bakış (WPF)](xaml-overview-wpf.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Yönlendirilmiş olay nedir?

Yönlendirilmiş olayları, işlevsel veya uygulama perspektifinden düşünebilirsiniz. Burada her iki tanım de sunulmuştur, çünkü bazı kişiler bir veya diğer tanımın daha kullanışlı olduğunu fark ettiğinden.

İşlevsel Tanım: Yönlendirilmiş olay, yalnızca olayı oluşturan nesne yerine bir öğe ağacındaki birden çok dinleyiciyle işleyicileri çağırabilen bir olay türüdür.

Uygulama tanımı: Yönlendirilmiş olay, <xref:System.Windows.RoutedEvent> sınıfının bir örneği tarafından desteklenen ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi tarafından işlenen bir clr olayıdır.

Tipik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama birçok öğesi içerir. Kodda oluşturulup açıklanmadığı veya içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bildirildiği, bu öğeler birbirleriyle bir öğe ağacı ilişkisinde bulunur. Olay yolu, olay tanımına bağlı olarak iki yönden birine hareket edebilir, ancak genellikle yol kaynak öğeden geçer ve öğe ağacı köküne (genellikle bir sayfa veya pencere) ulaşana kadar öğe ağacı aracılığıyla "kabarcıklar". Bu kabarcıklanma kavramı, daha önce DHTML nesne modeliyle çalıştıysanız size tanıdık gelebilir.

Aşağıdaki basit öğe ağacını göz önünde bulundurun:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Bu öğe ağacı aşağıdakine benzer bir şey üretir:

![Evet, hayır ve iptal düğmeleri](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

Bu basitleştirilmiş öğe ağacında, bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayın kaynağı <xref:System.Windows.Controls.Button> öğelerden biridir ve <xref:System.Windows.Controls.Button> tıklandığı, olayı işleme fırsatına sahip olan ilk öğedir. Ancak olay üzerinde işlem yapmak için <xref:System.Windows.Controls.Button> iliştirilen bir işleyici yoksa, olay, öğe <xref:System.Windows.Controls.StackPanel>ağacında yukarı doğru bir <xref:System.Windows.Controls.Button> şekilde kabarcık olur. Potansiyel olarak, olay kabarcıkları <xref:System.Windows.Controls.Border>ve daha sonra öğe ağacının sayfa kökünü (gösterilmez).

Diğer bir deyişle, bu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için olay rotası şu şekilde olur:

Düğme--> StackPanel--> Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Yönlendirilmiş olaylar için üst düzey senaryolar

Aşağıda, yönlendirilmiş olay kavramını motive eden senaryoların kısa bir özeti ve tipik bir CLR olayının Bu senaryolar için yeterli olmadığı hakkında genel bir Özet verilmiştir:

**Denetim oluşturma ve kapsülleme:** İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli denetimlerin zengin içerik modeli vardır. Örneğin, bir görüntüsünü, düğmenin görsel ağacını etkin bir şekilde <xref:System.Windows.Controls.Button>genişleten bir resim içine yerleştirebilirsiniz. Ancak, eklenen görüntü, Kullanıcı teknik olarak görüntünün parçası olan piksellere tıklasa bile, bir düğmenin içeriğine yanıt vermesine <xref:System.Windows.Controls.Primitives.ButtonBase.Click> neden olan isabet testi davranışını bozmamalıdır.

**Tekil işleyici ek noktaları:** ' [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]De, birden çok öğeden çıkarılan olayları işlemek için aynı işleyiciyi birden çok kez iliştirmeye ihtiyacınız vardır. Yönlendirilmiş olaylar, önceki örnekte gösterildiği gibi, bu işleyiciyi yalnızca bir kez iliştirmeyi sağlar ve gerekirse olayın nereden geldiğini tespit etmek için işleyici mantığını kullanır. Örneğin, bu, daha önce gösterilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]işleyici olabilir:

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Sınıf işleme:** Yönlendirilmiş olaylar, sınıfı tarafından tanımlanan statik işleyiciye izin verir. Bu sınıf işleyicisinin, ekli örnek işleyicilerinin kullanabilmesi için önce bir olayı işleme fırsatı vardır.

**Yansıma olmadan bir olaya başvurma:** Belirli kod ve biçimlendirme teknikleri belirli bir olayı tanımlamak için bir yol gerektirir. Yönlendirilmiş olay, statik veya <xref:System.Windows.RoutedEvent> çalışma zamanı yansıması gerektirmeyen sağlam bir olay tanımlama tekniği sağlayan tanımlayıcı olarak bir alan oluşturur.

### <a name="how-routed-events-are-implemented"></a>Yönlendirilmiş olaylar nasıl uygulanır

Yönlendirilmiş olay, <xref:System.Windows.RoutedEvent> sınıfının bir örneği tarafından desteklenen ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemine kaydedilen bir clr olayıdır. Kayıt işleminden elde edilen `public` `static` `readonly` örnek genellikle, yönlendirilmiş olayı kaydeden ve bu nedenle "sahip olunan" sınıfının alan üyesi olarak tutulur. <xref:System.Windows.RoutedEvent> Aynı adlı CLR olayına bağlantı (bazen "sarmalayıcı" olayı), CLR olayının `add` ve `remove` uygulamaları geçersiz kılınarak yapılır. Genellikle, `remove` ve bu olayın işleyicilerini eklemek ve kaldırmak için dile özgü uygun olay sözdizimini kullanan örtülü bir varsayılan olarak bırakılır. `add` Yönlendirilmiş olay yedekleme ve bağlantı mekanizması, bağımlılık özelliğinin <xref:System.Windows.DependencyProperty> sınıf tarafından desteklenen ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemine kaydedilen bir CLR özelliği olan kavramsal olarak benzerdir.

`Tap` Aşağıdaki örnek, <xref:System.Windows.RoutedEvent> tanımlayıcı alanın `add` kaydı ve pozlaması, `Tap` clr olayı için ve `remove` uygulamaları da dahil olmak üzere özel bir yönlendirilmiş olaya yönelik bildirimi gösterir.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Yönlendirilmiş olay Işleyicileri ve XAML

Kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir olaya bir işleyici eklemek için, olay adını olay dinleyicisi olan öğe üzerinde bir öznitelik olarak bildirirsiniz. Özniteliğin değeri, uygulanan işleyici yönteminizin, arka plan kod dosyasının kısmi sınıfında bulunması gereken addır.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

Standart CLR olay işleyicilerini eklemek için sözdizimi,aşağıdakiyönlendirilmişolayuygulamalarınasahipolanCLRolaysarmalayıcıyagerçektenişleyicilereklediğiniziçin,yönlendirilmişolayişleyicilerinieklemeiçinaynıdır.[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olay işleyicilerini ekleme hakkında daha fazla bilgi için bkz. [xaml genel bakış (WPF)](xaml-overview-wpf.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Yönlendirme stratejileri

Yönlendirilmiş olaylar üç yönlendirme stratejisinden birini kullanır:

- **Tırmanma** Olay kaynağındaki olay işleyicileri çağrılır. Yönlendirilmiş olay daha sonra öğe ağacı köküne ulaşıncaya kadar art arda gelen üst öğelere yönlendirir. Çoğu yönlendirilmiş olay, kabarcıklanma yönlendirme stratejisini kullanır. Kabarcıklanma yönlendirilmiş olayları genellikle farklı denetimlerden veya diğer kullanıcı arabirimi öğelerinden giriş veya durum değişikliklerini raporlamak için kullanılır.

- **DirectSound** Yalnızca kaynak öğeye, yanıt olarak işleyicileri çağırma fırsatı verilir. Bu, olaylar için [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kullanan "yönlendirmeye" benzerdir. Ancak, standart bir CLR olayının aksine, doğrudan yönlendirilmiş olaylar sınıf işlemeyi destekler (sınıf işleme yaklaşan bölümde açıklanmıştır) ve ve <xref:System.Windows.EventSetter> <xref:System.Windows.EventTrigger>tarafından kullanılabilir.

- **Kullanılamayan** Başlangıçta, öğe ağacı kökündeki olay işleyicileri çağrılır. Yönlendirilmiş olay daha sonra, yönlendirilmiş olay kaynağı (yönlendirilmiş olayı oluşturan öğe) olan node öğesine doğru yol boyunca ardışık alt öğeler aracılığıyla bir yol dolaşır. Tünel yönlendirilmiş olayları genellikle bir denetimin birleştirme parçası olarak kullanılır veya işlenir. Bu, bileşik parçalardan gelen olaylar kasıtlı olarak gizlenebilir veya tüm denetime özgü olaylar tarafından değiştirilebilir. Genellikle ' de sunulan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olayları, bir tünel oluşturma/kabarcıklanma çifti olarak uygulanır. Ayrıca, çiftler için kullanılan bir adlandırma kuralı nedeniyle, tünel olayları bazen önizleme olayları olarak adlandırılır.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Neden yönlendirilmiş olayları kullanmalıyım?

Uygulama geliştiricisi olarak, işlemekte olduğunuz olayın yönlendirilmiş olay olarak uygulandığını her zaman bilmeniz gerekmez. Yönlendirilmiş olaylar özel bir davranışa sahiptir, ancak oluşturulduğu öğede bir olayı işliyorsa bu davranış büyük ölçüde görünmez olur.

Önerilen senaryolardan birini kullanıyorsanız, yönlendirilmiş olaylar güçlü hale gelir: ortak bir kökte ortak işleyiciler tanımlama, kendi denetiminizi birleştirme veya kendi özel denetim sınıfınızı tanımlama.

Yönlendirilmiş olay dinleyicileri ve yönlendirilmiş olay kaynakları, hiyerarşide ortak bir olay paylaşmalıdır. Herhangi bir yönlendirilmiş olay için herhangi <xref:System.Windows.UIElement> bir olay dinleyicisi olabilir. <xref:System.Windows.ContentElement> Bu nedenle, çalışma API 'SI kümesi boyunca, uygulamanın farklı öğelerinin olay bilgilerini değiş tokuş edebilir kavramsal bir "arabirim" olarak kullanılabilir olan tüm yönlendirilmiş olaylar kümesini kullanabilirsiniz. Yönlendirilmiş olaylar için bu "arabirim" kavramı özellikle giriş olayları için geçerlidir.

Yönlendirilmiş olaylar, öğe ağacı üzerinden iletişim kurmak için de kullanılabilir, çünkü olayın olay verileri rotadaki her bir öğeye yeniden yönlendirilir. Bir öğe olay verilerinde bir şeyi değiştirebilir ve bu değişiklik rotadaki bir sonraki öğe için kullanılabilir.

Yönlendirme yönü dışında, belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir olayın standart bir clr olayı yerine yönlendirilmiş olay olarak uygulanmasının iki nedeni vardır. Kendi olaylarınızı uygulamadıysanız, şu ilkeleri de göz önünde bulundurmanız gerekebilir:

- Gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belirli stil ve şablon oluşturma özellikleri <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger> başvurulan olayın yönlendirilmiş olay olması gerekir. Bu, daha önce bahsedilen olay tanımlayıcı senaryosudur.

- Yönlendirilmiş olaylar, bir kayıtlı örnek işleyicilerinin erişebilmesi için önce yönlendirilmiş olayları işleme fırsatına sahip statik yöntemler belirtebilir sınıf işleme mekanizmasını destekler. Sınıfınız, bir örnekteki olayı işleyerek yanlışlıkla gizlenemez olay odaklı sınıf davranışlarını zorlayabildiğinden, denetim tasarımında çok yararlı olur.

Yukarıdaki önemli noktalar, bu konunun ayrı bir bölümünde ele alınmıştır.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Yönlendirilmiş bir olay için olay Işleyicisi ekleme ve uygulama

' De [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir olay işleyicisi eklemek için, bir öğeye olay adını bir öznitelik olarak ekleyin ve öznitelik değerini, aşağıdaki örnekte olduğu gibi uygun bir temsilciyi uygulayan olay işleyicisinin adı olarak ayarlamanız yeterlidir.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı işleyen kodu içeren uygulanan işleyicinin adıdır. `b1SetColor`, <xref:System.Windows.RoutedEventHandler> olay<xref:System.Windows.Controls.Primitives.ButtonBase.Click> için olay işleyicisi temsilcisi olan temsilciyle aynı imzaya sahip olmalıdır. Tüm yönlendirilmiş olay işleyicisi temsilcilerinin ilk parametresi, olay işleyicisinin eklendiği öğeyi belirtir ve ikinci parametre olay için verileri belirtir.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler>, temel yönlendirilmiş olay işleyicisi temsilcisidir. Belirli denetimler veya senaryolar için özelleştirilmiş olan yönlendirilmiş olaylar için, yönlendirilmiş olay işleyicileri için kullanılacak temsilciler da daha özelleştirilmiş hale gelebilir, böylece özel olay verilerini iletebilirler. Örneğin, ortak bir giriş senaryosunda, yönlendirilmiş bir <xref:System.Windows.UIElement.DragEnter> olayı işleyebilirsiniz. İşleyiciniz <xref:System.Windows.DragEventHandler> temsilciyi uygulamalıdır. En belirli temsilciyi kullanarak, <xref:System.Windows.DragEventArgs> öğesini işleyicide işleyebilir ve sürükleme işleminin Pano yükünü içeren <xref:System.Windows.DragEventArgs.Data%2A> özelliğini okuyabilirsiniz.

Kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir öğeye olay işleyicisi ekleme hakkında bir örnek için, bkz. [yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).

Kodda oluşturulan bir uygulamaya yönlendirilmiş olay için bir işleyici eklemek basittir. Yönlendirilmiş olay işleyicileri her zaman bir yardımcı yöntem <xref:System.Windows.UIElement.AddHandler%2A> (mevcut yedeklemenin `add`çağırdığı Yöntem) aracılığıyla eklenebilir. Ancak, mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olaylar genellikle, yönlendirilmiş olayların işleyicilerinin `add` , `remove` dile özgü bir olay sözdizimi tarafından eklenmesine izin veren ve mantığın, bu değerden daha sezgisel bir sözdizimi olan yardımcı yöntemi. Yardımcı yönteminin örnek kullanımı aşağıda verilmiştir:

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

Sonraki örnek, C# işleç söz dizimini gösterir (Visual Basic, başvurusunun işlenmesi nedeniyle biraz farklı işleç sözdizimine sahiptir):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Kodda olay işleyicisi ekleme hakkında bir örnek için bkz. [Code kullanarak olay Işleyicisi ekleme](how-to-add-an-event-handler-using-code.md).

Visual Basic kullanıyorsanız, işleyicileri işleyici bildirimlerinin bir parçası olarak eklemek için `Handles` anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Işlenen kavramı

Tüm yönlendirilmiş olaylar ortak bir olay veri tabanı sınıfını <xref:System.Windows.RoutedEventArgs>paylaşır. <xref:System.Windows.RoutedEventArgs>Boole değeri alan özelliği tanımlar. <xref:System.Windows.RoutedEventArgs.Handled%2A> <xref:System.Windows.RoutedEventArgs.Handled%2A> Özelliğinin amacı, ' nin <xref:System.Windows.RoutedEventArgs.Handled%2A> değerini olarak `true`ayarlayarak yönlendirilmiş olayı *işlenmiş*olarak işaretlemek için yol üzerinde herhangi bir olay işleyicisini etkinleştirmektir. Yol üzerinde bir öğede işleyici tarafından işlendikten sonra, paylaşılan olay verileri her bir dinleyiciye yol üzerinde yeniden bildirilir.

Değeri, yönlendirilen <xref:System.Windows.RoutedEventArgs.Handled%2A> bir olayın yol üzerinde daha fazla hareket ettiği şekilde nasıl bildirileceğini veya işleneceğini etkiler. <xref:System.Windows.RoutedEventArgs.Handled%2A> ,Yönlendirilmişbirolayınolayverileriise,diğeröğelerdebuyönlendirilmişolayıdinleyenişleyicilergenelliklebubelirli`true` olay örneği için çağrılmaz. Bu, hem ' de eklenen işleyiciler için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de `+=` veya `Handles`gibi dile özgü olay işleyicisi ek sözdizimleri tarafından eklenen işleyiciler için geçerlidir. En yaygın işleyici senaryolarında, bir olayı bir tünel yolu veya kabarcıklanma rotası <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` "Durdur" olarak işaretleyerek ve ayrıca, bir sınıf işleyicisi tarafından rotadaki bir noktada işlenen herhangi bir olay için, bir olayı ayarıyla işlenen olarak işaretleyin.

Ancak, dinleyicilerinin olay verilerinde <xref:System.Windows.RoutedEventArgs.Handled%2A> olduğu `true` yönlendirilmiş olaylara yanıt olarak işleyicileri hala çalıştırabildiği bir "handledEventsToo" mekanizması vardır. Diğer bir deyişle, olay rotası olay verileri işlenmiş olarak işaretlenerek gerçekten durdurulmaz. HandledEventsToo mekanizmasını yalnızca kodda veya bir <xref:System.Windows.EventSetter>' de kullanabilirsiniz:

- Kodda, genel CLR olayları için çalışacak dile özgü bir olay sözdizimi kullanmak yerine, işleyiciyi eklemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yöntemini <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> çağırın. Değerini `handledEventsToo` olarak`true`belirtin.

- Bir <xref:System.Windows.EventSetter>içinde, <xref:System.Windows.EventSetter.HandledEventsToo%2A> özniteliğini `true`olarak ayarlayın.

' Nin <xref:System.Windows.RoutedEventArgs.Handled%2A> <xref:System.Windows.RoutedEventArgs.Handled%2A> yönlendirilmiş olaylarda durum üretmesinin yanı sıra, kavramı, uygulamanızı tasarlamak ve olay işleyici kodunu yazmak için bazı etkileri vardır. Yönlendirilmiş olaylar tarafından açığa çıkarılan <xref:System.Windows.RoutedEventArgs.Handled%2A> basit bir protokol olarak kavramsa getirebilirsiniz. Bu protokolü nasıl kullanacağınızı tam olarak kullanıyorsunuz, ancak değerinin <xref:System.Windows.RoutedEventArgs.Handled%2A> nasıl kullanılacağına yönelik kavramsal tasarım şu şekildedir:

- Yönlendirilmiş bir olay işlenmiş olarak işaretlenmişse, bu yol üzerindeki diğer öğeler tarafından yeniden işlenmesi gerekmez.

- Yönlendirilmiş bir olay işlenmiş olarak işaretlenmemişse, daha önce yol üzerinde olan diğer dinleyiciler bir işleyiciyi kaydetmemeyi ya da kayıtlı işleyiciler olay verilerini işlemek ve olarak <xref:System.Windows.RoutedEventArgs.Handled%2A> `true`ayarlamak için öğesini seçti. (Veya, geçerli dinleyicinin rotadaki ilk nokta olması mümkündür.) Geçerli dinleyicide bulunan işleyiciler artık olası üç işlem kurssuna sahiptir:

  - Hiç bir işlem yapın; olay işlenmemiş kalır ve olay bir sonraki dinleyiciye yönlendirir.

  - Olaya yanıt olarak kod yürütün, ancak gerçekleştirilecek eylemin olayı işlenmiş olarak işaretlemeyi sağlamak için yeterince önemli olmadığını belirleme. Olay bir sonraki dinleyiciye yönlendirir.

  - Olaya yanıt olarak kodu yürütün. Gerçekleştirilen eylem, işlenen olarak işaretlemek için yeterince önemli bir değer kabul edildiğinden, olayı işleyiciye geçirilen olay verilerinde işlendi olarak işaretleyin. Olay yine de bir sonraki dinleyiciye yönlendirir, ancak olay <xref:System.Windows.RoutedEventArgs.Handled%2A> verilerinde ile = `true` , yalnızca `handledEventsToo` dinleyiciler daha fazla işleyicileri çağırma fırsatına sahiptir.

Bu kavramsal tasarım daha önce bahsedilen yönlendirme davranışına göre zorlanmıştır: yol üzerinde önceki bir işleyici zaten ayarlanmış <xref:System.Windows.RoutedEventArgs.Handled%2A>olsabileçağrılanyönlendirilmişolaylarayönelikişleyicilereklemekdahazordur(kodveyastillerdehalamümkünolsa) .`true`

Yönlendirilmiş olayların sınıf işlemesi ve yönlendirilmiş olayı olarak <xref:System.Windows.RoutedEventArgs.Handled%2A>işaretlemek için uygun olduğunda ilgili öneriler için, bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md). <xref:System.Windows.RoutedEventArgs.Handled%2A>

Uygulamalarda, yalnızca onu oluşturan nesne üzerinde kabarcıklanma yönlendirilmiş olayını işlemek ve olayın yönlendirme özellikleriyle ilgili hiçbir şey olmaması çok yaygındır. Ancak, aynı zamanda aynı yönlendirilmiş olay için eklenen bir işleyici de varsa, bir yandan beklenmeyen yan etkileri engellemek için, yönlendirilmiş olayı olay verilerinde işlenmiş olarak işaretlemek iyi bir uygulamadır.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Sınıf Işleyicileri

' Dan <xref:System.Windows.DependencyObject>bir şekilde türetilen bir sınıf tanımlıyorsanız, sınıfınızın tanımlanmış veya devralınmış bir olay üyesi olan bir yönlendirilmiş olay için bir sınıf işleyicisi tanımlayabilir ve ekleyebilirsiniz. Sınıf işleyicileri, bir yönlendirilmiş olay kendi rotasında bir öğe örneğine ulaştığında, bu sınıfın örneğine iliştirilmiş herhangi bir örnek dinleyicisi işleyicisinden önce çağrılır.

Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin, belirli yönlendirilmiş olaylar için devralınan sınıf işlemesi vardır. Bu, yönlendirilmiş olayın hiçbir zaman yükseltilmediği, ancak gerçekte sınıf işlendiği ve yönlendirilmiş olayın belirli teknikleri kullanıyorsanız örnek İşleyicileriniz tarafından hala işlenebileceği bir durum verebilir. Ayrıca, birçok temel sınıf ve denetim, sınıf işleme davranışını geçersiz kılmak için kullanılabilen sanal yöntemleri sunar. Hem istenmeyen sınıf işlemeyi geçici olarak yapma hem de özel bir sınıfta kendi sınıf işlemeyi tanımlama hakkında daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>WPF 'de ekli olaylar

Dil Ayrıca ekli olay adlı özel bir olay türünü tanımlar.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Ekli bir olay, belirli bir olaya yönelik işleyiciyi rastgele bir öğeye eklemenizi sağlar. Olay işleme gereksinimi, ekli olayı belirtmemelidir veya almamalıdır; ne de nesne, olayı ya da hedef işleme örneği, bir sınıf üyesi olarak bu olayı tanımlamalıdır veya başka bir şekilde "sahip değil".

Giriş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistemi, ekli olayları kapsamlı olarak kullanır. Ancak, bu ekli olayların neredeyse hepsi temel öğeler aracılığıyla iletilir. Daha sonra giriş olayları, temel öğe sınıfının üyeleri olan eşdeğer, eklenmemiş yönlendirilmiş olaylar olarak görüntülenir. Örneğin, temel alınan eklenen <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> olay, veya kodu içindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay sözdizimi ile uğraşmaktansa <xref:System.Windows.UIElement.MouseDown> , üzerinde <xref:System.Windows.UIElement> kullanılarak <xref:System.Windows.UIElement> herhangi bir şekilde daha kolay işlenebilir.

İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekli olaylar hakkında daha fazla bilgi için bkz. [ekli olaylara genel bakış](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>XAML 'de nitelikli olay adları

*TypeName*'e benzeyen başka bir sözdizimi kullanımı.  başvuran olay söz dizimi, ancak ekli olay kullanımını kesin bir şekilde söylemez, bu, alt öğeler tarafından oluşturulan yönlendirilmiş olaylar için işleyiciler iliştirilmesidir. Ortak üst öğe, ilgili yönlendirilmiş olaya üye olarak sahip olmasa bile, işleyicileri ortak bir üst öğeye iliştirmiş olursunuz. Bu örneği bir daha göz önünde bulundurun:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Burada, işleyicinin eklendiği üst öğe dinleyicisi ' dır <xref:System.Windows.Controls.StackPanel>. Ancak, yönlendirilmiş bir olay için bir işleyici ekliyor ve <xref:System.Windows.Controls.Button> sınıf tarafından tetiklenir (<xref:System.Windows.Controls.Primitives.ButtonBase> <xref:System.Windows.Controls.Button> aslında, devralma aracılığıyla kullanılabilir). <xref:System.Windows.Controls.Button>"buna sahip olan", ancak yönlendirilmiş olay sistemi, herhangi bir yönlendirilmiş olayın işleyicilerinin, başka bir ortak dil çalışma <xref:System.Windows.UIElement> zamanı <xref:System.Windows.ContentElement> (CLR) olayı için dinleyicileri iliştiremeyen herhangi bir veya örnek dinleyiciye iliştirmesine izin verir. Bu nitelikli olay özniteliği adları için varsayılan xmlns ad alanı genellikle varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns ad alanıdır, ancak özel yönlendirilmiş olaylar için önekli ad alanlarını da belirtebilirsiniz. Xmlns hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>WPF giriş olayları

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Platform içinde yönlendirilmiş olayların sıklıkla bir uygulaması giriş olaylardır. ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, tünel yönlendirilmiş olayları adlarına göre "Önizleme" sözcüğünün ön eki alınır. Giriş olayları genellikle bir tane kabarcıklanma olayı ve diğeri de tünel oluşturma olayı olacak şekilde çiftler halinde gelir. Örneğin, <xref:System.Windows.ContentElement.KeyDown> olay <xref:System.Windows.ContentElement.PreviewKeyDown> ve olay aynı imzaya sahiptir, ilki kabarcıklanma giriş olayıdır ve bu, son tünel giriş olayıdır. Bazen, giriş olayları yalnızca bir kabarcıklanma sürümüne veya belki yalnızca doğrudan yönlendirilen sürüme sahiptir. Belgelerde, yönlendirilmiş olay konuları, bu tür yönlendirilmiş olaylar varsa diğer yönlendirme stratejileriyle benzer yönlendirilmiş olaylara çapraz başvuru yapılır ve yönetilen başvuru sayfalarındaki bölümler her bir yönlendirilmiş olayın yönlendirme stratejisini açıklığa kavuşturacaktır.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]çiftler halinde gelen giriş olayları, bir fare düğmesine basma gibi bir girişten gelen tek bir kullanıcı eyleminin, çift yönlü olarak her iki yönlendirilmiş olayı da oluşturacak şekilde uygulanır. İlk olarak, Tünel olayı tetiklenir ve kendi rotasında dolaşır. Ardından, kabarcıklanma olayı oluşturulur ve kendi rotasında dolaşır. İki olay aynı olay veri örneğini paylaşır, çünkü <xref:System.Windows.UIElement.RaiseEvent%2A> kabarcıklanma olayını oluşturan uygulama sınıfında çağrı yapan yöntem çağrısı, tünel olayından olay verilerini dinler ve yeni oluşturulan olayda yeniden kullanır. Tünel olayına yönelik işleyicilerle olan dinleyiciler, yönlendirilmiş olayı işlenmiş olarak işaretlemek için ilk fırsata sahiptir (önce sınıf işleyicileri, sonra örnek işleyicileri). Tünel rotası boyunca yönlendirilmiş olayı işlenen olarak işaretlenen bir öğe, kabarcıklanma olayı için önceden işlenmiş olay verileri gönderilir ve eşdeğer kabarcıklanma giriş olayları için eklenen tipik işleyiciler çağrılmaz. Görünümleri dışa aktarmak için, işlenmiş kabarcıklanma olayı bile işlenmese de olur. Bu işleme davranışı, tüm isabet temelli giriş olayları veya odak tabanlı giriş olaylarının, bileşik parçaları yerine son denetiminiz tarafından bildirilmesini isteyebileceğiniz denetim birleştirme için yararlıdır. Son denetim öğesi, birleştirme içindeki köke daha yakındır ve bu nedenle, denetimi yedekleyen kodun bir parçası olarak bu yönlendirilmiş olayı daha fazla denetime özgü bir olayla "değiştirmek" sınıfı.

Giriş olayı işlemenin nasıl çalıştığına ilişkin bir çizim olarak, aşağıdaki giriş olayı örneğini göz önünde bulundurun. Aşağıdaki ağaç çiziminde, `leaf element #2` hem a `PreviewMouseDown` hem de bir `MouseDown` olayın kaynağıdır:

![Olay yönlendirme diyagramı](./media/routed-events-overview/input-event-routing.png)

Olay işlemenin sırası aşağıdaki gibidir:

1. `PreviewMouseDown`(Tunnel) in root öğesi.

2. `PreviewMouseDown`(Tunnel) ara öğesi #1.

3. `PreviewMouseDown`(Tunnel) #2 kaynak öğesi.

4. `MouseDown`(kabarcık) #2 kaynak öğesi.

5. `MouseDown`(kabarcık) ara öğe #1.

6. `MouseDown`(kabarcık) kök öğesi.

Yönlendirilmiş olay işleyicisi temsilcisi iki nesneye başvurular sağlar: olayı oluşturan nesne ve işleyicinin çağrıldığı nesne. İşleyicinin çağrıldığı nesne, `sender` parametre tarafından raporlanan nesnedir. Olayın ilk oluşturulduğu nesne, olay verilerinde <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği tarafından raporlanır. Yönlendirilmiş bir olay hala aynı nesne `sender` <xref:System.Windows.RoutedEventArgs.Source%2A> tarafından oluşturulabilir ve işlenebilir ve aynı zamanda aynı olur (Bu durum, olay işleme örnek listesinde 3 ve 4. adımlarda yer alabilir).

Tünelleme ve kabarcıklanma nedeniyle, üst öğeler, alt öğelerinden biri <xref:System.Windows.RoutedEventArgs.Source%2A> olan giriş olayları alır. Kaynak öğenin ne olduğunu bilmeniz önemli olduğunda, bu <xref:System.Windows.RoutedEventArgs.Source%2A> özelliğe erişerek kaynak öğeyi belirleyebilirsiniz.

Genellikle, giriş olayı işaretlendiğinde <xref:System.Windows.RoutedEventArgs.Handled%2A>, daha fazla işleyici çağrılmaz. Genellikle, giriş olaylarınızın anlamı olan uygulamaya özgü mantıksal işleme adreslemek üzere bir işleyici çağrıldığında giriş olaylarını işlenmiş olarak işaretlemelisiniz.

Bu genel bildirimin durumu hakkında <xref:System.Windows.RoutedEventArgs.Handled%2A> , olay verilerinin kasıtlı olarak yoksayılmasına <xref:System.Windows.RoutedEventArgs.Handled%2A> kayıtlı giriş olay işleyicilerinin, her iki yol da çağrılabilir. Daha fazla bilgi için bkz. [olayları önizleme](preview-events.md) veya [yönlendirilmiş olayları işlenmiş olarak Işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

Tünel oluşturma ve kabarcıklanma olayları arasındaki paylaşılan olay veri modeli ve ilk tünelin sıralı oluşturma ve ardından kabarcıklanma olayları, tüm yönlendirilmiş olaylar için genellikle doğru bir kavram değildir. Bu davranış, giriş cihazlarının giriş olay [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çiftlerini oluşturmayı ve bağlamayı nasıl seçmesinin özel olarak uygulandığı bir davranıştır. Kendi giriş olaylarınızı uygulamak Gelişmiş bir senaryodur, ancak bu modeli kendi giriş olaylarınız için de izlemeyi tercih edebilirsiniz.

Belirli sınıflar, genellikle belirli bir kullanıcı odaklı giriş olayının bu denetimde ne anlama geldiğini yeniden tanımlama ve yeni bir olay oluşturma amacıyla belirli giriş olaylarını sınıf olarak işleyecek şekilde tercih edilir. Daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

Giriş ve olayların tipik uygulama senaryolarında nasıl etkileşim kurduğu hakkında daha fazla bilgi için bkz. [girişe genel bakış](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetter ve EventTriggers

Stillerde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.EventSetter>kullanarak biçimlendirme içinde önceden tanımlanmış bazı olay işleme sözdizimini ekleyebilirsiniz. Stil uygulandığında, başvurulan işleyici stilli örneğe eklenir. <xref:System.Windows.EventSetter> Yalnızca bir yönlendirilmiş olay için bildirebilirsiniz. Bir örnek verilmiştir. Burada başvurulan yöntemin bir arka plan kod dosyasında olduğunu unutmayın. `b1SetColor`

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

Burada elde edilen avantaj, stilin uygulamanızdaki herhangi bir düğmeye uygulanabilecek çok büyük bir bilgiyi içermesi ve <xref:System.Windows.EventSetter> bu stilin bir parçası olması, biçimlendirme düzeyinde bile kod yeniden kullanımını yükseltir. Ayrıca, işleyiciler <xref:System.Windows.EventSetter> için bir adım olarak genel uygulama ve sayfa işaretlemesinin bir adım daha uzakta bir yöntem adı da soyutlar.

' In [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olay ve animasyon özelliklerini birleştiren bir özel sözdizimi bir <xref:System.Windows.EventTrigger>. ' De olduğu gibi, yalnızca yönlendirilmiş olaylar bir <xref:System.Windows.EventTrigger>için kullanılabilir. <xref:System.Windows.EventSetter> Genellikle, <xref:System.Windows.EventTrigger> bir stilin parçası olarak tanımlanır, ancak bir <xref:System.Windows.EventTrigger> <xref:System.Windows.FrameworkElement.Triggers%2A> koleksiyonun parçası olarak sayfa düzeyi öğelerde de veya bir <xref:System.Windows.Controls.ControlTemplate>içinde de belirtilebilir. , Bir yönlendirilmiş olay <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.EventTrigger> , bu olay için bildiren bir öğeye her ulaştığında çalışan bir öğesi belirtmenize olanaksağlar.<xref:System.Windows.EventTrigger> ' In <xref:System.Windows.EventTrigger> yalnızca olayı işleme ve var olan bir görsel taslağa başlatılmasına neden olan avantajı, film şeridi ve <xref:System.Windows.EventTrigger> onun çalışma zamanı davranışı üzerinde daha iyi bir denetim sağlar. Daha fazla bilgi için bkz. [bir film şeridini başladıktan sonra denetlemek Için Olay Tetikleyicilerini Kullanma](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Yönlendirilmiş olaylar hakkında daha fazla bilgi

Bu konu, temel kavramları açıklama açısından ve çeşitli temel öğelerde ve denetimlerde zaten mevcut olan yönlendirilmiş olaylara nasıl ve ne zaman yanıt verebileceğine ilişkin yönergeler sunarak yönlendirilmiş olayları ele alır. Ancak, özel sınıfınıza özel olay veri sınıfları ve temsilciler gibi tüm gerekli destekle birlikte kendi yönlendirilmiş olaylarınızı oluşturabilirsiniz. Yönlendirilmiş olay sahibi herhangi bir sınıf olabilir, ancak yönlendirilmiş olayların yararlı olması için <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> türetilmiş sınıflar tarafından oluşturulması ve işlenmesi gerekir. Özel olaylar hakkında daha fazla bilgi için bkz. [özel bir yönlendirilmiş olay oluşturma](how-to-create-a-custom-routed-event.md).

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
