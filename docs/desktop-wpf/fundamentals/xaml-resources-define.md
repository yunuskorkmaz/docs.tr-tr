---
title: XAML kaynaklarını tanımlama
description: .NET Core için WPF'deki XAML kaynakları hakkında bilgi edinin. XAML kaynaklarının türlerini anlayın ve XAML kaynaklarını nasıl tanımlaylayacağınızı öğrenin.
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

Kaynak, uygulamanızdaki farklı yerlerde yeniden kullanılabilen bir nesnedir. Kaynaklara örnek olarak fırçalar ve stiller verilebilir. Bu genel bakış, Genişletilebilir Uygulama Biçimlendirme Dili'nde (XAML) kaynakların nasıl kullanılacağını açıklar. Ayrıca kod kullanarak kaynakları oluşturabilir ve kaynaklara erişebilirsiniz.

> [!NOTE]
> Bu makalede açıklanan XAML kaynakları, genellikle bir uygulamaya eklenen içerik, veri veya katıştırılmış dosyalar gibi uygulama *kaynaklarından* farklıdır.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>XAML'deki kaynakları kullanma

Aşağıdaki örnek, bir <xref:System.Windows.Media.SolidColorBrush> sayfanın kök öğesi üzerinde bir kaynak olarak tanımlar. Örnek daha sonra kaynağa başvurur ve bir <xref:System.Windows.Shapes.Ellipse>, a <xref:System.Windows.Controls.TextBlock>, ve bir <xref:System.Windows.Controls.Button>.

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Her framework düzeyindeöğe<xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>( veya <xref:System.Windows.FrameworkElement.Resources%2A> ) tanımlanmış <xref:System.Windows.ResourceDictionary> kaynakları içeren bir tür olan bir özelliği vardır. Kaynakları herhangi bir öğeüzerinde tanımlayabilirsiniz, örneğin. <xref:System.Windows.Controls.Button> Ancak, kaynaklar genellikle <xref:System.Windows.Controls.Page> örnekte olan kök öğesi üzerinde tanımlanır.

Kaynak sözlüğündeki her kaynağın benzersiz bir anahtarı olmalıdır. Biçimlendirmede kaynakları tanımladığınızda, [x:Key Yönergesi](../xaml-services/xkey-directive.md)aracılığıyla benzersiz anahtarı atarsınız. Genellikle, anahtar bir dize; ancak, uygun biçimlendirme uzantılarını kullanarak diğer nesne türlerine de ayarlayabilirsiniz. Kaynakların dize olmayan anahtarları, özellikle stiller, bileşen kaynakları ve veri şekillendirme için WPF'deki belirli özellik alanları tarafından kullanılır.

Kaynağın anahtar adını belirten kaynak biçimlendirme uzantısı sözdizimi ile tanımlanmış bir kaynak kullanabilirsiniz. Örneğin, kaynağı başka bir öğedeki bir özelliğin değeri olarak kullanın.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

Önceki örnekte, XAML `{StaticResource MyBrush}` yükleyici üzerinde <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>özellik için değeri işlediğinde, kaynak arama mantığı ilk <xref:System.Windows.Controls.Button> öğe için kaynak sözlüğü denetler. Kaynak <xref:System.Windows.Controls.Button> `MyBrush` anahtarının bir tanımı yoksa (bu örnekte yok; kaynak koleksiyonu boşsa), sonraki arama , <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>yani . <xref:System.Windows.Controls.Page> Kök öğe üzerinde bir kaynak tanımlarsanız, mantıksal ağaçtaki <xref:System.Windows.Controls.Page> tüm öğeler erişebilir. Ayrıca, kaynağın temsil ettiği aynı türü kabul eden herhangi bir özelliğin değerini ayarlamak için aynı kaynağı yeniden kullanabilirsiniz. Önceki örnekte, aynı `MyBrush` kaynak iki farklı <xref:System.Windows.Controls.Control.Background%2A> özellik <xref:System.Windows.Controls.Button>ayarlar: <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Rectangle>ve bir .

## <a name="static-and-dynamic-resources"></a>Statik ve dinamik kaynaklar

Bir kaynak statik veya dinamik olarak başvurulabilir. Başvurular, Statik Kaynak [Biçimlendirme Uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md) veya [Dinamik Kaynak Biçimlendirme Uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md)kullanılarak oluşturulur. Biçimlendirme uzantısı, biçimlendirme uzantısı öznitelik dizesini işleyerek bir nesne başvurusu belirtmenizi ve nesneyi XAML yükleyicisine döndürmenizi sağlayan bir XAML özelliğidir. Biçimlendirme uzantısı davranışı hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)

