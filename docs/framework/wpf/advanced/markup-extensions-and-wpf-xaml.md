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
ms.openlocfilehash: 1726ce0798f2511ee2e7d910ee5f6a0f30f9a282
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585649"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Biçimlendirme Uzantıları ve WPF XAML
Bu konu, kendi sözdizimi kurallarını, amacı ve bunları altını sınıfı nesne modeli de dahil olmak üzere XAML için biçimlendirme uzantıları kavramı tanıtır. Biçimlendirme uzantıları bir XAML dili ve .NET uygulamasının XAML hizmetleri genel özelliğidir. Bu konuda özellikle kullanılmak üzere WPF XAML biçimlendirme uzantıları ayrıntıları.  
  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML işlemci ve İşaretleme uzantıları  
 Genel olarak bakıldığında, XAML ayrıştırıcı bir ilkel dönüştürülebilir veya bazı durumlarda bir nesneye dönüştürmek değişmez değer dize olarak ya da bir öznitelik değeri yorumlayabilir. Bir tür dönüştürücüsü başvurarak olduğu gibi bir anlamına gelir; Bu konu başlığı altında belgelenen [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md). Ancak, farklı bir davranış gerekli olduğu senaryolar da vardır. Örneğin, bir öznitelik değeri içinde yeni bir nesne grafiğinin sonuçlanması gerektiğini değil bir XAML işlemci sağlanabilir. Bunun yerine, öznitelik grafiğin başka bir parçası olarak zaten oluşturulmuş bir nesne veya statik nesne başvuru sağlayan bir nesne grafiğinin neden. XAML işlemci oluşturucusuna bir nesnenin varsayılan olmayan bağımsız değişkenleri sağlayan bir söz dizimini kullanacak şekilde sağlanabilir başka bir senaryodur. Bu işaretleme uzantısı çözümü burada sağlayabilir senaryoları türleridir.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Temel biçimlendirme uzantısı sözdizimi  
 İşaretleme uzantısı değerlerini sağlamak için bir öznitelik kullanımı özelliklerinde, özellikleri bir özellik öğesi kullanımı ya da her ikisi de uygulanabilir.  
  
 Bir öznitelik değeri sağlamak için kullanıldığında, bir işaretleme uzantısı dizisine bir XAML işlemci ayıran açma ve kapatma küme ayraçlarını varlığı sözdizimidir ({ve}). İşaretleme uzantısı türü sonra büyük ayracını açtıktan hemen ardından dize belirteci tanımlanır.  
  
 Özellik öğesi sözdizimine kullanıldığında, bir işaretleme uzantısı görsel olarak bir özellik öğesi değeri sağlamak için kullanılan herhangi bir öğe aynıdır: işaretleme uzantısı sınıfı (<> açılı köşeli ayraç içine, bir öğe olarak başvuran bir XAML öğe bildirimi ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları  
 Çeşitli biçimlendirme uzantıları, XAML WPF uygulamasına özel değildir ancak bunun yerine iç uygulamaları veya özellikleri XAML dili olarak mevcut. Bu işaretleme uzantıları System.Xaml derleme genel .NET Framework XAML hizmetlerin bir parçası olarak uygulanır ve XAML dil XAML ad alanı içinde. Bu işaretleme Uzantıları yaygın biçimlendirme kullanımı açısından genellikle adlarıyla `x:` kullanım önek. <xref:System.Windows.Markup.MarkupExtension> Temel sınıf (System.Xaml ayrıca tanımlanmıştır) tüm biçimlendirme uzantıları XAML okuyucular ve WPF XAML dahil olmak üzere, XAML yazıcılar desteklenmesi için kullanması gereken desenini sağlar.  
  
-   `x:Type` Kaynakları <xref:System.Type> adlandırılmış bir türün nesnesi. Bu özellik, stilleri ve şablonları içinde en sık kullanıldığı. Ayrıntılar için bkz [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
-   `x:Static` statik değer oluşturur. Değerleri, doğrudan bir hedef özelliğin değerinin türü olmayan değer türü kod varlıklardan gelir, ancak bu türe değerlendirilebilir. Ayrıntılar için bkz [x: Static işaretleme uzantısı](../../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
-   `x:Null` belirtir `null` bir özellik için bir değer olarak ve öznitelikleri veya özellik öğe değerleri için kullanılabilir. Ayrıntılar için bkz [x: Null işaretleme uzantısı](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
-   `x:Array` genel XAML sözdizimi, nereye koleksiyonu desteği WPF temel öğeler tarafından sağlanan ve denetim modelleri kasıtlı olarak kullanılmaz çalışmalarını dizilerde oluşturulması için destek sağlar. Ayrıntılar için bkz [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Önek, XAML dili ön tanımlı bir XAML dosyası veya üretim kök öğesi tipik XAML ad alanı eşlemesi için kullanılır. Örneğin, WPF uygulamaları için Visual Studio şablonları kullanan bir XAML dosyası başlatmak `x:` eşleme. Kendi XAML ad alanı eşlemesi, farklı ön ek belirteç seçebilir, ancak bu belgeleri varsayılan kabul edecek `x:` karşılık olarak, XAML dili için XAML ad alanı tanımlı bir parçası olan bu varlıklar tanımlayan bir yol eşleme WPF için varsayılan ad alanı veya diğer XAML ad alanları için belirli bir framework ilişkili değil.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>WPF özel biçimlendirme uzantıları  
 Kaynak başvurularının destekleyen WPF programlamada kullanılan en yaygın biçimlendirme uzantıları olanlardır (`StaticResource` ve `DynamicResource`) hem de veri bağlamayı destekleyen (`Binding`).  
  
-   `StaticResource` bir değer için bir özellik zaten tanımlı bir kaynak değerini değiştirerek sağlar. A `StaticResource` değerlendirme XAML yükleme zamanında nihai olarak yapılır ve çalışma zamanında nesne grafiğini erişiminiz yok. Ayrıntılar için bkz [StaticResource işaretleme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   `DynamicResource` değeri, bu değer bir kaynağa bir çalışma zamanı başvurusu olmasını erteleyerek için bir özellik sağlar. Dinamik kaynak başvuru her zaman böyle bir kaynak erişilir ve çalışma zamanında nesne grafiğini erişimi olan yeni bir arama zorlar. Bu erişim sağlamak `DynamicResource` kavramı WPF özelliği sistemde bağımlılık özellikleri tarafından desteklenir ve ifade değerlendirilir. Bu nedenle yalnızca kullanabilirsiniz `DynamicResource` bir bağımlılık özelliği hedef için. Ayrıntılar için bkz [DynamicResource işaretleme uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
-   `Binding` sınır değeri üst nesneye çalışma zamanında uygular veri bağlamını kullanarak, bir özellik için veri sağlar. Veri bağlama belirtmek için bir önemli satır içi söz dizimi sağlar çünkü bu işaretleme uzantısı oldukça karmaşıktır. Ayrıntılar için bkz [biçimlendirme uzantısı bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
-   `RelativeSource` kaynak bilgileri sağlar bir <xref:System.Windows.Data.Binding> çalışma zamanı nesne ağacındaki birkaç olası ilişkilerin gidebilirsiniz. Bu, çok amaçlı şablonlarında oluşturulan veya kod çevreleyen nesne ağacının tam bilgisi olmadan oluşturulmuş bağlamaları için özelleştirilmiş kaynağını sağlar. Ayrıntılar için bkz [RelativeSource işaretleme uzantısı](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md).  
  
-   `TemplateBinding` Şablon kullanacağı sınıfının nesne model tanımlı özelliklerinden gelen şablonlu özellikleri için değerleri kullanmak üzere bir denetim şablonu sağlar. Diğer bir deyişle, özelliği şablon tanımı içinden şablonu uygulandıktan sonra yalnızca var olan bir bağlam erişebilirsiniz. Ayrıntılar için bkz [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md). Pratik kullanımı hakkında daha fazla bilgi için `TemplateBinding`, bkz: [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
-   `ColorConvertedBitmap` göreceli olarak gelişmiş bir görüntü senaryosunu destekler. Ayrıntılar için bkz [ColorConvertedBitmap işaretleme uzantısı](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md).  
  
-   `ComponentResourceKey` ve `ThemeDictionary` kaynakları ve özel denetimler ile paketlenmiştir temaları için özellikle kaynak arama özelliklerini destekler. Daha fazla bilgi için [ComponentResourceKey işaretleme uzantısı](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md), [ThemeDictionary işaretleme uzantısı](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md), veya [denetim yazmaya genel bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Uzantı sınıfları  
 Genel XAML dil hem WPF'ye özgü biçimlendirme uzantıları için her bir işaretleme uzantısı davranışını bir XAML işlemci tanımlanır bir `*Extension` türetilen sınıf <xref:System.Windows.Markup.MarkupExtension>ve bir uygulamasını sağlar <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> yöntem. Bu yöntem her uzantı üzerinde işaretleme uzantısı değerlendirildiğinde, döndürülen nesneyi sağlar. Döndürülen nesne, genellikle işaretleme uzantısı için geçirilen çeşitli dize belirteçleri göre değerlendirilir.  
  
 Örneğin, <xref:System.Windows.StaticResourceExtension> SAX gerçek kaynak araması yüzey uygulamasını böylece kendi <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> uygulaması için kullanılan bir dize olan, belirli bir uygulama girişi ile istenen nesneyi döndürür Kaynak tarafından arayın, `x:Key`. Bu uygulama ayrıntısı çoğunu, var olan bir işaretleme uzantısı kullanıyorsanız önemli değildir.  
  
 Bazı biçimlendirme uzantıları dize belirteci bağımsız değişken kullanmayın. Statik veya tutarlı bir değer döndürürler olduğundan veya hangi değeri döndürülmelidir için bağlam geçtiğini hizmetlerden biri aracılığıyla ulaşılabilir olduğundan budur `serviceProvider` parametresi.  
  
 `*Extension` Adlandırma desendir kolaylık ve tutarlılık için. Bu sırada bir işaretleme uzantısı için destek gibi o sınıfı tanımlamak XAML işlemcisi için gerekli değildir. Kod temelinizde System.Xaml içerir ve .NET Framework XAML hizmetlerinde uygulamaları kullanan sürece tüm olan bir XAML işaretleme uzantısı öğesinden türetilen olarak tanınması gerekli <xref:System.Windows.Markup.MarkupExtension> ve yapı sözdizimini desteklemek için. WPF değillerdir işaretleme uzantısı etkinleştirilirken sınıfları tanımlar `*Extension` deseni, örneğin adlandırma <xref:System.Windows.Data.Binding>. Genellikle Bunun nedeni sınıfı saf işaretleme uzantısı desteği ötesinde desteklemesidir. Durumunda, <xref:System.Windows.Data.Binding>, sınıf XAML ile ilgisi olan senaryoları için yöntemlere ve özelliklere nesnenin çalışma zamanı erişimi destekler.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Uzantı sınıfı yorumu başlatma metin  
 Ad ve küme ayraçları içinde hala işaretleme uzantısı aşağıdaki dize belirteçleri aşağıdaki yollardan biriyle XAML işlemcisi tarafından yorumlanır:  
  
-   Virgül her zaman ayırıcı veya ayrı ayrı belirteçlerin sınırlayıcı temsil eder.  
  
-   Her belirteç, ayrı ayrı belirteçlerin herhangi bir eşittir işareti içermiyorsa, bir oluşturucu bağımsız değişken olarak kabul edilir. Her Oluşturucu parametresi olarak bu imza tarafından saklanır ve doğru sırada bu imza tarafından beklenen beklenen türde verilmelidir.  
  
    > [!NOTE]
    >  XAML işlemci çiftlerinin sayısını bağımsız değişken sayısı ile eşleşen bir oluşturucu çağırmanız gerekir. Özel biçimlendirme uzantısı uyguluyorsanız, bu nedenle, aynı bağımsız değişken sayısı ile birden çok Oluşturucu sağlamaz. Birden fazla biçimlendirme uzantısı Oluşturucusu yoluyla aynı parametre sayısı mevcutsa XAML işlemci nasıl davranacağını davranışını tanımlı değil, ancak XAML işlemci uygulamasında bu durum varsa, kullanımıyla ilgili bir özel durum izni olduğunu tahmin etmeleri gereken İşaretleme uzantısı tür tanımlarını.  
  
-   Tek tek ayrılmış, belirteçleri eşittir işareti içeren ve XAML işlemci için işaretleme uzantısı önce varsayılan oluşturucuyu çağırır. Ardından, her ad = değer çifti işaretleme uzantısı ve bu özelliğe atanacak bir değer var olan bir özellik adı olarak yorumlanır.  
  
-   Oluşturucu davranış ve davranışı bir işaretleme uzantısı'nda özelliğini arasında paralel bir sonuç ise, hangi davranışın kullandığınız önemli değildir. Kullanmak için daha yaygın bir kullanımdır *özelliği*`=`*değer* çiftleri için birden fazla ayarlanabilir özelliğe yalnızca, biçimlendirme daha bilinçli kolaylaştırır ve, varsa biçimlendirme uzantıları Oluşturucu parametresi yanlışlıkla sırasını değiştirmek olasılığı daha azdır. (Belirttiğinizde özellik = değer çiftleri, bu özelliklerin herhangi bir sırada olabilir.) Ayrıca, bir işaretleme uzantısı ayarlar, ayarlanabilir özelliklerin her biri bir oluşturucu parametresi sağlayan bir garanti yoktur. Örneğin, <xref:System.Windows.Data.Binding> uzantı aracılığıyla ayarlanabilir birçok özelliklere sahip bir işaretleme uzantısı *özelliği*`=`*değer* form, ancak <xref:System.Windows.Data.Binding> yalnızca iki destekler Oluşturucular: varsayılan bir oluşturucu ve bir başlangıç yolunu ayarlar bir.  
  
-   Değişmez değer virgül, bir işaretleme uzantısı olmadan escapement geçirilemez.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Kaçış dizileri ve İşaretleme uzantıları  
 Öznitelik bir XAML işlemcisi işleme ve küme ayraçlarının işaretleme uzantısı sırasının göstergeleri kullanır. Değişmez değer küme ayracı tarafından izlenen bir boş küme ayracı çifti kullanarak bir kaçış dizisi girerek bir değişmez değer küme ayracı karakteri öznitelik değeri gerekirse üretmek mümkündür. Bkz: [ {} kaçış sırası - işaretleme uzantısı](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>XAML kullanım işaretleme uzantılarında iç içe geçirme  
 İç içe geçmiş birden fazla biçimlendirme uzantıları desteklenir ve her bir işaretleme uzantısı en derin önce değerlendirilir. Örneğin, aşağıdaki kullanım göz önünde bulundurun:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 Bu kullanımı `x:Static` ifade değerlendirilir ve bir dize döndürür. Dize bağımsız değişkeni olarak ardından kullanılır `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>İşaretleme uzantıları ve özellik öğesi sözdizimi  
 Bir özellik öğesi değeri dolduran bir nesne öğesi kullanıldığında, bir işaretleme uzantısı sınıfı görsel olarak ayırt bir tipik nesne türü tarafından desteklenen öğesinden XAML içinde kullanılabilir. Tipik nesne öğesi ve bir işaretleme uzantısı pratik farkı işaretleme uzantısı türü belirtilmiş bir değer için değerlendirilen veya bir ifade olarak ertelenmiş, ' dir. Bu nedenle mekanizmaları muhtemel tür hatalarına işaretleme uzantısı için bir özellik değerleri farklı ve geç bağlama özelliği diğer programlama modellerinde nasıl işleneceğini benzer olacaktır. Bir sıradan nesne öğesi, XAML ayrıştırıldığında ayarı hedef özelliği türünü eşleştirin için değerlendirilecek.  
  
 Nesne öğesi sözdiziminde, bir özellik öğesi doldurmak için kullanılan çoğu biçimlendirme uzantıları içinde içerik ya da daha fazla özellik öğesi sözdizimine sahip olmaz. Bu nedenle nesne öğesi etiketi kapatın ve hiçbir alt öğeleri sağlamak. Herhangi bir nesne öğesi bir XAML işlemcisi tarafından karşılaşıldığında ayrıştırılmış öğeden oluşturulan nesne başlatır, o sınıf için oluşturucu çağrılır. İşaretleme uzantısı sınıfı farklı değildir: biçimlendirme uzantınızı nesne öğesi sözdiziminde kullanılabilir olmasını istiyorsanız, varsayılan bir oluşturucu sağlamanız gerekir. Var olan bazı biçimlendirme uzantıları etkili başlatma için belirtilen en az bir gerekli özellik değerine sahip. Bu durumda, bu özellik değeri bir özellik özniteliğini nesne öğede genellikle verilir. İçinde [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md) ve [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md) başvuru sayfalarına, biçimlendirme gerekli özellikleri (ve gerekli özelliklerin adları) uzantıları not ettiğiniz. Nesne öğesi sözdizimi veya öznitelik sözdizimi belirli işaretleme uzantılarına izin verilmeyen, başvuru sayfaları da fark edeceksiniz. Önemli bir durumdur [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md), hangi destekleyemez öznitelik sözdizimi içeriği o dizinin içinde etiketleme içeriği olarak belirtilmesi gerektiğinden. Dizi içerikleri, genel nesneler olarak işlenir, bu yüzden hiçbir öznitelik için varsayılan tür dönüştürücüsü mantıklı olur. Ayrıca, [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md) gerektiren bir `type` parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)
- [StaticResource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
- [İşaretleme Uzantısı Bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
- [DynamicResource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
- [x:Type İşaretleme Uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
