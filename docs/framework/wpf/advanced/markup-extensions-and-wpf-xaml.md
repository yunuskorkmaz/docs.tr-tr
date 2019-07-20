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
ms.openlocfilehash: 25f6cbbc1df8a4a2b4ad9025b2381d26153e4b66
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364433"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Biçimlendirme Uzantıları ve WPF XAML
Bu konuda, XAML için biçimlendirme uzantıları kavramı, sözdizimi kuralları, amacı ve bunları kapsayan sınıf nesne modeli dahil olmak üzere anlatılmıştır. Biçimlendirme uzantıları XAML dilinin genel bir özelliğidir ve XAML Hizmetleri .NET uygulamasıdır. Bu konu, WPF XAML 'de kullanılmak üzere biçimlendirme uzantılarını özellikle ayrıntılarıyla ayrıntılardır.  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML Işlemcileri ve biçimlendirme uzantıları  
 Genellikle bir XAML ayrıştırıcısı, bir öznitelik değerini bir temel değere dönüştürülebilen bir sabit dize olarak yorumlayabilir veya bazı yollarla bir nesneye dönüştürebilirsiniz. Bu tür bir anlamı bir tür dönüştürücüsünün başvurmasıdır; Bu, [TypeConverters ve xaml](typeconverters-and-xaml.md)konularında belgelenmiştir. Ancak, farklı davranışın gerekli olduğu senaryolar vardır. Örneğin, bir XAML işlemcisi, bir öznitelik değerinin nesne grafiğinde yeni bir nesne ile sonuçlanmamalıdır. Bunun yerine öznitelik, grafiğin başka bir bölümünde zaten oluşturulmuş bir nesneye veya statik bir nesneye başvuru yapan bir nesne grafiğine neden olmalıdır. Başka bir senaryo, bir XAML işlemcisinin bir nesnenin oluşturucusuna varsayılan olmayan bağımsız değişkenler sağlayan bir sözdizimi kullanmasına izin verebilir. Bunlar, bir biçimlendirme uzantısının çözümü sağlayabildiği senaryoların türleridir.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Temel biçimlendirme uzantısı sözdizimi  
 Bir öznitelik kullanımı, özellik öğesi kullanımındaki özellikler veya her ikisi de özellikler için değerler sağlamak üzere bir işaretleme uzantısı uygulanabilir.  
  
 Bir öznitelik değeri sağlamak için kullanıldığında, bir biçimlendirme uzantısı sırasını XAML işlemcisine ayıran sözdizimi, açma ve kapatma küme ayraçları ({ve}) ile aynıdır. Biçimlendirme uzantısının türü daha sonra, açılan küme ayracından hemen sonra dize belirteci tarafından tanımlanır.  
  
 Özellik öğesi sözdiziminde kullanıldığında, bir biçimlendirme uzantısı bir özellik öğesi değeri sağlamak için kullanılan diğer tüm öğeler için görsel olarak aynıdır: bir öğe olarak biçimlendirme uzantısı sınıfına başvuran bir XAML öğesi bildirimi (< > ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları  
 XAML 'in WPF uygulamasına özgü olmayan çeşitli biçimlendirme uzantıları vardır, ancak bunun yerine bir dil olarak XAML 'in iç yapı veya özelliklerinin uygulamaları vardır. Bu biçimlendirme uzantıları, System. xaml derlemesinde genel .NET Framework XAML hizmetlerinin bir parçası olarak uygulanır ve XAML Language XAML ad alanı içindedir. Yaygın biçimlendirme kullanımı açısından, bu biçimlendirme uzantıları genellikle kullanımdaki `x:` ön ek tarafından tanımlanabilir. <xref:System.Windows.Markup.MarkupExtension> Temel sınıf (Ayrıca System. xaml içinde de tanımlanmıştır), WPF XAML dahil olmak üzere xaml okuyucular ve xaml yazıcılarında desteklenmesi için tüm işaretleme uzantılarının kullanması gereken düzeni sağlar.  
  
- `x:Type`adlandırılmış tür için nesne sağlar. <xref:System.Type> Bu özellik, en sık stiller ve şablonlarda kullanılır. Ayrıntılar için bkz. [X:Type Işaretleme uzantısı](../../xaml-services/x-type-markup-extension.md).  
  
- `x:Static`statik değerler üretir. Değerler, doğrudan bir hedef özelliğin değerinin türü olmayan değer türü kod varlıklarından gelir, ancak bu tür için değerlendirilebilirler. Ayrıntılar için bkz. [X:static Işaretleme uzantısı](../../xaml-services/x-static-markup-extension.md).  
  
- `x:Null`bir `null` özellik için değer olarak belirtir ve öznitelikler ya da Özellik öğesi değerleri için kullanılabilir. Ayrıntılar için bkz. [X:null Işaretleme uzantısı](../../xaml-services/x-null-markup-extension.md).  
  
- `x:Array`WPF temel öğeleri ve denetim modelleri tarafından sağlanan koleksiyon desteğinin kasıtlı olarak kullanılmasında, XAML sözdiziminde genel diziler oluşturma desteği sağlar. Ayrıntılar için bkz. [X:Array Işaretleme uzantısı](../../xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Ön ek xaml dil iç öğelerinin tipik XAML ad alanı eşlemesi için, bir xaml dosyasının veya üretiminin kök öğesinde kullanılır. Örneğin, WPF uygulamaları için Visual Studio şablonları bu `x:` eşlemeyi kullanarak bir xaml dosyası başlatır. Kendi xaml ad alanı eşlemesinde farklı bir ön ek belirteci seçebilirsiniz, ancak bu belge varsayılan `x:` eşlemeyi xaml dili için xaml ad alanının tanımlı bir parçası olan varlıkları tanımlama yöntemi olarak kabul eder. WPF varsayılan ad alanına veya belirli bir çerçeve ile ilgili olan diğer XAML ad alanlarına.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>WPF 'e özgü biçimlendirme uzantıları  
 WPF programlamasında kullanılan en yaygın biçimlendirme uzantıları, kaynak başvurularını (`StaticResource` ve `DynamicResource`) ve veri bağlamayı (`Binding`) destekleyen olanları destekledikleri olanlardır.  
  
- `StaticResource`önceden tanımlanmış bir kaynağın değerini değiştirerek özellik için bir değer sağlar. Bir `StaticResource` değerlendirme, sonunda XAML yükleme zamanında yapılır ve çalışma zamanında nesne grafiğine erişemez. Ayrıntılar için bkz. [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md).  
  
- `DynamicResource`Bu değeri bir kaynağa bir çalışma zamanı başvurusu olacak şekilde erteleyerek özellik için bir değer sağlar. Dinamik bir kaynak başvurusu, bu kaynağa her erişildiğinde yeni bir aramayı zorlar ve çalışma zamanında nesne grafiğine erişim sağlar. Bu erişimi almak için, `DynamicResource` kavram WPF özellik sisteminde bağımlılık özellikleri tarafından desteklenir ve değerlendirilen ifadeler desteklenir. Bu nedenle, yalnızca bir `DynamicResource` bağımlılık özelliği hedefi için kullanabilirsiniz. Ayrıntılar için bkz. [DynamicResource Işaretleme uzantısı](dynamicresource-markup-extension.md).  
  
- `Binding`çalışma zamanında üst nesne için geçerli olan veri bağlamını kullanarak bir özellik için veri bağlama değeri sağlar. Bu biçimlendirme uzantısı görece karmaşıktır, çünkü bir veri bağlama belirtmek için önemli bir satır içi sözdizimi sunar. Ayrıntılar için bkz. [Binding Işaretleme uzantısı](binding-markup-extension.md).  
  
- `RelativeSource`çalışma zamanı nesne ağacında birkaç <xref:System.Windows.Data.Binding> olası ilişkiye gidebileceğiniz bir için kaynak bilgileri sağlar. Bu, birden çok kullanım şablonlarında oluşturulan veya çevreleyen nesne ağacının tam bilgisi olmadan kodda oluşturulan bağlamalar için özelleştirilmiş kaynağı sağlar. Ayrıntılar için bkz. [RelativeSource MarkupExtension](relativesource-markupextension.md).  
  
- `TemplateBinding`bir denetim şablonunun, şablonu kullanacak sınıfın nesne modeli tanımlı özelliklerinden gelen değerleri kullanmasına olanak sağlar. Diğer bir deyişle, şablon tanımı içindeki özelliği, şablon uygulandıktan sonra yalnızca var olan bir içeriğe erişebilir. Ayrıntılar için bkz. [TemplateBinding Işaretleme uzantısı](templatebinding-markup-extension.md). Pratik kullanımı `TemplateBinding`hakkında daha fazla bilgi için bkz. [ControlTemplates ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`nispeten gelişmiş bir görüntüleme senaryosunu destekler. Ayrıntılar için bkz. [ColorConvertedBitmap Biçimlendirme Uzantısı](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey`ve `ThemeDictionary` özellikle özel denetimlerle paketlenmiş kaynaklar ve Temalar için kaynak aramasının destek yönlerini destekler. Daha fazla bilgi için bkz. [ComponentResourceKey Işaretleme uzantısı](componentresourcekey-markup-extension.md), [ThemeDictionary Biçimlendirme Uzantısı](themedictionary-markup-extension.md)veya [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>\* Uzantı sınıfları  
 Hem genel xaml dili hem de WPF 'e özgü biçimlendirme uzantıları için, her biçimlendirme uzantısının davranışı, öğesinden `*Extension` <xref:System.Windows.Markup.MarkupExtension>türetilen bir sınıf aracılığıyla XAML işlemcisi olarak tanımlanır ve <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> yöntemidir. Her bir uzantıdaki bu yöntem, biçimlendirme uzantısı değerlendirildiğinde döndürülen nesneyi sağlar. Döndürülen nesne genellikle biçimlendirme uzantısına geçirilen çeşitli dize belirteçlerine göre değerlendirilir.  
  
 Örneğin, <xref:System.Windows.StaticResourceExtension> sınıfı, gerçek kaynak aramasının yüzey uygulamasını sağlar, böylece <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> uygulama istenen nesneyi, belirli bir uygulamanın girişi için kullanılan bir dize olarak döndürür. kaynağına göre `x:Key`arama yapın. Mevcut bir işaretleme uzantısı kullanıyorsanız bu uygulama ayrıntısının büyük bölümü önemli değildir.  
  
 Bazı biçimlendirme uzantıları dize belirteci bağımsız değişkenlerini kullanmaz. Bunun nedeni, statik veya tutarlı bir değer döndürmeleri ya da değeri döndürülecek olan bağlamın `serviceProvider` parametresi aracılığıyla geçirilen hizmetlerden biri ile kullanılması olabilir.  
  
 `*Extension` Adlandırma deseninin kolaylığı ve tutarlılığı vardır. Bir XAML işlemcisinin, bu sınıfı bir işaretleme uzantısı için destek olarak tanımlaması için gerekli değildir. Kod tabanınız System. xaml içerdiğinden ve .NET Framework xaml Hizmetleri uygulamalarını kullandığından, bir XAML biçimlendirme uzantısı olarak tanınması gereken tek şey, oluşturma söz dizimini desteklemek ve ' den <xref:System.Windows.Markup.MarkupExtension> türetilmektir. WPF, örneğin `*Extension` <xref:System.Windows.Data.Binding>adlandırma modelini takip eden biçimlendirme uzantısı-etkinleştirme sınıflarını tanımlar. Genellikle bunun nedeni, sınıfının saf biçimlendirme uzantısı desteğinin ötesinde senaryolar desteklemedir. Bu durumda <xref:System.Windows.Data.Binding>, bu sınıf xaml ile hiçbir şeyin olmadığı senaryolar için nesnenin yöntemlere ve özelliklerine çalışma zamanı erişimini destekler.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Başlatma metninin uzantı sınıfı yorumu  
 Biçimlendirme uzantısı adı ve hala küme ayraçları içindeki dize belirteçleri, aşağıdaki yollarla bir XAML işlemcisi tarafından yorumlanır:  
  
- Virgül, her zaman ayrı belirteçlerin ayırıcısını veya ayırıcısını temsil eder.  
  
- Ayrı ayrı ayrılmış belirteçler bir eşittir işareti içermiyorsa, her belirteç bir Oluşturucu bağımsız değişkeni olarak değerlendirilir. Her Oluşturucu parametresi, bu imza tarafından beklenen tür olarak verilmelidir ve bu imza için beklenen doğru sırada olmalıdır.  
  
    > [!NOTE]
    >  XAML işlemcinin, Çift sayısı bağımsız değişken sayısıyla eşleşen oluşturucuyu çağırması gerekir. Bu nedenle, özel bir işaretleme uzantısı uyguladığınızda aynı bağımsız değişken sayısına sahip birden çok Oluşturucu sağlamamanız gerekir. Aynı parametre sayısına sahip birden fazla işaretleme uzantısı Oluşturucu yolu tanımlanmazsa, XAML işlemcisinin nasıl davranacağını gösteren davranış. bu durum, içinde varsa, bir XAML işlemcisinin kullanım için bir özel durum oluşturulmasına izin verildiğini tahmin etmeniz gerekir. Biçimlendirme Uzantısı tür tanımları.  
  
- Ayrı ayrı ayrılmış belirteçler eşittir işareti içeriyorsa, bir XAML işlemcisi önce biçimlendirme uzantısı için parametresiz oluşturucuyu çağırır. Ardından, her ad = değer çifti, biçimlendirme uzantısında var olan bir özellik adı olarak yorumlanır ve bu özelliğe atanacak bir değer.  
  
- Oluşturucu davranışı ile bir biçimlendirme uzantısında özellik ayarı davranışı arasında paralel bir sonuç varsa, hangi davranışı kullandığınıza bağımsız değildir. Yalnızca bir tane ayarlanabilir özelliği olan biçimlendirme uzantıları için *özellik*`=`*değeri* çiftlerini kullanmak için daha yaygın kullanımdır, ancak bu, işaretinizi daha bilinçli hale getirir ve yanlışlıkla yanlışlıkla değiştirilmesini daha az olabilir. Oluşturucu parametreleri. (Özellik = değer çiftlerini belirttiğinizde, bu özellikler herhangi bir sırada olabilir.) Ayrıca, biçimlendirme uzantısının ayarlanabilir özelliklerinden her birini ayarlayan bir oluşturucu parametresi sağladığı garanti yoktur. Örneğin, <xref:System.Windows.Data.Binding> *özellik*`=`*değeri* biçimindeki uzantı aracılığıyla ayarlanabilir çok sayıda özelliği olan bir biçimlendirme uzantısıdır, ancak <xref:System.Windows.Data.Binding> yalnızca iki oluşturucuyu destekler: parametresiz bir Oluşturucu ve bir Bu, bir başlangıç yolu belirler.  
  
- Sabit noktalı virgül, bir biçimlendirme uzantısına ilerlemeksizin geçirilemez.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Kaçış dizileri ve biçimlendirme uzantıları  
 XAML işlemcisinde öznitelik işleme, küme ayraçları bir işaretleme uzantısı sırasının göstergeleri olarak kullanır. Ayrıca, boş bir küme ayracı çifti ve ardından değişmez küme ayracı ile bir kaçış sırası girerek, gerekirse değişmez bir küme ayracı karakter özniteliği değeri oluşturmak mümkündür. Bkz. kaçış [ sırası-işaretlemeuzantısı{} ](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>XAML kullanımında biçimlendirme uzantılarını iç içe geçirme  
 Birden çok biçimlendirme uzantısının iç içe geçirilmesi desteklenir ve her biçimlendirme uzantısı önce ayrıntılı olarak değerlendirilir. Örneğin, aşağıdaki kullanımı göz önünde bulundurun:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 Bu kullanımda, `x:Static` önce ifade değerlendirilir ve bir dize döndürür. Bu dize daha sonra için `DynamicResource`bağımsız değişkeni olarak kullanılır.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Biçimlendirme uzantıları ve özellik öğesi sözdizimi  
 Bir özellik öğesi değerini dolduran bir nesne öğesi olarak kullanıldığında, biçimlendirme uzantısı sınıfı XAML 'de kullanılabilen tipik bir tür ile desteklenen nesne öğesinden görsel açıdan ayırt edilebilir. Tipik bir nesne öğesi ve bir biçimlendirme uzantısı arasındaki pratik fark, biçimlendirme uzantısının tür belirlenmiş bir değer olarak değerlendirilme veya bir ifade olarak ertelenmesi olabilir. Bu nedenle, biçimlendirme uzantısının özellik değerlerinin olası tür hatalarının mekanizmaları, geç bağlantılı bir özelliğin diğer programlama modellerinde nasıl ele alındığına benzer şekilde farklı olacaktır. Normal nesne öğesi, XAML ayrıştırıldığında ayar yaptığı hedef özelliğe karşı tür eşleşmesi için değerlendirilir.  
  
 Bir özellik öğesini dolduracak nesne öğesi sözdiziminde kullanıldığında birçok biçimlendirme uzantısı, içinde içerik veya başka bir özellik öğesi söz dizimi içermez. Bu nedenle, nesne öğesi etiketini kapatıp hiçbir alt öğe sağlamacaksınız. XAML işlemcisi tarafından herhangi bir nesne öğesiyle karşılaşıldığında, bu sınıf için Oluşturucu çağırılır ve ayrıştırılmış öğeden oluşturulan nesneyi başlatır. Biçimlendirme Uzantısı sınıfı farklı değil: biçimlendirme uzantınızın nesne öğesi söz diziminde kullanılabilir olmasını istiyorsanız parametresiz bir Oluşturucu sağlamanız gerekir. Bazı mevcut biçimlendirme uzantılarında, etkin başlatma için belirtilmesi gereken en az bir gerekli özellik değeri var. Öyleyse, bu özellik değeri genellikle nesne öğesinde bir özellik özniteliği olarak verilir. [Xaml ad alanında (x:) Dil özellikleri](../../xaml-services/xaml-namespace-x-language-features.md) ve [WPF XAML uzantıları](wpf-xaml-extensions.md) başvuru sayfaları, gerekli özellikleri olan biçimlendirme uzantıları (ve gerekli özelliklerin adları) not edilir. Başvuru sayfaları, belirli biçimlendirme uzantıları için nesne öğesi söz dizimi veya öznitelik söz dizimine izin verilmediğini de göz önünde bulunur. Bir önemli Case, öznitelik sözdizimini destekleyemediği [, bu](../../xaml-services/x-array-markup-extension.md)dizinin içeriği etiketleme içinde içerik olarak belirtilmelidir. Dizi içerikleri genel nesneler olarak işlenir, bu nedenle öznitelik için varsayılan tür dönüştürücüsü uygulanabilir değildir. Ayrıca, [x:Array Biçimlendirme Uzantısı](../../xaml-services/x-array-markup-extension.md) bir `type` parametre gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [XAML ad alanı (x:) Dil özellikleri](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML Uzantıları](wpf-xaml-extensions.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [İşaretleme Uzantısı Bağlama](binding-markup-extension.md)
- [DynamicResource İşaretleme Uzantısı](dynamicresource-markup-extension.md)
- [x:Type İşaretleme Uzantısı](../../xaml-services/x-type-markup-extension.md)
