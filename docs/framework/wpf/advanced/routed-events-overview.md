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
ms.openlocfilehash: f47eccac4e960bd6869da0da139803cd4e433393
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794298"
---
# <a name="routed-events-overview"></a>Gönderilmiş Olaylara Genel Bakış

Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]' de yönlendirilmiş olay kavramını açıklar. Bu konu, yönlendirilmiş olay terminolojisini tanımlar, yönlendirilmiş olayların bir öğe ağacı aracılığıyla nasıl yönlendirildiğini açıklar, yönlendirilmiş olayları nasıl işleyeceğinizi özetler ve kendi özel yönlendirilmiş olaylarınızı oluşturmayı tanıtır.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

Bu konu başlığı altında, ortak dil çalışma zamanı (CLR) ve nesne odaklı programlama hakkında temel bilgiye sahip olduğunuz ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri arasındaki ilişkilerin ağaç olarak nasıl anlaılabileceği kavramı varsayılmaktadır. Bu konudaki örnekleri izlemek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] anlamanız ve çok temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları ya da sayfaların nasıl yazılacağını bilmeniz gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü uygulaması](../getting-started/walkthrough-my-first-wpf-desktop-application.md) ve [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Yönlendirilmiş olay nedir?

Yönlendirilmiş olayları, işlevsel veya uygulama perspektifinden düşünebilirsiniz. Burada her iki tanım de sunulmuştur, çünkü bazı kişiler bir veya diğer tanımın daha kullanışlı olduğunu fark ettiğinden.

İşlevsel Tanım: yönlendirilmiş olay, yalnızca olayı oluşturan nesne yerine bir öğe ağacındaki birden çok dinleyiciyle işleyicileri çağırabilen bir olay türüdür.

Uygulama tanımı: yönlendirilmiş olay, <xref:System.Windows.RoutedEvent> sınıfının bir örneği tarafından desteklenen bir CLR olayıdır ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi tarafından işlenir.

Tipik bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması birçok öğesi içerir. Kod içinde oluşturulup oluşturulmayacağını veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olarak bildirilirse, bu öğeler birbirleriyle bir öğe ağacı ilişkisinde bulunur. Olay yolu, olay tanımına bağlı olarak iki yönden birine hareket edebilir, ancak genellikle yol kaynak öğeden geçer ve öğe ağacı köküne (genellikle bir sayfa veya pencere) ulaşana kadar öğe ağacı aracılığıyla "kabarcıklar". Bu kabarcıklanma kavramı, daha önce DHTML nesne modeliyle çalıştıysanız size tanıdık gelebilir.

Aşağıdaki basit öğe ağacını göz önünde bulundurun:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Bu öğe ağacı aşağıdakine benzer bir şey üretir:

![Evet, hayır ve Iptal düğmeleri](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

Bu basitleştirilmiş öğe ağacında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayının kaynağı <xref:System.Windows.Controls.Button> öğelerinden biridir ve tıklanmış <xref:System.Windows.Controls.Button>, olayı işleme fırsatına sahip olan ilk öğedir. Ancak <xref:System.Windows.Controls.Button> ekli bir işleyici olay üzerinde işlem yaptığı takdirde, bu durumda, etkinlik, <xref:System.Windows.Controls.StackPanel>olan öğe ağacındaki <xref:System.Windows.Controls.Button> üst öğesine doğru bir şekilde kabarcığa acaktır. Potansiyel olarak, <xref:System.Windows.Controls.Border>ve daha sonra öğe ağacının sayfa köküne kadar olan olay kabarcıkları (gösterilmez).

Diğer bir deyişle, bu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayına yönelik olay rotası şu şekilde olur:

Düğme--> StackPanel--> Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Yönlendirilmiş olaylar için üst düzey senaryolar

Aşağıda, yönlendirilmiş olay kavramını motive eden senaryoların kısa bir özeti ve tipik bir CLR olayının Bu senaryolar için yeterli olmadığı hakkında genel bir Özet verilmiştir:

**Denetim oluşturma ve kapsülleme:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli denetimlerin zengin içerik modeli vardır. Örneğin, düğmenin görsel ağacını etkin bir şekilde genişleten bir <xref:System.Windows.Controls.Button>içine görüntü yerleştirebilirsiniz. Ancak eklenen görüntü, Kullanıcı teknik olarak görüntünün parçası olan piksellere tıklasa bile, bir düğmenin içeriğinin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> yanıt vermesine neden olan isabet testi davranışını bozmamalıdır.

**Tekil işleyici ek noktaları:** Windows Forms, birden çok öğeden çıkarılan olayları işlemek için aynı işleyiciyi birden çok kez iliştirmelidir. Yönlendirilmiş olaylar, önceki örnekte gösterildiği gibi, bu işleyiciyi yalnızca bir kez iliştirmeyi sağlar ve gerekirse olayın nereden geldiğini tespit etmek için işleyici mantığını kullanır. Örneğin, bu, daha önce gösterilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]için işleyici olabilir:

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Sınıf işleme:** Yönlendirilmiş olaylar, sınıfı tarafından tanımlanan statik işleyiciye izin verir. Bu sınıf işleyicisinin, ekli örnek işleyicilerinin kullanabilmesi için önce bir olayı işleme fırsatı vardır.

**Yansıma olmadan bir olaya başvurma:** Belirli kod ve biçimlendirme teknikleri belirli bir olayı tanımlamak için bir yol gerektirir. Yönlendirilmiş bir olay, statik veya çalışma zamanı yansıması gerektirmeyen sağlam bir olay tanımlama tekniği sağlayan tanımlayıcı olarak bir <xref:System.Windows.RoutedEvent> alanı oluşturur.

### <a name="how-routed-events-are-implemented"></a>Yönlendirilmiş olaylar nasıl uygulanır

Yönlendirilmiş olay, <xref:System.Windows.RoutedEvent> sınıfının bir örneği tarafından desteklenen ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemine kaydedilen bir CLR olayıdır. Kayıt işleminden elde edilen <xref:System.Windows.RoutedEvent> örnek genellikle, yönlendirilmiş olayı kaydeden ve bu nedenle "sahip olunan" sınıfının bir `public` `static` `readonly` alan üyesi olarak tutulur. Aynı adlı CLR olayına bağlantı (bazen "sarmalayıcı" olayı), CLR olayının `add` ve `remove` uygulamalarını geçersiz kılarak gerçekleştirilir. Genellikle `add` ve `remove`, bu olayın işleyicilerini eklemek ve kaldırmak için dile özgü uygun olay sözdizimini kullanan örtük bir varsayılan olarak bırakılır. Yönlendirilmiş olay yedekleme ve bağlantı mekanizması, bağımlılık özelliğinin <xref:System.Windows.DependencyProperty> sınıfı tarafından desteklenen ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemine kayıtlı olan bir CLR özelliği olan kavramsal olarak benzerdir.

Aşağıdaki örnek, <xref:System.Windows.RoutedEvent> tanımlayıcı alanın kaydı ve pozlaması ve `Tap` CLR olayı `add` ve `remove` uygulamaları dahil olmak üzere özel `Tap` yönlendirilmiş bir olay için bildirimi gösterir.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Yönlendirilmiş olay Işleyicileri ve XAML

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir olaya bir işleyici eklemek için, olay adını olay dinleyicisi olan öğe üzerinde bir öznitelik olarak bildirirsiniz. Özniteliğin değeri, uygulanan işleyici yönteminizin, arka plan kod dosyasının kısmi sınıfında bulunması gereken addır.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

Standart CLR olay işleyicilerini eklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] söz dizimi, aşağıdaki yönlendirilmiş olay uygulamalarına sahip olan CLR olay sarmalayıcıya gerçekten işleyiciler eklediğiniz için, yönlendirilmiş olay işleyicilerini ekleme için aynıdır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]'de olay işleyicileri ekleme hakkında daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Yönlendirme stratejileri

