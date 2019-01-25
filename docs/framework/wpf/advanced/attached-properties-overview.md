---
title: Ekli Özelliklere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: e4f2b88b075a7806d2ca4c4a1e2cf3f027e71f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706238"
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış

Ekli özelliği, XAML tarafından tanımlanan bir kavramdır. Ekli özelliği herhangi bir nesne nelze nastavit v objektu genel özellik türü olarak kullanılmak üzere tasarlanmıştır. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]iliştirilmiş özellikler genellikle geleneksel "sarmalayıcı" özelliği yok. bir bağımlılık özelliği özel biçimi tanımlanır.

## Önkoşulları <a name="prerequisites"></a>

Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Bu konudaki örnekleri izlemek için ayrıca XAML anlamak ve WPF uygulamalarının nasıl yazılacağı bilmeniz.

## Neden ekli özelliklerini kullanma <a name="attached_properties_usage"></a>

Ekli özelliği tek amacı, farklı alt öğelerin aslında bir üst öğe içinde tanımlanan bir özellik için benzersiz değerler belirtmek izin vermektir. Belirli bir uygulama bu senaryonun nasıl içinde oldukları üst öğenin bildirmek alt öğeleri yaşıyor [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Bir örnek <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Özellik içinde yer alan öğeler üzerinde ayarlamak için tasarlandığından ekli özelliği oluşturulan bir <xref:System.Windows.Controls.DockPanel>, yerine <xref:System.Windows.Controls.DockPanel> kendisi. <xref:System.Windows.Controls.DockPanel> Sınıfı statik tanımlar <xref:System.Windows.DependencyProperty> adlı alan <xref:System.Windows.Controls.DockPanel.DockProperty>ve ardından sağlar <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> ekli özellik için ortak erişimciler olarak yöntemler.

## XAML içinde ekli özellikler <a name="attached_properties_xaml"></a>

XAML içinde ekli özellikler söz dizimini kullanarak ayarladığınız *AttachedPropertyProvider*. *PropertyName*

Nasıl ayarlanacağını gösteren bir örnek verilmiştir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> XAML içinde:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Kullanım için statik bir özellik biraz benzer olduğunu unutmayın; her zaman türü başvuru <xref:System.Windows.Controls.DockPanel> sahip olan ve ekli özellik kaydeder adıyla belirtilen herhangi bir örneğe başvuran yerine.

Ayrıca, XAML içinde ekli özelliği biçimlendirme içinde ayarlanan bir öznitelik olduğundan, yalnızca ayarlama işlemi herhangi bir ilgisi yoktur. Stiller Tetikleyicileri gibi değerleri karşılaştırmak için bazı dolaylı mekanizmalar olmasına rağmen bir özelliği XAML içinde doğrudan alınamıyor (Ayrıntılar için bkz [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>WPF uygulamasında ekli özellik

İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], kullanıcı Arabirimi sunum için ilgili WPF türleri üzerinde mevcut eklenen özelliklerin çoğu, bağımlılık özellikleri uygulanır. Bağımlılık özellikleri bir WPF kavramı ise iliştirilmiş özellikler bir XAML kavram olarak oldukça basittir. WPF iliştirilmiş özellikler bağımlılık özellikleri olduğundan, bunlar bağımlılık özelliği meta verileri ve bu özellik meta verisinden varsayılan değerleri gibi özelliği kavramlarını destekler.

## Ekli özelliklere sahip olan türü tarafından kullanılan nasıl <a name="howused"></a>

Ekli özellikler herhangi bir nesnede ayarlanabilir olsa da, bu otomatik olarak özelliğini ayarlayarak somut bir sonuç üretmek ya da değeri hiç olmadığı kadar başka bir nesne tarafından kullanılacak anlamına gelmez. Genellikle, böylece çok çeşitli olası sınıf Hiyerarşiler veya mantıksal ilişkileri gelen nesneleri tanımlayan ekli özellik türü, her rapor ortak bilgileri iliştirilmiş özellikler yöneliktir. Ekli özellik genellikle tanımlayan tür aşağıdakilerden birini bu modeller aşağıdaki gibidir:

-   Ekli özellik tanımlayan tür ekli özellik değerlerini ayarlar öğelerin üst öğesi olabilir şekilde tasarlanmıştır. Türü ardından alt nesneleri bazı nesne ağaç yapısı karşı İç mantık aracılığıyla yinelenir, değerlerini alır ve bu değerleri bir şekilde davranır.

-   Ekli özellik tanımlayan tür çeşitli olası üst öğe ve içerik modelleri için alt öğesi kullanılır.

-   Ekli özellik tanımlayan türü, bir hizmeti temsil eder. Diğer türleri ekli özellik değerlerini ayarlayın. Ardından, özelliğinin öğe service bağlamında değerlendirilir, ekli özellik değerleri hizmet sınıfı, dahili mantığını elde edilir.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Üst tanımlı ekli özellik örneği

Bir üst öğesi bir alt öğe koleksiyonu destekler ve ayrıca bir davranışı uygulayan WPF Ekli özelliği burada tanımlar en tipik bir senaryo burada davranışı tek tek her alt öğe için raporlandığı andır.

<xref:System.Windows.Controls.DockPanel> tanımlar <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özellik, ve <xref:System.Windows.Controls.DockPanel> işleme mantığı bir parçası olarak sınıf düzeyi koduna sahiptir (özellikle <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> ve <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> örneği herhangi ilk alt öğelerinden biri için bir değer ayarlamış olup olmadığını görmek için her zaman denetleyecek <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Bu durumda, bu değerleri, belirli bir alt öğeye uygulanan işleme mantığı için giriş haline gelir. İç içe geçmiş <xref:System.Windows.Controls.DockPanel> örnekleri kendi ilk alt öğe koleksiyonlarını kabul ancak uygulamaya özel, davranıştır nasıl <xref:System.Windows.Controls.DockPanel> işlemleri <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değerleri. Öğelerin ötesindeki ilk üst öğe etkileyen özellikler eklenmiş teorik olarak mümkündür. Varsa <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özellik sahip olmayan bir öğe üzerinde ayarlanmış <xref:System.Windows.Controls.DockPanel> üst öğesi, hata veya özel durum sırasında yapılacak oluşturulur. Bu yalnızca genel özellik değeri ayarlandı, ancak geçerli olduğu anlamına gelir <xref:System.Windows.Controls.DockPanel> bilgileri kullanabilecek üst.

## Kodda ekli özellikler <a name="attached_properties_code"></a>

Ekli Özellikler ' WPF'de tipik gerekmez [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] get/set kolay erişim için "sarmalayıcı" yöntemleri. Ekli özellik olmadığından budur mutlaka parçası [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı için örnekler özelliğinin ayarlandığı. Ancak, XAML işlemci XAML ayrıştırıldığında bu değerleri ayarlayabilirsiniz olması gerekir. Bir etkin ekli özellik kullanımı desteklemek için ekli özellik sahibi türü özel erişimci metotlarını biçiminde uygulamalıdır **Get_PropertyName_** ve **Set_PropertyName_**. Bu özel erişimci metotlarını almak veya kodda ekli özellik ayarlamak de kullanışlıdır. Kod açısından bakıldığında, ekli özelliği özellik erişimcileri yerine yöntemi erişimcileri sahip destek alanı benzer ve Destek alanı'nün herhangi bir nesne yerine özellikle tanımlanmasına gerek kalmadan bulunabilir var.

Aşağıdaki örnek kodda ekli özelliği nasıl ayarlayabileceğinizi gösterir. Bu örnekte, `myCheckBox` örneğidir <xref:System.Windows.Controls.CheckBox> sınıfı.

[!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML benzer durumda olmadığını `myCheckBox` zaten bir alt öğesi olarak eklenmemişse `myDockPanel` tarafından üçüncü kod satırının, Dördüncü satır kod bir özel durum oluşturmaz, ancak özellik değeri ile etkileşime değil bir <xref:System.Windows.Controls.DockPanel> üst ve bu nedenle hiçbir şey yapabilirsiniz. Yalnızca bir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değer kümesi varlığı ile birleştirilmiş bir alt öğesi üzerinde bir <xref:System.Windows.Controls.DockPanel> üst öğenin işlenmiş uygulamada etkili bir davranışa neden olur. (Bu durumda, ekli özellik ayarlayın, sonra ağacına iliştirin. Veya ağaca iliştirip sonra ekli özellik ayarlayın. Herhangi bir eylem sırada aynı sonucu sağlar.)

## İliştirilmiş özellik meta verileri <a name="attached_properties_metadata"></a>

Özellik kaydı sırasında <xref:System.Windows.FrameworkPropertyMetadata> özelliği işleme, ölçüm ve benzeri etkileyip özelliğinin özelliklerini belirtmek için ayarlanır. Ekli özelliği için meta veriler üzerinde bir bağımlılık özelliği genellikle farklı değildir. İliştirilmiş özellik meta verileri geçersiz kılmada varsayılan bir değer belirtirseniz, değer'örtük ekli özelliği geçersiz kılma sınıfının örneklerini varsayılan değerini olur. Varsayılan değer sorguları eklenen bir özellik değeri için bazı işlem, özellikle bildirilir `Get` yöntemi erişimcisi bu özellik, burada belirttiğiniz değerin yanı sıra meta veriler için sınıfının bir örneğini belirtme ekli özelliği ayarlı değil Aksi takdirde.

Özellik değeri kalıtımı özelliğini etkinleştirmek istiyorsanız, bağlı olmayan bir bağımlılık özellikleri yerine ekli özellikler kullanmanız gerekir. Ayrıntılar için bkz [özellik değeri kalıtımı](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

## Özel ekli özellikler <a name="custom"></a>

### Ekli özelliği oluşturma zamanı <a name="create_attached_properties"></a>

Bir özelliği tanımlayan sınıf dışındaki sınıflara yönelik mekanizmasını ayarlamak için bir neden olduğunda ekli özelliği oluşturabilirsiniz. En yaygın senaryo için bu düzeni ' dir. Varolan bir düzen özelliklerini örnekler <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. İşte burada etkin senaryo düzeni denetleme alt öğeleri olarak mevcut öğeleri öğeleri tek tek düzen üst öğeleri düzen gereksinimlerini ifade edebilirsiniz, her bir özellik değeri ayarı üst bağlı tanımlanan özellik.

Ekli özelliği kullanarak başka bir senaryo sınıfınızın bir hizmeti temsil eder ve hizmet daha saydam bir şekilde tümleştirebilir sınıflar istediğiniz durumdur.

Visual Studio WPF Tasarımcısı desteği gibi almak için başka bir senaryodur ancak **özellikleri** penceresi düzenleme. Daha fazla bilgi için [denetim yazmaya genel bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

Özellik değeri kalıtımı kullanmak istiyorsanız önce bahsedildiği gibi ekli özelliği kaydetme.

### Ekli özelliği oluşturma <a name="how_do_i_create_attached_properties"></a>

Sınıfınıza ekli özellik kullanımı için kesin olarak diğer türlerde tanımlanıyor demektir sınıfın türetilmesi gerekmez, <xref:System.Windows.DependencyObject>. Ancak türetilmesi gerekir <xref:System.Windows.DependencyObject> bağımlılık özelliği de, ekli özellik yaşama genel WPF modeli izleyin.

Bildirerek, ekli özellik bir bağımlılık özelliği olarak tanımlayan bir `public static readonly` türü alanını <xref:System.Windows.DependencyProperty>. Dönüş değerini kullanarak bu alan tanımladığınız <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. İliştirilmiş özellik adı dizesi ile eklenen alan adı eşleşmelidir `Property`, tanımlayıcı alanları temsil ettikleri özellikleri karşı adlandırma kurulan WPF desenini izler. İliştirilmiş özellik sağlayıcısı ayrıca statik sağlamalısınız **Get_PropertyName_** ve **Set_PropertyName_** ; iliştirilmiş özellik erişimcileri olarak yöntemler Bunu yapmak, başarısız özelliğin neden olur Sistem, ekli özellik erişememe.

> [!NOTE]
> Eklenen özelliğin get erişimcisine atlarsanız, veri bağlama özelliğini temel alan Tasarım araçları, Visual Studio ve Expression Blend gibi çalışmaz.

#### <a name="the-get-accessor"></a>Get erişimcisi

İmzası **Get_PropertyName_** erişimcisi olmalıdır:

`public static object GetPropertyName(object target)`

-   `target` Nesnesi, uygulamanızdaki daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> yöntemi türleri parametre olarak <xref:System.Windows.UIElement>, ekli özellik yalnızca üzerinde ayarlanmış olması da amaçlandığından <xref:System.Windows.UIElement> örnekleri.

-   Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntemi türleri olarak <xref:System.Windows.Controls.Dock>, değeri yalnızca, sabit listesine ayarlanabilir.

#### <a name="the-set-accessor"></a>Set erişimcileri

İmzası **Set_PropertyName_** erişimcisi olmalıdır:

`public static void SetPropertyName(object target, object value)`

-   `target` Nesnesi, uygulamanızdaki daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi türleri olarak <xref:System.Windows.UIElement>, ekli özellik yalnızca üzerinde ayarlanmış olması da amaçlandığından <xref:System.Windows.UIElement> örnekleri.

-   `value` Nesnesi, uygulamanızdaki daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi türleri olarak <xref:System.Windows.Controls.Dock>, değeri yalnızca, sabit listesine ayarlanabilir. Bu yöntem değeri, ekli özellik biçimlendirmede ekli özellik kullanımı karşılaştığında XAML yükleyicisinden gelen giriş olduğunu unutmayın. Söz konusu giriş biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle olmalıdır tür dönüştürme, değeri seri hale getirici veya kullanın, türü için işaretleme uzantısı desteği sağlayacak şekilde uygun türde (olan sonuç olarak bir dize) öznitelik değerinden oluşturulabilir.

Aşağıdaki örnek, bağımlılık özelliği kayıt gösterir (kullanarak <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi), hem de **Get_PropertyName_** ve **Set_PropertyName_** erişimcileri. Örnekte, ekli özellik addır `IsBubbleSource`. Bu nedenle, erişimcileri adlandırılmalıdır `GetIsBubbleSource` ve `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>İliştirilmiş özellik öznitelikleri

WPF tanımlar birkaç [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] yansıma işlemleri ve yansıma ve özellik bilgileri tasarımcıları gibi tipik kullanıcıların iliştirilmiş özellikler hakkında bilgi sağlamak için yöneliktir. Ekli özellikler sınırsız kapsam türü olduğundan, tasarımcılar genel XAML kullanan bir belirli teknoloji uygulama içinde tanımlanan tüm ekli özellikler listesini zorlamayı kullanıcılarla önlemek için bir yol gerekir. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] İliştirilmiş özellikler nerede ekli özelliğe gösterilip gösterilemeyeceğini Özellikler penceresinde durumlarda kapsam için kullanılabilir, WPF tanımlar. Bu öznitelikler için kendi özel ekli özellikler uygulamayı düşünebilirsiniz. Amaç ve sözdizimi [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] uygun başvuru sayfalarına açıklanmıştır:

-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Ekli özellikler hakkında daha fazla öğrenme <a name="more"></a>

-   Ekli özelliği oluşturma hakkında daha fazla bilgi için bkz. [iliştirilmiş özellik](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).

-   Daha fazla Gelişmiş bağımlılık özellikleri için kullanım senaryoları ve iliştirilmiş özellikler için bkz [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

-   Ayrıca bir özelliği ekli özelliği ve bağımlılık özelliği olarak kaydedebilirsiniz, ancak hala "sarmalayıcı" uygulamaları sunarsınız. Bu durumda, özellik, bu öğe üzerinde ayarlanabilir veya XAML aracılığıyla herhangi bir öğe üzerinde özellik sözdizimi bağlı. Bir özellik hem standart hem de bağlı kullanımlar için uygun bir senaryoyla örneğidir <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Ekli Özelliği Kaydetme](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)