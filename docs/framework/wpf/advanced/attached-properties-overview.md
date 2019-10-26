---
title: Ekli Özelliklere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: cee80ca0880e046870f699f45624df61ee507a47
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919856"
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış

İliştirilmiş özellik XAML tarafından tanımlanan bir kavramdır. İliştirilmiş bir özellik, herhangi bir nesne üzerinde ayarlanabilir bir genel özellik türü olarak kullanılmak üzere tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], ekli özellikler genellikle geleneksel özelliği "sarmalayıcı" olmayan bir bağımlılık özelliği biçimi olarak tanımlanmıştır.

## Kaynakları<a name="prerequisites"></a>

Bu konu başlığı altında, bağımlılık özelliklerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarında var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)' ı okuduğunuzu varsaymış olursunuz. Bu konudaki örnekleri izlemek için XAML 'yi de anlamanız ve WPF uygulamalarının nasıl yazılacağını bilmeniz gerekir.

## Ekli Özellikler neden kullanılmalıdır<a name="attached_properties_usage"></a>

İliştirilmiş bir özelliğin amacı, farklı alt öğelerin gerçekten üst öğede tanımlanmış olan bir özellik için benzersiz değerler belirtmesini sağlamaktır. Bu senaryonun belirli bir uygulaması, alt öğeleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]nasıl sunulduğunu üst öğeye bildirir. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği bir örnektir. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği, <xref:System.Windows.Controls.DockPanel> kendi kendine değil <xref:System.Windows.Controls.DockPanel>içinde yer alan öğelerde ayarlanacak şekilde tasarlandığından, ekli özellik olarak oluşturulur. <xref:System.Windows.Controls.DockPanel> sınıfı <xref:System.Windows.Controls.DockPanel.DockProperty>adlı statik <xref:System.Windows.DependencyProperty> alanını tanımlar ve ardından ekli özellik için ortak erişimciler olarak <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemlerini sağlar.

## XAML 'de Ekli Özellikler<a name="attached_properties_xaml"></a>

XAML 'de, *AttachedPropertyProvider*söz dizimini kullanarak iliştirilmiş özellikleri ayarlarsınız. *PropertyName*

XAML 'de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> nasıl ayarlayakullanabileceğinizi gösteren bir örnek aşağıda verilmiştir:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Kullanımın statik bir özelliğe biraz benzediğini unutmayın; ada göre belirtilen herhangi bir örneğe başvurmak yerine, ' ın sahip olduğu <xref:System.Windows.Controls.DockPanel> türüne her zaman başvurabilirsiniz ve ekli özelliği kaydeder.

Ayrıca, XAML 'deki iliştirilmiş bir özellik, biçimlendirme içinde ayarladığınız bir öznitelik olduğundan, yalnızca ayarlama işleminin herhangi bir ilgisi vardır. , Stillerdeki tetikleyiciler (Ayrıntılar için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma) gibi değerleri karşılaştırmak için bazı dolaylı mekanizmalar OLMASıNA rağmen xaml 'de doğrudan bir özelliği alamaz.

### <a name="attached-property-implementation-in-wpf"></a>WPF 'de ekli özellik uygulama

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], Kullanıcı arabirimi sunumu ile ilgili WPF türlerinde bulunan ekli özelliklerin çoğu bağımlılık özellikleri olarak uygulanır. İliştirilmiş özellikler bir XAML kavramıdır, ancak bağımlılık özellikleri bir WPF kavramıdır. WPF ekli özellikleri bağımlılık özellikleri olduğundan, özellik meta verileri gibi bağımlılık özelliği kavramlarını ve bu özellik meta verilerinden varsayılan değerleri destekler.

## Iliştirilmiş özellikler sahip olan tür tarafından nasıl kullanılır<a name="howused"></a>

İliştirilmiş özellikler herhangi bir nesne üzerinde ayarlanabilir olsa da, özelliğin somut bir sonuç üreteceğinden veya değerin başka bir nesne tarafından kullanılmasını her zaman otomatik olarak anlamı yoktur. Genellikle, ekli özellikler, çok çeşitli olası sınıf hiyerarşileri veya mantıksal ilişkilerden gelen nesnelerin her biri, ekli özelliği tanımlayan türe ortak bilgiler raporlamasını sağlayacak şekilde tasarlanmıştır. İliştirilmiş özelliği tanımlayan tür genellikle bu modellerden birini izler:

