---
title: Ekli Özelliklere Genel Bakış
description: Tüm nesneler üzerinde ayarlanabilir genel özellikler olan Windows Presentation Foundation eklenen özellikler hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 993f65024fcfc4f39a408c81af43b798360e6cf6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168389"
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış

İliştirilmiş özellik XAML tarafından tanımlanan bir kavramdır. İliştirilmiş bir özellik, herhangi bir nesne üzerinde ayarlanabilir bir genel özellik türü olarak kullanılmak üzere tasarlanmıştır. ' De [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , ekli özellikler genellikle geleneksel özelliği "sarmalayıcı" olmayan bir bağımlılık özelliği biçimi olarak tanımlanmıştır.

## <a name="prerequisites"></a>Kaynakları<a name="prerequisites"></a>

Bu makalede, sınıflarda var olan bağımlılık özellikleri tüketicisinin perspektifinden bağımlılık özelliklerini anladığınızı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)konusunu okuduğunuzu varsaymış olursunuz. Bu makaledeki örnekleri izlemek için XAML 'yi de anlamanız ve WPF uygulamalarının nasıl yazılacağını bilmeniz gerekir.

## <a name="why-use-attached-properties"></a>Ekli Özellikler neden kullanılmalıdır<a name="attached_properties_usage"></a>

İliştirilmiş bir özelliğin amacı, farklı alt öğelerin bir üst öğede tanımlanan bir özellik için benzersiz değerler belirtmesini sağlamaktır. Bu senaryonun belirli bir uygulaması, alt öğelerinin ' de sunulmaları için üst öğeyi bilgilendirmesini sağlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Özellik bir örnektir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>Özelliği iliştirilmiş bir özellik olarak oluşturulur, çünkü kendisi yerine içinde yer alan öğelerde ayarlanacak şekilde tasarlanmıştır <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel> . <xref:System.Windows.Controls.DockPanel>Sınıfı <xref:System.Windows.DependencyProperty> , adlı statik alanı tanımlar <xref:System.Windows.Controls.DockPanel.DockProperty> ve ardından <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemlerini iliştirilmiş özellik için ortak erişimci olarak sağlar.

## <a name="attached-properties-in-xaml"></a>XAML 'de Ekli Özellikler<a name="attached_properties_xaml"></a>

XAML 'de, *AttachedPropertyProvider*söz dizimini kullanarak iliştirilmiş özellikleri ayarlarsınız. *PropertyName*

XAML 'de nasıl ayarlayakullanabileceğinizi gösteren bir örnek aşağıda verilmiştir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> :

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Kullanım biraz statik bir özelliğe benzer; her zaman <xref:System.Windows.Controls.DockPanel> , ekli özelliği ada göre belirtilen herhangi bir örneğe başvurmak yerine, sahip olan türe başvurur ve kaydettirir.

Ayrıca, XAML 'deki iliştirilmiş bir özellik, biçimlendirme içinde ayarladığınız bir öznitelik olduğundan, yalnızca ayarlama işleminin herhangi bir ilgisi vardır. , Stillerdeki tetikleyiciler (Ayrıntılar için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma) gibi değerleri karşılaştırmak için bazı dolaylı mekanizmalar OLMASıNA rağmen xaml 'de doğrudan bir özelliği alamaz.

### <a name="attached-property-implementation-in-wpf"></a>WPF 'de ekli özellik uygulama

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]' De, WPF TÜRLERINDE UI ile ilgili iliştirilmiş özelliklerin çoğu bağımlılık özellikleri olarak uygulanır. İliştirilmiş özellikler bir XAML kavramıdır, ancak bağımlılık özellikleri bir WPF kavramıdır. WPF ekli özellikleri bağımlılık özellikleri olduğundan, özellik meta verileri gibi bağımlılık özelliği kavramlarını ve bu özellik meta verilerinden varsayılan değerleri destekler.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Iliştirilmiş özellikler sahip olan tür tarafından nasıl kullanılır<a name="howused"></a>

İliştirilmiş özellikler herhangi bir nesne üzerinde ayarlanabilir olsa da, özelliğin somut bir sonuç üreteceğinden veya değerin başka bir nesne tarafından kullanılmasını her zaman otomatik olarak anlamı yoktur. Genellikle, ekli özellikler, çok çeşitli olası sınıf hiyerarşileri veya mantıksal ilişkilerden gelen nesnelerin her biri, ekli özelliği tanımlayan türe ortak bilgiler raporlamasını sağlayacak şekilde tasarlanmıştır. İliştirilmiş özelliği tanımlayan tür genellikle bu modellerden birini izler:

