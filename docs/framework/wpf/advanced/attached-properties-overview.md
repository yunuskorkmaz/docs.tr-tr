---
title: Ekli Özelliklere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 2eacb0ff49b868f144bf35af4bb64b7d049b30cb
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401372"
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış

İliştirilmiş özellik XAML tarafından tanımlanan bir kavramdır. İliştirilmiş bir özellik, herhangi bir nesne üzerinde ayarlanabilir bir genel özellik türü olarak kullanılmak üzere tasarlanmıştır. ' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]De, ekli özellikler genellikle geleneksel özelliği "sarmalayıcı" olmayan bir bağımlılık özelliği biçimi olarak tanımlanmıştır.

## Kaynakları<a name="prerequisites"></a>

Bu konu başlığında bağımlılık özelliklerini, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarda var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)konusunu okuduğunuzu varsaymaktadır. Bu konudaki örnekleri izlemek için XAML 'yi de anlamanız ve WPF uygulamalarının nasıl yazılacağını bilmeniz gerekir.

## Ekli Özellikler neden kullanılmalıdır<a name="attached_properties_usage"></a>

İliştirilmiş bir özelliğin amacı, farklı alt öğelerin gerçekten üst öğede tanımlanmış olan bir özellik için benzersiz değerler belirtmesini sağlamaktır. Bu senaryonun belirli bir uygulaması, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]alt öğelerinin ' de sunulmaları için üst öğeyi bilgilendirmesini sağlar. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Özellik bir örnektir. Özelliği iliştirilmiş bir özellik olarak oluşturulur <xref:System.Windows.Controls.DockPanel>, çünkü <xref:System.Windows.Controls.DockPanel> kendi içinde değil, kendi içinde yer alan öğeler üzerinde ayarlanacak şekilde tasarlanmıştır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.DependencyProperty> <xref:System.Windows.Controls.DockPanel.GetDock%2A> Sınıfı, <xref:System.Windows.Controls.DockPanel.SetDock%2A> adlı statikalanıtanımlarveardındanveyöntemleriniiliştirilmişözellikiçinortakerişimciolaraksağlar.<xref:System.Windows.Controls.DockPanel.DockProperty> <xref:System.Windows.Controls.DockPanel>

## XAML 'de Ekli Özellikler<a name="attached_properties_xaml"></a>

XAML 'de, *AttachedPropertyProvider*söz dizimini kullanarak iliştirilmiş özellikleri ayarlarsınız. *PropertyName*

XAML 'de nasıl ayarlayakullanabileceğinizi <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> gösteren bir örnek aşağıda verilmiştir:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Kullanımın statik bir özelliğe biraz benzediğini unutmayın; her zaman, ekli özelliği <xref:System.Windows.Controls.DockPanel> ada göre belirtilen herhangi bir örneğe başvurmak yerine, sahip olan türe başvurur ve kaydettirir.

Ayrıca, XAML 'deki iliştirilmiş bir özellik, biçimlendirme içinde ayarladığınız bir öznitelik olduğundan, yalnızca ayarlama işleminin herhangi bir ilgisi vardır. , Stillerdeki tetikleyiciler (Ayrıntılar için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma) gibi değerleri karşılaştırmak için bazı dolaylı mekanizmalar OLMASıNA rağmen xaml 'de doğrudan bir özelliği alamaz.

### <a name="attached-property-implementation-in-wpf"></a>WPF 'de ekli özellik uygulama

' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]De, Kullanıcı arabirimi sunumu ile ilgili WPF türlerinde bulunan ekli özelliklerin çoğu bağımlılık özellikleri olarak uygulanır. İliştirilmiş özellikler bir XAML kavramıdır, ancak bağımlılık özellikleri bir WPF kavramıdır. WPF ekli özellikleri bağımlılık özellikleri olduğundan, özellik meta verileri gibi bağımlılık özelliği kavramlarını ve bu özellik meta verilerinden varsayılan değerleri destekler.

## Iliştirilmiş özellikler sahip olan tür tarafından nasıl kullanılır<a name="howused"></a>

İliştirilmiş özellikler herhangi bir nesne üzerinde ayarlanabilir olsa da, özelliğin somut bir sonuç üreteceğinden veya değerin başka bir nesne tarafından kullanılmasını her zaman otomatik olarak anlamı yoktur. Genellikle, ekli özellikler, çok çeşitli olası sınıf hiyerarşileri veya mantıksal ilişkilerden gelen nesnelerin her biri, ekli özelliği tanımlayan türe ortak bilgiler raporlamasını sağlayacak şekilde tasarlanmıştır. İliştirilmiş özelliği tanımlayan tür genellikle bu modellerden birini izler:

- İliştirilmiş özelliği tanımlayan tür, ekli özellik için değerler ayarlanacak öğelerin üst öğesi olabilecek şekilde tasarlanmıştır. Daha sonra tür, alt nesnelerini bazı nesne ağacı yapısına karşı iç mantık aracılığıyla yineler, değerleri edinir ve bu değerler üzerinde bir şekilde davranır.

- İliştirilmiş özelliği tanımlayan tür, bir dizi olası üst öğe ve içerik modeli için alt öğe olarak kullanılacaktır.

- İliştirilmiş özelliği tanımlayan tür bir hizmeti temsil eder. Diğer türler ekli özellik için değerleri ayarlar. Ardından, özelliği ayarlanan öğe hizmet bağlamında değerlendirildiğinde, ekli özellik değerleri, hizmet sınıfının iç mantığı aracılığıyla elde edilir.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Üst tanımlı Iliştirilmiş özelliğe bir örnek

WPF 'in iliştirilmiş bir özelliği tanımladığı en tipik senaryo, bir üst öğe bir alt öğe koleksiyonunu desteklediğinde ve ayrıca davranışın özelliklerinin her bir alt öğe için ayrı olarak bildirildiği bir davranış uygular.

<xref:System.Windows.Controls.DockPanel>iliştirilmiş özelliği tanımlar ve <xref:System.Windows.Controls.DockPanel> kendi <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> işleme mantığının bir parçası olarak sınıf düzeyi koda sahiptir (özellikle ve <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Örnek, her zaman ilk alt öğelerinden birinin için <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>bir değer ayarlayıp ayarlayamadığını kontrol eder. <xref:System.Windows.Controls.DockPanel> Bu durumda, bu değerler söz konusu alt öğeye uygulanan işleme mantığı için giriş haline gelir. İç <xref:System.Windows.Controls.DockPanel> içe yerleştirilmiş örneklerin her biri kendi kendine kendi alt öğe koleksiyonlarını değerlendirir, ancak bu davranış, <xref:System.Windows.Controls.DockPanel> işlem <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değerlerine göre uygulamaya özgüdür. En üst öğenin ötesinde öğeleri etkileyen iliştirilmiş özelliklerin olması teorik olarak mümkündür. İliştirilmiş özellik üzerinde işlem yapacak <xref:System.Windows.Controls.DockPanel> üst öğesi olmayan bir öğede ayarlandıysa, hata veya özel durum oluşmaz. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Bu, genel bir özellik değerinin ayarlandığı, ancak bu bilgileri kullanabilecek geçerli <xref:System.Windows.Controls.DockPanel> bir üst öğesi olmadığı anlamına gelir.

## Koddaki Ekli Özellikler<a name="attached_properties_code"></a>

WPF 'deki Ekli özellikler, kolay get/set erişimi için tipik CLR "sarmalayıcı" yöntemlerine sahip değildir. Bunun nedeni, iliştirilmiş özelliğin, özelliğin ayarlandığı örnekler için CLR ad alanının bir parçası olması değildir. Ancak, XAML ayrıştırıldığında XAML işlemcisi bu değerleri ayarlayabilmelidir. Etkin bir eklenmiş özellik kullanımını desteklemek için, iliştirilmiş özelliğin sahip türü **Get_PropertyName_** ve **Set_PropertyName_** biçiminde adanmış erişimci yöntemleri uygulamalıdır. Bu adanmış erişimci yöntemleri, kodda ekli özelliği almak veya ayarlamak için de kullanışlıdır. Bir kod perspektifinden, iliştirilmiş bir özellik, özellik erişimcileri yerine Yöntem erişimcilerine sahip bir yedekleme alanıyla benzerdir ve bu alan, özellikle tanımlanmış olması gereken herhangi bir nesne üzerinde bulunabilir.

Aşağıdaki örnek, kodda ekli bir özelliği nasıl ayarlayakullanabileceğinizi gösterir. Bu örnekte, `myCheckBox` <xref:System.Windows.Controls.CheckBox> sınıfının bir örneğidir.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML örneğine benzer şekilde, `myCheckBox` üçüncü kod satırı `myDockPanel` tarafından zaten bir alt öğe olarak eklenmediyse, dördüncü kod satırı bir özel durum oluşturmaz, ancak özellik değeri bir <xref:System.Windows.Controls.DockPanel> üst öğeyle etkileşime girmemelidir, böylece hiçbir şey yapmaz. Yalnızca <xref:System.Windows.Controls.DockPanel> üst <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> öğenin varlığı ile Birleşik bir alt öğe üzerinde ayarlanan bir değer, işlenen uygulamada etkin davranışa neden olur. (Bu durumda, ekli özelliği ayarlayabilir ve sonra ağaca iliştirebilirsiniz. Ya da ağaca iliştirilebilecek ve ardından ekli özelliği ayarlayabilirsiniz. Her iki eylem sırası da aynı sonucu sağlar.)

## Ekli Özellik meta verileri<a name="attached_properties_metadata"></a>

Özelliği <xref:System.Windows.FrameworkPropertyMetadata> kaydederken özelliği, özelliğin işleme, ölçüm ve benzerlerini etkilemesinin yanı sıra özelliğin özelliklerini belirtmek üzere ayarlanır. İliştirilmiş bir özelliğin meta verileri genellikle bağımlılık özelliğinden farklı değildir. İliştirilmiş özellik meta verilerinde bir geçersiz kılmada varsayılan bir değer belirtirseniz, bu değer geçersiz kılma sınıfının örneklerine örtük iliştirilmiş özelliğin varsayılan değeri olur. Özellikle, varsayılan değer, bazı bir işlem bu özelliğe ilişkin `Get` Yöntem erişimcisi aracılığıyla ekli bir özelliğin değerini sorguladığında, meta verileri belirttiğiniz sınıfın bir örneğini ve bu değere ait değeri belirten iliştirilmiş özellik başka bir şekilde ayarlanmadı.

Özellik değeri devralmayı bir özellikte etkinleştirmek istiyorsanız, eklenmemiş bağımlılık özellikleri yerine iliştirilmiş özellikleri kullanmanız gerekir. Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).