Yönlendirilmiş olaylar üç yönlendirme stratejisinden birini kullanır:

- **Köpürme:** Olay kaynağındaki olay işleyicileri çağrılır. Yönlendirilmiş olay daha sonra öğe ağacı köküne ulaşıncaya kadar art arda gelen üst öğelere yönlendirir. Çoğu yönlendirilmiş olay, kabarcıklanma yönlendirme stratejisini kullanır. Kabarcıklanma yönlendirilmiş olayları genellikle farklı denetimlerden veya diğer kullanıcı arabirimi öğelerinden giriş veya durum değişikliklerini raporlamak için kullanılır.

- **Doğrudan:** Yalnızca kaynak öğeye, yanıt olarak işleyicileri çağırma fırsatı verilir. Bu, Windows Forms olaylar için kullandığı "yönlendirmeye" benzer. Ancak, standart bir CLR olayından farklı olarak, doğrudan yönlendirilmiş olaylar sınıf işlemeyi destekler (sınıf işleme gelecek bölümde açıklanmıştır) ve <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger>tarafından kullanılabilir.

- **Tünel oluşturma:** Başlangıçta, öğe ağacı kökündeki olay işleyicileri çağrılır. Yönlendirilmiş olay daha sonra, yönlendirilmiş olay kaynağı (yönlendirilmiş olayı oluşturan öğe) olan node öğesine doğru yol boyunca ardışık alt öğeler aracılığıyla bir yol dolaşır. Tünel yönlendirilmiş olayları genellikle bir denetimin birleştirme parçası olarak kullanılır veya işlenir. Bu, bileşik parçalardan gelen olaylar kasıtlı olarak gizlenebilir veya tüm denetime özgü olaylar tarafından değiştirilebilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde sunulan giriş olayları genellikle bir tünel oluşturma/kabarcıklanma çifti olarak uygulanır. Ayrıca, çiftler için kullanılan bir adlandırma kuralı nedeniyle, tünel olayları bazen önizleme olayları olarak adlandırılır.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Neden yönlendirilmiş olayları kullanmalıyım?

