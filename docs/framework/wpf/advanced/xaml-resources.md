---
title: XAML Kaynakları
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: f92519ca1f960961f95722bce5c8e1f3b4419292
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662193"
---
# <a name="xaml-resources"></a>XAML Kaynakları
Bir kaynak, uygulamanızın farklı bölümlerinde yeniden kullanılabilir bir nesnedir. Fırçalar ve stilleri kaynakları örnekleridir. Bu genel bakışta, kaynakları kullanmayı açıklar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ayrıca oluşturabilir ve kod kullanarak veya birbirinin yerine kod arasında kaynaklarına erişin ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Daha fazla bilgi için [kaynaklar ve kod](resources-and-code.md).  
  
> [!NOTE]
>  Bu konuda açıklanan kaynak dosyaları kaynak dosyaları açıklanan farklı [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../app-development/wpf-application-resource-content-and-data-files.md) ve açıklanan gömülü veya bağlantılı kaynakların farklı [Yönet Uygulama kaynaklarını (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML kaynakları kullanma  
 Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Media.SolidColorBrush> kök öğesi bir sayfanın bir kaynak olarak. Örnek sonra kaynağa başvuruda ve dahil olmak üzere çeşitli alt öğelerinin özelliklerini ayarlamak için kullandığı bir <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>ve <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Her bir çerçeve düzeyi öğesi (<xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>) sahip bir <xref:System.Windows.FrameworkElement.Resources%2A> kaynakları içeren özellik özelliğini (olarak bir <xref:System.Windows.ResourceDictionary>), bir kaynağı tanımlar. Herhangi bir öğede kaynakları tanımlayabilirsiniz. Ancak, kaynakları olan kök öğe üzerinde en sık tanımlanan <xref:System.Windows.Controls.Page> örnekte.  
  
 Her kaynak bir kaynak sözlüğünde benzersiz bir anahtar olması gerekir. Kaynakları işaretlemede tanımlarken aracılığıyla benzersiz bir anahtar atadığınız [x: Key yönergesi](../../xaml-services/x-key-directive.md). Genellikle, anahtarı bir dizedir; Ancak, ayrıca, diğer nesne türlerine uygun biçimlendirme uzantılarını kullanarak ayarlayabilirsiniz. Belirli özellik alanlarında tarafından kullanılan kaynaklar için dize olmayan anahtarlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özellikle stilleri, bileşen kaynakları ve veri stil için.  
  
 Bir kaynak tanımladıktan sonra anahtar adını, örneğin belirten bir kaynak biçimlendirme uzantısı sözdizimi kullanarak bir özellik değeri için kullanılacak kaynak başvurabilirsiniz:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Yukarıdaki örnekte, zaman [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyici işler değeri `{StaticResource MyBrush}` için <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Button>, kaynak arama mantığı ilk kaynak sözlüğü denetler <xref:System.Windows.Controls.Button> öğesi. Varsa <xref:System.Windows.Controls.Button> kaynak anahtarı tanımı yok `MyBrush` (yok; kendi kaynak koleksiyonu boş olan), arama üst öğenin yanındaki denetler <xref:System.Windows.Controls.Button>, olduğu <xref:System.Windows.Controls.Page>. Bu nedenle, tanımladığınızda bir kaynak üzerinde <xref:System.Windows.Controls.Page> kök öğesinde, tüm öğeleri mantıksal ağacının <xref:System.Windows.Controls.Page> erişebileceğini ve herhangi bir özelliğin değerini kabul için aynı kaynak yeniden <xref:System.Type> , kaynak temsil eder. Önceki örnekte, aynı `MyBrush` kaynak iki farklı özellikleri ayarlar: <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statik ve dinamik kaynakları  
 Bir kaynak, bir statik kaynak veya dinamik bir kaynak olarak başvurulabilir. Kullanarak yapıldığını [StaticResource işaretleme uzantısı](staticresource-markup-extension.md) veya [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md). Bir özelliği olan bir işaretleme uzantısıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik dizesini işlemek ve nesneyi döndürmek için işaretleme uzantısı sağlayarak bir nesne başvurusu belirtebilirsiniz gerçekleştirilmesine bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyicisi. Biçimlendirme uzantı davranışı hakkında daha fazla bilgi için bkz. [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 İşaretleme uzantısı kullandığınızda, belirli biçimlendirme uzantısı tarafından işlenen bir veya daha fazla parametreleri dize biçiminde yerine ayarlanan özelliğin bağlamında değerlendirilen normalde sağlar. [StaticResource işaretleme uzantısı](staticresource-markup-extension.md) tüm kullanılabilir kaynak sözlükleri bu anahtar için değer bakarak bir anahtar işler. Bu, zaman alan statik kaynak başvurusu özellik değeri atamak için yükleme işlemi gerektiği zaman noktası olan bir yükleme sırasında gerçekleşir. [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md) bunun yerine işlemleri deyim ve ifade oluşturarak bir anahtar değerlendirilmemiş uygulama çalıştırdığı kadar kalır, hangi zaman, ifade değerlendirilir ve bir değer sağlar.  
  
 Bir kaynağa başvuruda bulunduğunuzda bir statik kaynak başvurusu veya bir dinamik kaynak başvurusu kullanıp aşağıdaki maddeler etkileyebilir:  
  
- Genel tasarım, uygulamanız için kaynakları oluşturmaya (uygulamada, sayfa başına de kaybedilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir kaynak yalnızca derleme içinde).  
  
- Uygulama işlevselliği: uygulamanızın gereksinimleri bölümünde gerçek zamanlı kaynaklar güncelleştiriliyor?  
  
- İlgili arama davranışı kaynak başvuru türü.  
  
- Belirli bir özellik veya kaynak türü ve o türden yerel davranışı.  
  
### <a name="static-resources"></a>Statik kaynaklar  
 Statik kaynak iş aşağıdaki koşullarda en iyi başvuruyor:  
  
- Uygulama tasarımının en tüm kaynaklar sayfasına veya uygulama düzeyinde kaynak sözlükleri yoğunlaşır. Statik kaynak başvuruları değil yeniden değerlendirimiş bir sayfayı yeniden yüklemeyi gibi çalışma zamanı davranışları göre ve bu nedenle olabilir, kaynak başına gerekli olmadığı durumlarda çok sayıda dinamik kaynak başvurularını kaçınmak için bazı performans avantajı ve uygulama tasarımı.  
  
- Açık olmadığından bir özelliğin değerini ayarladığınız bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable>.  
  
- Bir DLL içine derlenmiş ve uygulamanın bir parçası paketlenmiş veya uygulamalar arasında paylaşılan bir kaynak sözlüğü oluşturuyorsunuz.  
  
- Özel denetim için bir tema oluşturma ve tema içinde kullanılan kaynakları tanımlarsınız. Bu durum için tipik olarak dinamik kaynak başvurusu arama davranışı istemiyorsanız, böylece öngörülebilir ve kendi başına bir tema için arama statik kaynak başvuru davranışı bunun yerine istersiniz. Dinamik kaynak ile başvuru, hatta bir temasının bir başvuru sol çalışma zamanına kadar değerlendirilmez ve temayı olduğunda uygulanan, bazı yerel öğe temanızı başvuru çalışılırken bir anahtarı yeniden tanımlayacak ve yerel öğenin önceki kalacak kaybedilebilir Tema için kendi arama. Bu durumda, temanızı beklenen şekilde davranmaz.  
  
- Çok sayıda bağımlılık özellikleri ayarlamak için kaynakları kullanıyorsanız. Bağımlılık özelliklerine sahip geçerli değerini önbelleğe alma özelliği sistem tarafından etkin olarak, yükleme zamanında değerlendirilebilen bir bağımlılık özelliği için bir değer belirtirseniz, bağımlılık özelliği için yeniden değerlendirimiş ifadelerinin denetlemek sahip değil ve döndürebilir Son etkin değeri. Bu teknik bir performans kazancı olabilir.  
  
- Temel alınan kaynak için tüm tüketicileri değiştirmek istediğinizde ya da ayrı yazılabilir örnekleri için her bir tüketici kullanarak korumak istediğiniz [x: Shared Attribute](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Statik kaynak arama davranışı  
  
1. İstenen anahtar özelliğini ayarlayan bir öğe tarafından tanımlanan kaynak sözlüğünün içinde arama işlemi olup olmadığını denetler.  
  
2. Arama işlemi üst öğe ve kendi kaynak sözlüğü için mantıksal ağaç yukarı, ardından erişir. Kök öğe ulaşılana kadar bu devam eder.  
  
3. Ardından, uygulama kaynaklarının denetlenir. Uygulama kaynakları tarafından tanımlanan kaynak sözlüğü içindeki kaynakları olan <xref:System.Windows.Application> nesnesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
 Statik kaynak başvurulara bir kaynak sözlüğü, zaten sözcüksel olarak kaynak başvurusu önce tanımlanmış bir kaynağa başvurması gerekir. İleri başvurulara tarafından bir statik kaynak başvurusu çözümlenemiyor. Statik kaynak başvurularını kullanıyorsanız, kaynak olarak kullanılmak üzere tasarlanmış kaynakları veya her bir ilgili kaynak sözlüğü başına yakın tanımlanan şekilde bu nedenle, kaynak sözlüğü yapısını tasarlamanız gerekir.  
  
 Statik kaynak araması, temalar veya sistem kaynakları genişletebilir, ancak bu olduğundan, yalnızca desteklenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyici istek erteler. Çalışma zamanı teması sayfayı yüklemez zaman düzgün bir şekilde uygulama için geçerli olacak şekilde erteleme gereklidir. Ancak, temalar veya sistem kaynakları önerilmez yalnızca mevcut bilinen anahtarlarına statik kaynak başvuruyor. Tema gerçek zamanlı kullanıcı tarafından değiştirilirse bu başvuruları değerlendirilmez olmasıdır. Tema veya sistem kaynakları istediğinizde bir dinamik kaynak başvurusu daha güvenilir oldu. Bir tema öğesi başka bir kaynak istediğinde istisnadır. Bu başvurular, daha önce belirtilen nedenlerden dolayı statik kaynak başvurularını olmalıdır.  
  
 Statik kaynak başvuru bulunamazsa özel durum davranışını değiştirir. Kaynak ertelendi özel çalışma zamanında oluşur. Kaynak ertelenmiş değil, yükleme zamanında özel durum oluşur.  
  
### <a name="dynamic-resources"></a>Dinamik kaynak  
 Dinamik kaynak aşağıdaki koşullarda en iyi şekilde çalışır:  
  
- Kaynak değeri çalışma zamanına kadar bilinmemesi koşullara bağlıdır. Bu, sistem veya başka kullanıcı tarafından ayarlanabilir olan kaynaklar içerir. Örneğin, tarafından kullanıma sunulan gibi sistem özelliklerine başvuran bir ayarlayıcı değerleri oluşturabilirsiniz <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, veya <xref:System.Windows.SystemParameters>. Sonuç olarak kullanıcı ve işletim sisteminin çalışma zamanı ortamından geldiğinden, bu değerler gerçek anlamda dinamiktir. Ayrıca, burada sayfa düzeyinde kaynak erişim değişikliği de yakalamalısınız değiştirebilirsiniz uygulama düzeyi Temalar da olabilir.  
  
- Oluşturuyorsanız veya özel bir denetim için tema stilleri başvuruyor.  
  
- İçeriğini ayarlamak istediğinize bir <xref:System.Windows.ResourceDictionary> uygulama ömrü boyunca.  
  
- Burada bir ileri başvuru gerekebilir bağımlılıklarını içeren bir karmaşık kaynak yapısı var. Statik kaynak başvurularını İleri başvurulara desteklemez ancak çalışma zamanına kadar değerlendirilecek kaynak gerekmediği için dinamik kaynak başvuruları bunları destekleyen ve İleri başvurulara bu nedenle ilgili bir kavram değildir.  
  
- Bir derleme veya çalışma kümesi perspektifinden özellikle büyük bir kaynağa başvuruyor ve kaynak sayfa yüklendiğinde hemen kullanılamayabilir. Statik kaynak başvuruları her zaman yük [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Sayfa yüklediğinde; aslında kullanılana kadar bir dinamik kaynak başvurusu ancak yüklemez.  
  
- Bir stil ayarlayıcı değerleri Temalar veya diğer kullanıcı ayarlarını etkileyen diğer değerlerden burada gelebilir oluşturuyorsunuz.  
  
- Mantıksal ağaçta uygulama ömrü boyunca yeniden üst öğeleri kaynakları uygulamaya koyuyor. Kaynak arama kapsamı değişiklikleri ayrıca olası üst değiştirme, yeni kapsamına göre hesaplanması reparented öğesinin kaynak istiyorsanız, bir dinamik kaynak başvurusu her zaman kullanın.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Dinamik kaynak arama davranışı  
 Kaynak arama davranışı bir dinamik kaynak başvurusu çağırırsanız, kodunuzda arama davranışı parallels <xref:System.Windows.FrameworkElement.FindResource%2A> veya <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1. İstenen anahtar özelliğini ayarlayan bir öğe tarafından tanımlanan kaynak sözlüğünün içinde arama işlemi olup olmadığını denetler.  
  
    - Öğe tanımlıyorsa bir <xref:System.Windows.FrameworkElement.Style%2A> özelliği <xref:System.Windows.Style.Resources%2A> sözlükte <xref:System.Windows.Style> denetlenir.  
  
    - Öğe tanımlıyorsa bir <xref:System.Windows.Controls.Control.Template%2A> özelliği <xref:System.Windows.FrameworkTemplate.Resources%2A> sözlükte <xref:System.Windows.FrameworkTemplate> denetlenir.  
  
2. Arama işlemi üst öğe ve kendi kaynak sözlüğü için mantıksal ağaç yukarı, ardından erişir. Kök öğe ulaşılana kadar bu devam eder.  
  
3. Ardından, uygulama kaynaklarının denetlenir. Uygulama kaynakları tarafından tanımlanan kaynak sözlüğü içindeki kaynakları olan <xref:System.Windows.Application> nesnesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
4. Tema kaynak sözlüğü, şu anda etkin tema için denetlenir. Tema çalışma zamanında değişirse, değeri değerlendirilir.  
  
5. Sistem kaynakları denetlenir.  
  
 Özel durum davranışını (varsa) değişir:  
  
- Bir kaynak tarafından istenmişse bir <xref:System.Windows.FrameworkElement.FindResource%2A> çağırın ve bulunamadı; bir özel durum oluşturulur.  
  
- Bir kaynak tarafından istenmişse bir <xref:System.Windows.FrameworkElement.TryFindResource%2A> çağırın ve bulunamadı, hiçbir özel durum oluşturulur, ancak döndürülen değer `null`. Ayarlanan özelliğin kabul edilmez, `null`, daha derin bir özel durum tetiklenir hala mümkün ise (ayarlanan bireysel özelliğe bağlıdır).  
  
- Bir kaynak olarak dinamik kaynak başvuru istenip istenmediğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve, bulunamadı sonra genel özellik sistemde davranışı bağlıdır, ancak genel hiçbir özellik ayarlama işlemini kaynağın bulunduğu düzeyinde oluştu gibi davranıştır. Örneğin, arka planı ayarlamayı denerseniz, bir değerlendirilemeyen bir kaynağı kullanarak bir düğmeye öğenin sonuçları herhangi bir değer ayarlayın, ancak geçerli değerini özelliği sistem ve değer önceliği diğer katılımcılardan yine de gelebilir. Örneğin, arka plan değeri hala yerel olarak tanımlanan düğme stilini veya tema stili gelebilir. Tema stilleri tarafından tanımlanmayan özellikler için özellik meta verileri varsayılan değerden başarısız kaynak değerlendirmesinden sonra etkili değer gelebilir.  
  
#### <a name="restrictions"></a>Kısıtlamalar  
 Dinamik kaynak başvurularını önemli bazı kısıtlamalar vardır. Aşağıdakilerden en az biri true olması gerekir:  
  
- Bir özellik olmalıdır ayarlanan özelliğin bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Özelliği tarafından yedeklenmesi gereken bir <xref:System.Windows.DependencyProperty>.  
  
- Başvuru arasında bir değer için olan bir <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
- Ayarlanan özelliğin üzerinde bir özelliği olmalıdır bir <xref:System.Windows.Freezable> değerlerinden birine sağlanan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> özelliği veya <xref:System.Windows.Setter> değeri.  
  
 Ayarlanan özelliğin olması gerektiğinden bir <xref:System.Windows.DependencyProperty> veya <xref:System.Windows.Freezable> özelliği, çoğu özellik değişiklikleri yaymak için kullanıcı Arabirimi bir özellik değişiminin (değiştirilen dinamik kaynak değeri) özellik sistemi tarafından onaylanır. Çoğu denetimleri başka bir düzen denetimi, zorlayacak mantığı içerir bir <xref:System.Windows.DependencyProperty> değişiklikleri ve özellik düzeni etkileyebilir. Ancak, tüm özellikleri sahip bir [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md) süreliğine kullanıcı arabiriminde güncelleştirme şekilde değeri sağlamak için değer olarak garanti edilir. Bu işlevselliği hala özelliğine bağlı olarak yanı sıra özelliği veya bile uygulamanızın mantıksal yapısı sahibi türüne bağlı olarak değişebilir.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Stiller ve DataTemplates örtük anahtarları  
 Tüm öğeleri, daha önce belirtilen bir <xref:System.Windows.ResourceDictionary> bir anahtar olması gerekir. Ancak, gelmez tüm kaynakların bir açık olması gerektiğini `x:Key`. Anahtar değeri için başka bir özelliğin değerini yere bağlıdır, bir kaynak tanımlandığında bir örtülü anahtar birden fazla nesne türlerini destekler. Ancak bu bir örtülü anahtar bilinir bir `x:Key` açık bir anahtarı bir özniteliktir. Açık bir anahtarı belirterek herhangi bir örtük anahtarı geçersiz kılabilirsiniz.  
  
 Kaynaklar için çok önemli bir senaryo olduğundan tanımlarken bir <xref:System.Windows.Style>. Aslında, bir <xref:System.Windows.Style> stilleri için yeniden kullanılması kendiliğinden yönelik olduğundan neredeyse her zaman bir kaynak sözlüğünde bir girdi olarak tanımlanır. Stilleri hakkında daha fazla bilgi için bkz. [stil ve şablon oluşturma](../controls/styling-and-templating.md).  
  
 Denetimler için stiller hem ile oluşturulabilir ve bir örtük anahtar ile başvurulan. Tema stilleri bir denetimin varsayılan görünümünü tanımlayan örtük bu anahtara bağlıdır. Örtük anahtar istediği, açısından <xref:System.Type> denetimi. Kaynak tanımlama açısından örtük anahtar <xref:System.Windows.Style.TargetType%2A> stili. Özel denetimler için temaları oluşturuyorsanız, bu nedenle, mevcut tema stilleri ile etkileşimde bulunan stiller oluşturmak, belirtmeniz gerekmez bir [x: Key yönergesi](../../xaml-services/x-key-directive.md) söz konusu <xref:System.Windows.Style>. Ve tema stilleri kullanmak istiyorsanız, herhangi bir stili belirtmeniz gerekmez. Örneğin, aşağıdaki stil tanımını olsa bile çalışır <xref:System.Windows.Style> anahtara sahip kaynak görünmez:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Stil gerçekten bir anahtarı yok: örtük anahtarı `typeof(` <xref:System.Windows.Controls.Button> `)`. Biçimlendirme içinde belirttiğiniz bir <xref:System.Windows.Style.TargetType%2A> doğrudan türü olarak adı (veya isteğe bağlı olarak kullanabileceğiniz [{... x: Type}](../../xaml-services/x-type-markup-extension.md) döndürülecek bir <xref:System.Type>.  
  
 Tarafından kullanılan varsayılan tema stil mekanizmaları aracılığıyla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], stil ve çalışma zamanı stil olarak uygulanır bir <xref:System.Windows.Controls.Button> sayfasında olsa bile <xref:System.Windows.Controls.Button> kendisini belirtmek çalışmaz, <xref:System.Windows.FrameworkElement.Style%2A> özelliği veya belirli bir kaynak Stil başvuru. Sayfada tanımlı stil kodunuzu daha önce arama sırası tema sözlük stilde aynı anahtarı kullanarak tema sözlük stili daha bulunur. Yalnızca belirtebilirsiniz `<Button>Hello</Button>` sayfası ve stil ile tanımlanan yerinde <xref:System.Windows.Style.TargetType%2A> , `Button` için bu düğmeyi uygular. İsterseniz, aynı türü değere stiliyle hala açıkça anahtarlayabilirsiniz <xref:System.Windows.Style.TargetType%2A>, anlaşılabilir olması adına, biçimlendirme, ancak bu isteğe bağlıdır.  
  
 Örtük stiller tuşları, Denetim uygulanmaz <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> olduğu `true` (Ayrıca <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> yerel davranışı için denetim sınıfı yerine açıkça denetim örneği üzerinde bir parçası olarak ayarlanmış olabilir). Ayrıca, türetilmiş sınıf senaryoları için örtük anahtarları desteklemek için Denetim kılmalı <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (parçası olarak sağlanan tüm mevcut denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bunu). Stilleri, temalar ve denetim tasarımı hakkında daha fazla bilgi için bkz. [Stillenebilir Denetimleri Tasarlama için yönergeler](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> Ayrıca bir örtülü anahtar vardır. Örtük anahtarı için bir <xref:System.Windows.DataTemplate> olduğu <xref:System.Windows.DataTemplate.DataType%2A> özellik değeri. <xref:System.Windows.DataTemplate.DataType%2A> açıkça kullanmak yerine türü adı olarak da belirtilebilir [{... x: Type} ](../../xaml-services/x-type-markup-extension.md). Ayrıntılar için bkz [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [Kaynağı Tanımlama ve Kaynağa Başvurma](how-to-define-and-reference-a-resource.md)
- [Uygulama Yönetimine Genel Bakış](../app-development/application-management-overview.md)
- [x:Type İşaretleme Uzantısı](../../xaml-services/x-type-markup-extension.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [DynamicResource İşaretleme Uzantısı](dynamicresource-markup-extension.md)