- İliştirilmiş özelliği tanımlayan tür, ekli özellik için değerler ayarlanacak öğelerin üst öğesi olabilecek şekilde tasarlanmıştır. Daha sonra tür, alt nesnelerini bazı nesne ağacı yapısına karşı iç mantık aracılığıyla yineler, değerleri edinir ve bu değerler üzerinde bir şekilde davranır.

- İliştirilmiş özelliği tanımlayan tür, bir dizi olası üst öğe ve içerik modeli için alt öğe olarak kullanılacaktır.

- İliştirilmiş özelliği tanımlayan tür bir hizmeti temsil eder. Diğer türler ekli özellik için değerleri ayarlar. Ardından, özelliği ayarlanan öğe hizmet bağlamında değerlendirildiğinde, ekli özellik değerleri, hizmet sınıfının iç mantığı aracılığıyla elde edilir.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Üst tanımlı Iliştirilmiş özelliğe bir örnek

WPF 'in iliştirilmiş bir özelliği tanımladığı en tipik senaryo, bir üst öğe bir alt öğe koleksiyonunu desteklediğinde ve ayrıca davranışın özelliklerinin her bir alt öğe için ayrı olarak bildirildiği bir davranış uygular.

<xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> iliştirilmiş özelliği tanımlar ve <xref:System.Windows.Controls.DockPanel> işleme mantığının bir parçası olarak sınıf düzeyi koda sahiptir (özellikle, <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> ve <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). <xref:System.Windows.Controls.DockPanel> örnek her zaman ilk alt öğelerinin <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>için bir değer ayarlayıp ayarlayamadığını kontrol eder. Bu durumda, bu değerler söz konusu alt öğeye uygulanan işleme mantığı için giriş haline gelir. İç içe <xref:System.Windows.Controls.DockPanel> örneklerin her biri kendi anlık alt öğe koleksiyonlarını değerlendirir, ancak bu davranış, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değerleri işleme biçimine özgüdür. En üst öğenin ötesinde öğeleri etkileyen iliştirilmiş özelliklerin olması teorik olarak mümkündür. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özelliği üzerinde işlem yapacak <xref:System.Windows.Controls.DockPanel> üst öğesi olmayan bir öğede ayarlandıysa, hata veya özel durum oluşmaz. Bu, genel bir özellik değerinin ayarlandığı, ancak bilgileri kullanabilen geçerli <xref:System.Windows.Controls.DockPanel> üst öğesi olmadığı anlamına gelir.

## Koddaki Ekli Özellikler<a name="attached_properties_code"></a>

WPF 'deki Ekli özellikler, kolay get/set erişimi için tipik CLR "sarmalayıcı" yöntemlerine sahip değildir. Bunun nedeni, iliştirilmiş özelliğin, özelliğin ayarlandığı örnekler için CLR ad alanının bir parçası olması değildir. Ancak, XAML ayrıştırıldığında XAML işlemcisi bu değerleri ayarlayabilmelidir. Etkin bir eklenmiş özellik kullanımını desteklemek için, iliştirilmiş özelliğin sahip türü **Get_PropertyName_** ve **Set_PropertyName_** biçiminde adanmış erişimci yöntemleri uygulamalıdır. Bu adanmış erişimci yöntemleri, kodda ekli özelliği almak veya ayarlamak için de kullanışlıdır. Bir kod perspektifinden, iliştirilmiş bir özellik, özellik erişimcileri yerine Yöntem erişimcilerine sahip bir yedekleme alanıyla benzerdir ve bu alan, özellikle tanımlanmış olması gereken herhangi bir nesne üzerinde bulunabilir.