Uygulama geliştiricisi olarak, işlemekte olduğunuz olayın yönlendirilmiş olay olarak uygulandığını her zaman bilmeniz gerekmez. Yönlendirilmiş olaylar özel bir davranışa sahiptir, ancak oluşturulduğu öğede bir olayı işliyorsa bu davranış büyük ölçüde görünmez olur.

Önerilen senaryolardan birini kullanıyorsanız, yönlendirilmiş olaylar güçlü hale gelir: ortak bir kökte ortak işleyiciler tanımlama, kendi denetiminizi birleştirme veya kendi özel denetim sınıfınızı tanımlama.

Yönlendirilmiş olay dinleyicileri ve yönlendirilmiş olay kaynakları, hiyerarşide ortak bir olay paylaşmalıdır. Herhangi bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> herhangi bir yönlendirilmiş olay için olay dinleyicisi olabilir. Bu nedenle, çalışma API 'SI kümesi boyunca, uygulamanın farklı öğelerinin olay bilgilerini değiş tokuş edebilir kavramsal bir "arabirim" olarak kullanılabilir olan tüm yönlendirilmiş olaylar kümesini kullanabilirsiniz. Yönlendirilmiş olaylar için bu "arabirim" kavramı özellikle giriş olayları için geçerlidir.

Yönlendirilmiş olaylar, öğe ağacı üzerinden iletişim kurmak için de kullanılabilir, çünkü olayın olay verileri rotadaki her bir öğeye yeniden yönlendirilir. Bir öğe olay verilerinde bir şeyi değiştirebilir ve bu değişiklik rotadaki bir sonraki öğe için kullanılabilir.

Yönlendirme yönü dışında, belirli bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayının standart bir CLR olayı yerine yönlendirilmiş olay olarak uygulanmasının iki farklı nedeni vardır. Kendi olaylarınızı uygulamadıysanız, şu ilkeleri de göz önünde bulundurmanız gerekebilir:

- <xref:System.Windows.EventSetter> ve <xref:System.Windows.EventTrigger> gibi bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil ve şablon oluşturma özellikleri, başvurulan olayın yönlendirilmiş bir olay olmasını gerektirir. Bu, daha önce bahsedilen olay tanımlayıcı senaryosudur.

- Yönlendirilmiş olaylar, bir kayıtlı örnek işleyicilerinin erişebilmesi için önce yönlendirilmiş olayları işleme fırsatına sahip statik yöntemler belirtebilir sınıf işleme mekanizmasını destekler. Sınıfınız, bir örnekteki olayı işleyerek yanlışlıkla gizlenemez olay odaklı sınıf davranışlarını zorlayabildiğinden, denetim tasarımında çok yararlı olur.

Yukarıdaki önemli noktalar, bu konunun ayrı bir bölümünde ele alınmıştır.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Yönlendirilmiş bir olay için olay Işleyicisi ekleme ve uygulama

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir olay işleyicisi eklemek için, bir öğeye bir öznitelik olarak olay adını ekleyin ve öznitelik değerini, aşağıdaki örnekte olduğu gibi uygun bir temsilciyi uygulayan olay işleyicisinin adı olarak ayarlarsınız.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını işleyen kodu içeren uygulanan işleyicinin adıdır. `b1SetColor`, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için olay işleyicisi temsilcisi olan <xref:System.Windows.RoutedEventHandler> temsilcisiyle aynı imzaya sahip olmalıdır. Tüm yönlendirilmiş olay işleyicisi temsilcilerinin ilk parametresi, olay işleyicisinin eklendiği öğeyi belirtir ve ikinci parametre olay için verileri belirtir.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler> temel yönlendirilmiş olay işleyicisi temsilcisidir. Belirli denetimler veya senaryolar için özelleştirilmiş olan yönlendirilmiş olaylar için, yönlendirilmiş olay işleyicileri için kullanılacak temsilciler da daha özelleştirilmiş hale gelebilir, böylece özel olay verilerini iletebilirler. Örneğin, ortak bir giriş senaryosunda, <xref:System.Windows.UIElement.DragEnter> yönlendirilmiş bir olay işleyebilirsiniz. İşleyiciniz <xref:System.Windows.DragEventHandler> temsilcisini uygulamalıdır. En belirli temsilciyi kullanarak, <xref:System.Windows.DragEventArgs> işleyicide işleyebilir ve sürükleme işleminin Pano yükünü içeren <xref:System.Windows.DragEventArgs.Data%2A> özelliğini okuyabilirsiniz.

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir öğeye olay işleyicisi ekleme hakkında bir örnek için, bkz. [yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).

