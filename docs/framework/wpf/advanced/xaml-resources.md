---
title: XAML Kaynakları
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958812"
---
# <a name="xaml-resources"></a>XAML Kaynakları
Kaynak, uygulamanızdaki farklı yerlerde yeniden kullanılabilen bir nesnedir. Kaynak örnekleri, fırçalar ve stiller içerir. Bu genel bakışta, içindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kaynakların nasıl kullanılacağı açıklanmaktadır. Ayrıca, kod kullanarak veya kod ile [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]arasında birbirlerinin yerine kaynak oluşturup erişebilirsiniz. Daha fazla bilgi için bkz. [kaynaklar ve kod](resources-and-code.md).  
  
> [!NOTE]
> Bu konuda açıklanan kaynak dosyaları [WPF uygulama kaynağı, içerik ve veri dosyaları](../app-development/wpf-application-resource-content-and-data-files.md) bölümünde açıklanan kaynak dosyalarından farklıdır ve [uygulama kaynaklarını yönetme (.net) bölümünde açıklanan katıştırılmış veya bağlı kaynaklardan farklıdır ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML 'de kaynakları kullanma  
 Aşağıdaki örnek bir sayfanın kök <xref:System.Windows.Media.SolidColorBrush> öğesinde kaynak olarak bir kaynağı tanımlar. Örnek daha sonra kaynağa başvurur ve bir <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Controls.TextBlock>,, ve <xref:System.Windows.Controls.Button>gibi çeşitli alt öğelerin özelliklerini ayarlamak için kullanır.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Her çerçeve düzeyindeki öğe<xref:System.Windows.FrameworkElement> (veya <xref:System.Windows.FrameworkContentElement>), bir kaynağın <xref:System.Windows.FrameworkElement.Resources%2A> tanımladığı kaynakları (bir <xref:System.Windows.ResourceDictionary>olarak) içeren özellik olan bir özelliğine sahiptir. Herhangi bir öğe üzerinde kaynakları tanımlayabilirsiniz. Bununla birlikte, kaynaklar genellikle, örnekteki kök öğe <xref:System.Windows.Controls.Page> üzerinde tanımlanmıştır.  
  
 Kaynak sözlüğündeki her kaynak benzersiz bir anahtara sahip olmalıdır. Biçimlendirme içinde kaynakları tanımlarken, [X:Key yönergesi](../../xaml-services/x-key-directive.md)aracılığıyla benzersiz anahtarı atarsınız. Genellikle, anahtar bir dizedir; Bununla birlikte, uygun biçimlendirme uzantılarını kullanarak da diğer nesne türlerine ayarlayabilirsiniz. Kaynakların dize olmayan anahtarları, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]belirli özellik alanlarında, özellikle stiller, bileşen kaynakları ve veri stili için kullanılır.  
  
 Bir kaynağı tanımladıktan sonra, anahtar adını belirten bir kaynak biçimlendirme uzantısı söz dizimini kullanarak bir özellik değeri için kullanılacak kaynağa başvurabilirsiniz, örneğin:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Yukarıdaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekte, yükleyici <xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini `{StaticResource MyBrush}` üzerinde <xref:System.Windows.Controls.Button>işlediğinde, kaynak arama mantığı ilk olarak <xref:System.Windows.Controls.Button> öğe için kaynak sözlüğünü denetler. Kaynak anahtarının `MyBrush` bir tanımına sahip değilse (kaynak koleksiyonu boş ise), bir sonraki arama üst <xref:System.Windows.Controls.Page>öğesi olan <xref:System.Windows.Controls.Button>' ı denetler. <xref:System.Windows.Controls.Button> Bu nedenle, <xref:System.Windows.Controls.Page> kök öğesinde bir kaynak tanımladığınızda, <xref:System.Windows.Controls.Page> öğesinin mantıksal ağacındaki tüm öğeler buna erişebilir ve kaynağı kabul <xref:System.Type> eden herhangi bir özelliğin değerini ayarlamak için aynı kaynağı yeniden kullanabilirsiniz gösterirse. `MyBrush` Önceki örnekte, aynı kaynak iki farklı özellik ayarlıyor <xref:System.Windows.Controls.Control.Background%2A> : <xref:System.Windows.Shapes.Shape.Fill%2A> öğesinin <xref:System.Windows.Controls.Button>ve bir <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statik ve dinamik kaynaklar  
 Bir kaynağa bir statik kaynak veya dinamik kaynak olarak başvurulabilirler. Bu işlem, [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) ya da [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md)kullanılarak yapılır. Biçimlendirme uzantısı, biçimlendirme uzantısının öznitelik dizesini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemesini ve nesneyi bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyiciye döndürmesini sağlayarak bir nesne başvurusunu belirtebileceğiniz bir özelliktir. Biçimlendirme Uzantısı davranışı hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Biçimlendirme uzantısı kullandığınızda, genellikle, ayarlanan özellik bağlamında değerlendirilmek yerine, bu belirli biçimlendirme uzantısı tarafından işlenen dize biçiminde bir veya daha fazla parametre sağlarsınız. [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) , tüm kullanılabilir kaynak sözlüklerinde bu anahtarın değerine bakarak bir anahtarı işler. Yükleme sırasında bu durum, yükleme işleminin statik kaynak başvurusunu alan özellik değerini ataması gereken zaman noktasıdır. Bunun yerine [DynamicResource Işaretleme uzantısı](dynamicresource-markup-extension.md) bir ifade oluşturarak bir anahtarı işler ve bu ifade, uygulama gerçekten çalıştırılana kadar değerlendirilmeden kalır ve bir değer sağlar.  
  
 Bir kaynağa başvurduğunuzda, bir statik kaynak başvurusu veya dinamik kaynak başvurusu kullanıp kullanmayacağınızı aşağıdaki önemli noktalar etkileyebilir:  
  
