---
title: XAML isim skopları
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
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186282"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML Ad Kapsamları
XAML adskopları, XAML'de tanımlanan nesneleri tanımlayan bir kavramdır. XAML adskopundaki adlar, nesnelerin XAML tanımlı adları ile nesne ağacındaki örnek eşdeğerleri arasında ilişki kurmak için kullanılabilir. Genellikle, yönetilen koddaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML adskopları, bir XAML uygulaması için tek tek XAML sayfa köklerini yüklerken oluşturulur. Programlama nesnesi olarak XAML adskopları <xref:System.Windows.Markup.INameScope> arayüz tarafından tanımlanır ve <xref:System.Windows.NameScope>pratik sınıf tarafından da uygulanır.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>Yüklü XAML Uygulamalarında Namescopes  
 Daha geniş bir programlama veya bilgisayar bilimi bağlamında, programlama kavramları genellikle bir nesneye erişmek için kullanılabilecek benzersiz bir tanımlayıcı veya ad ilkesini içerir. Tanımlayıcılar veya adlar kullanan sistemler için ad kapsamı, bir işlemin veya tekniğin bu ada sahip bir nesnenin istenip istenmediğini veya ad tanımlamanın benzersizliğinin zorlandığı sınırları tanımlar. Bu genel ilkeler XAML isimskopları için geçerlidir. WPF'de, sayfa yüklendiğinde xaml sayfasının kök öğesi üzerinde XAML adskopları oluşturulur. Sayfa kökünden başlayarak XAML sayfasında belirtilen her ad, ilgili bir XAML adskopuna eklenir.  
  
 WPF XAML'de, ortak kök öğeleri <xref:System.Windows.Controls.Page>olan <xref:System.Windows.Window>öğeler (, ve ) her zaman bir XAML adskopu kontrol eder. Biçimlendirmedeki <xref:System.Windows.FrameworkElement> sayfanın <xref:System.Windows.FrameworkContentElement> kök öğesi gibi veya öğe ise, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci <xref:System.Windows.Controls.Page> çalışan bir XAML adayır <xref:System.Windows.Controls.Page> sağlayabilmek için dolaylı olarak bir kök ekler.  
  