Kodda oluşturulan bir uygulamaya yönlendirilmiş olay için bir işleyici eklemek basittir. Yönlendirilmiş olay işleyicileri her zaman bir yardımcı yöntem <xref:System.Windows.UIElement.AddHandler%2A> (mevcut yedeklemenin `add`çağırdıkları Yöntem) aracılığıyla eklenebilir.) Ancak, mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olaylar genellikle, yönlendirilmiş olayların işleyicilerinin, yardımcı yöntemden daha sezgisel bir sözdizimi olan dile özgü bir olay sözdizimi tarafından eklenmesine izin veren `add` ve `remove` mantığının uygulamalarını yedeklemelidir. Yardımcı yönteminin örnek kullanımı aşağıda verilmiştir:

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

Sonraki örnek, C# işleç söz dizimini gösterir (Visual Basic, başvurusunun işlenmesi nedeniyle biraz farklı işleç sözdizimine sahiptir):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Kodda olay işleyicisi ekleme hakkında bir örnek için bkz. [Code kullanarak olay Işleyicisi ekleme](how-to-add-an-event-handler-using-code.md).

Visual Basic kullanıyorsanız, işleyicileri işleyici bildirimlerinin bir parçası olarak eklemek için `Handles` anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Işlenen kavramı

Tüm yönlendirilmiş olaylar, <xref:System.Windows.RoutedEventArgs>ortak bir olay veri tabanı sınıfını paylaşır. <xref:System.Windows.RoutedEventArgs>, Boolean değer alan <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliğini tanımlar. <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliğinin amacı, <xref:System.Windows.RoutedEventArgs.Handled%2A> değerini `true`olarak ayarlayarak yönlendirilmiş olayı *işlenmiş*olarak işaretlemek için yol üzerinde herhangi bir olay işleyicisini etkinleştirmektir. Yol üzerinde bir öğede işleyici tarafından işlendikten sonra, paylaşılan olay verileri her bir dinleyiciye yol üzerinde yeniden bildirilir.