## Özel Ekli Özellikler<a name="custom"></a>

### Ekli Özellik ne zaman oluşturulur<a name="create_attached_properties"></a>

Tanımlama sınıfı dışındaki sınıflar için kullanılabilir bir özellik ayarı mekanizmasının nedeni olduğunda iliştirilmiş bir özellik oluşturabilirsiniz. Bunun için en yaygın senaryo düzenidir. Var olan düzen özelliklerine örnekler, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>ve <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>' dir. Burada etkinleştirilen senaryo, düzen için alt öğe olarak var olan öğelerin düzen ve düzen üst öğelerine tek tek hızlı bir şekilde, her biri üst öğe olarak tanımlanan bir özellik değeri olarak ifade edebilmesini sağlar. özelliði.

İliştirilmiş bir özelliği kullanmak için başka bir senaryo ise sınıfınız bir hizmeti temsil ettiğinde ve sınıfların hizmeti daha saydam bir şekilde tümleştirmesini istediğinizde.

Ancak başka bir senaryo, **Özellikler** penceresi düzenlemesi gibi VISUAL Studio WPF tasarımcı desteğini almadır. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

Daha önce bahsedildiği gibi, özellik değeri devralmayı kullanmak istiyorsanız, ekli bir özellik olarak kaydetmeniz gerekir.

### Ekli Özellik oluşturma<a name="how_do_i_create_attached_properties"></a>

Sınıfınız, ekli özelliği başka türlerde kullanım için tamamen tanımlıyorsa, sınıfın türetilmesi <xref:System.Windows.DependencyObject>gerekmez. Ancak, iliştirilmiş özelliğinin de bir bağımlılık <xref:System.Windows.DependencyObject> özelliği olması için genel WPF modeli ' ni izlerseniz, ' den türetmeniz gerekir.

İliştirilmiş özelliği, türünde `public static readonly` <xref:System.Windows.DependencyProperty>bir alan bildirerek bağımlılık özelliği olarak tanımlayın. Bu alanı, <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yönteminin dönüş değerini kullanarak tanımlarsınız. Alan adı, eklenen özellik adı ile `Property`eşleşmelidir ve tanımlayıcı alanları adlandırdıkları özelliklere karşılık olarak adlandırılan şirket WPF modelini takip eder. İliştirilmiş özellik sağlayıcısı, ekli özellik için erişimci olarak static **Get_PropertyName_** ve **Set_PropertyName_** yöntemleri sağlamalıdır; Bunun başarısız olması, özellik sisteminin ekli özelliği kullanmasına neden olur.

