---
title: Biçimlendirme Uzantıları ve WPF XAML
ms.date: 03/30/2017
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
ms.openlocfilehash: f18a369157c1e37411a3c8d8b6dfcce99bc347c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="markup-extensions-and-wpf-xaml"></a>Biçimlendirme Uzantıları ve WPF XAML
Bu konu, kendi sözdizimi kurallarına, amaç ve bunları altını çizen sınıfı nesne modeli de dahil olmak üzere XAML, biçimlendirme uzantıları kavramı tanıtır. Biçimlendirme uzantıları bir XAML dili ve XAML Hizmetleri .NET uygulaması genel özelliğidir. Bu konuda özellikle kullanımda WPF XAML işaretleme uzantılarına ayrıntılarını verir.  
  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML işlemcileri ve İşaretleme uzantıları  
 Genel olarak bakıldığında, XAML ayrıştırıcı bir ilkel türe dönüştürülebilir veya bazı yollarla nesneye dönüştürülemiyor sabit değerli bir dize olarak ya da bir öznitelik değeri çevirebilir. Tür dönüştürücüsünü başvurarak bu tür bir anlamına gelir; Bu konuda belgelenmiştir [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md). Ancak, farklı bir davranışı gerekli olduğu senaryolar vardır. Örneğin, bir XAML işlemci özniteliğin değerini yeni bir nesne grafiğinin nesne içinde sonuçlanması gerektiğini değil sağlanabilir. Bunun yerine, öznitelik grafiğin başka bir parçası olarak zaten yapılandırılmış bir nesne veya statik bir nesneye başvuru yapan bir nesne grafiğinin neden. XAML işlemci oluşturucunun bir nesnenin varsayılan olmayan bağımsız değişkenler sağlayan bir sözdizimi kullanılacak sağlanabilir başka bir senaryodur. Bu senaryolar biçimlendirme uzantısı çözümü burada sağlayabilir türleridir.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Temel biçimlendirme uzantısı sözdizimi  
 Biçimlendirme uzantısı değerlerini sağlamak için bir öznitelik kullanımı özelliklerinde, bir özellik öğesi kullanımı ya da her ikisini de özellikleri için uygulanabilir.  
  
 Bir öznitelik değeri sağlamak için kullanılan bir biçimlendirme uzantısı sırası bir XAML işlemciye ayırt sözdizimi açma ve küme ayraçları kapatma varlığını olur ({ve}). İşaretleme uzantısı türü sonra hemen parantezinden izleyen dize belirteci tarafından tanımlanır.  
  
 Özellik öğesi sözdiziminde kullanıldığında, bir işaretleme uzantısı görsel olarak bir özellik öğesi değeri sağlamak için kullanılan başka bir öğenin aynıdır: biçimlendirme uzantısı sınıfı (<> köşeli parantez alınmış bir öğe olarak başvuran bir XAML öğe bildirimi ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlanan biçimlendirme uzantıları  
 Birçok biçimlendirme uzantıları XAML WPF uygulaması özel değildir ancak bunun yerine iç bilgileri uygulamalarında veya XAML dili olarak özelliklerini olan mevcut. Bu biçimlendirme uzantıları System.Xaml derleme genel .NET Framework XAML Hizmetleri bir parçası olarak uygulanır ve XAML dili XAML ad içinde. Ortak biçimlendirme kullanımı açısından bu biçimlendirme uzantıları tarafından tanımlanabilen genellikle `x:` kullanımı öneki. <xref:System.Windows.Markup.MarkupExtension> (System.Xaml ayrıca tanımlanmıştır) temel sınıf tüm biçimlendirme uzantıları XAML okuyucuları ve WPF XAML dahil olmak üzere XAML yazıcılarının desteklenmesi için kullanması gereken desen sağlar.  
  
-   `x:Type` sağladığı <xref:System.Type> adlandırılmış türü için nesnesi. Bu özellik, stil ve şablonlar en sık kullanılır. Ayrıntılar için bkz [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
-   `x:Static` statik değer oluşturur. Değerleri doğrudan hedef özelliğin değeri türü olmayan değer türü kodu varlıklardan gelir, ancak bu tür değerlendirilebilir. Ayrıntılar için bkz [x: Static işaretleme uzantısı](../../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
-   `x:Null` belirtir `null` bir özellik için bir değer olarak ve öznitelikler veya özellik öğesi değerleri için kullanılabilir. Ayrıntılar için bkz [x: Null işaretleme uzantısı](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
-   `x:Array` XAML sözdizimi, durumlarda koleksiyonu desteği WPF temel öğeleri tarafından sağlanan ve denetim modelleri kasıtlı olarak kullanılmaz genel dizilerde oluşturulması için destek sağlar. Ayrıntılar için bkz [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Öneki, XAML dili ön tanımlı bir XAML dosyası veya üretim kök öğesinin tipik XAML ad alanı eşlemesi için kullanılır. Örneğin, bunu kullanan XAML dosyası WPF uygulamalar için Visual Studio şablonları başlatmak `x:` eşleme. Kendi XAML ad alanı eşlemesi farklı önek belirteci seçebilir, ancak bu belgeleri varsayılan varsayacak `x:` XAML ad uzayı XAML dili için tanımlanmış bir parçası olan bu varlıkların aygıtlardır tanımlamanın bir araç olarak eşleme WPF ile varsayılan ad alanı veya diğer XAML ad uzayları belirli bir framework ilişkili değil.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>WPF özgü biçimlendirme uzantıları  
 Kaynak başvuruları destekleyen WPF programlamada kullanılan en yaygın biçimlendirme uzantıları dosyalardır (`StaticResource` ve `DynamicResource`), veri bağlamayı destekleyen (`Binding`).  
  
-   `StaticResource` önceden tanımlanan bir kaynağa değerini getirilmesiyle bir özellik için bir değer sağlar. A `StaticResource` değerlendirme sonuçta XAML yükleme sırasında yaptığı ve çalışma zamanında nesne grafiğinin erişimi yok. Ayrıntılar için bkz [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   `DynamicResource` bir değer özelliği için bir kaynak için çalışma zamanı başvuru olması için bu değeri ertelemeyi tarafından sağlar. Dinamik kaynak başvurusu yeni bir arama her zaman böyle bir kaynak erişilir ve çalışma zamanında nesne grafiğinin erişimi zorlar. Bu erişim alabilmek için `DynamicResource` kavram WPF özellik sistemindeki bağımlılık özellikleri tarafından desteklenir ve ifadeler değerlendirilir. Bu nedenle yalnızca kullanabilirsiniz `DynamicResource` bir bağımlılık özelliği hedef için. Ayrıntılar için bkz [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
-   `Binding` Çalışma zamanında üst nesne için geçerli veri bağlamı kullanarak bir özellik için değer veri bağlı sağlar. Veri bağlama belirtmek için önemli satır içi sözdizimi sağladığından bu biçimlendirme uzantısı oldukça karmaşıktır. Ayrıntılar için bkz [biçimlendirme uzantısı bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
-   `RelativeSource` ait kaynak bilgileri sağlayan bir <xref:System.Windows.Data.Binding> birkaç olası çalışma zamanı nesne ağacına ilişkilerde gezinme. Bu, çok kullanım şablonlarında oluşturulan veya çevresindeki nesne ağacının hakkında tam bilgi olmadan kod oluşturulan bağlamaları için özel kaynak sağlar. Ayrıntılar için bkz [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md).  
  
-   `TemplateBinding` Şablon kullanacağınız sınıfının nesne modeli tanımlanan özelliklerinden gelen şablonlu özellikleri için değerleri kullanmak bir denetim şablonu sağlar. Diğer bir deyişle, şablon tanımının içinde özelliği şablon uygulandıktan sonra yalnızca var olan bir bağlam erişebilirsiniz. Ayrıntılar için bkz [TemplateBinding biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md). Pratik kullanımı hakkında daha fazla bilgi için `TemplateBinding`, bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
-   `ColorConvertedBitmap` göreceli olarak gelişmiş bir görüntü senaryoyu destekler. Ayrıntılar için bkz [ColorConvertedBitmap biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md).  
  
-   `ComponentResourceKey` ve `ThemeDictionary` özellikle kaynakları ve özel denetimler ile paketlenmiştir Temalar için kaynak arama özelliklerini destekler. Daha fazla bilgi için bkz: [ComponentResourceKey Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md), [ThemeDictionary biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md), veya [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Uzantısı sınıfları  
 Genel XAML dili hem WPF özgü biçimlendirme uzantıları için her biçimlendirme uzantısı davranışını XAML işlemciye tanımlanan bir `*Extension` öğesinden türetilen sınıf <xref:System.Windows.Markup.MarkupExtension>ve bir uygulamasını sağlar <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> yöntem. Bu yöntem her uzantı üzerinde biçimlendirme uzantısı değerlendirildiğinde, döndürülen nesneyi sağlar. Döndürülen nesne, genellikle biçimlendirme uzantısı geçirilen çeşitli dize belirteçleri göre değerlendirilir.  
  
 Örneğin, <xref:System.Windows.StaticResourceExtension> SAX gerçek kaynak arama yüzey uyarlamasını böylece kendi <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> uygulaması için kullanılan bir dize olması, belirli bir uygulamaya girişi istenen nesnesini döndürür Kaynak tarafından aramak kendi `x:Key`. Bu uygulama ayrıntılarını çoğunu varolan bir işaretleme uzantısı kullanıyorsanız, önemli değildir.  
  
 Bazı biçimlendirme uzantıları dize belirteci bağımsız değişkenleri kullanmayın. Bir statik veya tutarlı değeri döndürmeleri olduğundan veya hangi değeri döndürülmelidir için bağlam geçtiğini hizmetlerden biri aracılığıyla kullanılabilir olduğundan budur `serviceProvider` parametresi.  
  
 `*Extension` Adlandırma modeli aşağıdaki kolaylığı ve tutarlılığı için gibidir. Biçimlendirme uzantısı için destek gibi o sınıfın tanımlamak XAML işlemci sırayla gerekli değildir. Kod temeliniz System.Xaml içerir ve .NET Framework XAML hizmetlerinde uygulamaları kullanan sürece, tüm olan XAML biçimlendirme uzantısı öğesinden türetilen olarak kabul edilecek gerekli <xref:System.Windows.Markup.MarkupExtension> ve yapım sözdizimini desteklemek için. WPF devam etmeyin biçimlendirme uzantı etkinleştiriliyor sınıfları tanımlar `*Extension` düzeni, örneğin adlandırma <xref:System.Windows.Data.Binding>. Genellikle bu sınıfı, saf biçimlendirme uzantısı desteği ötesinde destekler nedeni. Durumunda <xref:System.Windows.Data.Binding>, sınıf XAML ile ilgisi yoktur senaryoları için çalışma zamanı erişim yöntemleri ve nesne özelliklerini destekler.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Uzantı sınıfı başlatma metin yorumu  
 İşaretleme uzantısı adını ve küme ayraçları içinde hala aşağıdaki dize belirteçleri XAML işlemcisi tarafından aşağıdaki yollardan biriyle yorumlanır:  
  
-   Virgül, her zaman bir ayırıcı veya bireysel belirteçlerin sınırlayıcı'temsil eder.  
  
-   Tek tek ayrılmış belirteçlerin herhangi eşittir işareti içermiyorsa, her belirteç oluşturucu bağımsız değişkeni olarak kabul edilir. Her Oluşturucu parametresi, bu imza ve bu imzaya göre beklenen doğru sırada beklenen türe olarak verilmelidir.  
  
    > [!NOTE]
    >  XAML işlemci çifti bağımsız değişken sayısı eşleşen oluşturucu çağırmanız gerekir. Özel biçimlendirme uzantısı uyguluyorsanız, bu nedenle, birden çok parametre ile aynı bağımsız değişken sayısı sağlamaz. Aynı parametre sayısı ile birden fazla biçimlendirme uzantısı Oluşturucusu yolu varsa bir XAML işlemci nasıl davranacağını davranışını tanımlı değil, ancak bir XAML işlemci bu durum varsa kullanımıyla ilgili bir özel durum izni olduğunu düşündüğünüz biçimlendirme uzantısı türü tanımlar.  
  
-   Tek tek ayrılmış belirteçleri eşittir işareti içeren, sonra XAML işlemci biçimlendirme uzantısı için önce varsayılan oluşturucu çağırır. Ardından, her ad = değer çifti biçimlendirme uzantısı ve bu özelliğe atamak için bir değer var. özellik adı olarak yorumlanır.  
  
-   Oluşturucu davranışını ve bir işaretleme uzantısı ayarı davranışını özelliği arasında paralel bir sonuç ise, hangi davranışın kullandığınız bir önemi yoktur. Kullanmak için daha yaygın bir kullanımdır *özelliği*`=`*değeri* çiftleri için birden fazla ayarlanabilir özelliği, yalnızca, biçimlendirme daha kasıtlı kolaylaştırır ve, varsa biçimlendirme uzantıları yanlışlıkla Oluşturucu parametreleri sırasını değiştirmek daha az olabilir. (Özellik belirttiğinizde, değer çiftleri = bu özelliklerin herhangi bir sırada olabilir.) Ayrıca, bir işaretleme uzantısı her biri ayarlanabilir özelliklerini ayarlar Oluşturucu parametresini sağlayan garantisi yoktur. Örneğin, <xref:System.Windows.Data.Binding> uzantısı aracılığıyla ayarlanabilir birçok özelliklere sahip bir biçimlendirme uzantısı *özelliği*`=`*değeri* form, ancak <xref:System.Windows.Data.Binding> yalnızca iki destekler Oluşturucular: varsayılan bir oluşturucu ve bir başlangıç yolunu ayarlar biri.  
  
-   Değişmez değer virgül escapement olmadan biçimlendirme uzantısı için geçirilemez.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Kaçış sıraları ve İşaretleme uzantıları  
 XAML işlemcide işleme özniteliğini süslü ayraçlar biçimlendirme uzantısı dizisi göstergesi olarak kullanır. Değişmez değer kuşak tarafından izlenen bir boş kaşlı ayraç çifti kullanarak bir kaçış sırası girerek değişmez değer kuşak karakter öznitelik değer gerekirse oluşturmak mümkündür. Bkz: [ {} çıkış sırası - biçimlendirme uzantısı](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Biçimlendirme uzantıları XAML kullanımı iç içe geçme  
 Birden çok biçimlendirme uzantıları iç içe geçmiş desteklenir ve her biçimlendirme uzantısı derin önce değerlendirilir. Örneğin, aşağıdaki kullanım göz önünde bulundurun:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 Bu kullanımı `x:Static` deyimi ilk olarak değerlendirilir ve bir dize döndürür. Dize bağımsız değişkeni olarak sonra kullanılır `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Biçimlendirme uzantıları ve özellik öğesi sözdizimi  
 Bir özellik öğesi değeri dolduran bir nesne öğesi olarak kullanıldığında, bir işaretleme uzantısı XAML'de kullanılabilir tipik nesne türü destekli öğeden görsel olarak ayırt sınıftır. Pratik arasındaki tipik nesne öğesi ve bir işaretleme uzantısı biçimlendirme uzantısı türü belirtilmiş bir değer hesaplanan veya bir ifade olarak ertelenmiş olduğunu farktır. Bu nedenle mekanizmaları biçimlendirme uzantısı için özellik değerlerinin olası tür hatalar için farklı ve diğer programlama modelleri geç bağlama özelliğini nasıl işleneceğini benzer olacaktır. Sıradan object öğesi türü eşleştirin XAML ayrıştırıldığında ayarını hedef özelliği için değerlendirilir.  
  
 Nesne öğesi sözdiziminde bir özellik öğesi doldurmak için kullanıldığında, çoğu biçimlendirme uzantıları, içerik ya da daha fazla özellik öğesi sözdizimini içinde sahip olmaz. Bu nedenle nesne öğe etiketi kapatın ve hiçbir alt öğeleri sağlayın. Herhangi bir nesne öğesi XAML işlemcisi tarafından karşılaşıldığında, ayrıştırılmış öğesinden oluşturulan nesnesini başlatır o sınıfın Oluşturucusu çağrılır. Biçimlendirme uzantısı sınıfı farklı değildir: nesne öğesi sözdiziminde kullanılabilmesi için biçimlendirme uzantısı istiyorsanız, varsayılan bir oluşturucu sağlamanız gerekir. Var olan bazı biçimlendirme uzantıları etkili başlatma için belirtilen en az bir gerekli özellik değerine sahip. Öyleyse, bu özellik değeri olarak bir özellik özniteliği genellikle nesnesi öğesinde verilir. İçinde [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md) ve [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md) başvuru sayfaları, biçimlendirme gerekli özellikleri (ve gerekli özellikleri adları) sahip olan uzantı not ettiğiniz. Başvuru sayfaları, ayrıca nesne öğesi sözdizimi veya öznitelik sözdizimi belirli biçimlendirme uzantıları için izin verilmeyen olmadığını unutmayın. Önemli bir durumdur [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md), hangi destekleyemez öznitelik sözdizimi çünkü bu dizinin içeriğini içinde etiketleme içeriği olarak belirtilmelidir. Dizi içeriği genel nesneler olarak işlenir, bu nedenle hiçbir öznitelik için varsayılan tür dönüştürücüsünü uygulanabilirdir. Ayrıca, [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md) gerektiren bir `type` parametresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML Ad Alanı (x:) Dil Özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [StaticResource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [İşaretleme Uzantısı Bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)  
 [DynamicResource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)  
 [x:Type İşaretleme Uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
