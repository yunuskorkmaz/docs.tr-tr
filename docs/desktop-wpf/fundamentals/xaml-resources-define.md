---
title: XAML kaynaklarını tanımlama
description: .NET Core için WPF 'de XAML Kaynakları hakkında bilgi edinin. XAML kaynaklarının türlerini anlayın ve XAML kaynaklarını nasıl tanımlayacağınızı öğrenin.
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071285"
---
# <a name="overview-of-xaml-resources"></a>XAML kaynaklarına genel bakış

Kaynak, uygulamanızdaki farklı yerlerde yeniden kullanılabilen bir nesnedir. Kaynak örnekleri, fırçalar ve stiller içerir. Bu genel bakışta Extensible Application Markup Language (XAML) içindeki kaynakların nasıl kullanılacağı açıklanmaktadır. Ayrıca, kodu kullanarak kaynak oluşturup erişebilirsiniz.

> [!NOTE]
> Bu makalede açıklanan XAML Kaynakları, genellikle içerik, veri veya katıştırılmış dosyalar gibi bir uygulamaya eklenen dosya olan *uygulama kaynaklarından* farklıdır.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>XAML 'de kaynakları kullanma

Aşağıdaki örnek bir sayfanın kök <xref:System.Windows.Media.SolidColorBrush> öğesinde kaynak olarak bir kaynağı tanımlar. Örnek daha sonra kaynağa başvurur ve bir <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>, ve gibi çeşitli alt öğelerin özelliklerini ayarlamak için kullanır. <xref:System.Windows.Controls.Button>

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Her çerçeve düzeyindeki öğe<xref:System.Windows.FrameworkElement> (veya <xref:System.Windows.FrameworkContentElement>), tanımlı kaynakları <xref:System.Windows.FrameworkElement.Resources%2A> içeren bir <xref:System.Windows.ResourceDictionary> tür olan bir özelliğine sahiptir. Herhangi bir <xref:System.Windows.Controls.Button>öğe üzerinde (örneğin,) kaynak tanımlayabilirsiniz. Bununla birlikte, kaynaklar genellikle, örnekteki kök öğe <xref:System.Windows.Controls.Page> üzerinde tanımlanmıştır.

Kaynak sözlüğündeki her kaynak benzersiz bir anahtara sahip olmalıdır. Biçimlendirme içinde kaynakları tanımlarken, [X:Key yönergesi](../xaml-services/xkey-directive.md)aracılığıyla benzersiz anahtarı atarsınız. Genellikle, anahtar bir dizedir; Bununla birlikte, uygun biçimlendirme uzantılarını kullanarak da diğer nesne türlerine ayarlayabilirsiniz. Kaynaklar için dize olmayan anahtarlar, özellikle stiller, bileşen kaynakları ve veri stili için WPF 'deki belirli özellik alanlarında kullanılır.

Kaynağın anahtar adını belirten kaynak biçimlendirme uzantısı sözdizimi ile tanımlı bir kaynak kullanabilirsiniz. Örneğin, kaynağı başka bir öğesindeki bir özelliğin değeri olarak kullanın.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

`{StaticResource MyBrush}` Yukarıdaki örnekte, XAML yükleyicisi <xref:System.Windows.Controls.Control.Background%2A> özelliği üzerinde <xref:System.Windows.Controls.Button>özelliğinin değerini işlediğinde, kaynak arama mantığı öncelikle <xref:System.Windows.Controls.Button> öğenin kaynak sözlüğünü denetler. <xref:System.Windows.Controls.Button> Kaynak `MyBrush` anahtarının tanımına sahip değilse (Bu örnekte değil; kaynak koleksiyonu boş ise), bir <xref:System.Windows.Controls.Button>sonraki arama üst öğesini denetler, yani <xref:System.Windows.Controls.Page>. <xref:System.Windows.Controls.Page> Kök öğesinde bir kaynak tanımlarsanız, öğesinin <xref:System.Windows.Controls.Page> mantıksal ağacındaki tüm öğeler buna erişebilir. Aynı kaynağı, kaynağın temsil ettiği aynı türü kabul eden herhangi bir özelliğin değerini ayarlamak için yeniden kullanabilirsiniz. `MyBrush` Önceki örnekte, aynı kaynak iki farklı özellik ayarlıyor: <xref:System.Windows.Controls.Control.Background%2A> öğesinin <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Shapes.Shape.Fill%2A> bir. <xref:System.Windows.Shapes.Rectangle>