- İliştirilmiş özelliği tanımlayan tür, ekli özellik için değerler ayarlanacak öğelerin üst öğesi olabilecek şekilde tasarlanmıştır. Daha sonra tür, alt nesnelerini bazı nesne ağacı yapısına karşı iç mantık aracılığıyla yineler, değerleri edinir ve bu değerler üzerinde bir şekilde davranır.

- İliştirilmiş özelliği tanımlayan tür, bir dizi olası üst öğe ve içerik modeli için alt öğe olarak kullanılacaktır.

- İliştirilmiş özelliği tanımlayan tür bir hizmeti temsil eder. Diğer türler ekli özellik için değerleri ayarlar. Ardından, özelliği ayarlanan öğe hizmet bağlamında değerlendirildiğinde, ekli özellik değerleri, hizmet sınıfının iç mantığı aracılığıyla elde edilir.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Üst tanımlı Iliştirilmiş özelliğe bir örnek

WPF 'in iliştirilmiş bir özelliği tanımladığı en tipik senaryo, bir üst öğe bir alt öğe koleksiyonunu desteklediğinde ve ayrıca davranışın özelliklerinin her bir alt öğe için ayrı olarak bildirildiği bir davranış uygular.

<xref:System.Windows.Controls.DockPanel><xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>iliştirilmiş özelliği tanımlar ve <xref:System.Windows.Controls.DockPanel> kendi işleme mantığının bir parçası olarak sınıf düzeyi koda sahiptir (özellikle <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> ve <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> ). <xref:System.Windows.Controls.DockPanel>Örnek, her zaman ilk alt öğelerinden birinin için bir değer ayarlayıp ayarlayamadığını kontrol eder <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . Bu durumda, bu değerler söz konusu alt öğeye uygulanan işleme mantığı için giriş haline gelir. İç içe yerleştirilmiş <xref:System.Windows.Controls.DockPanel> örneklerin her biri kendi kendine kendi alt öğe koleksiyonlarını değerlendirir, ancak bu davranış, işlem değerlerine göre uygulamaya özgüdür <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . En üst öğenin ötesinde öğeleri etkileyen iliştirilmiş özelliklerin olması teorik olarak mümkündür. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>İliştirilmiş özellik üzerinde <xref:System.Windows.Controls.DockPanel> işlem yapacak üst öğesi olmayan bir öğede ayarlandıysa, hata veya özel durum oluşmaz. Bu, genel bir özellik değerinin ayarlandığı, ancak bu bilgileri kullanabilecek geçerli bir üst öğesi olmadığı anlamına gelir <xref:System.Windows.Controls.DockPanel> .

## <a name="attached-properties-in-code"></a>Koddaki Ekli Özellikler<a name="attached_properties_code"></a>

WPF 'deki Ekli özellikler, kolay get/set erişimi için tipik CLR "sarmalayıcı" yöntemlerine sahip değildir. Bunun nedeni, iliştirilmiş özelliğin, özelliğin ayarlandığı örnekler için CLR ad alanının bir parçası olması değildir. Ancak, XAML ayrıştırıldığında XAML işlemcisi bu değerleri ayarlayabilmelidir. Etkin bir eklenmiş özellik kullanımını desteklemek için, iliştirilmiş özelliğin sahip türü, **Get_PropertyName_** ve **Set_PropertyName_** biçiminde adanmış erişimci yöntemleri uygulamalıdır. Bu adanmış erişimci yöntemleri, kodda ekli özelliği almak veya ayarlamak için de kullanışlıdır. Bir kod perspektifinden, iliştirilmiş bir özellik, özellik erişimcileri yerine Yöntem erişimcilerine sahip bir yedekleme alanıyla benzerdir ve bu alan, özellikle tanımlanmış olması gereken herhangi bir nesne üzerinde bulunabilir.

