---
title: "XAML Kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f9d0ff535d0784343b36d0b2df48b123ff3beef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-resources"></a>XAML Kaynakları
Uygulamanız farklı yerde yeniden kullanılabilir bir nesne bir kaynaktır. Fırçalar ve stiller kaynakları örneklerindendir. Bu genel bakışta, kaynakları kullanmayı açıklar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ayrıca oluşturabilir ve kod kullanarak veya birbirinin yerine kodu arasında kaynaklarına erişim ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Daha fazla bilgi için bkz: [kaynaklar ve kod](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Bu konuda açıklanan kaynak dosyaları kaynak dosyaları açıklanan farklı [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) ve açıklanan katıştırılmış veya bağlantılı kaynakları farklı [ Uygulama kaynaklarını (.NET) yönetme](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML içinde kaynakları kullanma  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Media.SolidColorBrush> sayfasının kök öğesinde bir kaynak olarak. Örnek sonra kaynağa başvuran ve de dahil olmak üzere çeşitli alt öğelerinin özelliklerini ayarlamak için kullandığı bir <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>ve bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Her çerçeve düzeyi öğesi (<xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>) sahip bir <xref:System.Windows.FrameworkElement.Resources%2A> kaynakları içeren özellik özelliği (olarak bir <xref:System.Windows.ResourceDictionary>), bir kaynak tanımlar. Herhangi bir öğede kaynakları tanımlayabilirsiniz. Ancak, kaynaklar, kök öğe üzerinde en sık tanımlanır <xref:System.Windows.Controls.Page> örnekte.  
  
 Her bir kaynak sözlüğü kaynağında benzersiz bir anahtar olması gerekir. Biçimlendirmede kaynakları tanımlarken aracılığıyla benzersiz bir anahtar atama [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md). Genellikle, bir dize anahtarıdır; Ancak, ayrıca, diğer nesne türlerine uygun biçimlendirme uzantıları kullanarak ayarlayabilirsiniz. Dize olmayan anahtarları kaynakları için belirli özellik alanlarında tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özellikle stiller, bileşen kaynakları ve veri stil için.  
  
 Bir kaynak tanımladıktan sonra anahtar adını belirtir, örneğin bir kaynak biçimlendirme uzantısı sözdizimi kullanarak bir özellik değeri için kullanılacak kaynak başvurusu yapabilir:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Önceki örnekte, zaman [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyicisi işler değeri `{StaticResource MyBrush}` için <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Button>, kaynak sözlüğü için ilk olarak kaynak arama mantığını denetler <xref:System.Windows.Controls.Button> öğesi. Varsa <xref:System.Windows.Controls.Button> kaynak anahtarı tanımının yok `MyBrush` (yok; kendi kaynak koleksiyonu boş olan), arama üst öğenin yanındaki denetler <xref:System.Windows.Controls.Button>, olduğu <xref:System.Windows.Controls.Page>. Bu nedenle, tanımladığınızda kaynak üzerinde <xref:System.Windows.Controls.Page> kök öğesi, mantıksal ağacının tüm öğeler <xref:System.Windows.Controls.Page> erişebildiğinizi ve herhangi bir özelliğin değerini kabul ettiği için aynı kaynak yeniden <xref:System.Type> , kaynak temsil eder. Önceki örnekte, aynı `MyBrush` kaynak iki farklı özelliklerini ayarlar: <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statik ve dinamik kaynaklar  
 Bir kaynak statik kaynak veya dinamik bir kaynak olarak başvurulabilir. Bu kullanarak yapılır [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) veya [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Biçimlendirme uzantısı özelliğidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik dizesini işlemek ve nesneyi döndürür biçimlendirme uzantısı sağlayarak bir nesne başvurusu belirtebilirsiniz aslına bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyicisi. Biçimlendirme uzantısı davranışı hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Biçimlendirme uzantısı kullandığınızda, belirli biçimlendirme uzantısı tarafından işlenen bir veya daha fazla dize formunda parametreyi yerine ayarlanan özelliği bağlamında değerlendirilen genellikle sağlar. [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) tüm kullanılabilir kaynak sözlüklerindeki bu anahtarın değeri bakarak bir anahtarı işler. Bu yükleme işlemi statik kaynak başvurusu alan özellik değeri atamak için gerektiği zaman zamanında noktasıdır yükleme sırasında gerçekleşir. [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) bunun yerine işlemleri bir ifade ve ifade oluşturarak bir anahtar korunur değerlendirilmemiş uygulama gerçekte çalıştırılıncaya kadar hangi bir zamanda ifade değerlendirilir ve bir değer sağlar.  
  
 Bir kaynak başvuru yaptığınızda, aşağıdaki noktaları statik kaynak başvurusu veya dinamik kaynak başvurusu kullanıp etkileyebilir:  
  
-   Uygulamanız için kaynakları oluşturma, genel tasarım (her sayfada, uygulama içinde kaybetmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir kaynak yalnızca derlemesindeki).  
  
-   Uygulama işlevselliği: uygulama gereksinimlerinizi gerçek zamanlı parçası kaynaklarında güncelleştiriliyor?  
  
-   İlgili arama davranışı kaynak başvuru türü.  
  
-   Belirli bir özellik veya kaynak türü ve bu türlerin yerel davranışı.  
  
### <a name="static-resources"></a>Statik kaynakları  
 Statik kaynak iş en iyi aşağıdaki koşullarda başvuruyor:  
  
-   Uygulama tasarımı en tüm kendi kaynaklarını sayfaya veya uygulama düzeyi kaynak sözlüklerindeki yoğunlaşır. Statik kaynak başvuruları değil yeniden değerlendirimiş bir sayfa yeniden yükleniyor gibi çalışma zamanı davranışlarını temel ve bu nedenle olabilir kaynağınız gerekli olmadığı zaman dinamik kaynak başvuruları sayıda kaçınmak için bazı performans avantajı ve uygulama tasarımı.  
  
-   Açık olmayan bir özelliğin değerini ayarlama bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable>.  
  
-   Bir DLL'e derlenmiş ve uygulamanın bir parçası paketlenmiş veya uygulamalar arasında paylaşılan bir kaynak sözlüğü oluşturuyorsunuz.  
  
-   Özel bir denetim için bir tema oluşturma ve tema içinde kullanılan kaynakları tanımlama. Bu durumda genellikle dinamik kaynak başvuru arama davranışını istiyor musunuz, böylece arama tahmin edilebilir ve tema için kendi içinde bulunan statik kaynak başvuru davranışı yerine istersiniz. Dinamik bir kaynakla bir başvuru içinde tema sol başvuru, hatta çalışma zamanına kadar değerlendirilmez ve tema olduğunda uygulanan, bazı yerel öğesi tema başvuru çalışılırken bir anahtarı yeniden tanımlamak ve yerel öğenin önceden düşen bir fırsat yok Tema için kendisini arama. Bu durumda, tema beklenen şekilde davranır değil.  
  
-   Çok sayıda bağımlılık özelliklerini ayarlamak için kaynaklarını kullanıyor. Bağımlılık özelliklerine sahip özellik sistemi tarafından etkin olarak, yükleme zamanında değerlendirilebilen bağımlılık özelliği için bir değer sağlarsanız, bağımlılık özelliği için bir yeniden değerlendirimiş ifadesi denetlemek sahip değil ve geri dönmek için geçerli değer önbelleğe alma Son etkin değeri. Bu teknik bir performans avantajı olabilir.  
  
-   Tüm Tüketiciler için temel alınan kaynak değiştirmek istediğinizde ya da ayrı yazılabilir örnekler için her bir tüketici kullanarak korumak istediğiniz [x: Shared Attribute](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Statik kaynak arama davranışı  
  
1.  Arama işlemi istenen anahtarı özelliği ayarlar öğesi tarafından tanımlanan kaynak sözlüğüne içinde olup olmadığını denetler.  
  
2.  Arama işlemi, mantıksal ağaçta yukarı doğru sonra üst öğesi ve kendi kaynak sözlüğü erişir. Bu kök öğesi ulaşılana kadar devam eder.  
  
3.  Ardından, uygulama kaynakları denetlenir. Uygulama kaynakları tarafından tanımlanan kaynak sözlüğü içinde bu kaynakları olan <xref:System.Windows.Application> nesnesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
 Statik kaynak başvurulara bir kaynak sözlüğü zaten sözcüksel olarak önce kaynak başvurusu tanımlanmış bir kaynağa başvurması gerekir. İleri başvuruları tarafından statik kaynak başvurusu çözümlenemiyor. Statik kaynak başvurularını kullanıyorsanız, kaynak olarak kullanılmak üzere tasarlanmış kaynakları hiç veya neredeyse her ilgili kaynak sözlüğünün başına tanımlanan gibi bu nedenle, kaynak sözlüğü yapısını tasarlamanız gerekir.  
  
 Statik kaynak arama Temalar veya sistem kaynakları genişletebilir, ancak bu yalnızca çünkü desteklenir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyicisi istek erteler. Erteleme, sayfa yüklendiği zaman çalışma zamanı teması düzgün uygulamaya uygulandığı için gereklidir. Ancak, yalnızca Temalar veya sistem kaynakları önerilmez olarak mevcut bilinen anahtarlarına statik kaynak başvurur. Tema gerçek zamanlı kullanıcı tarafından değiştirilirse bu başvuruları değerlendirilmez olmasıdır. Tema veya sistem kaynakları istediğinde, dinamik kaynak başvurusu daha güvenilirdir. Bir tema öğesi başka bir kaynak istediğinde istisnadır. Bu başvuruları statik kaynak başvuruları, daha önce bahsedilen nedenlerle olmalıdır.  
  
 Statik kaynak başvurusu bulunamazsa, özel durum davranışı değişir. Kaynak ertelendi özel çalışma zamanında oluşur. Kaynak ertelenmiş değil, yükleme zamanında özel durum oluşur.  
  
### <a name="dynamic-resources"></a>Dinamik kaynaklar  
 Dinamik kaynaklar aşağıdaki durumlarda en iyi çalışır:  
  
-   Kaynağın değeri çalışma zamanına kadar bilinmeyen koşullar bağlıdır. Bu, sistem kaynakları veya aksi durumda kullanıcı tarafından ayarlanabilir olan kaynakları içerir. Örneğin, sistem özelliklerine başvuran ayarlayıcı değerleri tarafından sunulan olarak oluşturabileceğiniz <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, veya <xref:System.Windows.SystemParameters>. Sonuç olarak kullanıcı ve işletim sisteminin çalışma zamanı ortamından geldiğinden bu gerçekten dinamik bir değerlerdir. Burada sayfa düzeyi kaynak erişimi de değişiklik yakalama gerekir değişebilir, bu uygulama düzeyi Temalar da olabilir.  
  
-   Oluşturuyorsanız veya özel bir denetim için tema stilleri başvuruyor.  
  
-   İçeriğini ayarlamak istiyorsanız bir <xref:System.Windows.ResourceDictionary> uygulama ömrü sırasında.  
  
-   Burada ileri başvuru gerekebilir bağımlılıklarını sahip bir karmaşık kaynak yapıya sahip. Statik kaynak başvuruları İleri başvuruları desteklemez, ancak kaynak çalışma zamanına kadar değerlendirilmesi gerekmez çünkü dinamik kaynak başvurular bunları destekler ve İleri başvuruları bu nedenle ilgili bir kavram değildir.  
  
-   Açısından bir derleme veya çalışma kümesi, özellikle büyük bir kaynağa başvuran ve sayfa hemen yüklediğinde, kaynak kullanılmayabilir. Statik kaynak başvuruları her zaman yük [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Sayfa yüklediğinde; gerçekte kullanılan kadar dinamik kaynak başvurusu ancak yüklemez.  
  
-   Temalar veya diğer kullanıcı ayarları etkileyen diğer değerler arasından ayarlayıcı değerleri nerede gelebilir stil oluşturuyorsunuz.  
  
-   Mantıksal ağaçta uygulama ömrü boyunca yeniden üst öğelerine kaynakları uyguladığınızı. Ayrıca olası üst değiştirme kaynak arama kapsamı değişiklikleri, bu nedenle, yeni kapsamına göre olmasını reparented öğesi için kaynak istiyorsanız, her zaman dinamik kaynak başvurusu kullanın.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Dinamik kaynak arama davranışı  
 Dinamik kaynak başvurusu kaynak arama davranışı çağırırsanız, kodunuzda arama davranışı parallels <xref:System.Windows.FrameworkElement.FindResource%2A> veya <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Arama işlemi istenen anahtarı özelliği ayarlar öğesi tarafından tanımlanan kaynak sözlüğüne içinde olup olmadığını denetler.  
  
    -   Öğe tanımlıyorsa bir <xref:System.Windows.FrameworkElement.Style%2A> özelliği, <xref:System.Windows.Style.Resources%2A> sözlükte <xref:System.Windows.Style> denetlenir.  
  
    -   Öğe tanımlıyorsa bir <xref:System.Windows.Controls.Control.Template%2A> özelliği, <xref:System.Windows.FrameworkTemplate.Resources%2A> sözlükte <xref:System.Windows.FrameworkTemplate> denetlenir.  
  
2.  Arama işlemi, mantıksal ağaçta yukarı doğru sonra üst öğesi ve kendi kaynak sözlüğü erişir. Bu kök öğesi ulaşılana kadar devam eder.  
  
3.  Ardından, uygulama kaynakları denetlenir. Uygulama kaynakları tarafından tanımlanan kaynak sözlüğü içinde bu kaynakları olan <xref:System.Windows.Application> nesnesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
4.  Tema kaynak sözlüğü, şu anda etkin tema için denetlenir. Temanın çalışma zamanında değişirse değeri değerlendirilir.  
  
5.  Sistem kaynakları denetlenir.  
  
 Özel durum davranışı (varsa) değişir:  
  
-   Bir kaynak tarafından istenmişse bir <xref:System.Windows.FrameworkElement.FindResource%2A> çağırın ve bulunamadı, bir özel durum oluşturulur.  
  
-   Bir kaynak tarafından istenmişse bir <xref:System.Windows.FrameworkElement.TryFindResource%2A> çağırın ve bulunamadı, hiçbir özel durum oluşturuldu, ancak döndürülen değer `null`. Ayarlanan özelliği kabul etmediği varsa `null`, derin bir özel durum gerçekleştirilecektir hala mümkün ise (ayarlanan bireysel özelliğe bağlıdır).  
  
-   Bir kaynak dinamik kaynak başvuruya göre istenip istenmediğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve, bulunamadı sonra davranışı genel özellik sistemine bağlıdır, ancak genel hiçbir özellik ayarlama işlemini kaynağın bulunduğu düzeyinde oluştu gibi bir davranıştır. Örneğin, arka plan üzerinde ayarlamaya çalışırsanız bir değil değerlendirilmesi bir kaynağı kullanarak bir bireysel button öğesi, hiçbir değer sonra sonuçları ayarlayın. ancak geçerli değer hala özelliği sistem ve değer önceliği diğer katılımcıları gelebilir. Örneğin, arka plan değeri hala yerel olarak tanımlanmış düğme stilini veya tema stili gelebilir. Tema stilleri tarafından tanımlanmamış olan özellikler için özellik meta verileri varsayılan değerinden başarısız kaynak değerlendirmesinden sonra etkili değer gelebilir.  
  
#### <a name="restrictions"></a>Kısıtlamalar  
 Dinamik kaynak başvuruları önemli bazı sınırlamaları vardır. Aşağıdaki en az biri doğru olmalıdır:  
  
-   Bir özellik olmalıdır ayarlanan özelliği bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Özelliği tarafından yedeklenmelidir bir <xref:System.Windows.DependencyProperty>.  
  
-   İçindeki bir değer başvurudur bir <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
-   Ayarlanan özelliği üzerinde bir özellik olmalıdır bir <xref:System.Windows.Freezable> herhangi birinin değeri olarak sağlanan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> özelliği, veya bir <xref:System.Windows.Setter> değeri.  
  
 Ayarlanan özelliği olması gerektiğinden bir <xref:System.Windows.DependencyProperty> veya <xref:System.Windows.Freezable> özelliği, çoğu özellik değişiklikleri yayılması için kullanıcı Arabirimi özellik değişikliği (değiştirilen dinamik kaynak değeri) özellik sistemi tarafından onaylanır. Bir denetimin başka bir yerleşim, zorlayacağı mantığı çoğu denetim dahil bir <xref:System.Windows.DependencyProperty> değişiklikleri ve özellik düzeni etkileyebilir. Ancak, tüm özellikler sahip bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) değerin gerçek zamanlı kullanıcı arabiriminde güncelleştirme şekilde sağlamak için bunların değeri olarak garanti. Bu işlevselliği hala özelliği bağlı olarak yanı sıra özelliği veya hatta mantıksal yapısını uygulamanızın sahibi türüne bağlı olarak değişebilir.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Stiller, DataTemplates ve örtülü anahtarlar  
 Tüm öğeleri, daha önce belirtildiği bir <xref:System.Windows.ResourceDictionary> bir anahtara sahip olmalıdır. Ancak, gelmez tüm kaynakların bir açık olması gerektiğini `x:Key`. Anahtar değeri başka bir özellik değerine burada bağlı bir kaynak olarak tanımlandığında örtülü anahtar birkaç nesne türlerini destekler. Ancak bu örtük bir anahtar olarak bilinir bir `x:Key` özniteliği olan açık bir anahtarı. Açık bir anahtarı belirterek örtük tuşa geçersiz kılabilirsiniz.  
  
 Kaynaklar için çok önemli bir senaryo tanımladığınız olduğunda bir <xref:System.Windows.Style>. Aslında, bir <xref:System.Windows.Style> stilleri temelde yeniden kullanmak üzere yönelik olduğundan neredeyse her zaman bir kaynak sözlüğü bir girdi olarak tanımlanır. Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Denetimlerin stilleri hem ile oluşturulabilir ve örtülü anahtar ile başvurulan. Bir denetimin varsayılan görünümünü tanımlayan tema stilleri bu örtülü anahtara bağlıdır. Örtük anahtar istediği, açısından <xref:System.Type> denetimi. Kaynak tanımlama açısından örtük anahtar <xref:System.Windows.Style.TargetType%2A> stili. Özel denetimler için Temalar oluşturuyorsanız, bu nedenle, varolan tema stilleri ile etkileşim stiller oluşturma, belirtmek gerekmez bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) söz konusu <xref:System.Windows.Style>. Ve tema stilleri kullanmak istiyorsanız, herhangi bir stili belirtmeniz gerekmez. Örneğin, aşağıdaki stil tanımını bile çalışır <xref:System.Windows.Style> anahtara sahip kaynak görünmez:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Stil gerçekten bir anahtarı yok: örtülü anahtar `typeof(` <xref:System.Windows.Controls.Button> `)`. Biçimlendirme içinde belirttiğiniz bir <xref:System.Windows.Style.TargetType%2A> türü olarak doğrudan adı (veya isteğe bağlı olarak kullanabileceğiniz [{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) döndürülecek bir <xref:System.Type>.  
  
 Tarafından kullanılan varsayılan tema stili mekanizmalar aracılığıyla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], stil ve çalışma zamanı stil olarak uygulanır bir <xref:System.Windows.Controls.Button> sayfasında olsa bile <xref:System.Windows.Controls.Button> kendisini belirtmek denemez kendi <xref:System.Windows.FrameworkElement.Style%2A> özelliği veya belirli bir kaynak Stil başvuru. Sayfa içinde tanımlanan stilinize arama dizisinde daha önce tema sözlük stilde aynı anahtarı kullanarak tema sözlük stili'den önceki bulunamadı. Yalnızca belirtebilirsiniz `<Button>Hello</Button>` sayfa ve ile tanımlanan stil yerindeki <xref:System.Windows.Style.TargetType%2A> , `Button` bu düğme için geçerli olur. İsterseniz, aynı tür değeri stiliyle hala açıkça anahtarlayabilirsiniz <xref:System.Windows.Style.TargetType%2A>için daha anlaşılır olması, biçimlendirme, ancak bu isteğe bağlıdır.  
  
 Örtük anahtarları stilleri için geçerli olmayan bir denetim varsa <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> olan `true` (Ayrıca <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> yerel davranışı control sınıfı için yerine açıkça denetim örneği üzerinde bir parçası olarak ayarlanmış olabilir). Ayrıca, türetilmiş sınıf senaryolarının örtülü anahtarlarını desteklemek için denetim geçersiz kılmanız gerekir <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (parçası olarak sağlanan tüm var olan denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bunu). Stiller, temalar ve tasarım denetimi hakkında daha fazla bilgi için bkz: [tasarlama Stillenebilir Denetimleri için yönergeleri](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>Ayrıca bir örtük anahtar içeriyor. Örtük anahtar için bir <xref:System.Windows.DataTemplate> olan <xref:System.Windows.DataTemplate.DataType%2A> özellik değeri. <xref:System.Windows.DataTemplate.DataType%2A>açıkça kullanmak yerine türünün adı da belirtilebilir [{x: Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Ayrıntılar için bkz [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.ResourceDictionary>  
 [Uygulama kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Kaynaklar ve kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Bir kaynağa başvurması ve tanımlayın](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)  
 [Uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [DynamicResource Biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
