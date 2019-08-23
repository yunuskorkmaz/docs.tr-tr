---
title: WPF XAML Ad Kapsamları
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917332"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML Ad Kapsamları
Xaml ad kapsamları, XAML 'de tanımlanan nesneleri tanımlayan bir kavramdır. XAML namescope 'daki adlar, nesne ağacındaki nesnelerin XAML tanımlı adları ve örnek eşdeğerleri arasında ilişki kurmak için kullanılabilir. Genellikle, bir xaml uygulaması için tek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML sayfa kökleri yüklenirken Yönetilen koddaki xaml ad kapsamları oluşturulur. Programlama nesnesi <xref:System.Windows.Markup.INameScope> arabirim tarafından tanımlandığından ve ayrıca pratik sınıf <xref:System.Windows.NameScope>tarafından uygulanan xaml ad kapsamları.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Yüklenen XAML uygulamalarında Namescopes  
 Daha geniş bir programlama veya bilgisayar bilimi bağlamında, programlama kavramları genellikle bir nesneye erişmek için kullanılabilecek benzersiz bir tanımlayıcı veya ad ilkesini içerir. Tanımlayıcı veya ad kullanan sistemlerde, NameScope bir işlemin veya tekniğin, bu adı bir nesne isteniyorsa veya tanımlayıcı adların benzersizlik alanındaki sınırlar zorlandığında arama yapılacak sınırları tanımlar. Bu genel ilkeler XAML namescopes için geçerlidir. WPF 'de, xaml ad kapsamları, sayfa yüklendiğinde bir XAML sayfası için kök öğede oluşturulur. Sayfa kökünden başlayarak XAML sayfasında belirtilen her ad, ilgili XAML namescope 'a eklenir.  
  
 WPF XAML 'de ortak kök öğeler ( <xref:System.Windows.Controls.Page>ve <xref:System.Windows.Window>gibi) olan öğeler her zaman bir xaml namescope 'u denetler. <xref:System.Windows.FrameworkElement> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Ya <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> da gibi bir öğe, biçimlendirme içindeki sayfanın kök öğesi ise, bir işlemci, çalışma xaml namescope sağlamak üzere örtülü olarak bir kök ekler. <xref:System.Windows.FrameworkContentElement>  
  
> [!NOTE]
> WPF derleme eylemleri, `Name` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İşaretlemede herhangi bir öğe üzerinde hiçbir veya `x:Name` öznitelik tanımlanmasa bile xaml üretimi için xaml namescope oluşturur.  
  
 Aynı adı herhangi bir XAML namescope 'da iki kez kullanmayı denerseniz, bir özel durum oluşturulur. Kod arkasında ve derlenmiş bir uygulamanın parçası olan WPF XAML için, ilk biçimlendirme derlemesi sırasında sayfa için oluşturulan sınıf oluşturulurken WPF derleme eylemleri tarafından derleme zamanında oluşturulur. Herhangi bir yapı eylemi tarafından işaretleme tarafından derlenmediği XAML için, XAML yüklendiğinde XAML namescope sorunlarıyla ilgili özel durumlar ortaya çıkabilir. XAML tasarımcıları Ayrıca tasarım zamanında XAML namescope sorunlarını da tahmin edebilir.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Çalışma zamanı nesne ağaçlarına nesne ekleme  
 XAML 'nin ayrıştırılmasından sonra WPF XAML namescope 'un oluşturulduğu ve tanımlandığı zaman şu anda temsil edilir. Bu ağacı oluşturan xaml ayrıştırıldıktan sonra bir noktada nesne ağacına bir nesne eklerseniz, yeni nesnedeki bir `Name` veya `x:Name` değer bir xaml namescope 'daki bilgileri otomatik olarak güncelleştirmez. Xaml yüklendikten sonra bir nesne için bir WPF XAML namescope 'a bir ad eklemek için, genellikle XAML sayfa kökü olan xaml namescope <xref:System.Windows.Markup.INameScope.RegisterName%2A> öğesini tanımlayan nesnenin uygun uygulamasını çağırmanız gerekir. Ad kayıtlı değilse, eklenen nesneye <xref:System.Windows.FrameworkElement.FindName%2A>, gibi yöntemler aracılığıyla adı başvuramaz ve bu adı animasyon hedefleme için kullanamazsınız.  
  
 Uygulama geliştiricileri için en yaygın senaryo, adları sayfanın geçerli kökündeki xaml <xref:System.Windows.FrameworkElement.RegisterName%2A> NameScope 'a kaydetmek için kullanacaksınız. <xref:System.Windows.FrameworkElement.RegisterName%2A>animasyonların nesnelerini hedefleyen görsel taslak için önemli bir senaryonun bir parçasıdır. Daha fazla bilgi için bkz. görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
 Xaml namescope <xref:System.Windows.FrameworkElement.RegisterName%2A> 'u tanımlayan nesne dışında bir nesne üzerinde çağrı yaparsanız, bu ad hala çağıran nesnenin içinde tutulduğu xaml namescope 'a kaydedilir, nesne tanımlayan xaml namescope üzerinde çağırmışsınız <xref:System.Windows.FrameworkElement.RegisterName%2A> gibi.  
  