- Uygulamanıza yönelik kaynakları oluşturma (sayfada, uygulamada [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], yalnızca kaynak derlemesinde olduğu gibi) için genel tasarım.  
  
- Uygulama işlevi: uygulama gereksinimlerinizin gerçek zamanlı olarak kaynakları güncelleştiriyor mu?  
  
- Bu kaynak başvuru türünün ilgili arama davranışı.  
  
- Belirli bir özellik veya kaynak türü ve bu türlerin yerel davranışı.  
  
### <a name="static-resources"></a>Statik kaynaklar  
 Statik kaynak başvuruları aşağıdaki koşullarda en iyi şekilde çalışır:  
  
- Uygulama tasarımınız, tüm kaynaklarının çoğunu sayfa veya uygulama düzeyi kaynak sözlüklerine indirger. Statik kaynak başvuruları, bir sayfayı yeniden yükleme gibi çalışma zamanı davranışlarına göre yeniden değerlendirilmez ve bu nedenle, kaynağınız için gerekli olmadıkları zaman çok sayıda dinamik kaynak başvurmaktan kaçınmanın bazı performans avantajları olabilir ve uygulama tasarımı.  
  
- <xref:System.Windows.DependencyObject> Bir<xref:System.Windows.Freezable>veya içinde olmayan bir özelliğin değerini ayarlardır.  
  
- DLL 'de derlenecek ve uygulamanın parçası olarak paketlenmiş veya uygulamalar arasında paylaşılan bir kaynak sözlüğü oluşturuyorsunuz.  
  
- Özel bir denetim için bir tema oluşturuyor ve Temalar içinde kullanılan kaynakları tanımlıyor. Bu durumda, genellikle dinamik kaynak başvuru arama davranışını istemezsiniz, bunun yerine, aramanın öngörülebilir ve kendi temaya dahil olması için statik kaynak başvuru davranışını tercih edersiniz. Dinamik kaynak başvurusuyla, bir tema içindeki bir başvuru çalışma zamanına kadar değerlendirilmez ve tema uygulandığında, bazı yerel öğeler temanızın başvuruya çalıştığı bir anahtarı yeniden tanımlayabilir ve yerel öğe daha önce düşecek Arama sırasında temaya. Bu durumda, temanız beklenen şekilde davranmaz.  
  
