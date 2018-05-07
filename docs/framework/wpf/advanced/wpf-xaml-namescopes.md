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
ms.openlocfilehash: c13dba48d21235c57be64d90b6547902e0428a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML Ad Kapsamları
XAML ad kapsamları tanımlayan bir kavram XAML içinde tanımlanan nesneler var. XAML isim alanı adları, bir nesne ağacında nesneleri XAML tanımlanan adlarını ve örnek eşdeğerlerine arasındaki ilişkileri oluşturmak için kullanılabilir. Genellikle, XAML ad kapsamları içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kod XAML uygulama için ayrı ayrı XAML sayfası yükleniyor kökleri olduğunda oluşturulur. XAML ad kapsamları programlama nesnesi olarak tarafından tanımlanan <xref:System.Windows.Markup.INameScope> arabirim ve ayrıca pratik sınıfı tarafından uygulanan <xref:System.Windows.NameScope>.  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Yüklenen XAML uygulamaları içindeki ad kapsamları  
 Daha geniş programlama veya bilgisayar bilimi bağlamı programlama kavramları, genellikle benzersiz bir kimlik veya bir nesneye erişmek için kullanılan ad ilkesini içerir. Tanımlayıcıları veya adlarını kullanan sistemleri için sınırlar içinde isim alanı tanımlayan bir nesne adının isteniyorsa hangi işlemin veya teknik arama veya adları tanımlamanın benzersizlik; burada görüntülerle zorlanır sınırlar. Bu ilkeler için XAML ad kapsamları true. Sayfa yüklendiğinde, WPF XAML ad kapsamları XAML sayfası için kök öğesi oluşturulur. Sayfa kökte başlayan XAML sayfası içinde belirtilen her ad için ilgili bir XAML isim alanı eklenir.  
  
 WPF XAML, sık kullanılan kök öğe olan öğeler içinde (gibi <xref:System.Windows.Controls.Page>, ve <xref:System.Windows.Window>) her zaman bir XAML isim alanı denetim. Bir öğe gibi <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> sayfanın biçimlendirmede, kök öğe bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi ekler bir <xref:System.Windows.Controls.Page> örtük olarak kök böylece <xref:System.Windows.Controls.Page> çalışma XAML isim alanı sağlayabilir.  
  
> [!NOTE]
>  WPF yapı eylemleri XAML isim alanı XAML üretim için yoksa bile oluşturmak `Name` veya `x:Name` öznitelikleri herhangi bir öğe üzerinde tanımlanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 Aynı adı iki kez herhangi XAML isim alanı içinde kullanmaya çalışırsa, bir özel durum oluşturulur. WPF arka plan kod ve derlenmiş bir uygulamanın parçası olan XAML için özel durum derleme zamanında WPF yapı eylemleri tarafından oluşturulan sınıf sayfası için ilk biçimlendirmesi derleme sırasında oluştururken oluşturulur. XAML yüklendiğinde bir yapı eylemi tarafından biçimlendirme derlenmiş değil XAML için XAML isim alanı sorunlarıyla ilgili özel durumlar ortaya. XAML tasarımcıları tasarım zamanında XAML isim alanı sorunları tahmin.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Çalışma zamanı nesne ağaçları nesneler ekleme  
 XAML ayrıştırılır şu anda bir WPF XAML isim alanı oluşturulup tanımlı zaman birazdan temsil eder. Bir nesne bir nesne ağacına bir noktada ağacı üretilen XAML ayrıştırıldığında sonra zamanında eklerseniz bir `Name` veya `x:Name` yeni bir nesne değeri XAML isim alanı bilgileri otomatik olarak güncelleştirilmez. XAML yüklendikten sonra bir WPF XAML isim alanı bir nesne için bir ad eklemek için uygun uygulanması çağrı <xref:System.Windows.Markup.INameScope.RegisterName%2A> XAML isim alanı tanımlar nesnede olduğu genellikle XAML sayfası kök. Adı kayıtlı değilse, eklenen nesne adına göre yöntemlerle gibi başvurulamaz <xref:System.Windows.FrameworkElement.FindName%2A>, ve animasyon hedefleme için bu adı kullanamazsınız.  
  
 Uygulama geliştiricilerinin en yaygın bir senaryo, kullanmasıdır <xref:System.Windows.FrameworkElement.RegisterName%2A> sayfasının geçerli kökündeki XAML isim alanı içine adlarını kaydetmek için. <xref:System.Windows.FrameworkElement.RegisterName%2A> Bu hedef nesneler için animasyonları film şeritleri için önemli bir senaryo parçasıdır. Daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Çağırırsanız <xref:System.Windows.FrameworkElement.RegisterName%2A> çağrısı yaptığını sanki XAML isim alanı tanımlayan nesnesi başka bir nesnede adı hala çağıran nesne içinde tutulur XAML isim alanı için kayıtlı <xref:System.Windows.FrameworkElement.RegisterName%2A> nesnesi tanımlayarak XAML isim alanı üzerinde.  
  
