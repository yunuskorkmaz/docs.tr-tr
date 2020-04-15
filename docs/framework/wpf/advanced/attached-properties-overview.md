---
title: Ekli Özelliklere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 5086401f4616074d364c1d387b751116120d5969
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389008"
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış

Ekli özellik XAML tarafından tanımlanan bir kavramdır. Ekli bir özellik, herhangi bir nesne üzerinde ayarlanabilir genel özellik türü olarak kullanılmak üzere tasarlanmıştır. , [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ekli özellikleri genellikle geleneksel özelliği "sarıcı" olmayan bağımlılık özelliği özel bir form olarak tanımlanır.

## <a name="prerequisites"></a>Önkoşullar<a name="prerequisites"></a>

Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özellikleri Genel [Bakış'ı](dependency-properties-overview.md)okuduğunuzu varsayar. Bu konudaki örnekleri takip etmek için XAML'yi de anlamanız ve WPF uygulamalarının nasıl yazılabildiğini bilmeniz gerekir.

## <a name="why-use-attached-properties"></a>Neden Ekli Özellikleri Kullanın<a name="attached_properties_usage"></a>

Ekli bir özelliğin bir amacı, farklı alt öğelerin bir üst öğede gerçekten tanımlanan bir özellik için benzersiz değerler belirtmesine izin vermektir. Bu senaryonun belirli bir uygulama alt öğeleri nasıl sunulması için üst [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]öğeyi bilgilendirmek olmasıdır. Bir örnek <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliğidir. Özellik, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> kendi içinde <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel> değil, bir içinde bulunan öğeler üzerinde ayarlanacak şekilde tasarlandığından, ekli bir özellik olarak oluşturulur. Sınıf <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.DependencyProperty> adlı <xref:System.Windows.Controls.DockPanel.DockProperty>statik alanı tanımlar ve daha <xref:System.Windows.Controls.DockPanel.GetDock%2A> <xref:System.Windows.Controls.DockPanel.SetDock%2A> sonra ekli özellik için ortak erişimci olarak ve yöntemleri sağlar.

## <a name="attached-properties-in-xaml"></a>XAML'de Eklenen Özellikler<a name="attached_properties_xaml"></a>

XAML'de, bağlı özellikleri bağlı Özellik *Sağlayıcısı'nı*kullanarak ayarlarsınız. *Özellik Adı*

Aşağıda XAML'de nasıl <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ayarlayabildiğinize bir örnek verilmiştir:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Kullanımın statik bir özelliğe biraz benzediğini unutmayın; her zaman ada göre belirtilen herhangi bir örne başvurmak yerine ekli özelliğin sahibi ve kaydı olan türüne <xref:System.Windows.Controls.DockPanel> başvurursunuz.

Ayrıca, XAML'de eklenmiş bir özellik biçimlendirmede ayarladığınız bir özellik olduğundan, yalnızca ayarlanan işlemin herhangi bir önemi vardır. Stildeki tetikleyiciler gibi değerleri karşılaştırmak için bazı dolaylı mekanizmalar olmasına rağmen, Doğrudan XAML'de bir özellik alamazsınız (ayrıntılar için [Stil ve Templating'e](../controls/styling-and-templating.md)bakın).

### <a name="attached-property-implementation-in-wpf"></a>WPF'de Ekli Özellik Uygulaması

,, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]UI sunusuile ilgili WPF türlerinde bulunan ekli özelliklerin çoğunda bağımlılık özellikleri olarak uygulanır. Ekli özellikler bir XAML kavramı, bağımlılık özellikleri ise bir WPF kavramıdır. WPF eklenmiş özellikleri bağımlılık özellikleri olduğundan, özellik meta verileri gibi bağımlılık özelliği kavramlarını ve bu özellik meta verilerinden varsayılan değerleri desteklerler.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Ekli Özellikler SahipLenme Türüne Göre Nasıl Kullanılır?<a name="howused"></a>

Ekli özellikler herhangi bir nesne üzerinde ayarlanabilir olsa da, bu otomatik olarak özelliği ayarlama nın somut bir sonuç üreteceği veya değerin başka bir nesne tarafından kullanılacağı anlamına gelmez. Genel olarak, ekli özellikler, çok çeşitli olası sınıf hiyerarşilerinden veya mantıksal ilişkilerden gelen nesnelerin her biri ortak bilgileri bağlı özelliği tanımlayan türe bildirebilmeleri için tasarlanmıştır. Ekli özelliği tanımlayan tür genellikle aşağıdaki modellerden birini izler:

- Ekli özelliği tanımlayan tür, ekli özellik için değerleri ayarlayacak öğelerin ana öğesi olacak şekilde tasarlanmıştır. Tür daha sonra bazı nesne ağacı yapısına karşı iç mantık yoluyla alt nesneleri yineler, değerleri elde eder ve bir şekilde bu değerler üzerinde hareket eder.

- Ekli özelliği tanımlayan tür, çeşitli olası üst öğeler ve içerik modelleri için alt öğe olarak kullanılır.

- Ekli özelliği tanımlayan tür bir hizmeti temsil eder. Diğer türler ekli özellik için değerleri ayarlar. Daha sonra, özelliği ayarlayan öğe hizmet bağlamında değerlendirildiğinde, ekli özellik değerleri hizmet sınıfının iç mantığı yla elde edilir.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Üst Tanımlı Ekli Özellik Örneği

WPF'nin eklenmiş bir özelliği tanımladığı en tipik senaryo, bir üst öğenin bir alt öğe koleksiyonunu desteklemesi ve ayrıca davranışın ayrıntılarının her alt öğe için ayrı ayrı raporlandığı bir davranış uygulamasıdır.

<xref:System.Windows.Controls.DockPanel>ekli özelliği tanımlar ve <xref:System.Windows.Controls.DockPanel> işleme mantığının bir parçası olarak sınıf düzeyi <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> kodu vardır (özellikle ve). <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Bir <xref:System.Windows.Controls.DockPanel> örnek her zaman, yakın alt öğelerinden herhangi birinin <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Bu durumda, bu değerler, söz konusu alt öğeye uygulanan işleme mantığı için giriş olur. İç <xref:System.Windows.Controls.DockPanel> içe geçen örneklerin her biri kendi hemen alt öğe koleksiyonlarını <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ele alır, ancak bu davranış, işlemlerin değerlerine nasıl özel bir uygulamadır. Teorik olarak, yakın ebeveynin ötesindeki öğeleri etkileyen eklenmiş özelliklere sahip olmak mümkündür. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Ekli özellik, üzerinde hareket etmek için <xref:System.Windows.Controls.DockPanel> hiçbir üst öğe olan bir öğe üzerinde ayarlanmışsa, hiçbir hata veya özel durum yükseltilir. Bu sadece, genel bir özellik değerinin ayarlandığını, <xref:System.Windows.Controls.DockPanel> ancak bilgileri tüketebilecek geçerli bir üst öğesi olmadığı anlamına gelir.

## <a name="attached-properties-in-code"></a>Koda Ekli Özellikler<a name="attached_properties_code"></a>

WPF'deki ekli özellikler, kolay erişim/ayarla erişimi için tipik CLR "sarıcı" yöntemlerine sahip değildir. Bunun nedeni, ekli özelliğin, özelliğin ayarlandığı durumlar için CLR ad alanının mutlaka bir parçası olmamasıdır. Ancak, xaml ayrıştırıldığında bir XAML işlemci bu değerleri ayarlamak gerekir. Etkili bir ekli özellik kullanımını desteklemek için, ekli özelliğin sahibi nin **Get_PropertyName_** ve **Set_PropertyName_** şeklinde özel erişim yöntemleri uygulaması gerekir. Bu özel erişimyöntemleri, ekli özelliği kodda almak veya ayarlamak için de yararlıdır. Kod açısından bakıldığında, ekli bir özellik, özellik erişime girenler yerine yöntem erişime sahip bir destek alanına benzer ve destek alanı özel olarak tanımlanması yerine herhangi bir nesneüzerinde bulunabilir.

Aşağıdaki örnek, ekli bir özelliği kodda nasıl ayarlayabildiğinizi gösterir. Bu örnekte, `myCheckBox` <xref:System.Windows.Controls.CheckBox> sınıfın bir örneğidir.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML örneğine benzer `myCheckBox` şekilde, dördüncü kod satırı `myDockPanel` tarafından bir alt öğe olarak zaten eklenmemiş olsaydı, beşinci kod satırı bir özel <xref:System.Windows.Controls.DockPanel> durum uyandırmaz, ancak özellik değeri bir üst öğeyle etkileşime girmez ve bu nedenle hiçbir şey yapmaz. Yalnızca <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> bir alt öğe üzerinde ayarlanmış bir <xref:System.Windows.Controls.DockPanel> değer bir üst öğenin varlığı ile birlikte işlenen uygulamada etkili bir davranış neden olur. (Bu durumda, bağlı özelliği ayarlayabilir, sonra ağaca takabilirsiniz. Ya da ağaca bağlayıp bağlı özelliği ayarlayabilirsiniz. Her iki eylem sırası da aynı sonucu sağlar.)

## <a name="attached-property-metadata"></a>Ekli Özellik Meta verileri<a name="attached_properties_metadata"></a>

Özelliği kaydederken, <xref:System.Windows.FrameworkPropertyMetadata> özelliğin işleme, ölçüm ve benzeri etkileri olup olmadığı gibi özelliğin özelliklerini belirtmek için ayarlanır. Ekli bir özellik için meta veriler genellikle bağımlılık özelliğinden farklı değildir. Ekli özellik meta verilerine geçersiz bir geçersiz kılmada varsayılan değer belirtirseniz, bu değer geçersiz sınıf örneklerinde örtülü ekli özelliğin varsayılan değeri olur. Özellikle, meta verileri belirttiğiniz sınıfın bir örneğini belirterek ve `Get` ekteki özelliğin değeri aksi şekilde ayarlanmamışsa, bağlı bir özelliğin değeri için bazı işlem sorguları bildirilir.

Bir özellik üzerinde özellik değeri devralmasını etkinleştirmek istiyorsanız, iliştirilmeyen bağımlılık özellikleri yerine ekli özellikleri kullanmanız gerekir. Ayrıntılar [için, Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)

## <a name="custom-attached-properties"></a>Özel Ekli Özellikler<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Ekli Özellik Ne Zaman Oluşturulur?<a name="create_attached_properties"></a>

Tanımlayıcı sınıf dışındaki sınıflar için özellik ayar mekanizması nın bulunması için bir neden olduğunda ekli bir özellik oluşturabilirsiniz. Bunun için en yaygın senaryo düzendir. Varolan düzen özelliklerine <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>örnek <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>olarak , ve . Burada etkinleştirilen senaryo, düzen denetim elemanları için alt öğeler olarak var olan öğelerin, her ana aygıtın eklenmiş bir özellik olarak tanımladığı bir özellik değeri ayarlayarak, düzen üst öğelerine düzen gereksinimlerini ayrı ayrı ifade edebilmesidir.

Ekli bir özelliği kullanmak için başka bir senaryo, sınıfınızın bir hizmeti temsil etmesi ve sınıfların hizmeti daha saydam bir şekilde tümleştirebilmesini istediğiniz zamandır.

Başka bir senaryo, **Özellikler** pencere düzenleme gibi Visual Studio WPF Designer desteği almaktır. Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)

Daha önce de belirtildiği gibi, özellik değeri devralma kullanmak istiyorsanız ekli bir özellik olarak kaydolmanız gerekir.

### <a name="how-to-create-an-attached-property"></a>Ekli Özellik Nasıl Oluşturulur?<a name="how_do_i_create_attached_properties"></a>

Sınıfınız ekli özelliği kesinlikle diğer türlerde kullanılmak üzere tanımlıyorsa, sınıfın .'den <xref:System.Windows.DependencyObject>türemesi gerekmez. Ancak, bağlı özelliğinize <xref:System.Windows.DependencyObject> sahip olmanın genel WPF modelini takip ederseniz, bir bağımlılık özelliği de elde etmek gerekir.

Bir tür `public static readonly` <xref:System.Windows.DependencyProperty>alanı beyan ederek ekli özelliğinizi bağımlılık özelliği olarak tanımlayın. <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Yöntemin geri dönüş değerini kullanarak bu alanı tanımlarsınız. Alan adı, tanımlayıcı alanları temsil ettikleri özelliklere göre `Property`adlandırma kurulu WPF deseni izlemek için dize ile eklenen, ekli özellik adı eşleşmesi gerekir. Ekli özellik sağlayıcısı da ekli özellik için aksesuar olarak statik **Get_PropertyName_** ve **Set_PropertyName_** yöntemleri sağlamalıdır; bunu yapmamak, özellik sisteminin bağlı özelliğinizi kullanamamasına neden olur.

> [!NOTE]
> Ekli özelliğin erişime erişimini atlarsanız, özellik üzerindeki veri bağlama, Visual Studio ve Visual Studio için Blend gibi tasarım araçlarında çalışmaz.

#### <a name="the-get-accessor"></a>Erişime Erişim

**Get_PropertyName_** erişimcisinin imzası aşağıdaki olmalıdır:

`public static object GetPropertyName(object target)`

- Nesne, `target` uygulamanızda daha özel bir tür olarak belirtilebilir. Örneğin, bağlı <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> özellik yalnızca örneklerde <xref:System.Windows.UIElement> <xref:System.Windows.UIElement> ayarlanacak şekilde tasarlandığı için yöntem parametreyi , olarak yıtipler.

- İade değeri, uygulamanızda daha özel bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntem , değer <xref:System.Windows.Controls.Dock>yalnızca bu numaralandırmaya ayarlanabildiği için, yöntem olarak yıtürler.

#### <a name="the-set-accessor"></a>Set Erişimcisi

**Set_PropertyName_** erişimcisi için imza olmalıdır:

`public static void SetPropertyName(object target, object value)`

- Nesne, `target` uygulamanızda daha özel bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntem, ekli <xref:System.Windows.UIElement>özellik yalnızca örneklerüzerinde <xref:System.Windows.UIElement> ayarlanacak şekilde tasarlanmıştır, çünkü, olarak yı türler.

- Nesne, `value` uygulamanızda daha özel bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntem , değer <xref:System.Windows.Controls.Dock>yalnızca bu numaralandırmaya ayarlanabildiği için, yöntem olarak yıtürler. Bu yöntemin değerinin, işaretlemede ekli özellik kullanımında ekli özelliğinizle karşılaştığında XAML yükleyicisinden gelen giriş olduğunu unutmayın. Bu giriş, biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle, kullandığınız tür için tür dönüştürme, değer serializer veya biçimlendirme uzantısı desteği olmalıdır, böylece uygun tür öznitelik değerinden oluşturulabilir (sonuçta sadece bir dize).

Aşağıdaki örnek, bağımlılık özelliği kaydının <xref:System.Windows.DependencyProperty.RegisterAttached%2A> (yöntemi kullanarak) yanı sıra **Get_PropertyName_** ve **Set_PropertyName_** erişimcileri gösterir. Örnekte, ekli özellik `IsBubbleSource`adı. Bu nedenle, erişime girenlerin adı `GetIsBubbleSource` ve `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Ekli Özellik Öznitelikleri

WPF, yansıma işlemlerine eklenen özellikler ve tasarımcılar gibi tipik yansıma ve özellik bilgileri kullanıcıları hakkında bilgi sağlamayı amaçlayan birkaç .NET öznitelikleri tanımlar. Ekli özelliklerisınırsız kapsam türü olduğundan, tasarımcılar XAML kullanan belirli bir teknoloji uygulamasında tanımlanan tüm ekli özelliklerin genel bir listesi ile ezici kullanıcılar önlemek için bir yol gerekir. WPF'nin eklenmiş özellikler için tanımladığı .NET öznitelikleri, belirli bir ekli özelliğin özellikler penceresinde gösterilmesi gereken durumları kapsamak için kullanılabilir. Bu öznitelikleri kendi özel bağlı özellikleriniz için de uygulamayı düşünebilirsiniz. .NET özniteliklerinin amacı ve sözdizimi uygun başvuru sayfalarında açıklanmıştır:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Ekli Özellikler Hakkında Daha Fazla Bilgi Edinme<a name="more"></a>

- Ekli bir özellik oluşturma hakkında daha fazla bilgi için [bkz.](how-to-register-an-attached-property.md)

- Bağımlılık özellikleri ve bağlı özellikler için daha gelişmiş kullanım senaryoları için Bkz. [Özel Bağımlılık Özellikleri.](custom-dependency-properties.md)

- Ayrıca, bir özelliği ekli bir özellik olarak ve bağımlılık özelliği olarak kaydedebilirsiniz, ancak sonra yine de "sarıcı" uygulamalarını ortaya çıkarabilirsiniz. Bu durumda, özellik bu öğe üzerinde veya XAML ekli özellik sözdizimi aracılığıyla herhangi bir öğe üzerinde ayarlanabilir. Hem standart hem de bağlı kullanımlar için uygun bir <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>senaryoya sahip bir özelliğin bir örneği.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Ekli Özelliği Kaydetme](how-to-register-an-attached-property.md)