<xref:System.Windows.RoutedEventArgs.Handled%2A> değeri, yönlendirilmiş bir olayın yol üzerinde daha fazla hareket ettiği şekilde nasıl bildirileceğini veya işlendiğini etkiler. <xref:System.Windows.RoutedEventArgs.Handled%2A>, yönlendirilmiş bir olay için olay verilerinde `true`, daha sonra söz konusu olay örneği için bu yönlendirilmiş olayı dinleyen işleyiciler genellikle daha sonra çağrılmaz. Bu, her ikisi de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] eklenen işleyiciler için ve `+=` veya `Handles`gibi dile özgü olay işleyicisi ek sözdizimleri tarafından eklenen işleyiciler için geçerlidir. En yaygın işleyici senaryolarında, <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` olarak ayarlanarak olay, bir tünel rotası veya kabarcıklanma rotası için "durdurur" ve ayrıca bir sınıf işleyicisi tarafından rotadaki bir noktada işlenen herhangi bir olay için "durur".

Ancak, dinleyicilerinin olay verilerinde `true` <xref:System.Windows.RoutedEventArgs.Handled%2A> olduğu yönlendirilmiş olaylara yanıt olarak işleyicileri hala çalıştırabildiği bir "handledEventsToo" mekanizması vardır. Diğer bir deyişle, olay rotası olay verileri işlenmiş olarak işaretlenerek gerçekten durdurulmaz. HandledEventsToo mekanizmasını yalnızca kodda veya bir <xref:System.Windows.EventSetter>içinde kullanabilirsiniz:

- Kodda, genel CLR olayları için çalışacak dile özgü bir olay sözdizimi kullanmak yerine, işleyicinizi eklemek için <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yöntemini çağırın. `handledEventsToo` değerini `true`olarak belirtin.

- Bir <xref:System.Windows.EventSetter><xref:System.Windows.EventSetter.HandledEventsToo%2A> özniteliğini `true`olarak ayarlayın.

<xref:System.Windows.RoutedEventArgs.Handled%2A> durumunun yönlendirilmiş olaylarda ürettiği davranışa ek olarak, <xref:System.Windows.RoutedEventArgs.Handled%2A> kavramı uygulamanızı nasıl tasarlayacağınızı ve olay işleyici kodunu yazmanızı sağlar. Yönlendirilmiş olaylar tarafından açığa çıkarılan basit bir protokol olarak <xref:System.Windows.RoutedEventArgs.Handled%2A> kavramış hale getirebilirsiniz. Bu protokolü nasıl kullanacağınızı tam olarak kullanıyorsunuz, ancak <xref:System.Windows.RoutedEventArgs.Handled%2A> değerinin nasıl kullanılacağına yönelik kavramsal tasarım aşağıdaki gibidir:

- Yönlendirilmiş bir olay işlenmiş olarak işaretlenmişse, bu yol üzerindeki diğer öğeler tarafından yeniden işlenmesi gerekmez.

- Yönlendirilmiş bir olay işlenmiş olarak işaretlenmemişse, daha önce yol üzerinde olan diğer dinleyiciler bir işleyiciyi kaydetmemeyi ya da kayıtlı işleyiciler olay verilerini işlememeyi ve <xref:System.Windows.RoutedEventArgs.Handled%2A> `true`olarak ayarlamanıza izin vermez. (Veya, geçerli dinleyicinin rotadaki ilk nokta olması mümkündür.) Geçerli dinleyicide bulunan işleyiciler artık olası üç işlem kurssuna sahiptir:

  - Hiç bir işlem yapın; olay işlenmemiş kalır ve olay bir sonraki dinleyiciye yönlendirir.

  - Olaya yanıt olarak kod yürütün, ancak gerçekleştirilecek eylemin olayı işlenmiş olarak işaretlemeyi sağlamak için yeterince önemli olmadığını belirleme. Olay bir sonraki dinleyiciye yönlendirir.

  - Olaya yanıt olarak kodu yürütün. Gerçekleştirilen eylem, işlenen olarak işaretlemek için yeterince önemli bir değer kabul edildiğinden, olayı işleyiciye geçirilen olay verilerinde işlendi olarak işaretleyin. Olay yine de bir sonraki dinleyiciye yol açabilir, ancak olay verilerinde <xref:System.Windows.RoutedEventArgs.Handled%2A>=`true` ile yalnızca `handledEventsToo` dinleyicileri daha fazla işleyicileri çağırma fırsatına sahiptir.

Bu kavramsal tasarım daha önce bahsedilen yönlendirme davranışına göre zorlanmıştır: yol üzerinde önceki bir işleyici `true`<xref:System.Windows.RoutedEventArgs.Handled%2A> zaten ayarlanmış olsa bile çağrılan yönlendirilmiş olaylara yönelik işleyiciler eklemek daha zordur (kod veya stillerde hala mümkün olsa).

<xref:System.Windows.RoutedEventArgs.Handled%2A>, yönlendirilmiş olayların sınıf işlemesi ve yönlendirilmiş olayı <xref:System.Windows.RoutedEventArgs.Handled%2A>olarak işaretlemek için uygun olduğu zaman hakkında daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

Uygulamalarda, yalnızca onu oluşturan nesne üzerinde kabarcıklanma yönlendirilmiş olayını işlemek ve olayın yönlendirme özellikleriyle ilgili hiçbir şey olmaması çok yaygındır. Ancak, aynı zamanda aynı yönlendirilmiş olay için eklenen bir işleyici de varsa, bir yandan beklenmeyen yan etkileri engellemek için, yönlendirilmiş olayı olay verilerinde işlenmiş olarak işaretlemek iyi bir uygulamadır.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Sınıf Işleyicileri

<xref:System.Windows.DependencyObject>bir şekilde türetilen bir sınıf tanımlıyorsanız, sınıfınızın tanımlanmış veya devralınmış bir olay üyesi olan yönlendirilmiş bir olay için de bir sınıf işleyicisi tanımlayabilir ve iliştirebilirsiniz. Sınıf işleyicileri, bir yönlendirilmiş olay kendi rotasında bir öğe örneğine ulaştığında, bu sınıfın örneğine iliştirilmiş herhangi bir örnek dinleyicisi işleyicisinden önce çağrılır.

Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerinde, belirli yönlendirilmiş olaylar için devralınan sınıf işleme vardır. Bu, yönlendirilmiş olayın hiçbir zaman yükseltilmediği, ancak gerçekte sınıf işlendiği ve yönlendirilmiş olayın belirli teknikleri kullanıyorsanız örnek İşleyicileriniz tarafından hala işlenebileceği bir durum verebilir. Ayrıca, birçok temel sınıf ve denetim, sınıf işleme davranışını geçersiz kılmak için kullanılabilen sanal yöntemleri sunar. Hem istenmeyen sınıf işlemeyi geçici olarak yapma hem de özel bir sınıfta kendi sınıf işlemeyi tanımlama hakkında daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>WPF 'de ekli olaylar

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dili, *ekli olay*adlı özel bir olay türünü de tanımlar. Ekli bir olay, belirli bir olaya yönelik işleyiciyi rastgele bir öğeye eklemenizi sağlar. Olay işleme gereksinimi, ekli olayı belirtmemelidir veya almamalıdır; ne de nesne, olayı ya da hedef işleme örneği, bir sınıf üyesi olarak bu olayı tanımlamalıdır veya başka bir şekilde "sahip değil".

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş sistemi, ekli olayları kapsamlı şekilde kullanır. Ancak, bu ekli olayların neredeyse hepsi temel öğeler aracılığıyla iletilir. Daha sonra giriş olayları, temel öğe sınıfının üyeleri olan eşdeğer, eklenmemiş yönlendirilmiş olaylar olarak görüntülenir. Örneğin, temel alınan ekli olay <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kodda ekli olay sözdizimi ile ilgilenmektense, bu <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.MouseDown> kullanılarak herhangi bir <xref:System.Windows.UIElement> daha kolay işlenebilir.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]eklenen olaylar hakkında daha fazla bilgi için bkz. [ekli olaylara genel bakış](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>XAML 'de nitelikli olay adları

*TypeName*'e benzeyen başka bir sözdizimi kullanımı. başvuran olay söz dizimi, *ancak ekli olay* kullanımını kesin bir şekilde söylemez, bu, alt öğeler tarafından oluşturulan yönlendirilmiş olaylar için işleyiciler iliştirilmesidir. Ortak üst öğe, ilgili yönlendirilmiş olaya üye olarak sahip olmasa bile, işleyicileri ortak bir üst öğeye iliştirmiş olursunuz. Bu örneği bir daha göz önünde bulundurun:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Burada, işleyicinin eklendiği üst öğe dinleyicisi bir <xref:System.Windows.Controls.StackPanel>. Ancak, bu yönlendirilmiş bir olay için bir işleyici ekliyor ve <xref:System.Windows.Controls.Button> sınıfı tarafından tetiklenir (aslında<xref:System.Windows.Controls.Primitives.ButtonBase>, ancak devralmayla <xref:System.Windows.Controls.Button> için kullanılabilir). olaya "sahip olan" <xref:System.Windows.Controls.Button>, ancak yönlendirilmiş olay sistemi, herhangi bir yönlendirilmiş olay işleyicisinin, başka bir ortak dil çalışma zamanı (CLR) olayı için dinleyicileri iliştiremeyen herhangi bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> örnek dinleyicisine iliştirmesine izin verir. Bu nitelikli olay özniteliği adları için varsayılan xmlns ad alanı genellikle varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns ad alanıdır, ancak özel yönlendirilmiş olaylar için önekli ad alanlarını da belirtebilirsiniz. Xmlns hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>WPF giriş olayları

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformu içindeki yönlendirilmiş olayların sıklıkla bir uygulaması giriş olaylardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' de, tünel yönlendirilmiş olayları adlarına göre "Önizleme" sözcüğünün ön eki alınır. Giriş olayları genellikle bir tane kabarcıklanma olayı ve diğeri de tünel oluşturma olayı olacak şekilde çiftler halinde gelir. Örneğin, <xref:System.Windows.ContentElement.KeyDown> olayı ve <xref:System.Windows.ContentElement.PreviewKeyDown> olayı, daha önce kabarcıklanma giriş olayı ve ikinci tünelleme girişi olayı olacak şekilde aynı imzaya sahiptir. Bazen, giriş olayları yalnızca bir kabarcıklanma sürümüne veya belki yalnızca doğrudan yönlendirilen sürüme sahiptir. Belgelerde, yönlendirilmiş olay konuları, bu tür yönlendirilmiş olaylar varsa diğer yönlendirme stratejileriyle benzer yönlendirilmiş olaylara çapraz başvuru yapılır ve yönetilen başvuru sayfalarındaki bölümler her bir yönlendirilmiş olayın yönlendirme stratejisini açıklığa kavuşturacaktır.

çiftler halinde gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olayları, bir fare düğmesine basma gibi girişten gelen tek bir kullanıcı eyleminin, çiftin her iki yönlendirilen olayını sırayla oluşturacak şekilde uygulanır. İlk olarak, Tünel olayı tetiklenir ve kendi rotasında dolaşır. Ardından, kabarcıklanma olayı oluşturulur ve kendi rotasında dolaşır. Kabarcıklanma olayını oluşturan uygulama sınıfında <xref:System.Windows.UIElement.RaiseEvent%2A> yöntemi çağrısı, tünel olayından olay verilerini dinler ve yeni oluşturulan olayda yeniden kullandığından, iki olay aynı olay veri örneğini paylaşırlar. Tünel olayına yönelik işleyicilerle olan dinleyiciler, yönlendirilmiş olayı işlenmiş olarak işaretlemek için ilk fırsata sahiptir (önce sınıf işleyicileri, sonra örnek işleyicileri). Tünel rotası boyunca yönlendirilmiş olayı işlenen olarak işaretlenen bir öğe, kabarcıklanma olayı için önceden işlenmiş olay verileri gönderilir ve eşdeğer kabarcıklanma giriş olayları için eklenen tipik işleyiciler çağrılmaz. Görünümleri dışa aktarmak için, işlenmiş kabarcıklanma olayı bile işlenmese de olur. Bu işleme davranışı, tüm isabet temelli giriş olayları veya odak tabanlı giriş olaylarının, bileşik parçaları yerine son denetiminiz tarafından bildirilmesini isteyebileceğiniz denetim birleştirme için yararlıdır. Son denetim öğesi, birleştirme içindeki köke daha yakındır ve bu nedenle, denetimi yedekleyen kodun bir parçası olarak bu yönlendirilmiş olayı daha fazla denetime özgü bir olayla "değiştirmek" sınıfı.

Giriş olayı işlemenin nasıl çalıştığına ilişkin bir çizim olarak, aşağıdaki giriş olayı örneğini göz önünde bulundurun. Aşağıdaki ağaç çizimde, `leaf element #2` hem `PreviewMouseDown` hem de `MouseDown` olayının kaynağıdır:

![Olay yönlendirme diyagramı](./media/routed-events-overview/input-event-routing.png)

Olay işlemenin sırası aşağıdaki gibidir:

1. kök öğe üzerinde `PreviewMouseDown` (Tunnel).

2. ara öğe #1 `PreviewMouseDown` (tünel).

3. Kaynak öğe #2 `PreviewMouseDown` (tünel).

4. Kaynak öğe #2 `MouseDown` (kabarcık).

5. ara öğe #1 `MouseDown` (kabarcık).

6. kök öğe üzerinde `MouseDown` (kabarcık).

Yönlendirilmiş olay işleyicisi temsilcisi iki nesneye başvurular sağlar: olayı oluşturan nesne ve işleyicinin çağrıldığı nesne. İşleyicinin çağrıldığı nesne, `sender` parametresi tarafından raporlanan nesnedir. Olayın ilk olarak oluşturulduğu nesne, olay verilerinde <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği tarafından raporlanır. Yönlendirilmiş bir olay hala aynı nesne tarafından oluşturulabilir ve işlenebilir, bu durumda `sender` ve <xref:System.Windows.RoutedEventArgs.Source%2A> aynı olur (Bu durum, olay işleme örnek listesinde 3 ve 4. adımlarda olur).

Tünelleme ve kabarcıklanma nedeniyle, üst öğeler <xref:System.Windows.RoutedEventArgs.Source%2A> alt öğelerinden biri olan giriş olayları alır. Kaynak öğenin ne olduğunu bilmeniz önemli olduğunda, <xref:System.Windows.RoutedEventArgs.Source%2A> özelliğine erişerek kaynak öğeyi belirleyebilirsiniz.