> [!NOTE]
> WPF oluşturma eylemleri, `Name` `x:Name` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmedeki herhangi bir öğede hiçbir öznitelik tanımlanmamış olsa bile, XAML üretimi için bir XAML adayır oluşturma.  
  
 Herhangi bir XAML adalanında aynı adı iki kez kullanmaya çalışırsanız, bir özel durum yükseltilir. Kod arkası olan ve derlenmiş bir uygulamanın parçası olan WPF XAML için, ilk biçimlendirme derlemesi sırasında sayfa için oluşturulan sınıf oluşturulurken, özel durum WPF yapı eylemleri tarafından yapı zamanında yükseltilir. Herhangi bir yapı eylemi tarafından biçimlendirme-derlenmeyen XAML için, XAML yüklendiğinde XAML adayır sorunlarıyla ilgili özel durumlar yükseltilebilir. XAML tasarımcıları da tasarım zamanda XAML ad-scope sorunları tahmin edebilir.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Çalışma Zamanı Nesne Ağaçlarına Nesne Ekleme  
 XAML'nin ayrıştırıldığı an, wpf XAML adskopu oluşturulduğu ve tanımlandığı anı temsil eder. Bir nesneyi, o ağacı oluşturan XAML'den sonraki bir anda bir nesne `Name` eklerseniz, yeni nesnedeki bir veya `x:Name` değer XAML adskopundaki bilgileri otomatik olarak güncelleştirmez. XAML yüklendikten sonra Bir CIÇIN ad eklemek için, genellikle XAML sayfa kökü <xref:System.Windows.Markup.INameScope.RegisterName%2A> olan XAML adskopu tanımlayan nesneüzerinde uygun uygulama çağırmanız gerekir. Ad kaydedilmezse, eklenen nesne <xref:System.Windows.FrameworkElement.FindName%2A>, animasyon hedeflemesi için bu adı kullanamazsınız.  
  
 Uygulama geliştiricileri için en yaygın senaryo, sayfanın geçerli kökünde adları XAML adskopuna kaydetmek için kullanacağınız <xref:System.Windows.FrameworkElement.RegisterName%2A> senaryodur. <xref:System.Windows.FrameworkElement.RegisterName%2A>animasyonlar için nesneleri hedefleyen film panoları için önemli bir senaryonun bir parçasıdır. Daha fazla bilgi için [Storyboards Genel Bakış'a](../graphics-multimedia/storyboards-overview.md)bakın.  
  
 XAML <xref:System.Windows.FrameworkElement.RegisterName%2A> adscope tanımlayan nesne dışında bir nesneyi çağırırsanız, ad, çağrı nesnesinin içinde tutulduğu XAML adskobuna, sanki <xref:System.Windows.FrameworkElement.RegisterName%2A> nesneyi tanımlayan XAML adarağını çağırmışsınız gibi kaydedilir.  
  
### <a name="xaml-namescopes-in-code"></a>Koddaki XAML İsimSkopları  
 Kodda XAML adskopları oluşturabilir ve kullanabilirsiniz. ApI'ler ve XAML adskop oluşturma ile ilgili kavramlar saf kod kullanımı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bile aynıdır, çünkü XAML işlemci xaml kendisini işlerken bu API'leri ve kavramları kullanır. Kavramlar ve API, genellikle XAML'de kısmen veya tamamen tanımlanan bir nesne ağacında nesneleri ada göre bulabilmek amacıyla bulunur.  
  
 Yüklü XAML'den değil, programlı olarak oluşturulan uygulamalar için, örneklerinde bir XAML <xref:System.Windows.Markup.INameScope>adskopunun <xref:System.Windows.FrameworkContentElement> oluşturulmasını desteklemek için XAML adskopunu tanımlayan nesnenin uygulamalı veya türetilmiş bir <xref:System.Windows.FrameworkElement> sınıf olmalıdır.  
  
 Ayrıca, xaml işlemci tarafından yüklenmeyen ve işlenmeyen herhangi bir öğe için, nesnenin XAML adscope'u varsayılan olarak oluşturulmaz veya başharfe faturalandırılmaz. Adları daha sonra kaydetmeyi istediğiniz herhangi bir nesne için açıkça yeni bir XAML adskopu oluşturmanız gerekir. XAML adskopu oluşturmak için <xref:System.Windows.NameScope.SetNameScope%2A> statik yöntemi çağırırsınız. `dependencyObject` Parametre olarak ona sahip olacak nesneyi ve <xref:System.Windows.NameScope.%23ctor%2A> `value` parametre olarak yeni bir oluşturucu çağırın.  
  
 `dependencyObject` Amacıyla <xref:System.Windows.NameScope.SetNameScope%2A> sağlanan nesne bir uygulama <xref:System.Windows.Markup.INameScope> değilse <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>veya, <xref:System.Windows.FrameworkElement.RegisterName%2A> herhangi bir alt öğeyi çağırmak hiçbir etkiye sahip olmayacaktır. Yeni XAML adscope'u açıkça oluşturamazsanız, <xref:System.Windows.FrameworkElement.RegisterName%2A> çağrıların bir özel durum oluşturacağı.  
  
 Kodda XAML adscope API'lerini kullanma örneği [için](../graphics-multimedia/how-to-define-a-name-scope.md)bkz.  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>Stiller ve Şablonlarda XAML İsim Skopları  
 İçerikleri basit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir şekilde yeniden kullanma ve yeniden uygulama olanağı sağlayan stiller ve şablonlar. Ancak, stiller ve şablonlar, şablon düzeyinde tanımlanan XAML adlarına sahip öğeler de içerebilir. Aynı şablon bir sayfada birden çok kez kullanılabilir. Bu nedenle, stillerin ve şablonların her ikisi de stil veya şablonun uygulandığı nesne ağacındaki her konumdan bağımsız olarak kendi XAML adskoplarını tanımlar.  
  
 Aşağıdaki örneği inceleyin:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Burada, aynı şablon iki farklı düğmeye uygulanır. Şablonlarda ayrı xaml adscope'ları yoksa, `TheBorder` şablonda kullanılan ad XAML adskopunda bir ad çakışması neden olur. Şablonun her anlık kendi XAML adskopu vardır, bu nedenle bu örnekte her anlık şablonun XAML adskopu tam olarak bir ad içerir.  
  
 Stiller ayrıca kendi XAML adskoplarını tanımlar, böylece çoğunlukla film şeridinin bazı bölümleri belirli adlara atanmış olabilir. Bu adlar, şablon denetim özelleştirmesinin bir parçası olarak yeniden tanımlanmış olsa bile, bu adın öğelerini hedef alacak belirli davranışları denetlemeyi sağlar.  
  
 Ayrı XAML adskopları nedeniyle, şablonda adlandırılmış öğeleri bulmak, sayfada şablonsuz bir adlandırılmış öğe bulmaktan daha zordur. Öncelikle, şablonun uygulandığı denetimin <xref:System.Windows.Controls.Control.Template%2A> özellik değerini alarak uygulanan şablonu belirlemeniz gerekir. Ardından, şablonun ikinci <xref:System.Windows.FrameworkTemplate.FindName%2A>parametre olarak uygulandığı denetimi geçen şablon sürümünü çağırırsınız.  
  
 Denetim yazarıysanız ve uygulamalı şablondaki belirli bir adlandırılmış öğenin denetimin kendisi tarafından tanımlanan bir davranışın hedefi olduğu <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> bir kuralı oluşturuyorsanız, yöntemi denetim uygulama kodunuzdan kullanabilirsiniz. Yöntem <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> korunur, bu nedenle yalnızca denetim yazarı nın bu yönteme erişimi vardır.  
  
 Şablon un içinden çalışıyorsanız ve şablonun uygulandığı XAML adskopuna ulaşmak istiyorsanız, değerini <xref:System.Windows.FrameworkElement.TemplatedParent%2A> <xref:System.Windows.FrameworkElement.FindName%2A> alın ve ardından buradan arayın. Şablon içinde çalışmanın bir örneği, olayın uygulanan bir şablondaki bir öğeden yükseltilecek olay işleyicisi uygulamasını yazıyorsanız olacaktır.  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML İsim Scopes ve Ad ile ilgili API'ler  
 <xref:System.Windows.FrameworkElement>vardır <xref:System.Windows.FrameworkElement.FindName%2A> <xref:System.Windows.FrameworkElement.RegisterName%2A> ve <xref:System.Windows.FrameworkElement.UnregisterName%2A> yöntemleri vardır. Bu yöntemleri üzerinde dediğiniz nesne bir XAML adskopuna sahipse, yöntemler ilgili XAML adskopunun yöntemlerini çağırır. Aksi takdirde, üst öğe bir XAML adskopuna sahip olup olmadığını görmek için denetlenir ve bu işlem bir XAML adskopu bulunana kadar özyinelemeli olarak devam eder (XAML işlemci davranışı nedeniyle, kökte bir XAML adskopu olması garanti edilir). <xref:System.Windows.FrameworkContentElement>hiçbir xaml adskopsahibi <xref:System.Windows.FrameworkContentElement> olacak istisna, benzer davranışları vardır. Aramalar sonunda <xref:System.Windows.FrameworkContentElement> bir <xref:System.Windows.FrameworkElement> üst öğeye iletilebilir böylece yöntemler var.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>varolan bir nesneyle yeni bir XAML adskopu eşlemek için kullanılır. XAML <xref:System.Windows.NameScope.SetNameScope%2A> adkapsamını sıfırlamak veya temizlemek için birden fazla kez arayabilirsiniz, ancak bu yaygın bir kullanım değildir. Ayrıca, <xref:System.Windows.NameScope.GetNameScope%2A> genellikle koddan kullanılmaz.  
  
### <a name="xaml-namescope-implementations"></a>XAML Namescope Uygulamaları  
 Aşağıdaki sınıflar <xref:System.Windows.Markup.INameScope> doğrudan uygular:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>XAML adları veya namescopes kullanmaz; sözlük uygulaması olduğundan, bunun yerine anahtarları kullanır. Uygulamanın <xref:System.Windows.ResourceDictionary> tek <xref:System.Windows.Markup.INameScope> nedeni, gerçek bir XAML adscope ve nasıl bir <xref:System.Windows.ResourceDictionary> işişler anahtarları arasındaki ayrımı açıklığa kavuşturmak yardımcı kullanıcı kodu için özel durumlar yükseltmek <xref:System.Windows.ResourceDictionary> ve aynı zamanda XAML adskopları bir üst öğeler tarafından uygulanmaz sağlamak için.  
  
 <xref:System.Windows.FrameworkTemplate>ve <xref:System.Windows.Style> <xref:System.Windows.Markup.INameScope> açık arayüz tanımları ile uygulayın. Açık uygulamalar, bu XAML adskoplarının <xref:System.Windows.Markup.INameScope> arabirim üzerinden erişildiğinde geleneksel olarak gibi çalışmasına olanak tanır, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu da XAML adskoplarının dahili işlemler tarafından nasıl iletildiğidir. Ama açık arayüz tanımları geleneksel API yüzeyinin <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style>bir parçası değildir ve , <xref:System.Windows.Markup.INameScope> nadiren <xref:System.Windows.FrameworkTemplate> ve <xref:System.Windows.Style> doğrudan yöntemleri aramak gerekir <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>çünkü, ve bunun yerine diğer API kullanır .  
  
 Aşağıdaki sınıflar, <xref:System.Windows.NameScope?displayProperty=nameWithType> yardımcı sınıfını kullanarak ve <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> ekli özellik aracılığıyla XAML adskop uygulamasına bağlanarak kendi XAML adskoplarını tanımlar:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name Yönergesi](../../../desktop-wpf/xaml-services/xname-directive.md)