### <a name="xaml-namescopes-in-code"></a>Koddaki XAML namescopes  
 Kodda xaml ad kapsamları oluşturabilir ve bunları kullanabilirsiniz. XAML, XAML kendisini işlerken bu API 'leri ve kavramları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullandığından, xaml namescope oluşturmaya dahil olan API 'ler ve kavramlar, saf kod kullanımı için de aynıdır. Kavramlar ve API, genellikle XAML 'de kısmen veya tamamen tanımlanmış bir nesne ağacı içinde ada göre nesne bulabilme amacıyla vardır.  
  
 Programlı olarak oluşturulan ve yüklü xaml 'den olmayan uygulamalar için, bir xaml namescope <xref:System.Windows.Markup.INameScope>tanımlayan nesne, bir xaml namescope 'un kendi üzerinde oluşturulmasını desteklemek için veya bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf olmalıdır. larında.  
  
 Ayrıca, XAML işlemcisi tarafından yüklenmeyen ve işlenen tüm öğeler için, nesne için XAML namescope varsayılan olarak oluşturulmaz veya başlatılmaz. Adları daha sonra kaydetmek istediğiniz herhangi bir nesne için açıkça yeni bir XAML namescope oluşturmanız gerekir. XAML namescope oluşturmak için static <xref:System.Windows.NameScope.SetNameScope%2A> yöntemi çağırın. `dependencyObject` Parametresi olarak sahip olacağı nesneyi ve `value` parametresi olarak yeni <xref:System.Windows.NameScope.%23ctor%2A> bir Oluşturucu çağrısını belirtin.  
  
 İçin `dependencyObject` <xref:System.Windows.Markup.INameScope> <xref:System.Windows.FrameworkElement.RegisterName%2A> olarak belirtilen nesne bir uygulama<xref:System.Windows.FrameworkElement> değilse veya<xref:System.Windows.FrameworkContentElement>herhangi bir alt öğenin çağrılması hiçbir etkiye sahip olmaz. <xref:System.Windows.NameScope.SetNameScope%2A> Yeni xaml namescope 'u açıkça oluşturmadıysanız, çağrısı <xref:System.Windows.FrameworkElement.RegisterName%2A> bir özel durum oluşturacak.  
  
 Kodda XAML namescope API 'Lerinin kullanılmasına ilişkin bir örnek için bkz. [ad kapsamını tanımlama](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Stillerde ve şablonlarda XAML namescopes  
 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stiller ve şablonlar, içeriği kolay bir şekilde yeniden kullanma ve yeniden uygulama yeteneği sağlar. Ancak, stiller ve şablonlar, şablon düzeyinde tanımlı XAML adları olan öğeleri de içerebilir. Aynı şablon bir sayfada birden çok kez kullanılabilir. Bu nedenle, stiller ve şablonlar, stil veya şablonun uygulandığı bir nesne ağacındaki herhangi bir konumdan bağımsız olarak kendi XAML namescopes değerlerini tanımlar.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Burada, aynı şablon iki farklı düğmeye de uygulanır. Şablonlarda ayrık xaml namescopes yoksa, `TheBorder` şablonda kullanılan ad xaml namescope 'da ad çakışmasına neden olur. Şablonun her örneklenmesi kendi XAML namescope 'a sahiptir. bu nedenle, bu örnekte oluşturulan her şablonun XAML namescope tam olarak bir ad içerir.  
  
 Stiller, genellikle görsel taslaklara ait bölümlerin atanabileceği belirli adlara sahip olması için kendi XAML namescope değerlerini de tanımlar. Bu adlar, şablon denetim özelleştirmenin bir parçası olarak yeniden tanımlansa bile, bu adın öğelerini hedefleyecek özel davranışları denetlemenize olanak tanır.  
  
 Ayrı XAML namescopes 'ler nedeniyle, bir şablonda adlandırılmış öğelerin bulunması, bir sayfada Şablonsuz adlandırılmış bir öğe bulmadan daha zor. Önce şablonun uygulandığı denetimin <xref:System.Windows.Controls.Control.Template%2A> özellik değerini alarak uygulanan şablonu belirlemeniz gerekir. Daha sonra, şablonunun ikinci parametre olarak uygulandığı <xref:System.Windows.FrameworkTemplate.FindName%2A>denetimi geçirerek uygulamasının şablon sürümünü çağırabilirsiniz.  
  
 Bir denetim yazarınız ve uygulanan bir şablonda belirli bir adlandırılmış öğenin, denetimin kendisi tarafından tanımlanan bir davranışın hedefi olduğu bir kural oluşturuyorsanız, denetim uygulama kodunuzda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> yöntemini kullanabilirsiniz. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Yöntemi korunur, bu nedenle yalnızca denetim yazarının buna erişimi vardır.  
  
 Bir şablon içinden çalışıyorsanız ve şablonun uygulandığı xaml namescope 'a erişmeniz gerekiyorsa, değerini alın ve ardından bu değeri <xref:System.Windows.FrameworkElement.TemplatedParent%2A>çağırın. <xref:System.Windows.FrameworkElement.FindName%2A> Şablon içinde çalışma örneği, etkinliğin uygulanan şablondaki bir öğeden oluşturulduğu olay işleyicisi uygulamasını yazıyorsanız olur.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML namescopes ve adla ilgili API 'Ler  
 <xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkElement.FindName%2A> ,<xref:System.Windows.FrameworkElement.RegisterName%2A> ve yöntemleri<xref:System.Windows.FrameworkElement.UnregisterName%2A> . Bu yöntemleri bir XAML namescope 'ın sahibi olarak çağırırsanız, Yöntemler ilgili XAML namescope 'un yöntemlerine çağrı yapılır. Aksi takdirde, üst öğe bir XAML namescope 'a sahip olup olmadığını görmek için denetlenir ve bu işlem XAML namescope bulunana kadar yinelemeli olarak devam eder (XAML işlemci davranışı nedeniyle, kökte XAML namescope olması garanti edilir). <xref:System.Windows.FrameworkContentElement>, hiçbir <xref:System.Windows.FrameworkContentElement> zaman xaml namescope 'a sahip olmadığı özel durum dışında, benzer davranışları vardır. Yöntemler, çağrının sonunda <xref:System.Windows.FrameworkContentElement> bir <xref:System.Windows.FrameworkElement> üst öğeye iletilebilmesi için üzerinde bulunur.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>, yeni bir XAML namescope 'ı varolan bir nesneyle eşlemek için kullanılır. XAML namescope <xref:System.Windows.NameScope.SetNameScope%2A> 'u sıfırlamak veya temizlemek için birden çok kez çağırabilirsiniz, ancak bu genel kullanım değildir. Ayrıca, <xref:System.Windows.NameScope.GetNameScope%2A> koddan genellikle kullanılmaz.  
  