## <a name="static-and-dynamic-resources"></a>Statik ve dinamik kaynaklar

Kaynağa statik veya dinamik olarak başvurulabilirler. Başvurular, [StaticResource Işaretleme uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md) ya da [DynamicResource işaretleme uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md)kullanılarak oluşturulur. Biçimlendirme uzantısı, biçimlendirme uzantısının öznitelik dizesini işlemesini ve nesneyi XAML yükleyicisine döndürmesini sağlayarak bir nesne başvurusu belirtmenize imkan tanıyan bir XAML özelliğidir. Biçimlendirme Uzantısı davranışı hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Biçimlendirme uzantısı kullandığınızda, genellikle bu belirli biçimlendirme uzantısı tarafından işlenen dize biçiminde bir veya daha fazla parametre sağlarsınız. [StaticResource Işaretleme uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md) , tüm kullanılabilir kaynak sözlüklerinde bu anahtarın değerine bakarak bir anahtarı işler. İşlem yükleme sırasında gerçekleşir, yükleme işleminin özellik değerini ataması gerekir. Bunun yerine [DynamicResource Işaretleme uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md) bir ifade oluşturarak bir anahtarı işler ve bu ifade, uygulamanın çalıştırılıncaya kadar değerlendirilmeden kalır ve bir değer sağlar.

Bir kaynağa başvurduğunuzda, bir statik kaynak başvurusu veya dinamik kaynak başvurusu kullanıp kullanmayacağınızı aşağıdaki önemli noktalar etkileyebilir:

- Uygulamanıza yönelik kaynakları nasıl oluşturacağınız (sayfada, uygulamada, gevşek XAML 'de veya yalnızca kaynak derlemesinde) genel tasarımı belirlerken, aşağıdakileri göz önünde bulundurun:

- Uygulamanın işlevselliği. Uygulama gereksinimlerinizin gerçek zamanlı bölümünde kaynakları güncelleştiriyor mu?
- Bu kaynak başvuru türünün ilgili arama davranışı.
- Belirli bir özellik veya kaynak türü ve bu türlerin yerel davranışı.

## <a name="static-resources"></a>Statik kaynaklar

Statik kaynak başvuruları aşağıdaki koşullarda en iyi şekilde çalışır:

- Uygulama tasarımınız, kaynaklarının çoğunu sayfa veya uygulama düzeyi kaynak sözlüklerine indirger. Statik kaynak başvuruları, bir sayfayı yeniden yükleme gibi çalışma zamanı davranışlarına göre yeniden değerlendirilmez. Bu nedenle, kaynak ve uygulama tasarımınıza göre gerekli olmadıklarında çok sayıda dinamik kaynak başvurusunun önünden kaçınmanın bazı performans avantajları olabilir.

- Bir <xref:System.Windows.DependencyObject> veya içinde olmayan bir özelliğin değerini ayarlıyoruz <xref:System.Windows.Freezable>.

- Bir DLL 'ye derlenecek ve uygulamanın parçası olarak paketlenebilecek veya uygulamalar arasında paylaşılan bir kaynak sözlüğü oluşturuyorsunuz.

- Özel bir denetim için bir tema oluşturuyorsunuz ve Temalar içinde kullanılan kaynakları tanımlıyor. Bu durumda, genellikle dinamik kaynak başvuru arama davranışını istemezsiniz; Bunun yerine, aramanın öngörülebilir ve kendi temaya dahil olması için statik kaynak başvuru davranışını istersiniz. Dinamik kaynak başvurusuyla, bir tema içindeki bir başvuru bile çalışma zamanına kadar değerlendirilmemiştir. Ayrıca, tema uygulandığında, bazı yerel öğe, temanızın başvuruya çalıştığı bir anahtarı yeniden tanımlayacaktır ve yerel öğe, arama sırasında temanın kendisinden önce kalır. Bu durumda, temanız beklendiği gibi davranmaz.

- Çok sayıda bağımlılık özelliğini ayarlamak için kaynaklar kullanıyorsunuz. Bağımlılık özellikleri, özellik sistemi tarafından etkinleştirilen şekilde etkili bir değer önbelleğe alma özelliğine sahiptir, bu nedenle yük zamanında değerlendirilebilen bir bağımlılık özelliği için bir değer sağlarsanız, bağımlılık özelliği yeniden değerlendirilen bir ifadeyi denetlemek zorunda değildir ve en son etkin değeri döndürebilir. Bu teknik bir performans avantajı olabilir.

- Tüm tüketiciler için temel alınan kaynağı değiştirmek veya [X:Shared özniteliğini](../xaml-services/xshared-attribute.md)kullanarak her bir tüketici için ayrı yazılabilir örnekler saklamak istiyorsunuz.

### <a name="static-resource-lookup-behavior"></a>Statik kaynak arama davranışı

Aşağıdaki, bir statik kaynağa bir özellik veya öğe tarafından başvurulduğunda otomatik olarak gerçekleşen arama işlemini açıklar:

01. Arama işlemi, özelliği ayarlayan öğe tarafından tanımlanan kaynak sözlüğünde istenen anahtarı denetler.

01. Arama işlemi daha sonra mantıksal ağacı üst öğeye ve kaynak sözlüğüne yukarı doğru taşır. Bu işlem, kök öğeye ulaşılana kadar devam eder.

01. Uygulama kaynakları denetlenir. Uygulama kaynakları, WPF uygulamanız için <xref:System.Windows.Application> nesne tarafından tanımlanan kaynak sözlüğünde yer alan kaynaklardır.

Kaynak sözlüğü içinden statik kaynak başvurularının, kaynak başvurusundan önce zaten sözcüksel olarak tanımlanmış bir kaynağa başvurması gerekir. İleri başvurular statik kaynak başvurusuyla çözümlenemez. Bu nedenle, kaynak sözlüğü yapınızı, kaynakların ilgili her kaynak sözlüğün başında veya sonunda tanımlandıkları şekilde tasarlayın.

Statik kaynak arama, temalara veya sistem kaynaklarına genişletebilir, ancak bu arama yalnızca XAML yükleyicisi isteği erteler olduğundan desteklenir. Erteleme, sayfa yüklenirken çalışma zamanı temasının uygulamaya düzgün şekilde uygulanması için gereklidir. Bununla birlikte, tema Kullanıcı tarafından gerçek zamanlı olarak değiştirilmişse, bu tür başvurular yeniden değerlendirilmediği için, yalnızca temalarda bulunan veya sistem kaynakları olarak bilinen anahtarlara statik kaynak başvuruları önerilmez. Tema veya sistem kaynakları istediğinizde dinamik bir kaynak başvurusu daha güvenilirdir. Bir tema öğesinin kendisi başka bir kaynağı istemesi durumunda özel durum olur. Bu başvurular, daha önce bahsedilen nedenlerle statik kaynak başvuruları olmalıdır.

Statik bir kaynak başvurusu bulunamazsa özel durum davranışı değişir. Kaynak ertelendikten sonra özel durum çalışma zamanında oluşur. Kaynak ertelenmediğinde, özel durum yükleme zamanında oluşur.

## <a name="dynamic-resources"></a>Dinamik kaynaklar

Dinamik kaynaklar şu durumlarda en iyi şekilde çalışır:

- Kaynak değeri, sistem kaynakları dahil, aksi takdirde Kullanıcı tarafından ayarlanabilen kaynaklar da dahil olmak üzere, çalışma zamanına kadar bilinmeyen koşullara bağlıdır. Örneğin,, veya <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts> <xref:System.Windows.SystemParameters>tarafından kullanıma sunulan sistem özelliklerine başvuran ayarlayıcı değerleri oluşturabilirsiniz. Bu değerler, son olarak Kullanıcı ve işletim sisteminin çalışma zamanı ortamından geldiğinden, gerçekten dinamiktir. Ayrıca, sayfa düzeyi kaynak erişiminin değişikliği yakalaması gereken uygulama düzeyi temalara de sahip olabilirsiniz.

- Özel bir denetim için Tema stilleri oluşturuyor veya başvuruyoruz.

- Bir uygulama ömrü boyunca bir <xref:System.Windows.ResourceDictionary> uygulamasının içeriğini ayarlamayı amaçlamıştınız.

- Bir ileri başvurunun gerekli olabileceği, bağımlılıkları olan karmaşık bir kaynak yapısına sahipsiniz. Statik kaynak başvuruları İleri başvuruları desteklemez, ancak kaynak çalışma zamanına kadar değerlendirilmek zorunda olmadığından ve ileri başvurular bu nedenle ilgili bir kavram olmadığından, dinamik kaynak başvuruları bunları destekler.

- Derleme veya çalışma kümesinin perspektifinden büyük bir kaynağa başvuruyorsunuz ve kaynak sayfa yüklendiğinde hemen kullanılamayabilir. Statik kaynak başvuruları, sayfa yüklendiğinde XAML 'den her zaman yüklenir. Ancak, dinamik bir kaynak başvurusu kullanılana kadar yüklenmez.

- Ayarlayıcı değerlerinin, Temalar veya diğer kullanıcı ayarlarından etkilenen diğer değerlerden gelebileceği bir stil oluşturuyorsunuz.

- Uygulama ömrü boyunca mantıksal ağaçta yeniden üst öğe olabilecek öğelere kaynak uygulayacağız. Üst öğeyi değiştirmek, kaynak arama kapsamını da büyük olasılıkla değiştirir, bu nedenle bir yeniden üst öğe olan kaynağın yeni kapsama göre yeniden değerlendirilmasını istiyorsanız, her zaman dinamik bir kaynak başvurusu kullanın.

### <a name="dynamic-resource-lookup-behavior"></a>Dinamik kaynak arama davranışı

Bir dinamik kaynak başvurusu için kaynak arama davranışı, veya <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>öğesini çağırırsanız kodunuzda arama davranışına paraleldir:

01. Arama, özelliği ayarlayan öğe tarafından tanımlanan kaynak sözlüğünde istenen anahtarı denetler:

    - Öğesi bir <xref:System.Windows.FrameworkElement.Style%2A> özelliği tanımlıyorsa, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> öğesinin <xref:System.Windows.Style.Resources> sözlüğü denetlenir.

    - Öğesi bir <xref:System.Windows.Controls.Control.Template%2A> özelliği tanımlıyorsa, öğesinin <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> sözlüğü denetlenir.

01. Arama mantıksal ağacı üst öğeye ve kaynak sözlüğüne göre yukarı taşır. Bu işlem, kök öğeye ulaşılana kadar devam eder.

01. Uygulama kaynakları denetlenir. Uygulama kaynakları, WPF uygulamanız için <xref:System.Windows.Application> nesne tarafından tanımlanan kaynak sözlüğünde yer alan kaynaklardır.

01. Tema kaynak sözlüğü, şu anda etkin olan tema için denetlenir. Tema çalışma zamanında değişirse değer yeniden değerlendirilecektir.

01. Sistem kaynakları denetlenir.

Özel durum davranışı (varsa) farklılık gösterir:

- Bir kaynak bir <xref:System.Windows.FrameworkElement.FindResource%2A> çağrı tarafından isteniyorsa ve bulunmazsa, bir özel durum oluşturulur.

- Bir kaynak bir <xref:System.Windows.FrameworkElement.TryFindResource%2A> çağrı tarafından isteniyorsa ve bulunmazsa, özel durum oluşturulmaz ve döndürülen değer `null`. Ayarlanmakta olan özellik kabul `null`edilemediği takdirde, ayarlanmakta olan özelliğe bağlı olarak daha derin bir özel durum oluşturulması mümkün olur.

- Bir kaynak XAML 'de dinamik bir kaynak başvurusu tarafından isteniyorsa ve bulunmazsa, davranış genel özellik sistemine bağlıdır. Genel davranış, kaynağın bulunduğu düzeyde hiçbir özellik ayarı işlemi gerçekleşmesiz değildir. Örneğin, tek bir düğme öğesinde değerlendirilemeyen bir kaynağı kullanarak arka planı ayarlamaya çalışırsanız, hiçbir değer kümesi sonucu yoktur ancak etkin değer hala Özellik sisteminde ve değer önceliğinde diğer katılımcılardan gelebilir. Örneğin, arka plan değeri yine de yerel olarak tanımlanmış bir düğme stilinden veya tema stilinden gelebilir. Tema stilleriyle tanımlanmayan özellikler için, başarısız bir kaynak değerlendirmesinden sonra geçerli değer, özellik meta verilerindeki varsayılan değerden gelebilir.

### <a name="restrictions"></a>Kısıtlamalar

Dinamik kaynak başvurularının bazı önemli kısıtlamaları vardır. Aşağıdaki koşullardan en az biri doğru olmalıdır:

- Ayarlanan özellik bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>üzerinde bir özellik olmalıdır. Bu özelliğin bir <xref:System.Windows.DependencyProperty>ile kullanılması gerekir.

- Başvuru, içindeki bir değer içindir `StyleSetter`.

- Ayarlanan <xref:System.Windows.Freezable> özellik, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> özelliğinin değeri ya da bir <xref:System.Windows.Setter> değer olarak sağlanmış bir üzerinde özelliği olmalıdır.

Ayarlanan özellik bir <xref:System.Windows.DependencyProperty> veya <xref:System.Windows.Freezable> özelliği olmalıdır, çünkü özellik değişikliği (değiştirilen dinamik kaynak değeri) özellik sistemi tarafından onaylandığından, çoğu özellik değişikliği Kullanıcı arabirimine yayabilir. Çoğu denetim, bir <xref:System.Windows.DependencyProperty> değişiklik olduğunda bir denetimin başka bir yerleşimini zorlayan mantığı içerir ve bu özellik düzeni etkileyebilir. Ancak, bir [DynamicResource biçimlendirme uzantısına](../../framework/wpf/advanced/dynamicresource-markup-extension.md) sahip olan tüm özelliklerin, Kullanıcı arabiriminde gerçek zamanlı güncelleştirmeler sağlama garantisi garanti edilir. Bu işlevsellik, özelliğe ve hatta uygulamanızın mantıksal yapısına bağlı olarak farklılık gösterebilir ve bu özellik de değişir.

## <a name="styles-datatemplates-and-implicit-keys"></a>Stiller, veri şablonları ve örtük anahtarlar

İçindeki tüm öğelerin bir anahtarı <xref:System.Windows.ResourceDictionary> olmalıdır, ancak tüm kaynakların açık `x:Key`olması anlamına gelmez. Birçok nesne türü, bir kaynak olarak tanımlandığında, anahtar değerinin başka bir özelliğin değerine bağlı olduğu örtük bir anahtarı destekler. Bu anahtar türü örtük anahtar olarak bilinir, ancak `x:Key` öznitelik açık bir anahtardır. Açık bir anahtar belirterek herhangi bir örtük anahtarın üzerine yazabilirsiniz.

Kaynak için önemli bir senaryo, bir <xref:System.Windows.Style>tanımladığınızda. Aslında, stiller kendiliğinden <xref:System.Windows.Style> yeniden kullanım için tasarlanan bir kaynak sözlüğünde bir girdi olarak neredeyse her zaman tanımlanır. Stiller hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](styles-templates-overview.md)oluşturma.