Aşağıdaki örnek, kodda ekli bir özelliği nasıl ayarlayakullanabileceğinizi gösterir. Bu örnekte, `myCheckBox` <xref:System.Windows.Controls.CheckBox> sınıfının bir örneğidir.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML örneğine benzer şekilde, `myCheckBox` zaten üçüncü kod satırı tarafından `myDockPanel` bir alt öğesi olarak eklenmediyse, dördüncü kod satırı bir özel durum oluşturmaz, ancak özellik değeri bir <xref:System.Windows.Controls.DockPanel> üst öğesiyle etkileşime girmemelidir ve bu sayede yapma. Yalnızca bir <xref:System.Windows.Controls.DockPanel> üst öğesi bulunan bir alt öğe üzerinde ayarlanan <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değeri, işlenen uygulamada etkin bir davranışa neden olur. (Bu durumda, ekli özelliği ayarlayabilir ve sonra ağaca iliştirebilirsiniz. Ya da ağaca iliştirilebilecek ve ardından ekli özelliği ayarlayabilirsiniz. Her iki eylem sırası da aynı sonucu sağlar.)

## Ekli Özellik meta verileri<a name="attached_properties_metadata"></a>

Özelliği kaydederken, özelliğin işleme, ölçüm ve benzeri özellikleri etkilemediği gibi özelliğin özelliklerini belirtmek için <xref:System.Windows.FrameworkPropertyMetadata> ayarlanır. İliştirilmiş bir özelliğin meta verileri genellikle bağımlılık özelliğinden farklı değildir. İliştirilmiş özellik meta verilerinde bir geçersiz kılmada varsayılan bir değer belirtirseniz, bu değer geçersiz kılma sınıfının örneklerine örtük iliştirilmiş özelliğin varsayılan değeri olur. Özellikle, varsayılan değer, bazı bir işlem söz konusu özellik için `Get` yöntemi erişimcisi aracılığıyla ekli bir özelliğin değerini sorguladığında, meta verileri belirttiğiniz sınıfın bir örneğini ve bu ekli öğenin değerini belirterek raporlanır. özellik başka bir şekilde ayarlanmadı.

Özellik değeri devralmayı bir özellikte etkinleştirmek istiyorsanız, eklenmemiş bağımlılık özellikleri yerine iliştirilmiş özellikleri kullanmanız gerekir. Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).

## Özel Ekli Özellikler<a name="custom"></a>

### Ekli Özellik ne zaman oluşturulur<a name="create_attached_properties"></a>

Tanımlama sınıfı dışındaki sınıflar için kullanılabilir bir özellik ayarı mekanizmasının nedeni olduğunda iliştirilmiş bir özellik oluşturabilirsiniz. Bunun için en yaygın senaryo düzenidir. Var olan düzen özelliklerine örnek olarak <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>ve <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>verilebilir. Burada etkinleştirilen senaryo, düzen için alt öğe olarak var olan öğelerin düzen ve düzen üst öğelerine tek tek hızlı bir şekilde, her biri üst öğe olarak tanımlanan bir özellik değeri olarak ifade edebilmesini sağlar. özelliði.

İliştirilmiş bir özelliği kullanmak için başka bir senaryo ise sınıfınız bir hizmeti temsil ettiğinde ve sınıfların hizmeti daha saydam bir şekilde tümleştirmesini istediğinizde.

Ancak başka bir senaryo, **Özellikler** penceresi düzenlemesi gibi VISUAL Studio WPF tasarımcı desteğini almadır. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

Daha önce bahsedildiği gibi, özellik değeri devralmayı kullanmak istiyorsanız, ekli bir özellik olarak kaydetmeniz gerekir.

### Ekli Özellik oluşturma<a name="how_do_i_create_attached_properties"></a>

Sınıfınız, ekli özelliği başka türlerde kullanım için tamamen tanımlıyorsa, sınıfın <xref:System.Windows.DependencyObject>türetmesini gerektirmez. Ancak, iliştirilmiş özelliği de bağımlılık özelliği olan genel WPF modelini izlerseniz <xref:System.Windows.DependencyObject> türetmeniz gerekir.

<xref:System.Windows.DependencyProperty>türünde bir `public static readonly` alanı bildirerek iliştirilmiş özelliği bir bağımlılık özelliği olarak tanımlayın. Bu alanı, <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yönteminin dönüş değerini kullanarak tanımlarsınız. Alan adının eklenmiş özellik adıyla eşleşmesi gerekir, bu, tanımlayıcı alanları adlandırmanın, temsil ettiği özelliklere karşı, belirlenen WPF düzenine uymak için `Property`. İliştirilmiş özellik sağlayıcısı, ekli özellik için erişimci olarak static **Get_PropertyName_** ve **Set_PropertyName_** yöntemleri sağlamalıdır; Bunun başarısız olması, özellik sisteminin ekli özelliği kullanmasına neden olur.