### <a name="xaml-namescopes-in-code"></a>XAML ad kapsamları kodu  
 Oluşturun ve ardından kodda XAML ad kapsamları kullanın. API'ler ve kavramları XAML isim alanı oluşturmada yer alan bir saf kod kullanımı için bile aynı olduğu için XAML İşlemci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML kendisini işlerken bu API'ları ve kavramları kullanır. Kavramlar ve API çoğunlukla genellikle XAML'de kısmen veya tamamen tanımlanan bir nesne ağacına içinde ada göre nesneleri bulmak bölümlemeye amacıyla mevcut.  
  
 Program aracılığıyla oluşturulan uygulamaları için ve yüklenen XAML değil, XAML isim alanı tanımlayan nesnesi uygulamalıdır <xref:System.Windows.Markup.INameScope>, veya bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> XAML isim alanı oluşturulmasını desteklemek için türetilmiş sınıf, kendi örnekleri.  
  
 Ayrıca, değil yüklenen ve XAML processor tarafından işlenen herhangi bir öğe için nesne için XAML isim alanı oluşturulamadı veya varsayılan olarak başlatıldı. Açıkça adlarına sonradan kaydetmek istediğiniz herhangi bir nesne için yeni bir XAML isim alanı oluşturmanız gerekir. XAML isim alanı oluşturmak için statik çağırın <xref:System.Windows.NameScope.SetNameScope%2A> yöntemi. Olarak sahip olacağını nesnesi belirtin `dependencyObject` parametresi ve yeni bir <xref:System.Windows.NameScope.%23ctor%2A> Oluşturucusu araması olarak `value` parametresi.  
  
 Nesne olarak sağladıysanız `dependencyObject` için <xref:System.Windows.NameScope.SetNameScope%2A> değil bir <xref:System.Windows.Markup.INameScope> uygulaması, <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, arama <xref:System.Windows.FrameworkElement.RegisterName%2A> tüm alt öğeleri hiçbir etkisi olmaz. Yeni XAML isim alanı açıkça oluşturmak başarısız olursa, ardından çağrılar <xref:System.Windows.FrameworkElement.RegisterName%2A> bir özel durum oluşturacak.  
  
 Code XAML isim alanı API'lerini kullanarak bir örnek için bkz: [ad kapsamı tanımlama](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>XAML ad kapsamları stilleri ve şablonları  
 Stilleri ve şablonlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeniden kullanmak ve içeriği kolay bir şekilde yeniden yeteneği sağlar. Ancak, stil ve Şablonlar ayrıca öğeleri şablon düzeyinde tanımlanan XAML adlarıyla içerebilir. Aynı şablon bir sayfa birden çok kez kullanılabilir. Bu nedenle, kendi XAML ad kapsamları, burada stil veya şablon uygulanan herhangi bir nesne ağacındaki konumdan bağımsız stilleri ve şablonları tanımlayın.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Burada, aynı şablonu için iki farklı düğmeler uygulanır. Şablonları ayrık XAML ad kapsamları değilse `TheBorder` şablonda kullanılan adın XAML isim alanı içinde bir ad çakışması neden. Şablonun her örneklemesi kendi XAML isim alanı sahiptir, bu nedenle bu örnekte her örneklenen şablonun XAML isim alanı tam olarak bir ad içerecektir.  
  
 Çoğunlukla film şeritleri bölümlerini atanan belirli adları böylece stilleri de kendi XAML isim alanı tanımlar. Şablon denetim özelleştirme bir parçası olarak yeniden tanımlandı olsa bile bu adlar, bu adı öğeleri hedeflediğini denetim belirli davranışları etkinleştirin.  
  
 Nedeniyle ayrı XAML ad kapsamları bir şablonda adlandırılmış öğeleri bulma, bir oluşturulmamış bir sayfa öğesinde adlı bulma değerinden daha zorlu olur. İlk alarak uygulanan şablon belirlemek gereken <xref:System.Windows.Controls.Control.Template%2A> şablon uygulanan burada denetimin özellik değeri. Ardından, şablon sürümü çağıran <xref:System.Windows.FrameworkTemplate.FindName%2A>, şablon ikinci parametre olarak uygulandığı denetimi geçirme.  
  
 Bir denetim yazar ve uygulanan şablon öğesinde adlı belirli bir denetim tarafından tanımlanan bir davranış için hedef olduğu bir kural oluşturmak, kullanabileceğiniz <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> denetim uygulama kodunuzdan yöntemi. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Yöntem korunur, böylece yalnızca denetim yazarı erişimi vardır.  
  
 Bir şablon ve burada şablonun için XAML isim alanı almak için gerek içinde çalışıyorsanız, değerini alın <xref:System.Windows.FrameworkElement.TemplatedParent%2A>ve ardından arama <xref:System.Windows.FrameworkElement.FindName%2A> vardır. Şablonu içindeki çalışma örneği olay işleyicisinin uygulaması yazma varsa, uygulanan bir şablonda bir öğeden olay burada gerçekleştirilecektir olacaktır.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML ad kapsamları ve ad ile ilgili API'ler  
 <xref:System.Windows.FrameworkElement> sahip <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> ve <xref:System.Windows.FrameworkElement.UnregisterName%2A> yöntemleri. Bu yöntemleri çağırmak nesne XAML isim alanı sahipse, ilgili XAML isim alanı yöntemlerin içine yöntemlerini çağırın. Aksi takdirde, üst öğenin XAML isim alanı sahibi ve XAML isim alanı bulunana kadar yinelemeli olarak bu işlem devam görmek için kontrol edilir (XAML işlemci davranışı nedeniyle var bir XAML isim alanı kökünde olması garanti). <xref:System.Windows.FrameworkContentElement> özel durum ile benzer davranışları sahip, hiçbir <xref:System.Windows.FrameworkContentElement> hiç XAML isim alanı sahibi. Yöntemleri mevcut <xref:System.Windows.FrameworkContentElement> çağrıları sonunda çok iletilebilir böylece bir <xref:System.Windows.FrameworkElement> üst öğesi.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> var olan bir nesne için yeni bir XAML isim alanı eşlemek için kullanılır. Çağırabilirsiniz <xref:System.Windows.NameScope.SetNameScope%2A> birden çok kez sıfırlama veya XAML temizlemek için isim alanı değildir, ancak, ortak kullanım. Ayrıca, <xref:System.Windows.NameScope.GetNameScope%2A> koddan genellikle kullanılmaz.  
  