> [!NOTE]
> İliştirilmiş özelliğin al erişimcisini atlarsanız, özelliğindeki veri bağlama Visual Studio ve Expression Blend gibi tasarım araçlarında çalışmaz.

#### <a name="the-get-accessor"></a>Get erişimcisi

**Get_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static object GetPropertyName(object target)`

- Nesne `target` , uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> yöntemi parametresi olarak <xref:System.Windows.UIElement>, iliştirilmiş özelliği yalnızca <xref:System.Windows.UIElement> örneklere ayarlanmayacak şekilde türlenmiştir.

- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> değeri yalnızca bu sabit listesine ayarlanabileceğinden, yöntemi olarak <xref:System.Windows.Controls.Dock>.

#### <a name="the-set-accessor"></a>Set erişimcisi

**Set_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static void SetPropertyName(object target, object value)`

- Nesne `target` , uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> Yöntemi öğesini olarak <xref:System.Windows.UIElement>, iliştirilmiş özelliği yalnızca <xref:System.Windows.UIElement> örneklere ayarlanmış şekilde türlenmiştir.

- Nesne `value` , uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> değeri yalnızca bu sabit listesine ayarlanabileceğinden, yöntemi olarak <xref:System.Windows.Controls.Dock>. Bu yöntemin değerinin, biçimlendirme içindeki iliştirilmiş özellik kullanımında ekli özelliğinizle karşılaştığında XAML yükleyicisindeki gelen giriş olduğunu unutmayın. Bu giriş, biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle, kullandığınız tür için tür dönüştürmesi, değer seri hale getirici veya biçimlendirme uzantısı desteğinin olması gerekir. bu şekilde, uygun tür öznitelik değerinden (sonunda yalnızca bir dize) oluşturulabilir.

Aşağıdaki örnek, bağımlılık özelliği kaydını ( <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi kullanılarak) ve **Get_PropertyName_** ve **Set_PropertyName_** erişimcileri gösterilmektedir. Örnekte, ekli özellik adı ' dir `IsBubbleSource`. Bu nedenle, erişimcilerinin ve `GetIsBubbleSource` `SetIsBubbleSource`olarak adlandırılması gerekir.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>İliştirilmiş özellik öznitelikleri

WPF, yansıma [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] işlemlerine eklenen özellikler hakkında bilgi sağlamak için tasarlanan birkaç tane tanımlar ve tasarımcı gibi normal yansıma ve özellik bilgileri kullanıcılarına yöneliktir. İliştirilmiş özelliklerde sınırsız kapsam türü olduğundan, tasarımcıların XAML kullanan belirli bir teknoloji uygulamasında tanımlanmış tüm iliştirilmiş özelliklerin genel bir listesini kullanarak kullanıcıların aşırı yük duymaması için bir yol gerekir. Bu [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] WPF Ekli Özellikler için tanımlar, belirli bir iliştirilmiş özelliğin bir Özellikler penceresinde gösterilmesi gereken durumları kapsam için kullanılabilir. Kendi özel ekli özellikleri için de bu öznitelikleri uygulamayı düşünebilirsiniz. Öğesinin [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] amacı ve sözdizimi, uygun başvuru sayfalarında açıklanmıştır:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Ekli Özellikler hakkında daha fazla bilgi<a name="more"></a>

- Ekli Özellik oluşturma hakkında daha fazla bilgi için bkz. [ekli özelliği kaydetme](how-to-register-an-attached-property.md).

- Bağımlılık özellikleri ve ekli özellikler için daha gelişmiş kullanım senaryoları için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).

- Ayrıca bir özelliği iliştirilmiş bir özellik olarak ve bağımlılık özelliği olarak kaydedebilir, ancak yine de "sarmalayıcı" uygulamalarını kullanıma sunabilirsiniz. Bu durumda, özelliği bu öğe üzerinde ya da XAML ekli özelliği sözdizimi aracılığıyla herhangi bir öğede ayarlanabilir. Hem standart hem de ekli kullanımlar <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>için uygun senaryoya sahip bir özellik örneği.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [Ekli Özelliği Kaydetme](how-to-register-an-attached-property.md)