> [!NOTE]
> İliştirilmiş özelliğin al erişimcisini atlarsanız, özelliğindeki veri bağlama Visual Studio ve Visual Studio için Blend gibi tasarım araçları 'nda çalışmaz.

#### <a name="the-get-accessor"></a>Get erişimcisi

**Get_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static object GetPropertyName(object target)`

- `target` nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> yöntemi parametre <xref:System.Windows.UIElement>olarak, iliştirilmiş özelliğin yalnızca <xref:System.Windows.UIElement> örneklerine ayarlanmış olması hedeflenmişse.

- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> metodu onu <xref:System.Windows.Controls.Dock>olarak yazdığında, bu değer yalnızca söz konusu numaralandırmaya ayarlanabilir.

#### <a name="the-set-accessor"></a>Set erişimcisi

**Set_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static void SetPropertyName(object target, object value)`

- `target` nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> metodu onu <xref:System.Windows.UIElement>olarak, iliştirilmiş özelliğin yalnızca <xref:System.Windows.UIElement> örneklerine ayarlanmayacak şekilde.

- `value` nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> metodu onu <xref:System.Windows.Controls.Dock>olarak yazdığında, bu değer yalnızca söz konusu numaralandırmaya ayarlanabilir. Bu yöntemin değerinin, biçimlendirme içindeki iliştirilmiş özellik kullanımında ekli özelliğinizle karşılaştığında XAML yükleyicisindeki gelen giriş olduğunu unutmayın. Bu giriş, biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle, kullandığınız tür için tür dönüştürmesi, değer seri hale getirici veya biçimlendirme uzantısı desteğinin olması gerekir. bu şekilde, uygun tür öznitelik değerinden (sonunda yalnızca bir dize) oluşturulabilir.

Aşağıdaki örnek, bağımlılık özelliği kaydını (<xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi kullanılarak) ve **Get_PropertyName_** ve **Set_PropertyName_** erişimcileri gösterir. Örnekte, ekli özellik adı `IsBubbleSource`. Bu nedenle, erişimciler `GetIsBubbleSource` ve `SetIsBubbleSource`olarak adlandırılmalıdır.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>İliştirilmiş özellik öznitelikleri

WPF, yansıma işlemlerine eklenen özellikler hakkında bilgi sağlamak için tasarlanan çeşitli [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] tanımlar ve tasarımcılar gibi tipik yansıma ve özellik bilgileri kullanıcılarına. İliştirilmiş özelliklerde sınırsız kapsam türü olduğundan, tasarımcıların XAML kullanan belirli bir teknoloji uygulamasında tanımlanmış tüm iliştirilmiş özelliklerin genel bir listesini kullanarak kullanıcıların aşırı yük duymaması için bir yol gerekir. WPF 'nin Ekli Özellikler için tanımladığı [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)], belirli bir iliştirilmiş özelliğin bir Özellikler penceresinde gösterilmesi gereken durumları kapsama almak için kullanılabilir. Kendi özel ekli özellikleri için de bu öznitelikleri uygulamayı düşünebilirsiniz. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] amacı ve sözdizimi, uygun başvuru sayfalarında açıklanmıştır:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Ekli Özellikler hakkında daha fazla bilgi<a name="more"></a>

- Ekli Özellik oluşturma hakkında daha fazla bilgi için bkz. [ekli özelliği kaydetme](how-to-register-an-attached-property.md).

- Bağımlılık özellikleri ve ekli özellikler için daha gelişmiş kullanım senaryoları için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).

- Ayrıca bir özelliği iliştirilmiş bir özellik olarak ve bağımlılık özelliği olarak kaydedebilir, ancak yine de "sarmalayıcı" uygulamalarını kullanıma sunabilirsiniz. Bu durumda, özelliği bu öğe üzerinde ya da XAML ekli özelliği sözdizimi aracılığıyla herhangi bir öğede ayarlanabilir. Hem standart hem de ekli kullanımlar için uygun senaryoya sahip bir özellik örneği <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [Ekli Özelliği Kaydetme](how-to-register-an-attached-property.md)