### <a name="xaml-namescope-implementations"></a>XAML namescope uygulamaları  
 Aşağıdaki sınıflar doğrudan uygulanır <xref:System.Windows.Markup.INameScope> :  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>XAML adlarını veya ad kapsamları 'yi kullanmaz; Bunun yerine anahtarları kullanır, çünkü bir sözlük uygulamasıdır. <xref:System.Windows.ResourceDictionary> Uygulayan <xref:System.Windows.ResourceDictionary> tek neden, gerçek bir xaml namescope ve bir tanıtıcı anahtarları arasındaki ayrımı açıklığa kavuşturmak ve ayrıca xaml ad kapsamları 'nin bir öğesine uygulanmamasını sağlamak için Kullanıcı koduna özel durumlar yükseltebilmesini sağlar. <xref:System.Windows.Markup.INameScope> <xref:System.Windows.ResourceDictionary> üst öğelere göre.  
  
 <xref:System.Windows.FrameworkTemplate>ve <xref:System.Windows.Style> açık <xref:System.Windows.Markup.INameScope> arabirim tanımları aracılığıyla uygulayın. Açık uygulamalar, bu xaml ad copes 'nin <xref:System.Windows.Markup.INameScope> arabirim üzerinden erişildiğinde genel olarak davranmasına izin verir, bu da xaml ad kapsamları 'in iç işlemlere göre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nasıl iletileceği. Ancak açık arabirim tanımları <xref:System.Windows.FrameworkTemplate> , ve <xref:System.Windows.Style>' ın geleneksel API yüzeyinin bir parçası değildir, çünkü <xref:System.Windows.Markup.INameScope> sık sık yöntemleri <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> doğrudan çağrı yapmanız ve bunun yerine diğer API 'leri kullanması gerekir <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>gibi.  
  
 Aşağıdaki sınıflar, <xref:System.Windows.NameScope?displayProperty=nameWithType> yardımcı sınıfını kullanarak ve <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> iliştirilmiş özelliği aracılığıyla xaml namescope uygulamasına bağlanarak kendi xaml namescope değerlerini tanımlar:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name Yönergesi](../../xaml-services/x-name-directive.md)
