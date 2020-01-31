---
title: XAML ad kapsamları
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
ms.openlocfilehash: 4383492157191f61cf04a2fdd6ce27e9183bda8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744409"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML Ad Kapsamları
Xaml ad kapsamları, XAML 'de tanımlanan nesneleri tanımlayan bir kavramdır. XAML namescope 'daki adlar, nesne ağacındaki nesnelerin XAML tanımlı adları ve örnek eşdeğerleri arasında ilişki kurmak için kullanılabilir. Genellikle, bir xaml uygulaması için tek XAML sayfa kökleri yüklenirken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yönetilen koddaki xaml ad kapsamları oluşturulur. Programlama nesnesi <xref:System.Windows.Markup.INameScope> arabirimi tarafından tanımlandığından ve ayrıca pratik sınıf <xref:System.Windows.NameScope>tarafından uygulanan XAML namesler.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Yüklenen XAML uygulamalarında Namescopes  
 Daha geniş bir programlama veya bilgisayar bilimi bağlamında, programlama kavramları genellikle bir nesneye erişmek için kullanılabilecek benzersiz bir tanımlayıcı veya ad ilkesini içerir. Tanımlayıcı veya ad kullanan sistemlerde, NameScope bir işlemin veya tekniğin, bu adı bir nesne isteniyorsa veya tanımlayıcı adların benzersizlik alanındaki sınırlar zorlandığında arama yapılacak sınırları tanımlar. Bu genel ilkeler XAML namescopes için geçerlidir. WPF 'de, xaml ad kapsamları, sayfa yüklendiğinde bir XAML sayfası için kök öğede oluşturulur. Sayfa kökünden başlayarak XAML sayfasında belirtilen her ad, ilgili XAML namescope 'a eklenir.  
  
 WPF XAML 'de ortak kök öğeler (örneğin, <xref:System.Windows.Controls.Page>ve <xref:System.Windows.Window>) öğeleri her zaman bir XAML namescope denetler. <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> gibi bir öğe, biçimlendirme içindeki sayfanın kök öğesi ise, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi, <xref:System.Windows.Controls.Page> çalışan bir XAML namescope sağlayabilmesi için bir <xref:System.Windows.Controls.Page> kökünü örtülü olarak ekler.  
  
> [!NOTE]
> WPF derleme eylemleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesinde herhangi bir öğe üzerinde hiçbir `Name` veya `x:Name` özniteliği tanımlanmasa bile XAML üretimi için XAML namescope oluşturun.  
  
 Aynı adı herhangi bir XAML namescope 'da iki kez kullanmayı denerseniz, bir özel durum oluşturulur. Kod arkasında ve derlenmiş bir uygulamanın parçası olan WPF XAML için, ilk biçimlendirme derlemesi sırasında sayfa için oluşturulan sınıf oluşturulurken WPF derleme eylemleri tarafından derleme zamanında oluşturulur. Herhangi bir yapı eylemi tarafından işaretleme tarafından derlenmediği XAML için, XAML yüklendiğinde XAML namescope sorunlarıyla ilgili özel durumlar ortaya çıkabilir. XAML tasarımcıları Ayrıca tasarım zamanında XAML namescope sorunlarını da tahmin edebilir.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Çalışma zamanı nesne ağaçlarına nesne ekleme  
 XAML 'nin ayrıştırılmasından sonra WPF XAML namescope 'un oluşturulduğu ve tanımlandığı zaman şu anda temsil edilir. Söz konusu ağacı üreten XAML ayrıştırıldıktan sonra bir noktada nesne ağacına bir nesne eklerseniz, yeni nesnedeki bir `Name` veya `x:Name` değeri bir XAML namescope 'daki bilgileri otomatik olarak güncelleştirmez. XAML yüklendikten sonra bir nesne için bir WPF XAML namescope 'a bir ad eklemek için, genellikle XAML sayfa kökü olan XAML namescope 'u tanımlayan nesne üzerinde <xref:System.Windows.Markup.INameScope.RegisterName%2A> uygun bir uygulamasını çağırmanız gerekir. Ad kayıtlı değilse, eklenen nesneye <xref:System.Windows.FrameworkElement.FindName%2A>gibi yöntemlerle ad ile başvurulamaz ve bu adı animasyon hedefleme için kullanamazsınız.  
  
 Uygulama geliştiricileri için en yaygın senaryo, adları sayfanın geçerli kökündeki XAML namescope 'a kaydetmek için <xref:System.Windows.FrameworkElement.RegisterName%2A> kullanacağınızı kullanmaktır. <xref:System.Windows.FrameworkElement.RegisterName%2A> animasyonlar için nesneleri hedef alan film şeritleri için önemli bir senaryonun bir parçasıdır. Daha fazla bilgi için bkz. görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
 XAML namescope 'u tanımlayan nesne dışında bir nesne üzerinde <xref:System.Windows.FrameworkElement.RegisterName%2A> çağırırsanız, bu ad hala çağıran nesnenin içinde tutulduğu XAML namescope 'a kaydedilir, ancak nesne tanımlayan XAML namescope üzerinde <xref:System.Windows.FrameworkElement.RegisterName%2A> adlandırmışsınız gibi.  
  