- Çok sayıda bağımlılık özelliğini ayarlamak için kaynaklar kullanıyorsunuz. Bağımlılık özellikleri, özellik sistemi tarafından etkinleştirilen şekilde etkili bir değer önbelleğe alma özelliğine sahiptir, bu nedenle yük zamanında değerlendirilebilen bir bağımlılık özelliği için bir değer sağlarsanız, bağımlılık özelliğinin yeniden değerlendirilen bir ifadeyi denetlemesi gerekmez ve son etkin değer. Bu teknik bir performans avantajı olabilir.  
  
- Tüm tüketiciler için temel alınan kaynağı değiştirmek veya [X:Shared özniteliğini](../../xaml-services/x-shared-attribute.md)kullanarak her bir tüketici için ayrı yazılabilir örnekler saklamak istiyorsunuz.  
  
#### <a name="static-resource-lookup-behavior"></a>Statik kaynak arama davranışı  
  
1. Arama işlemi, özelliği ayarlayan öğe tarafından tanımlanan kaynak sözlüğünde istenen anahtarı denetler.  
  
2. Arama işlemi daha sonra mantıksal ağacı üst öğeye ve kaynak sözlüğüne yukarı doğru taşır. Bu, kök öğeye ulaşılana kadar devam eder.  
  
3. Ardından, uygulama kaynakları denetlenir. Uygulama kaynakları, <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanız için nesne tarafından tanımlanan kaynak sözlüğünde yer alan kaynaklardır.  
  
 Kaynak sözlüğü içinden statik kaynak başvurularının, kaynak başvurusundan önce zaten sözcüksel olarak tanımlanmış bir kaynağa başvurması gerekir. İleri başvurular statik kaynak başvurusuyla çözümlenemez. Bu nedenle, statik kaynak başvurularını kullanırsanız, kaynak sözlüğü yapınızı, kaynak kullanımı için tasarlanan kaynakların ilgili her kaynak sözlüğün başlangıcında veya başında tanımlanmış olacak şekilde tasarlamanız gerekir.  
  
 Statik kaynak arama, temalara veya sistem kaynaklarına genişletebilir, ancak yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyici isteği erteler çünkü bu yalnızca desteklenir. Erteleme, sayfa yüklenirken çalışma zamanı temasının uygulamaya düzgün şekilde uygulanması için gereklidir. Ancak, yalnızca temalarda bulunan veya sistem kaynakları olarak bilinen anahtarlara statik kaynak başvuruları önerilmez. Bunun nedeni, temanın Kullanıcı tarafından gerçek zamanlı olarak değişmesi durumunda bu tür başvuruların yeniden değerlendirilmemelidir. Tema veya sistem kaynakları istediğinizde dinamik bir kaynak başvurusu daha güvenilirdir. Bir tema öğesinin kendisi başka bir kaynağı istemesi durumunda özel durum olur. Bu başvurular, daha önce bahsedilen nedenlerle statik kaynak başvuruları olmalıdır.  
  
 Statik bir kaynak başvurusu bulunamazsa özel durum davranışı değişir. Kaynak ertelendikten sonra özel durum çalışma zamanında oluşur. Kaynak ertelenmediğinde, özel durum yükleme zamanında oluşur.  
  
### <a name="dynamic-resources"></a>Dinamik kaynaklar  
 Dinamik kaynaklar aşağıdaki koşullarda en iyi şekilde çalışır:  
  
- Kaynak değeri, çalışma zamanına kadar bilinmeyen koşullara bağlıdır. Bu, sistem kaynaklarını veya başka türlü Kullanıcı tarafından ayarlanabilen kaynakları içerir. Örneğin,, veya <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts> <xref:System.Windows.SystemParameters>tarafından gösterilen sistem özelliklerine başvuran ayarlayıcı değerleri oluşturabilirsiniz. Bu değerler, son olarak Kullanıcı ve işletim sisteminin çalışma zamanı ortamından geldiğinden, gerçekten dinamiktir. Ayrıca, sayfa düzeyi kaynak erişiminin değişikliği yakalaması gereken uygulama düzeyi temalara de sahip olabilirsiniz.  
  