Bir biçimlendirme uzantısı kullandığınızda, genellikle belirli bir biçimlendirme uzantısı tarafından işlenen dize formunda bir veya daha fazla parametre sağlarsınız. [Statik Kaynak Biçimlendirme Uzantısı,](../../framework/wpf/advanced/staticresource-markup-extension.md) kullanılabilir tüm kaynak sözlüklerinde bu anahtarın değerini bakarak bir anahtarı işler. İşleme yükleme işlemi özellik değeri atamak gerektiğinde yük sırasında olur. [Dinamik Kaynak Biçimlendirme Uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md) bunun yerine bir ifade oluşturarak bir anahtarı işler ve bu ifade uygulama çalışana kadar değerlendirilmeden kalır ve bu zamanda ifade değerlendirilir ve bir değer sağlar.

Bir kaynağa başvururken, aşağıdaki hususlar statik bir kaynak başvurusu mu yoksa dinamik bir kaynak başvurusu mu kullandığınızı etkileyebilir:

- Uygulamanız için kaynakları nasıl oluşturduğunuzla ilgili genel tasarımı belirlerken (sayfa başına, uygulamada, gevşek XAML'de veya yalnızca kaynak derlemesinde), aşağıdakileri göz önünde bulundurun:

- Uygulamanın işlevselliği. Kaynakları uygulama gereksinimlerinizin gerçek zamanlı bir bölümünde güncelliyor musunuz?
- Bu kaynak başvuru türünün ilgili arama davranışı.
- Belirli özellik veya kaynak türü ve bu tür yerel davranış.

## <a name="static-resources"></a>Statik kaynaklar

Statik kaynak başvuruları aşağıdaki durumlar için en iyi şekilde çalışır:

- Uygulama tasarımınız kaynaklarının çoğunu sayfa veya uygulama düzeyinde kaynak sözlüklerinde yoğunlaştır. Statik kaynak başvuruları, sayfayı yeniden yüklemek gibi çalışma zamanı davranışlarına göre yeniden değerlendirilmez. Böylece, kaynak ve uygulama tasarımınıza bağlı olarak gerekli olmadıklarında çok sayıda dinamik kaynak referansını önlemek için bazı performans avantajı olabilir.

- Üzerinde olmayan <xref:System.Windows.DependencyObject> bir özelliğin değerini <xref:System.Windows.Freezable>ayarlıyorsun.

- DLL'de derlenecek ve uygulamanın bir parçası olarak paketlenecek veya uygulamalar arasında paylaşılan bir kaynak sözlüğü oluşturuyorsunuz.

- Özel denetim için bir tema oluşturuyorsunuz ve temalar içinde kullanılan kaynakları tanımlıyorsunuz. Bu durumda, genellikle dinamik kaynak başvurusu arama davranışı istemiyorum; bunun yerine, aramanın öngörülebilir ve temaya bağımsız olması için statik kaynak başvuru davranışı istiyorsunuz. Dinamik bir kaynak başvurusuyla, tema içindeki bir başvuru bile çalışma süresine kadar değerlendirilmez hale bırakılır. ve tema uygulandığında, bazı yerel öğenin temanızın başvurmaya çalıştığı bir anahtarı yeniden tanımlaması ve yerel öğenin aramadaki temanın kendisinden önce düşme olasılığı vardır. Bu durumda, temanız beklendiği gibi olmayacak.

- Çok sayıda bağımlılık özelliği ayarlamak için kaynakları kullanıyorsunuz. Bağımlılık özellikleri, özellik sistemi tarafından etkinleştirilen etkin değer önbelleğe alma özelliğine sahiptir, bu nedenle yük zamanında değerlendirilebilecek bir bağımlılık özelliği için bir değer sağlarsanız, bağımlılık özelliğiyeniden değerlendirilen ifadeyi denetlemek zorunda değildir ve son etkin değeri döndürebilir. Bu teknik bir performans yararı olabilir.

- Tüm tüketiciler için temel kaynağı değiştirmek veya [x:Shared Özniteliği'ni](../xaml-services/xshared-attribute.md)kullanarak her tüketici için ayrı yazılabilir örnekleri korumak istiyorsunuz.

### <a name="static-resource-lookup-behavior"></a>Statik kaynak arama davranışı

Statik bir kaynak bir özellik veya öğe tarafından başvurulduğunda otomatik olarak gerçekleşen arama işlemini açıklar:

01. Arama işlemi, özelliği kümeleyen öğe tarafından tanımlanan kaynak sözlüğü içinde istenen anahtarı denetler.

01. Arama işlemi daha sonra mantıksal ağacı yukarı doğru üst öğeye ve kaynak sözlüğüne geçer. Bu işlem kök öğeye ulaşılına kadar devam ediyor.

01. Uygulama kaynakları kontrol edilir. Uygulama kaynakları, WPF uygulamanızın <xref:System.Windows.Application> nesnesi tarafından tanımlanan kaynak sözlüğündeki kaynaklardır.

Kaynak sözlüğü içinden statik kaynak başvuruları, kaynak başvurusundan önce sözlü olarak tanımlanmış bir kaynağa başvurmalıdır. İleri referansları statik kaynak başvurusu ile çözülemez. Bu nedenle, kaynak sözlüğü yapınızı, kaynakların her bir kaynak sözlüğünün başında veya yakınında tanımlandığı şekilde tasarla.

Statik kaynak araması temalara veya sistem kaynaklarına genişletilebilir, ancak bu arama yalnızca XAML yükleyici isteği ertelediği için desteklenir. Erteleme, sayfa yüklerini yüklerken çalışma zamanı temasının uygulamaya düzgün şekilde uygulanabilmesi için gereklidir. Ancak, tema kullanıcı tarafından gerçek zamanlı olarak değiştirilirse, bu tür başvurular yeniden değerlendirilmediği için, yalnızca temalarda veya sistem kaynakları olarak var olduğu bilinen anahtarlara statik kaynak başvuruları önerilmez. Dinamik bir kaynak başvurusu, tema veya sistem kaynakları istediğinizde daha güvenilirdir. Özel durum, bir tema öğesinin başka bir kaynak istemesidir. Bu başvurular, daha önce belirtilen nedenlerle statik kaynak başvuruları olmalıdır.

Statik kaynak başvurusu bulunamazsa özel durum davranışı değişir. Kaynak ertelendiyse, özel durum çalışma zamanında oluşur. Kaynak ertelenmediyse, özel durum yükleme zamanında oluşur.

## <a name="dynamic-resources"></a>Dinamik kaynaklar

Dinamik kaynaklar en iyi zaman:

- Sistem kaynakları veya kullanıcı ayarlanabiliri olan kaynaklar da dahil olmak üzere kaynağın değeri, çalışma süresine kadar bilinmeyecek koşullara bağlıdır. Örneğin, sistem özelliklerini <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>veya <xref:System.Windows.SystemParameters>. Sonuçta kullanıcı ve işletim sisteminin çalışma zamanı ortamından geldiği için bu değerler gerçekten dinamiktir. Sayfa düzeyinde kaynak erişiminin de değişikliği yakalaması gereken uygulama düzeyinde temalar da olabilir.

- Özel bir denetim için tema stilleri oluşturuyor veya başvuruyorsunuz.

- Bir uygulama ömrü boyunca <xref:System.Windows.ResourceDictionary> bir içeriği ayarlamak niyetinde.

- Bir ileri başvuru gerektirebilir, karşılıklı bağımlılıkları olan karmaşık bir kaynak yapısı var. Statik kaynak başvuruları ileri başvurularını desteklemez, ancak kaynağın çalışma zamanına kadar değerlendirilmesi gerekmedığından ve ileri başvurubunedenle ilgili bir kavram olmadığından dinamik kaynak başvuruları bunları destekler.

- Derleme veya çalışma kümesi açısından büyük bir kaynağa başvuruyorsunuz ve sayfa yüklendiğinde kaynak hemen kullanılmayabilir. Statik kaynak başvuruları, sayfa yüklendiğinde her zaman XAML'den yüklenir. Ancak, dinamik bir kaynak başvurusu kullanılmadan yüklenmez.

- Ayarlayıcı değerlerinin temalardan veya diğer kullanıcı ayarlarından etkilenen diğer değerlerden gelebileceği bir stil oluşturuyorsunuz.

- Kaynakları, uygulama ömrü boyunca mantıksal ağaçta yeniden ebeveynlik yapılabilecek öğelere uyguluyorsunuz. Üst öğenin değiştirilmesi de kaynak arama kapsamını değiştirebilir, bu nedenle yeniden ebeveynlik öğesi kaynağının yeni kapsama göre yeniden değerlendirilmesini istiyorsanız, her zaman dinamik bir kaynak başvurusu kullanın.

### <a name="dynamic-resource-lookup-behavior"></a>Dinamik kaynak arama davranışı

Dinamik bir kaynak başvurusu için kaynak arama davranışı, kodunuzda arama <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>veya aşağıdakileri ararsanız arama davranışıyla paralellik verir:

01. Kaynak sözlüğünde, özelliği kümeleyen öğe tarafından tanımlanan istenen anahtarın arama denetimleri:

    - Öğe bir <xref:System.Windows.FrameworkElement.Style%2A> özelliği tanımlıyorsa, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> öğenin <xref:System.Windows.Style.Resources> sözlüğü denetlenir.

    - Öğe bir <xref:System.Windows.Controls.Control.Template%2A> özelliği tanımlıyorsa, öğenin <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> sözlüğü denetlenir.

01. Arama, mantıksal ağacı yukarı doğru üst öğeye ve kaynak sözlüğüne geçer. Bu işlem kök öğeye ulaşılına kadar devam ediyor.

01. Uygulama kaynakları kontrol edilir. Uygulama kaynakları, WPF uygulamanızın <xref:System.Windows.Application> nesnesi tarafından tanımlanan kaynak sözlüğündeki kaynaklardır.

01. Tema kaynağı sözlüğü, şu anda etkin olan tema için denetlenir. Tema çalışma zamanında değişirse, değer yeniden değerlendirilir.

01. Sistem kaynakları denetlenir.

Özel durum davranışı (varsa) değişir:

- Bir kaynak bir <xref:System.Windows.FrameworkElement.FindResource%2A> arama tarafından istendi yse ve bulunamadıysa, bir özel durum atılır.

- Bir kaynak bir <xref:System.Windows.FrameworkElement.TryFindResource%2A> arama tarafından istendiyse ve bulunamadıysa, özel durum atılmaz ve döndürülen değer . `null` Ayarlanan özellik kabul `null`etmiyorsa, ayarlanan tek tek özelliğe bağlı olarak daha derin bir özel durum atılabilir.

- XAML'de dinamik bir kaynak başvurusu tarafından bir kaynak istendiyse ve bulunamadıysa, davranış genel özellik sistemine bağlıdır. Genel davranış, kaynağın var olduğu düzeyde özellik ayarı işlemi oluşmuş gibi. Örneğin, değerlendirilemeyecek bir kaynak kullanarak tek bir düğme öğesi üzerinde arka plan ayarlamaya çalışırsanız, hiçbir değer kümesi sonuçları, ancak etkili değer yine de özellik sistemi ve değer önceliği diğer katılımcılardan gelebilir. Örneğin, arka plan değeri yine de yerel olarak tanımlanmış bir düğme stilinden veya tema stilinden gelebilir. Tema stilleri tarafından tanımlanmayan özellikler için, başarısız bir kaynak değerlendirmesinden sonraki etkin değer özellik meta verilerindeki varsayılan değerden gelebilir.

### <a name="restrictions"></a>Kısıtlamalar

Dinamik kaynak başvurularının bazı önemli kısıtlamaları var. Aşağıdaki koşullardan en az biri doğru olmalıdır:

- Ayarlanan özellik bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Bu özellik bir <xref:System.Windows.DependencyProperty>.

- Başvuru, bir değer içindeki `StyleSetter`bir değer içindir.

- Ayarlanan <xref:System.Windows.Freezable> özellik, bir <xref:System.Windows.FrameworkElement> veya özellik veya <xref:System.Windows.FrameworkContentElement> bir <xref:System.Windows.Setter> değer değeri olarak sağlanan bir özellik olmalıdır.

Ayarlanan özellik bir <xref:System.Windows.DependencyProperty> veya <xref:System.Windows.Freezable> özellik olması gerektiğinden, özellik değişikliği (değiştirilen dinamik kaynak değeri) özellik sistemi tarafından kabul edildiğinden, çoğu özellik değişikliği UI'ye yayılabilir. Çoğu denetim, bir <xref:System.Windows.DependencyProperty> değişiklik ve özelliğin düzeni etkileyebileceği nde denetimin başka bir düzenini zorlayacak mantık içerir. Ancak, değeri olarak [Dinamik Kaynak Biçimlendirme Uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md) olan tüm özelliklerin UI'de gerçek zamanlı güncelleştirmeler sağlaması garanti edilmez. Bu işlevsellik, özelliğin sahibinin türüne ve hatta uygulamanızın mantıksal yapısına bağlı olarak da değişebilir.

## <a name="styles-datatemplates-and-implicit-keys"></a>Stiller, Veri Şablonları ve örtük anahtarlar

A'daki <xref:System.Windows.ResourceDictionary> tüm öğelerin bir anahtarı olsa da, bu tüm `x:Key`kaynakların açık olması gerektiği anlamına gelmez. Birkaç nesne türü, anahtar değerinin başka bir özelliğin değerine bağlı olduğu bir kaynak olarak tanımlandığında örtük bir anahtarı destekler. Bu anahtar türü örtük anahtar olarak bilinirken, `x:Key` öznitelik açık bir anahtardır. Açık bir anahtar belirterek herhangi bir örtük anahtarın üzerine yazabilirsiniz.

Kaynaklar için önemli bir senaryo, <xref:System.Windows.Style>bir . Aslında, a <xref:System.Windows.Style> hemen hemen her zaman bir kaynak sözlüğünde bir giriş olarak tanımlanır, çünkü stilleri doğal olarak yeniden kullanılmak üzere tasarlanmıştır. Stiller hakkında daha fazla bilgi için [Stil ve Templating'e](styles-templates-overview.md)bakın.

Denetim stilleri hem örtülü bir anahtarla oluşturulabilir hem de başvurulabilir. Denetimin varsayılan görünümünü tanımlayan tema stilleri bu örtük anahtara dayanır. Bunu istemek açısından, örtük anahtar <xref:System.Type> denetimin kendisidir. Kaynakları tanımlama açısından, örtük anahtar <xref:System.Windows.Style.TargetType%2A> stildir. Bu nedenle, özel denetimler için temalar oluşturuyorsanız veya varolan tema stilleriyle etkileşimedebilen stiller oluşturuyorsanız, bunun <xref:System.Windows.Style>için bir [x:Key Yönergesi](../xaml-services/xkey-directive.md) belirtmeniz gerekmez. Temalı stilleri kullanmak istiyorsanız, herhangi bir stil belirtmeniz gerekmez. Örneğin, <xref:System.Windows.Style> kaynağın bir anahtarı yok gibi görünse de aşağıdaki stil tanımı çalışır:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Bu stil gerçekten bir anahtar var: örtük anahtar `typeof(System.Windows.Controls.Button)`. Biçimlendirmede, <xref:System.Windows.Style.TargetType%2A> doğrudan tür adı olarak belirtebilirsiniz (veya isteğe bağlı olarak [{x:Type...}](../xaml-services/xtype-markup-extension.md) bir <xref:System.Type>.

WPF tarafından kullanılan varsayılan tema stili mekanizmaları sayesinde, bu stil, <xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.Style%2A> özelliğini veya stiliçin <xref:System.Windows.Controls.Button> belirli bir kaynak referansını belirtmeye çalışmasa bile, sayfadaki bir stilin çalışma zamanı stili olarak uygulanır. Sayfada tanımlanan stiliniz, tema sözlüğü stiliyle aynı tuşu kullanarak, tema sözlüğü stilinden daha erken arama sırasında bulunur. Sayfanın herhangi `<Button>Hello</Button>` bir yerinde belirtebilirsiniz ve <xref:System.Windows.Style.TargetType%2A> tanımladığınız `Button` stil bu düğmeye uygulanır. İsterseniz, yine de açıkça biçimlendirme netlik <xref:System.Windows.Style.TargetType%2A> için aynı tür değeri ile stil anahtar olabilir, ancak bu isteğe bağlıdır.

Stiller için örtük tuşlar <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> bir `true`denetim üzerinde geçerli değildir. (Ayrıca, <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> denetimin bir örneğinde açıkça değil, denetim sınıfı için yerel davranışın bir parçası olarak ayarlanabileceğini unutmayın.) Ayrıca, türemiş sınıf senaryoları için örtük anahtarları <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> desteklemek için denetimgeçersiz kılınmalıdır (WPF'nin bir parçası olarak sağlanan tüm varolan denetimler bu geçersiz kılmayı içerir). Stiller, temalar ve denetim tasarımı hakkında daha fazla bilgi için [Stylable Denetimleri Tasarlama Yönergeleri'ne](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md)bakın.

<xref:System.Windows.DataTemplate>ayrıca örtülü bir anahtarı vardır. A <xref:System.Windows.DataTemplate> için örtük <xref:System.Windows.DataTemplate.DataType%2A> anahtar özellik değeridir. <xref:System.Windows.DataTemplate.DataType%2A>[{x:Type...}](../xaml-services/xtype-markup-extension.md)kullanmak yerine türün adı olarak da belirtilebilir. Ayrıntılar için [Bkz. Veri Templating Genel Bakış.](../../framework/wpf/data/data-templating-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [Uygulama kaynakları](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Kaynaklar ve kod](../../framework/wpf/advanced/resources-and-code.md)
- [Bir kaynağı tanımlama ve gönderme](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Uygulama yönetimine genel bakış](../../framework/wpf/app-development/application-management-overview.md)
- [x:Tür biçimlendirme uzantısı](../xaml-services/xtype-markup-extension.md)
- [StaticResource biçimlendirme uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DinamikKaynak biçimlendirme uzantısı](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
