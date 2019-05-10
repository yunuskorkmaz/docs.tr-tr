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
ms.openlocfilehash: d4a4e1eee5dc60e330a5425d5075c7e5b8c44127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666336"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML Ad Kapsamları
XAML ad kapsamları tanımlayan bir kavram, XAML içinde tanımlanan nesneler var. XAML namescope adlarında bir nesne ağacında nesnelerin XAML tanımlı adlarını ve örnek eşdeğerlerine arasındaki ilişkileri kurmak için kullanılabilir. Genellikle, XAML ad kapsamları içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kod, bir XAML uygulaması için tek tek XAML sayfa yükleme kökleri olduğunda oluşturulur. XAML ad kapsamları programlama nesnesi tarafından tanımlanan <xref:System.Windows.Markup.INameScope> arabirim ve ayrıca pratik bir sınıf tarafından uygulanan <xref:System.Windows.NameScope>.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Yüklenen XAML uygulamaları içinde ad kapsamları  
 Programlama Kavramları, genellikle daha geniş programlama veya bilgisayar bilimi bağlam benzersiz tanımlayıcısı veya bir nesneye erişmek için kullanılan ad ilkesini içerir. Tanımlayıcıları veya adları kullanan sistemler için namescope sınırlar içinde tanımlar. Bu ada sahip bir nesne istenirse, bir işlem veya teknik arar veya adları tanımlama benzersizlik burada görüntülerle zorlanır sınırlar. Bu ilkeler için XAML ad kapsamları doğrudur. Sayfa yüklendiğinde XAML sayfası için kök öğesinde, WPF XAML ad kapsamları oluşturulur. Başlangıç sayfası kök dizininde XAML sayfa içinde belirtilen her ad için ilgili bir XAML namescope eklenir.  
  
 WPF XAML, ortak kök öğeleri olan öğeler de (gibi <xref:System.Windows.Controls.Page>, ve <xref:System.Windows.Window>) her zaman bir XAML namescope denetim. Bir öğe gibi <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> kök öğe işaretleme, sayfanın bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci ekler bir <xref:System.Windows.Controls.Page> örtük olarak kök böylece <xref:System.Windows.Controls.Page> çalışma XAML namescope sağlayabilir.  
  