Genellikle, giriş olayı <xref:System.Windows.RoutedEventArgs.Handled%2A>olarak işaretlendiğinde, daha fazla işleyici çağrılmaz. Genellikle, giriş olaylarınızın anlamı olan uygulamaya özgü mantıksal işleme adreslemek üzere bir işleyici çağrıldığında giriş olaylarını işlenmiş olarak işaretlemelisiniz.

<xref:System.Windows.RoutedEventArgs.Handled%2A> durumu ile ilgili bu genel bildirimin özel durumu, olay verilerinin, kasıtlı olarak yoksayıl<xref:System.Windows.RoutedEventArgs.Handled%2A> masına kayıtlı giriş olay işleyicilerinin, her iki yol üzerinde de çağrılabilir. Daha fazla bilgi için bkz. [olayları önizleme](preview-events.md) veya [yönlendirilmiş olayları işlenmiş olarak Işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

Tünel oluşturma ve kabarcıklanma olayları arasındaki paylaşılan olay veri modeli ve ilk tünelin sıralı oluşturma ve ardından kabarcıklanma olayları, tüm yönlendirilmiş olaylar için genellikle doğru bir kavram değildir. Bu davranış, giriş cihazlarının giriş olay çiftlerini oluşturmayı ve bağlamayı nasıl seçmesinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özel olarak uygulanır. Kendi giriş olaylarınızı uygulamak Gelişmiş bir senaryodur, ancak bu modeli kendi giriş olaylarınız için de izlemeyi tercih edebilirsiniz.

Belirli sınıflar, genellikle belirli bir kullanıcı odaklı giriş olayının bu denetimde ne anlama geldiğini yeniden tanımlama ve yeni bir olay oluşturma amacıyla belirli giriş olaylarını sınıf olarak işleyecek şekilde tercih edilir. Daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).