Denetimlerin stilleri hem ile oluşturulabilir hem de örtük bir anahtarla başvuruda bulunabilir. Bir denetimin varsayılan görünümünü tanımlayan Tema stilleri, bu örtülü anahtara bağımlıdır. Bunu isteme açısından örtük anahtar, denetimin kendisidir <xref:System.Type> . Kaynakları tanımlama açısından örtülü anahtar stilin ' dir <xref:System.Windows.Style.TargetType%2A> . Bu nedenle, özel denetimler için Temalar oluşturuyorsanız veya mevcut Tema stilleriyle etkileşime geçen stiller oluşturuyorsanız, bunun için bir [X:Key yönergesi](../xaml-services/xkey-directive.md) belirtmeniz gerekmez <xref:System.Windows.Style>. Temalı stilleri kullanmak istiyorsanız, herhangi bir stil belirtmeniz gerekmez. Örneğin, aşağıdaki stil tanımı, <xref:System.Windows.Style> kaynak bir anahtara sahip gibi görünmese de işe yarar:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Bu stilin gerçekten bir anahtarı vardır: örtük anahtar `typeof(System.Windows.Controls.Button)`. Biçimlendirme bölümünde <xref:System.Windows.Style.TargetType%2A> doğrudan tür adı olarak belirtebilirsiniz (ya da isteğe bağlı olarak [{X:Type...exe](../xaml-services/xtype-markup-extension.md) ' i kullanabilirsiniz) bir <xref:System.Type>döndürür.