### <a name="xaml-namescope-implementations"></a>XAML isim alanı uygulamaları  
 Aşağıdaki sınıflar uygulama <xref:System.Windows.Markup.INameScope> doğrudan:  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> XAML adları veya ad kapsamları kullanmaz; bir sözlük uygulaması olduğu için bunun yerine, anahtarları kullanır. Yalnızca neden <xref:System.Windows.ResourceDictionary> uygulayan <xref:System.Windows.Markup.INameScope> true XAML isim alanı arasında ayrım açıklamak yardımcı özel durumlar kullanıcı kodu oluşturabilir ve nasıl olduğu bir <xref:System.Windows.ResourceDictionary> anahtarları, işler ve ayrıca XAML ad kapsamları için uygulanmaz güvence altına almak için bir <xref:System.Windows.ResourceDictionary> üst öğeler tarafından.  
  
 <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> uygulamak <xref:System.Windows.Markup.INameScope> açık arabirim tanımları aracılığıyla. Açık uygulamaları bu XAML ad kapsamları üzerinden zaman erişilen standart olarak davranmasına izin <xref:System.Windows.Markup.INameScope> XAML ad kapsamları nasıl bildirilir olduğu arabirimi tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç işlemler. Ancak açık arabirim tanımları geleneksel API yüzeyi parçası olmayan <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style>, nadiren çağırmanız gerekir çünkü <xref:System.Windows.Markup.INameScope> yöntemlere <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> doğrudan ve bunun yerine diğer API kullanır gibi <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Aşağıdaki sınıflar kullanarak kendi XAML isim alanı tanımlayın <xref:System.Windows.NameScope?displayProperty=nameWithType> yardımcı sınıfı ve XAML isim alanı uygulaması bağlanma <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> özelliği eklenmiş:  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)  
 [x:Name Yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md)