- Özel bir denetim için Tema stilleri oluşturuyor veya başvuruyorsunuz.  
  
- Bir uygulama ömrü boyunca bir <xref:System.Windows.ResourceDictionary> öğesinin içeriğini ayarlamayı amaçlamıştınız.  
  
- Bir ileri başvurunun gerekli olabileceği, bağımlılıkları olan karmaşık bir kaynak yapısına sahipsiniz. Statik kaynak başvuruları İleri başvuruları desteklemez, ancak kaynak çalışma zamanına kadar değerlendirilmek zorunda olmadığından ve İleri başvuruları ilgili bir kavram olmadığından, dinamik kaynak başvuruları bunları destekler.  
  
- Derleme veya çalışma kümesinin perspektifinden özellikle büyük bir kaynağa başvuruyorsunuz ve kaynak sayfa yüklendiğinde hemen kullanılamayabilir. Statik kaynak başvuruları sayfa yüklenirken her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zaman yüklenir; ancak, dinamik bir kaynak başvurusu gerçekte kullanılana kadar yüklenmez.  
  
- Ayarlayıcı değerlerinin, Temalar veya diğer kullanıcı ayarlarından etkilenen diğer değerlerden gelebileceği bir stil oluşturuyorsunuz.  
  
- Uygulama ömrü boyunca mantıksal ağaçta yeniden üst öğe olabilecek öğelere kaynak uyguluyorsanız. Üst öğeyi değiştirmek, kaynak arama kapsamını da büyük olasılıkla değiştirir, bu nedenle bir yeniden üst öğe olan kaynağın yeni kapsama göre yeniden değerlendirilmasını istiyorsanız, her zaman dinamik bir kaynak başvurusu kullanın.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Dinamik kaynak arama davranışı  
 Ya da <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>çağırırsanız, bir dinamik kaynak başvurusu için kaynak arama davranışı kodunuzda arama davranışına paraleldir.  
  
1. Arama işlemi, özelliği ayarlayan öğe tarafından tanımlanan kaynak sözlüğünde istenen anahtarı denetler.  
  
    - Öğesi bir <xref:System.Windows.FrameworkElement.Style%2A> özelliği <xref:System.Windows.Style.Resources%2A> tanımlıyorsa, içindeki <xref:System.Windows.Style> sözlük denetlenir.  
  
    - Öğesi bir <xref:System.Windows.Controls.Control.Template%2A> özelliği <xref:System.Windows.FrameworkTemplate.Resources%2A> tanımlıyorsa, içindeki <xref:System.Windows.FrameworkTemplate> sözlük denetlenir.  
  
2. Arama işlemi daha sonra mantıksal ağacı üst öğeye ve kaynak sözlüğüne yukarı doğru taşır. Bu, kök öğeye ulaşılana kadar devam eder.  
  
3. Ardından, uygulama kaynakları denetlenir. Uygulama kaynakları, <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanız için nesne tarafından tanımlanan kaynak sözlüğünde yer alan kaynaklardır.  
  
4. Geçerli etkin tema için tema kaynağı sözlüğü denetlenir. Tema çalışma zamanında değişirse değer yeniden değerlendirilecektir.  
  
5. Sistem kaynakları denetlenir.  
  
 Özel durum davranışı (varsa) farklılık gösterir:  
  
- Bir kaynak bir <xref:System.Windows.FrameworkElement.FindResource%2A> çağrı tarafından isteniyorsa ve bulunmazsa, bir özel durum oluşturulur.  
  
- Bir kaynak bir <xref:System.Windows.FrameworkElement.TryFindResource%2A> çağrı tarafından isteniyorsa ve bulunmazsa, hiçbir özel durum oluşturulmaz, ancak döndürülen `null`değer. Ayarlanmakta olan özellik kabul `null`etmez, daha derin bir özel durum ortaya çıkarılacaktır (Bu özellik ayarlanan tek özelliğe bağlıdır).  
  