WPF tarafından kullanılan varsayılan tema stili mekanizmaları aracılığıyla, bu stil, kendi <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.Style%2A> özelliğini veya stile belirli bir kaynak başvurusunu belirtmeyi denemese de, sayfanın çalışma zamanı stili olarak uygulanır. Sayfada tanımlanan stiliniz, tema sözlüğü stilinin sahip olduğu aynı anahtar kullanılarak, arama dizisinde, tema sözlüğü stilinden daha önce bulunur. Sayfada herhangi bir yeri `<Button>Hello</Button>` belirtebilirsiniz ve ile <xref:System.Windows.Style.TargetType%2A> `Button` tanımladığınız stil bu düğme için geçerlidir. İsterseniz, biçimlendirmedeki açıklık için aynı tür değeri ile stili açıkça anahtar olarak <xref:System.Windows.Style.TargetType%2A> girebilirsiniz, ancak bu isteğe bağlıdır.

Varsa <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> , `true`stiller için örtülü anahtarlar bir denetim üzerinde uygulanmaz. (Ayrıca, denetimin <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> bir örneğine açıkça değil, denetim sınıfı için yerel davranışın bir parçası olarak ayarlanmış olabileceğini unutmayın.) Ayrıca, türetilmiş sınıf senaryolarında örtük anahtarları desteklemek için, denetimin geçersiz kılması <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> gerekır (WPF kapsamında sunulan tüm mevcut denetimler bu geçersiz kılmayı içerir). Stiller, Temalar ve denetim tasarımı hakkında daha fazla bilgi için bkz. [Stillenebilir denetimler tasarlamak Için yönergeler](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>Ayrıca örtülü bir anahtara sahiptir. Bir <xref:System.Windows.DataTemplate> için örtük anahtar, <xref:System.Windows.DataTemplate.DataType%2A> Özellik değeridir. <xref:System.Windows.DataTemplate.DataType%2A>Ayrıca, açıkça [{X:Type...exe}](../xaml-services/xtype-markup-extension.md)kullanmak yerine türün adı olarak belirtilebilir. Ayrıntılar için bkz. [veri şablonu oluşturmaya genel bakış](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [Uygulama kaynakları](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Kaynaklar ve kod](../../framework/wpf/advanced/resources-and-code.md)
- [Kaynak tanımlama ve başvuru](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Uygulama yönetimine genel bakış](../../framework/wpf/app-development/application-management-overview.md)
- [x:Type işaretleme uzantısı](../xaml-services/xtype-markup-extension.md)
- [StaticResource biçimlendirme uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource biçimlendirme uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