### <a name="xaml-namescopes-in-code"></a>Koddaki XAML namescopes  
 Kodda xaml ad kapsamları oluşturabilir ve bunları kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemcisi, XAML kendisini işlerken bu API 'Leri ve kavramları kullandığından, xaml namescope oluşturma ile ilgili API 'Ler ve kavramlar, saf kod kullanımı için de aynıdır. Kavramlar ve API, genellikle XAML 'de kısmen veya tamamen tanımlanmış bir nesne ağacı içinde ada göre nesne bulabilme amacıyla vardır.  
  
 Programlı olarak oluşturulan ve yüklü XAML 'den olmayan uygulamalar için, bir XAML namescope tanımlayan nesne, örneklerinde XAML namescope oluşturmayı desteklemek için <xref:System.Windows.Markup.INameScope>veya bir <xref:System.Windows.FrameworkElement> ya da <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf olmalıdır.  
  
 Ayrıca, XAML işlemcisi tarafından yüklenmeyen ve işlenen tüm öğeler için, nesne için XAML namescope varsayılan olarak oluşturulmaz veya başlatılmaz. Adları daha sonra kaydetmek istediğiniz herhangi bir nesne için açıkça yeni bir XAML namescope oluşturmanız gerekir. XAML namescope oluşturmak için, statik <xref:System.Windows.NameScope.SetNameScope%2A> yöntemini çağırın. `dependencyObject` parametresi olarak sahip olacak nesneyi ve `value` parametresi olarak yeni bir <xref:System.Windows.NameScope.%23ctor%2A> Oluşturucu çağrısını belirtin.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> için `dependencyObject` olarak belirtilen nesne <xref:System.Windows.Markup.INameScope> bir uygulama, <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>değilse, herhangi bir alt öğe üzerinde <xref:System.Windows.FrameworkElement.RegisterName%2A> çağırma hiçbir etkiye sahip olmaz. Yeni XAML namescope 'u açıkça oluşturmadıysanız, <xref:System.Windows.FrameworkElement.RegisterName%2A> çağrıları bir özel durum oluşturur.  
  
 Kodda XAML namescope API 'Lerinin kullanılmasına ilişkin bir örnek için bkz. [ad kapsamını tanımlama](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Stillerde ve şablonlarda XAML namescopes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil ve şablonlar, içeriği kolay bir şekilde yeniden kullanma ve yeniden uygulama yeteneği sağlar. Ancak, stiller ve şablonlar, şablon düzeyinde tanımlı XAML adları olan öğeleri de içerebilir. Aynı şablon bir sayfada birden çok kez kullanılabilir. Bu nedenle, stiller ve şablonlar, stil veya şablonun uygulandığı bir nesne ağacındaki herhangi bir konumdan bağımsız olarak kendi XAML namescopes değerlerini tanımlar.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Burada, aynı şablon iki farklı düğmeye de uygulanır. Şablonlarda ayrı XAML namescopes yoksa, şablonda kullanılan `TheBorder` adı XAML namescope 'da ad çakışmasına neden olur. Şablonun her örneklenmesi kendi XAML namescope 'a sahiptir. bu nedenle, bu örnekte oluşturulan her şablonun XAML namescope tam olarak bir ad içerir.  
  
 Stiller, genellikle görsel taslaklara ait bölümlerin atanabileceği belirli adlara sahip olması için kendi XAML namescope değerlerini de tanımlar. Bu adlar, şablon denetim özelleştirmenin bir parçası olarak yeniden tanımlansa bile, bu adın öğelerini hedefleyecek özel davranışları denetlemenize olanak tanır.  
  
 Ayrı XAML namescopes 'ler nedeniyle, bir şablonda adlandırılmış öğelerin bulunması, bir sayfada Şablonsuz adlandırılmış bir öğe bulmadan daha zor. Önce şablonun uygulandığı denetimin <xref:System.Windows.Controls.Control.Template%2A> özellik değerini alarak uygulanan şablonu belirlemeniz gerekir. Daha sonra, şablonun ikinci parametre olarak uygulandığı denetimi geçirerek <xref:System.Windows.FrameworkTemplate.FindName%2A>şablon sürümünü çağırabilirsiniz.  
  
 Bir denetim yazarınız ve uygulanan bir şablonda belirli bir adlandırılmış öğenin, denetimin kendisi tarafından tanımlanan bir davranışın hedefi olduğu bir kural oluşturuyorsanız, denetim uygulama kodunuzda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> yöntemini kullanabilirsiniz. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> yöntemi korunuyor, bu nedenle yalnızca denetim yazarının buna erişimi vardır.  
  
 Bir şablon içinden çalışıyorsanız ve şablonun uygulandığı XAML namescope 'a erişmeniz gerekiyorsa, <xref:System.Windows.FrameworkElement.TemplatedParent%2A>değerini alın ve sonra da <xref:System.Windows.FrameworkElement.FindName%2A> çağırın. Şablon içinde çalışma örneği, etkinliğin uygulanan şablondaki bir öğeden oluşturulduğu olay işleyicisi uygulamasını yazıyorsanız olur.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML namescopes ve adla ilgili API 'Ler  
 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> ve <xref:System.Windows.FrameworkElement.UnregisterName%2A> yöntemlerine sahiptir. Bu yöntemleri bir XAML namescope 'ın sahibi olarak çağırırsanız, Yöntemler ilgili XAML namescope 'un yöntemlerine çağrı yapılır. Aksi takdirde, üst öğe bir XAML namescope 'a sahip olup olmadığını görmek için denetlenir ve bu işlem XAML namescope bulunana kadar yinelemeli olarak devam eder (XAML işlemci davranışı nedeniyle, kökte XAML namescope olması garanti edilir). <xref:System.Windows.FrameworkContentElement>, bir XAML namescope 'a hiçbir <xref:System.Windows.FrameworkContentElement> sahip olmadığı özel durum dışında, benzer davranışları vardır. Çağrılar, son olarak bir <xref:System.Windows.FrameworkElement> üst öğeye iletilebilmesi için <xref:System.Windows.FrameworkContentElement> vardır.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>, yeni bir XAML namescope 'ı varolan bir nesneyle eşlemek için kullanılır. XAML namescope 'u sıfırlamak veya temizlemek için birden çok kez <xref:System.Windows.NameScope.SetNameScope%2A> çağırabilirsiniz, ancak bu ortak bir kullanım değildir. Ayrıca, <xref:System.Windows.NameScope.GetNameScope%2A> genellikle koddan kullanılmaz.  
  