> [!NOTE]
>  WPF yapı eylemleri XAML namescope XAML üretim için bile hiçbir oluşturma `Name` veya `x:Name` tüm öğelerde tanımlı öznitelikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 Tüm XAML namescope iki kez aynı adı kullanmaya çalışırsanız, bir özel durum oluşturulur. WPF derlenmiş bir uygulamanın parçası olan arka plan kod ve XAML için özel durum oluşturma zamanında WPF yapı eylemleri tarafından oluşturulan sınıfın sayfa için ilk biçimlendirme derleme sırasında oluştururken oluşturulur. XAML yüklendiğinde olmayan herhangi bir derleme işlem biçimlendirme derlenmiş XAML için XAML namescope sorunlarıyla ilgili özel durum harekete geçirilen. XAML tasarımcıları tasarım zamanında XAML namescope sorunları tahmin.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Çalışma zamanı nesne ağaçları nesneler ekleme  
 XAML ayrıştırılır şu WPF XAML namescope oluşturup tanımlı zaman içinde bir ana temsil eder. Bir nesne için bir noktada bir nesne ağacının o ağaç üretilen XAML ayrıştırıldığında küpte sonra zaman içinde eklerseniz bir `Name` veya `x:Name` değeri yeni bir nesne üzerinde bir XAML namescope bilgileri otomatik olarak güncelleştirilmez. XAML yüklendikten sonra bir WPF XAML namescope bir nesne için bir ad eklemek için uygun uygulama çağrı <xref:System.Windows.Markup.INameScope.RegisterName%2A> XAML namescope tanımlayan nesne olduğu genellikle XAML sayfası kök. Ad kayıtlı değilse, eklenen nesne adına göre yöntemleri gibi başvurulamaz <xref:System.Windows.FrameworkElement.FindName%2A>, ve animasyon hedeflemek için bu adı kullanamazsınız.  
  
 Olduğunu, en yaygın bir senaryodur uygulama geliştiricileri için <xref:System.Windows.FrameworkElement.RegisterName%2A> adları geçerli sayfayı kökünde XAML namescope kaydedilecek. <xref:System.Windows.FrameworkElement.RegisterName%2A> Bu hedef nesneler için animasyon film şeritleri için önemli bir senaryo parçasıdır. Daha fazla bilgi için [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
 Eğer <xref:System.Windows.FrameworkElement.RegisterName%2A> adında gibi XAML namescope tanımlayan nesnesi başka bir nesne üzerinde adı hala çağrı nesnesi içinde tutulan XAML namescope kayıtlı <xref:System.Windows.FrameworkElement.RegisterName%2A> tanımlayan nesne XAML namescope üzerinde.  
  
### <a name="xaml-namescopes-in-code"></a>Kod içinde XAML ad kapsamları  
 Oluşturun ve ardından kodda XAML ad kapsamları kullanın. API'ler ve kavramları XAML namescope oluşturmada yer alan bir saf kod kullanımı için bile aynı olduğu için XAML İşlemci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML kendisini işlediğinde, bu API'leri ve kavramları kullanır. Kavramlar ve API çoğunlukla nesneler genellikle kısmen veya tamamen XAML içinde tanımlanmış bir nesne ağacının içinde adıyla bulabilme amacıyla mevcut.  
  
 Program aracılığıyla oluşturulan uygulamalar ve yüklenen XAML yerine, XAML namescope tanımlayan nesne gerçekleyebilmeli <xref:System.Windows.Markup.INameScope>, ya da bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf, XAML namescope oluşturulmasını desteklemek için örnekleri.  
  
 Ayrıca, XAML işlemcisi tarafından işlenen değil yüklenen ve herhangi bir öğe için nesne için XAML namescope değil oluşturulduğunda veya varsayılan olarak başlatılır. Açıkça adlarına sonradan kaydetmek istediğiniz herhangi bir nesne için yeni bir XAML namescope oluşturmanız gerekir. XAML namescope oluşturmak için statik çağrı <xref:System.Windows.NameScope.SetNameScope%2A> yöntemi. Olarak kendi nesne belirtin `dependencyObject` parametresi ve yeni bir <xref:System.Windows.NameScope.%23ctor%2A> oluşturucu çağrısı olarak `value` parametresi.  
  
 Nesne olarak sağlanmışsa `dependencyObject` için <xref:System.Windows.NameScope.SetNameScope%2A> değil bir <xref:System.Windows.Markup.INameScope> uygulaması <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>çağırarak <xref:System.Windows.FrameworkElement.RegisterName%2A> tüm alt öğeleri hiçbir etkisi olmaz. Yeni XAML namescope açıkça oluşturmak başarısız olursa, ardından için çağırdığı <xref:System.Windows.FrameworkElement.RegisterName%2A> bir özel durum oluşturacak.  
  
 Kodda XAML namescope API'leri kullanarak bir örnek için bkz: [ad kapsamı tanımlama](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>XAML ad kapsamları stilleri ve şablonları  
 Stilleri ve şablonları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeniden kullanmak ve içeriği basit bir şekilde yeniden olanağı sunar. Ancak, stilleri ve şablonları öğeleri şablon düzeyinde tanımlanan XAML adlarla de bulunabilir. Bu aynı şablonu bir sayfada birden çok kez kullanılabilir. Bu nedenle, kendi XAML ad kapsamları, stil veya şablonun uygulandığı herhangi bir nesne ağacında konumdan bağımsız stilleri ve şablonları tanımlayın.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Burada, aynı şablonu için iki farklı düğmeler uygulanır. Şablonları ayrık XAML ad kapsamları, yoksa `TheBorder` ad şablonunda kullanılan bir ad çakışması XAML namescope neden. Şablon her örneğinin kendi XAML namescope bulunduğundan bu örnekte, adı tam olarak bir her örneklenen şablonun XAML namescope içerecektir.  
  
 Böylece görsel Taslaklar bölümlerini atanan belirli adları çoğunlukla olabilir stilleri, ayrıca kendi XAML namescope tanımlayın. Şablon denetimi özelleştirme bir parçası olarak yeniden tanımlandı olsa bile bu adlar öğeleri, bu adı hedefleyen denetim belirli davranışları etkinleştirin.  
  
 Nedeniyle ayrı XAML ad kapsamları, şablonda adlandırılmış öğeleri bulma bir oluşturulmamış bir sayfa öğesinde adlı bulma değerinden daha zordur. Öncelikle uygulanan şablon alarak belirleyin gerekir <xref:System.Windows.Controls.Control.Template%2A> burada şablonun uygulandığı denetimin özellik değeri. Ardından, şablon sürümünü çağırmanızı <xref:System.Windows.FrameworkTemplate.FindName%2A>, ikinci parametre olarak şablonun uygulandığı denetimin geçirme.  
  
 Bir denetim yazar ve uygulanan bir şablon öğesinde adlı belirli bir denetim tarafından tanımlanan bir davranış için hedef olduğu bir kuralı ürettiğini kullanabileceğiniz <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> denetimi uygulama kodunuzu yöntemi. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Yöntem korunur, böylece yalnızca denetim yazarın erişimi olur.  
  
 Bir şablon ve şablonun uygulandığı için XAML namescope almaya gerek içinde çalıştığınız, değerini almak <xref:System.Windows.FrameworkElement.TemplatedParent%2A>ve sonra çağrı <xref:System.Windows.FrameworkElement.FindName%2A> vardır. Şablon içinde çalışan bir örnek olay işleyicisinin uygulaması yazıyorsanız, uygulanan bir şablonda bir öğeden olayın nerede gerçekleştirilecektir olacaktır.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML ad kapsamları ve ad ile ilgili API'ler  
 <xref:System.Windows.FrameworkElement> sahip <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> ve <xref:System.Windows.FrameworkElement.UnregisterName%2A> yöntemleri. Bu yöntemleri çağırmak nesne XAML namescope sahipse, ilgili XAML namescope yöntemlere yöntemleri çağırın. Aksi takdirde, üst öğenin XAML namescope aittir ve bu işlem, XAML namescope bulunana kadar yinelemeli olarak devam eder görmek için denetlenir (XAML işlemci davranışı nedeniyle garanti bir XAML namescope kökünde olacak şekilde). <xref:System.Windows.FrameworkContentElement> özel durum ile benzer davranışlara sahip, hiçbir <xref:System.Windows.FrameworkContentElement> hiç olmadığı kadar XAML namescope hakimi olursunuz. Yöntemleri üzerinde mevcut <xref:System.Windows.FrameworkContentElement> çağrıları sonunda iletilebilir böylece bir <xref:System.Windows.FrameworkElement> üst öğe.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> Varolan bir nesneye yeni bir XAML namescope eşlemek için kullanılır. Çağırabilirsiniz <xref:System.Windows.NameScope.SetNameScope%2A> birden çok kez sıfırlama veya XAML temizlemek için namescope değildir, ancak, bir ortak kullanımı. Ayrıca, <xref:System.Windows.NameScope.GetNameScope%2A> koddan genellikle kullanılmaz.  
  
### <a name="xaml-namescope-implementations"></a>XAML Namescope uygulamaları  
 Aşağıdaki sınıflar uygulama <xref:System.Windows.Markup.INameScope> doğrudan:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> XAML adı veya ad kapsamları kullanmaz; Sözlük uygulamasını olduğu için bunun yerine, anahtarları kullanır. Yalnızca neden <xref:System.Windows.ResourceDictionary> uygulayan <xref:System.Windows.Markup.INameScope> için doğru bir XAML namescope arasındaki ayrımı daha açıklayıcı özel durum kullanıcı kodunda oluşturabilir ve nasıl bir <xref:System.Windows.ResourceDictionary> anahtarları, işler ve ayrıca XAML ad kapsamları için uygulanmaz güvence altına almak için bir <xref:System.Windows.ResourceDictionary> üst öğeler tarafından.  
  
 <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> uygulamak <xref:System.Windows.Markup.INameScope> açık arabirim tanımları aracılığıyla. Açık uygulamaları bu XAML ad kapsamları ile ne zaman eriştiği standart olarak davranmasına izin ver <xref:System.Windows.Markup.INameScope> XAML ad kapsamları nasıl iletildiği olan arabirimi tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç işlemler. Ancak açık arabirim tanımları geleneksel API yüzeyinin parçası olmayan <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style>nadiren çağırmanız gerekir çünkü <xref:System.Windows.Markup.INameScope> yöntemlerde <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> doğrudan ve bunun yerine diğer API'sini kullanmanız gerekir gibi <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Aşağıdaki sınıfları kullanarak kendi XAML namescope tanımladığınız <xref:System.Windows.NameScope?displayProperty=nameWithType> yardımcı sınıf ve XAML namescope uygulaması bağlanma <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> ekli özellik:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name Yönergesi](../../xaml-services/x-name-directive.md)