- Bir kaynak, içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dinamik bir kaynak başvurusu tarafından isteniyorsa ve bulunmazsa, davranış genel özellik sistemine bağlıdır, ancak genel davranış, kaynağın bulunduğu düzeyde hiçbir özellik ayarı işlemi gerçekleşmemiş gibi olur. Örneğin, tek bir düğme öğesinde değerlendirilemeyen bir kaynağı kullanarak arka planı ayarlamaya çalışırsanız, hiçbir değer kümesi sonucu yoktur ancak etkin değer hala Özellik sisteminde ve değer önceliğinde diğer katılımcılardan gelebilir. Örneğin, arka plan değeri yine de yerel olarak tanımlanmış bir düğme stilinden veya tema stilinden gelebilir. Tema stilleriyle tanımlanmayan özellikler için, başarısız bir kaynak değerlendirmesinden sonra geçerli değer, özellik meta verilerindeki varsayılan değerden gelebilir.  
  
#### <a name="restrictions"></a>Kısıtlamalar  
 Dinamik kaynak başvurularının bazı önemli kısıtlamaları vardır. Aşağıdakilerden en az biri doğru olmalıdır:  
  
- Ayarlanan özellik bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>üzerinde bir özellik olmalıdır. Bu özelliğin bir <xref:System.Windows.DependencyProperty>ile kullanılması gerekir.  
  
- Başvuru, içindeki <xref:System.Windows.Style> <xref:System.Windows.Setter>bir değer içindir.  
  