Giriş ve olayların tipik uygulama senaryolarında nasıl etkileşim kurduğu hakkında daha fazla bilgi için bkz. [girişe genel bakış](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetter ve EventTriggers

Stillerde, bir <xref:System.Windows.EventSetter>kullanarak biçimlendirme içinde önceden tanımlanmış bazı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay işleme sözdizimini ekleyebilirsiniz. Stil uygulandığında, başvurulan işleyici stilli örneğe eklenir. Yalnızca yönlendirilmiş bir olay için <xref:System.Windows.EventSetter> bildirebilirsiniz. Aşağıda bir örnek verilmiştir. Burada başvurulan `b1SetColor` yönteminin arka plan kod dosyasında olduğunu unutmayın.

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

Burada elde edilen avantaj, stilin uygulamanızdaki herhangi bir düğmeye uygulanabilecek çok büyük bir bilgiyi içermesi ve <xref:System.Windows.EventSetter> bu stilin bir parçası olması halinde, biçimlendirme düzeyinde bile kod yeniden kullanımını yükseltir. Ayrıca, bir <xref:System.Windows.EventSetter>, işleyiciler için yöntem adlarını genel uygulama ve sayfa işaretlemesinin dışında bir adım soyutlar.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olay ve animasyon özelliklerini birleştiren başka bir özelleştirilmiş sözdizimi <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventSetter>olduğu gibi, bir <xref:System.Windows.EventTrigger>için yalnızca yönlendirilmiş olaylar kullanılabilir. Genellikle, bir <xref:System.Windows.EventTrigger> stilin bir parçası olarak tanımlanır, ancak <xref:System.Windows.EventTrigger> <xref:System.Windows.FrameworkElement.Triggers%2A> koleksiyonunun bir parçası olarak veya bir <xref:System.Windows.Controls.ControlTemplate>olan sayfa düzeyi öğelerde de bildirilemez. <xref:System.Windows.EventTrigger>, her bir yönlendirilmiş olay, bu olay için bir <xref:System.Windows.EventTrigger> bildiren rotasında bir öğeye ulaştığında çalışan bir <xref:System.Windows.Media.Animation.Storyboard> belirtmenizi sağlar. Yalnızca olayı işleme ve var olan bir film şeridini başlatmaya neden olan bir <xref:System.Windows.EventTrigger> avantajı, <xref:System.Windows.EventTrigger> film şeridi ve onun çalışma zamanı davranışı üzerinde daha iyi denetim sağlar. Daha fazla bilgi için bkz. [bir film şeridini başladıktan sonra denetlemek Için Olay Tetikleyicilerini Kullanma](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Yönlendirilmiş olaylar hakkında daha fazla bilgi

Bu konu, temel kavramları açıklama açısından ve çeşitli temel öğelerde ve denetimlerde zaten mevcut olan yönlendirilmiş olaylara nasıl ve ne zaman yanıt verebileceğine ilişkin yönergeler sunarak yönlendirilmiş olayları ele alır. Ancak, özel sınıfınıza özel olay veri sınıfları ve temsilciler gibi tüm gerekli destekle birlikte kendi yönlendirilmiş olaylarınızı oluşturabilirsiniz. Yönlendirilmiş olay sahibi herhangi bir sınıf olabilir, ancak <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> türetilmiş sınıflar tarafından yararlı olması için yönlendirilmiş olayların oluşturulması ve işlenmesi gerekir. Özel olaylar hakkında daha fazla bilgi için bkz. [özel bir yönlendirilmiş olay oluşturma](how-to-create-a-custom-routed-event.md).

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