Aşağıdaki örnek, kodda ekli bir özelliği nasıl ayarlayakullanabileceğinizi gösterir. Bu örnekte, `myCheckBox` sınıfının bir örneğidir <xref:System.Windows.Controls.CheckBox> .

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML örneğine benzer şekilde, `myCheckBox` dördüncü kod satırı tarafından zaten bir alt öğesi olarak eklenmediyse `myDockPanel` , beşinci kod satırı bir özel durum oluşturmaz, ancak özellik değeri bir üst öğeyle etkileşime girmemelidir <xref:System.Windows.Controls.DockPanel> ve bu nedenle hiçbir şey yapmaz. Yalnızca <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> üst öğenin varlığı ile Birleşik bir alt öğe üzerinde ayarlanan bir değer, <xref:System.Windows.Controls.DockPanel> işlenen uygulamada etkin davranışa neden olur. (Bu durumda, ekli özelliği ayarlayabilir ve sonra ağaca iliştirebilirsiniz. Ya da ağaca iliştirilebilecek ve ardından ekli özelliği ayarlayabilirsiniz. Her iki eylem sırası da aynı sonucu sağlar.)

## <a name="attached-property-metadata"></a>Ekli Özellik meta verileri<a name="attached_properties_metadata"></a>

Özelliği kaydederken özelliği, özelliğin <xref:System.Windows.FrameworkPropertyMetadata> işleme, ölçüm ve benzerlerini etkilemesinin yanı sıra özelliğin özelliklerini belirtmek üzere ayarlanır. İliştirilmiş bir özelliğin meta verileri genellikle bağımlılık özelliğinden farklı değildir. İliştirilmiş özellik meta verilerinde bir geçersiz kılmada varsayılan bir değer belirtirseniz, bu değer geçersiz kılma sınıfının örneklerine örtük iliştirilmiş özelliğin varsayılan değeri olur. Özellikle, varsayılan değer, bazı bir işlem bu özelliğe ilişkin Yöntem erişimcisi aracılığıyla ekli bir özelliğin değerini sorguladığında `Get` , meta verileri belirttiğiniz sınıfın bir örneğini belirterek ve bu iliştirilmiş özelliğin değeri başka bir şekilde ayarlanmamışsa raporlanır.

Özellik değeri devralmayı bir özellikte etkinleştirmek istiyorsanız, eklenmemiş bağımlılık özellikleri yerine iliştirilmiş özellikleri kullanmanız gerekir. Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Özel Ekli Özellikler<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Ekli Özellik ne zaman oluşturulur<a name="create_attached_properties"></a>

Tanımlama sınıfı dışındaki sınıflar için kullanılabilir bir özellik ayarı mekanizmasının nedeni olduğunda iliştirilmiş bir özellik oluşturabilirsiniz. Bunun için en yaygın senaryo düzenidir. Var olan düzen özelliklerine örnekler, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> ve ' dir <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> . Burada etkinleştirilen senaryo, Düzen denetim öğeleri için alt öğe olarak var olan öğelerin, düzen gereksinimlerini düzen üst öğelerine tek tek hızlı bir şekilde ifade edebilmesidir. her biri, üst öğenin ekli bir özellik olarak tanımladığı bir özellik değeri.

İliştirilmiş bir özelliği kullanmak için başka bir senaryo ise sınıfınız bir hizmeti temsil ettiğinde ve sınıfların hizmeti daha saydam bir şekilde tümleştirmesini istediğinizde.

Ancak başka bir senaryo, **Özellikler** penceresi düzenlemesi gibi VISUAL Studio WPF tasarımcı desteğini almadır. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

Daha önce bahsedildiği gibi, özellik değeri devralmayı kullanmak istiyorsanız, ekli bir özellik olarak kaydetmeniz gerekir.

### <a name="how-to-create-an-attached-property"></a>Ekli Özellik oluşturma<a name="how_do_i_create_attached_properties"></a>

Sınıfınız, ekli özelliği başka türlerde kullanım için tamamen tanımlıyorsa, sınıfın türetilmesi gerekmez <xref:System.Windows.DependencyObject> . Ancak, <xref:System.Windows.DependencyObject> iliştirilmiş özelliğinin de bir bağımlılık özelliği olması için genel WPF modeli ' ni izlerseniz, ' den türetmeniz gerekir.

İliştirilmiş özelliği, türünde bir alan bildirerek bağımlılık özelliği olarak tanımlayın `public static readonly` <xref:System.Windows.DependencyProperty> . Bu alanı, yönteminin dönüş değerini kullanarak tanımlarsınız <xref:System.Windows.DependencyProperty.RegisterAttached%2A> . Alan adı, eklenen özellik adı ile eşleşmelidir ve `Property` tanımlayıcı alanları adlandırdıkları özelliklere karşılık olarak adlandırılan ŞIRKET WPF modelini takip eder. İliştirilmiş özellik sağlayıcısı, ekli özellik için erişimci olarak statik **Get_PropertyName_** ve **Set_PropertyName_** yöntemleri sağlamalıdır; Bu durum, özellik sisteminde ekli özelliği kullanamayan şekilde sonuçlanır.