### <a name="xaml-namescope-implementations"></a>XAML namescope uygulamaları  
 Aşağıdaki sınıflar doğrudan <xref:System.Windows.Markup.INameScope> uygular:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> xaml adlarını veya ad kapsamları 'yi kullanmaz; Bunun yerine anahtarları kullanır, çünkü bir sözlük uygulamasıdır. <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Markup.INameScope> uygulayan tek neden, doğru xaml namescope ve bir <xref:System.Windows.ResourceDictionary> anahtarları nasıl işleyeceğinden ve xaml ad kapsamları 'nin bir <xref:System.Windows.ResourceDictionary> üst öğelere uygulanmamasını güvence altına almak için Kullanıcı koduna özel durumlar yükseltebilmesini sağlar.  
  
 <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> açık arabirim tanımları aracılığıyla <xref:System.Windows.Markup.INameScope> uygulayın. Açık uygulamalar, xaml ad kapsamları 'nin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç süreçler tarafından iletileceği <xref:System.Windows.Markup.INameScope> arabirimi aracılığıyla erişildiğinde bu xaml ad copes 'nin genel olarak davranmasına izin verir. Ancak açık arabirim tanımları <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style>geleneksel API yüzeyinin bir parçası değildir, çünkü doğrudan <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> <xref:System.Windows.Markup.INameScope> yöntemlerini çağırmanız ve bunun yerine <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>gibi diğer API 'leri kullanması gerekir.  
  
 Aşağıdaki sınıflar, <xref:System.Windows.NameScope?displayProperty=nameWithType> yardımcı sınıfını kullanarak ve <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> iliştirilmiş özelliği aracılığıyla XAML namescope uygulamasına bağlanarak kendi XAML namescope değerlerini tanımlar:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name Yönergesi](../../../desktop-wpf/xaml-services/xname-directive.md)