- <xref:System.Windows.Freezable> Ayarlanan özellik, bir <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>veyaözelliğinin değeri ya da bir değerolaraksağlanmışbirüzerindeözelliğiolmalıdır.<xref:System.Windows.Setter>  
  
 Ayarlanan özelliğin bir <xref:System.Windows.DependencyProperty> veya <xref:System.Windows.Freezable> özelliği olması gerektiğinden, özellik değişikliği (değiştirilen dinamik kaynak değeri) özellik sistemi tarafından onaylandığından çoğu özellik değişikliği Kullanıcı arabirimine yayılır. Çoğu denetim, bir <xref:System.Windows.DependencyProperty> değişiklik olduğunda bir denetimin başka bir yerleşimini zorlayan mantığı içerir ve bu özellik düzeni etkileyebilir. Ancak, bir [DynamicResource biçimlendirme uzantısına](dynamicresource-markup-extension.md) sahip olan tüm özelliklerin değeri, Kullanıcı arabiriminde gerçek zamanlı olarak güncelleştirilecek şekilde değeri sağlama garantisi garanti edilir. Bu işlevsellik, özelliğe ve hatta uygulamanızın mantıksal yapısına bağlı olarak farklılık gösterebilir ve bu özellik de değişir.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Stiller, veri şablonları ve örtük anahtarlar  
 Daha önce, içindeki <xref:System.Windows.ResourceDictionary> tüm öğelerin bir anahtar olması gerekir. Ancak, tüm kaynakların açık `x:Key`olması gerektiği anlamına gelmez. Birçok nesne türü, bir kaynak olarak tanımlandığında, anahtar değerinin başka bir özelliğin değerine bağlı olduğu örtük bir anahtarı destekler. Bu örtük anahtar olarak bilinir, ancak `x:Key` öznitelik açık bir anahtardır. Açık bir anahtar belirterek herhangi bir örtük anahtarın üzerine yazabilirsiniz.  
  
 Kaynaklar için çok önemli bir senaryo, bir <xref:System.Windows.Style>tanımladığınızda. Aslında, stiller kendiliğinden <xref:System.Windows.Style> yeniden kullanım için tasarlanan bir kaynak sözlüğünde bir girdi olarak neredeyse her zaman tanımlanır. Stiller hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
 Denetimlerin stilleri hem ile oluşturulabilir hem de örtük bir anahtarla başvuruda bulunabilir. Bir denetimin varsayılan görünümünü tanımlayan Tema stilleri, bu örtülü anahtara bağımlıdır. Bunu isteme açısından örtülü anahtar, denetimin kendisidir <xref:System.Type> . Kaynağı tanımlama açısından örtülü anahtar, stilin ' dır <xref:System.Windows.Style.TargetType%2A> . Bu nedenle, özel denetimler için Temalar oluşturuyorsanız, mevcut Tema stilleriyle etkileşime geçen stiller oluşturuyorsanız, bunun için <xref:System.Windows.Style>bir [x:Key yönergesi](../../xaml-services/x-key-directive.md) belirtmeniz gerekmez. Temalı stilleri kullanmak istiyorsanız, herhangi bir stil belirtmeniz gerekmez. Örneğin, aşağıdaki stil tanımı, <xref:System.Windows.Style> kaynak bir anahtara sahip gibi görünmese de işe yarar:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Bu stilin gerçekten bir anahtarı vardır: örtük anahtar `typeof(`. <xref:System.Windows.Controls.Button> `)` Biçimlendirme bölümünde <xref:System.Windows.Style.TargetType%2A> doğrudan tür adı olarak belirtebilirsiniz (ya da isteğe bağlı olarak [{x:Type...exe](../../xaml-services/x-type-markup-extension.md) ' i kullanabilirsiniz) bir <xref:System.Type>döndürür.  
  
 Tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanılan varsayılan tema stili mekanizmaları aracılığıyla, bu stil, kendi <xref:System.Windows.FrameworkElement.Style%2A> özelliğini veya belirli bir kaynağı belirtmeyi denemese <xref:System.Windows.Controls.Button> de, sayfanın çalışma zamanı stili <xref:System.Windows.Controls.Button> olarak uygulanır. stile başvuru. Sayfada tanımlanan stiliniz, tema sözlüğü stilinin sahip olduğu aynı anahtar kullanılarak, arama dizisinde, tema sözlüğü stilinden daha önce bulunur. Sayfada herhangi bir yeri `<Button>Hello</Button>` belirtebilirsiniz ve `Button` ile <xref:System.Windows.Style.TargetType%2A> tanımladığınız stil bu düğme için geçerlidir. İsterseniz, biçimlendirmedeki açıklık açısından, ancak bu isteğe bağlı olarak, stili aynı tür değeri <xref:System.Windows.Style.TargetType%2A>ile açıkça anahtar olarak girebilirsiniz.  
  
 Varsa <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> ,stiller<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> için örtülü anahtarlar bir denetim üzerinde uygulanmaz (ayrıcadenetimsınıfıiçinyereldavranışınparçasıolarak,denetiminbirörneğineaçıkçaayarlanmayabilir).`true` Ayrıca, türetilmiş sınıf senaryolarında örtük anahtarları desteklemek için, denetimin geçersiz kılması <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> gerekir (bunun bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parçası olarak sunulan tüm mevcut denetimler). Stiller, Temalar ve denetim tasarımı hakkında daha fazla bilgi için bkz. [Stillenebilir denetimler tasarlamak Için yönergeler](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>Ayrıca örtülü bir anahtara sahiptir. <xref:System.Windows.DataTemplate> Bir<xref:System.Windows.DataTemplate.DataType%2A> için örtük anahtar, özellik değeridir. <xref:System.Windows.DataTemplate.DataType%2A>Ayrıca, açıkça [{X:Type...exe}](../../xaml-services/x-type-markup-extension.md)kullanmak yerine türün adı olarak belirtilebilir. Ayrıntılar için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [Kaynağı Tanımlama ve Kaynağa Başvurma](how-to-define-and-reference-a-resource.md)
- [Uygulama Yönetimine Genel Bakış](../app-development/application-management-overview.md)
- [x:Type İşaretleme Uzantısı](../../xaml-services/x-type-markup-extension.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [DynamicResource İşaretleme Uzantısı](dynamicresource-markup-extension.md)