> [!NOTE]
> İliştirilmiş özelliğin al erişimcisini atlarsanız, özelliğindeki veri bağlama Visual Studio ve Visual Studio için Blend gibi tasarım araçları 'nda çalışmaz.

#### <a name="the-get-accessor"></a>Get erişimcisi

**Get_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static object GetPropertyName(object target)`

- `target`Nesne, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> yöntemi parametresi olarak, <xref:System.Windows.UIElement> iliştirilmiş özelliği yalnızca örneklere ayarlanmayacak şekilde türlenmiştir <xref:System.Windows.UIElement> .

- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> <xref:System.Windows.Controls.Dock> değeri yalnızca bu sabit listesine ayarlanabileceğinden, yöntemi olarak.

#### <a name="the-set-accessor"></a>Set erişimcisi

**Set_PropertyName_** erişimcisinin imzası şu olmalıdır:

`public static void SetPropertyName(object target, object value)`

- `target`Nesne, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, yöntemi öğesini <xref:System.Windows.Controls.DockPanel.SetDock%2A> olarak, <xref:System.Windows.UIElement> iliştirilmiş özelliği yalnızca örneklere ayarlanmış şekilde türlenmiştir <xref:System.Windows.UIElement> .

- `value`Nesne, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> <xref:System.Windows.Controls.Dock> değeri yalnızca bu sabit listesine ayarlanabileceğinden, yöntemi olarak. Bu yöntemin değerinin, biçimlendirme içindeki iliştirilmiş özellik kullanımında ekli özelliğinizle karşılaştığında XAML yükleyicisindeki gelen giriş olduğunu unutmayın. Bu giriş, biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle, kullandığınız tür için tür dönüştürmesi, değer seri hale getirici veya biçimlendirme uzantısı desteğinin olması gerekir. bu şekilde, uygun tür öznitelik değerinden (sonunda yalnızca bir dize) oluşturulabilir.

Aşağıdaki örnek, bağımlılık özelliği kaydını ( <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi kullanılarak) ve **Get_PropertyName_** ve **Set_PropertyName_** erişimcileri gösterir. Örnekte, ekli özellik adı ' dir `IsBubbleSource` . Bu nedenle, erişimcilerinin ve olarak adlandırılması gerekir `GetIsBubbleSource` `SetIsBubbleSource` .

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>İliştirilmiş özellik öznitelikleri

WPF, yansıma işlemlerine eklenen özellikler hakkında bilgi sağlamak için tasarlanan çeşitli .NET özniteliklerini ve tasarımcılar gibi yansıma ve özellik bilgilerinin tipik kullanıcılarını tanımlar. İliştirilmiş özelliklerde sınırsız kapsam türü olduğundan, tasarımcıların XAML kullanan belirli bir teknoloji uygulamasında tanımlanmış tüm iliştirilmiş özelliklerin genel bir listesini kullanarak kullanıcıların aşırı yük duymaması için bir yol gerekir. WPF 'nin Ekli Özellikler için tanımladığı .NET öznitelikleri, belirli bir iliştirilmiş özelliğin bir Özellikler penceresinde gösterilmesi gereken durumları kapsama almak için kullanılabilir. Kendi özel ekli özellikleri için de bu öznitelikleri uygulamayı düşünebilirsiniz. .NET özniteliklerinin amacı ve sözdizimi, uygun başvuru sayfalarında açıklanmıştır:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Ekli Özellikler hakkında daha fazla bilgi<a name="more"></a>

- Ekli Özellik oluşturma hakkında daha fazla bilgi için bkz. [ekli özelliği kaydetme](how-to-register-an-attached-property.md).

- Bağımlılık özellikleri ve ekli özellikler için daha gelişmiş kullanım senaryoları için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).

- Ayrıca bir özelliği iliştirilmiş bir özellik olarak ve bağımlılık özelliği olarak kaydedebilir, ancak yine de "sarmalayıcı" uygulamalarını kullanıma sunabilirsiniz. Bu durumda, özelliği bu öğe üzerinde ya da XAML ekli özelliği sözdizimi aracılığıyla herhangi bir öğede ayarlanabilir. Hem standart hem de ekli kullanımlar için uygun senaryoya sahip bir özellik örneği <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Ekli Özelliği Kaydetme](how-to-register-an-attached-property.md)
