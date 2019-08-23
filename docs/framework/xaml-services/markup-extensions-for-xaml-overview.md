---
title: XAML Biçimlendirme Uzantılarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 5c29899846e7210c02b6bcc2b677b05581a5c6b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939702"
---
# <a name="markup-extensions-for-xaml-overview"></a>XAML Biçimlendirme Uzantılarına Genel Bakış
Biçimlendirme uzantıları, temel olmayan veya belirli bir XAML türü olmayan bir değer elde etmek için XAML tekniğidir. Biçimlendirme uzantıları, öznitelik kullanımı için, işaretleme uzantısı kapsamını ve çıkış için bir kapanış küme `{` ayracı `}` girmek üzere bir açma küme ayracı bilinen karakter dizisini kullanır. .NET Framework XAML hizmetlerini kullanırken, System. Xaml derlemesinden önceden tanımlanmış XAML dili biçimlendirme genişletmelerini kullanabilirsiniz. Ayrıca, System. xaml içinde <xref:System.Windows.Markup.MarkupExtension> tanımlanan sınıftan alt sınıf oluşturabilir ve kendi biçimlendirme uzantılarınızı tanımlayabilirsiniz. Ya da söz konusu çerçeveye zaten başvuruyordıysanız belirli bir Framework tarafından tanımlanan biçimlendirme uzantılarını kullanabilirsiniz.  
  
 Biçimlendirme Uzantısı kullanımına erişildiğinde, xaml nesne yazıcısı <xref:System.Windows.Markup.MarkupExtension> <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> geçersiz kılma içindeki bir hizmet bağlantı noktası aracılığıyla özel bir sınıfa hizmet sağlayabilir. Hizmetler, nesne yazıcısının kullanımı, belirli özellikleri, XAML şeması bağlamı vb. için bağlam elde etmek üzere kullanılabilir.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları  
 Çeşitli biçimlendirme uzantıları XAML dil desteği için .NET Framework XAML Hizmetleri tarafından uygulanır. Bu biçimlendirme uzantıları, XAML belirtiminin bir dil olarak belirtilerinin bölümlerine karşılık gelir. Bunlar genellikle yaygın kullanımda görüldüğü gibi `x:` söz dizimi ön ekine göre tanımlanabilir. Bu XAML dil öğeleri için .NET Framework xaml Hizmetleri uygulamaları, tüm <xref:System.Windows.Markup.MarkupExtension> temel sınıftan türetilir.  
  
> [!NOTE]
> `x:` Önek, XAML üretiminin kök öğesinde XAML dili ad alanının tipik XAML ad alanı eşlemesi için kullanılır. Örneğin, çeşitli belirli çerçeveler için Visual Studio projesi ve sayfa şablonları, bu `x:` eşlemeyi kullanarak bir xaml dosyası başlatır. Kendi xaml ad alanı eşlecinizin farklı bir ön ek belirteci seçebilirsiniz, ancak bu belge varsayılan `x:` eşlemeyi xaml dili xaml ad alanının tanımlı bir parçası olan varlıkları tanımlama belirli Framework 'ün varsayılan XAML ad alanı veya diğer rasgele CLR veya XML ad alanları.  
  
### <a name="xtype"></a>x:Type  
 `x:Type`adlandırılmış tür için nesne sağlar. <xref:System.Type> Bu işlevsellik, temel alınan clr türü ve bir gruplama adı veya tanımlayıcı olarak tür Türetmenin kullanıldığı erteleme mekanizmalarındaki en sık kullanılır. WPF stilleri ve şablonları ve bunların `TargetType` özelliklerinin kullanımları belirli bir örnektir. Daha fazla bilgi için bkz. [X:Type Işaretleme uzantısı](x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x:Static  
 `x:Static`doğrudan bir özelliğin değerinin türü olmayan değer türü kod varlıklarından statik değerler üretir, ancak bu tür için değerlendirilebilirler. Bu, bir tür tanımında tanınmış sabitler olarak zaten var olan değerleri belirtmek için yararlıdır. Daha fazla bilgi için bkz. [X:static Işaretleme uzantısı](x-static-markup-extension.md).  
  
### <a name="xnull"></a>x:Null  
 `x:Null`XAML `null` üyesi için değer olarak belirtir. Belirli türlerin tasarımına veya daha büyük çerçeve kavramına bağlı olarak, `null` bir özellik için her zaman varsayılan bir değer veya boş bir dize özniteliğinin ima edilen değeri değildir. Daha fazla bilgi için bkz. [X:null Işaretleme uzantısı](x-null-markup-extension.md).  
  
### <a name="xarray"></a>x:Array  
 `x:Array`, temel öğeler ve denetim modelleri tarafından sunulan koleksiyon desteğinin kasıtlı olarak kullanılmasında XAML sözdiziminde genel diziler oluşturulmasını destekler. Daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](x-array-markup-extension.md). XAML 2009 ' de özellikle, dizilere uzantı olarak değil dil temelleri olarak erişilir. Daha fazla bilgi için bkz. [XAML 2009 dil özellikleri](xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x:Reference  
 `x:Reference`, özgün (2006) dil kümesinin bir uzantısı olan XAML 2009 ' in bir parçasıdır. `x:Reference`bir nesne grafiğinde varolan başka bir nesnenin başvurusunu temsil eder. Bu nesne, `x:Name`tarafından tanımlanır. Daha fazla bilgi için bkz. [X:Reference Işaretleme uzantısı](x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Diğer x: Yapılarını  
 XAML `x:` dil özelliklerini desteklemeye yönelik diğer yapılar mevcuttur, ancak bunlar biçimlendirme uzantıları olarak uygulanmaz. Daha fazla bilgi için bkz [. xaml ad alanı (x:) Dil özellikleri](xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>MarkupExtension temel sınıfı  
 System. xaml 'de xaml okuyucuları ve xaml yazıcılarının varsayılan uygulamalarıyla etkileşime girebilen özel bir işaretleme uzantısı tanımlamak için, soyut <xref:System.Windows.Markup.MarkupExtension> sınıftan bir sınıf türetirsiniz. Bu sınıfın, geçersiz kılmak <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>için bir yöntemi vardır. Ayrıca, biçimlendirme uzantısı kullanımının bağımsız değişkenlerini desteklemek için ek oluşturucular tanımlamanız ve ayarlanabilir özelliklerle eşleşmesi gerekebilir.  
  
 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, Özel bir biçimlendirme uzantısının, biçimlendirme uzantısının aslında bir XAML işlemcisi tarafından çağrıldığı ortamı raporlayan bir hizmet bağlamına erişimi vardır. Yükleme yolunda bu genellikle bir <xref:System.Xaml.XamlObjectWriter>' dır. Kaydetme yolunda bu genellikle bir <xref:System.Xaml.XamlXmlWriter>' dır. Her biri hizmet bağlamını bir hizmet sağlayıcı kalıbı uygulayan bir iç XAML hizmeti sağlayıcısı bağlam sınıfı olarak bildirir. Kullanılabilir hizmetler ve neleri temsil ettikleri hakkında daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).  
  
 Biçimlendirme Uzantısı sınıfınız ortak erişim düzeyi kullanmalıdır; XAML işlemcileri, hizmetlerini kullanmak için her zaman işaretleme uzantısının destek sınıfını örnekleyemez.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Özel bir Işaretleme uzantısı için destek türünü tanımlama  
 .NET Framework XAML Hizmetleri üzerinde yapı .NET Framework XAML Hizmetleri veya çerçeveler kullandığınızda, biçimlendirme uzantısı destek türünü adlandırma hakkında iki seçeneğiniz vardır. Tür adı, XAML nesne yazıcılarının XAML 'de biçimlendirme uzantısı kullanımıyla karşılaştıklarında biçimlendirme uzantısı destek türüne erişme ve çağırma ile ilgilidir. Aşağıdaki adlandırma stratejilerinden birini kullanın:  
  
- Tür adını XAML biçimlendirme kullanım belirtecine tam eşleşme olacak şekilde adlandırın. Örneğin, bir `{Collate ...}` uzantı kullanımını desteklemek için, destek türünü `Collate`adlandırın.  
  
- Tür adını kullanım dizesi belirteci artı soneki `Extension`olacak şekilde adlandırın. Örneğin, bir `{Collate ...}` uzantı kullanımını desteklemek için, destek türünü `CollateExtension`adlandırın.  
  
 Arama sırası, önce `Extension`-sonsabit sınıf adını aramak ve ardından `Extension` sonek olmadan sınıf adını arayıyoruz.  
  
 Kullanım açısından `Extension` sonek dahil, biçimlendirme kullanım perspektifinden geçerli olur. Ancak, bu, sınıf adının `Extension` gerçekten bir parçası olduğu gibi davranır ve destek sınıfı `Extension` sonekine sahip değilse xaml nesne yazarları bu kullanım için bir işaretleme uzantısı destek sınıfını çözemeyebilir.  
  
### <a name="the-default-constructor"></a>Varsayılan Oluşturucu  
 Tüm biçimlendirme uzantısı destek türleri için ortak parametresiz bir Oluşturucu kullanıma sunmalısınız. Parametresiz bir Oluşturucu, bir XAML nesne yazıcısının bir nesne öğesi kullanımındaki biçimlendirme uzantısını örneklemesinin oluşturulduğu herhangi bir durumda gereklidir. Destekleyici nesne öğesi kullanımı, özellikle serileştirme için bir işaretleme uzantısı için bir beklentidir. Ancak, yalnızca biçimlendirme uzantısının öznitelik kullanımlarını desteklemek istiyorsanız, bir ortak Oluşturucu olmadan bir işaretleme uzantısı uygulayabilirsiniz.  
  
 Biçimlendirme Uzantısı kullanımınızın bağımsız değişkeni yoksa, kullanımı desteklemek için parametresiz Oluşturucu gereklidir.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Özel bir Işaretleme uzantısı için Oluşturucu desenleri ve Konumsal bağımsız değişkenler  
 Bağımsız değişken kullanımı amaçlanan bir işaretleme uzantısı için, ortak oluşturucuların amaçlanan kullanım modlarına karşılık gelmesi gerekir. Diğer bir deyişle, biçimlendirme uzantınız geçerli kullanım olarak bir Konumsal bağımsız değişken gerektirecek şekilde tasarlanmışsa, konum bağımsız değişkenini alan bir giriş parametresiyle ortak bir oluşturucuyu desteklemeniz gerekir.  
  
 Örneğin, `Collate` biçimlendirme uzantısının yalnızca bir `CollationMode` numaralandırma sabiti olarak belirtilen modunu temsil eden bir konum bağımsız değişkeni olan bir modu desteklemeye yönelik olduğunu varsayalım. Bu durumda, aşağıdaki biçimde bir oluşturucu olmalıdır:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Temel düzeyde, biçimlendirme uzantısına geçirilen bağımsız değişkenler, biçimlendirmenin öznitelik değerlerinden iletileceği için bir dizedir. Bağımsız değişken Dizelerinizin tümünü yapabilir ve bu düzeyde giriş ile çalışabilirsiniz. Ancak, biçimlendirme uzantısı bağımsız değişkenleri destek sınıfına geçirilmeden önce gerçekleşen belirli işleme erişiminiz vardır.  
  
 İşleme, biçimlendirme uzantısı oluşturulacak bir nesne olup, sonra üye değerleri ayarlanmış gibi kavramsal olarak çalışacaktır. Ayarlanacak her bir özellik, XAML ayrıştırıldığında oluşturulan bir nesnede belirtilen üyenin nasıl ayarlanıladığına benzer şekilde değerlendirilir. İki önemli fark vardır:  
  
- Daha önce belirtildiği gibi, biçimlendirme uzantısı destek türünün XAML 'de örneklendirmenin parametresiz oluşturucusu olması gerekmez. Nesne oluşturma, metin sözdiziminde olası bağımsız değişkenlerin simgeleştirilmesine ve Konumsal ya da adlandırılmış bağımsız değişkenler olarak değerlendirilene kadar ertelenir ve uygun Oluşturucu o anda çağırılır.  
  
- Biçimlendirme uzantıları kullanımları iç içe olabilir. En içteki biçimlendirme uzantısı ilk olarak değerlendirilir. Bu nedenle, bu tür bir kullanımı varsayabilir ve oluşturma parametrelerinden birini bir değer Dönüştürücüsü (örneğin, biçimlendirme uzantısı) gerektiren bir tür olacak şekilde bildirebilirsiniz.  
  
 Bu tür bir işlem, önceki örnekte gösterilmemiştir. .NET Framework XAML Hizmetleri XAML nesne yazıcı, sabit listesi sabit adlarını yerel düzeyde numaralandırılmış değerlerle işler.  
  
 Bir işaretleme uzantısı konumsal parametresinin metin sözdizimi işleme, oluşturma bağımsız değişkeninde bulunan türle ilişkili bir tür dönüştürücüde de olabilir.  
  
 Kullanımdaki belirteçlerin karşılaştığı sıra, atandıkları Oluşturucu parametresinin konumsal sırasına karşılık gelen bağımsız değişkenler Konumsal bağımsız değişkenler olarak adlandırılır. Örneğin, aşağıdaki Oluşturucu imzasını göz önünde bulundurun:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 XAML işlemcisi, bu biçimlendirme uzantısı için iki Konumsal bağımsız değişken bekliyor. Bir kullanım `{Collate AlphaUp,{x:Reference circularFile}}`varsa `AlphaUp` , belirteç ilk parametreye gönderilir ve sabit adlı bir `CollationMode` sabit listesi olarak değerlendirilir. İç `x:Reference` sonucu ikinci parametreye gönderilir ve bir nesne olarak değerlendirilir.  
  
 Biçimlendirme uzantısı sözdizimi ve işleme için XAML tarafından belirtilen kurallarda, bu bağımsız değişkenlerin Konumsal bağımsız değişkenler veya adlandırılmış bağımsız değişkenler olup olmadığı bağımsız değişkenler arasındaki sınırlayıcı virgüldür.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Yinelenen sayıda Konumsal bağımsız değişken  
 XAML nesne yazarı, Konumsal bağımsız değişkenlerle bir biçimlendirme uzantısı kullanımıyla karşılaşırsa ve bu sayıda bağımsız değişken (yinelenen parametre sayısı) alan birden çok Oluşturucu bağımsız değişkeni varsa, bu bir hata olması gerekmez. Davranış, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>özelleştirilebilir bir xaml şeması bağlam ayarına bağlıdır. <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> İse`true`, bir xaml nesne yazıcısı yalnızca yinelenen parametre sayısının nedenleri için bir özel durum oluşturmaz. Bu noktanın ötesinde davranış kesin olarak tanımlanmamıştır. Temel tasarım varsayımına, şema bağlamının belirli parametrelere ait tür bilgilerine sahip olması ve hangi imzanın en iyi eşleşme olabileceğini görmek için yinelenen adaylara uyan açık yayınları deneyebileceği anlamına gelir. Bir XAML nesne yazıcısında çalışan belirli şema bağlamı tarafından uygulanan testleri geçemezse bir özel durum yine de oluşturulabilir.  
  
 Varsayılan olarak, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `false` .NET Framework xaml Hizmetleri için clr tabanlıdır <xref:System.Xaml.XamlSchemaContext> . Bu nedenle, varsayılan <xref:System.Xaml.XamlObjectWriter> olarak, bir biçimlendirme uzantısı kullanımı ile karşılaştığında, yedekleme türünün oluşturucularında yinelenen parametre sayısı olduğu durumlarda özel durumlar oluşturulur.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için adlandırılmış bağımsız değişkenler  
 XAML tarafından belirtilen biçimlendirme uzantıları, kullanım için adlandırılmış bağımsız değişkenler formunu da kullanabilir. Simgeleştirme 'nin ilk düzeyinde metin sözdizimi bağımsız değişkenlere bölünmüştür. Herhangi bir bağımsız değişken içindeki bir eşittir işareti (=) varlığı, adlandırılmış bağımsız değişken olarak bir bağımsız değişken tanımlar. Böyle bir bağımsız değişken aynı zamanda bir ad/değer çiftinde simgeleştirilir. Bu örnekte adı, biçimlendirme uzantısının destek türünün genel ayarlanabilir bir özelliğini adlandırır. Adlandırılmış bağımsız değişken kullanımını desteklemek istiyorsanız, bu genel ayarlanabilir özellikleri sağlamanız gerekir. Özellikler, ortak kaldığı sürece devralınmış özellikler olabilir.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı uygulamasından hizmet sağlayıcı bağlamına erişme  
 Kullanılabilir hizmetler herhangi bir değer Dönüştürücüsü için aynıdır. Fark, her bir değer dönüştürücünün hizmet bağlamını nasıl aldığına ilişkin farktır. Hizmetlere ve kullanılabilir hizmetlere erişme, [xaml Için biçimlendirme uzantıları ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md)konu başlığı altında belgelenmiştir.  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Biçimlendirme uzantısının Özellik öğesi kullanımı  
 Biçimlendirme uzantısı kullanımları için senaryolar genellikle öznitelik kullanımında biçimlendirme uzantısının kullanımı etrafında tasarlanır. Ancak, özellik öğesi kullanımını desteklemek için yedekleme sınıfını tanımlamak da olasıdır.  
  
 Biçimlendirme uzantınızın Özellik öğesi kullanımını desteklemek için ortak parametresiz bir Oluşturucu tanımlayın. Bu, bir statik Oluşturucu olmamalıdır örnek oluşturucu olmalıdır. Bu gereklidir çünkü bir XAML işlemcisi, biçimlendirmeden işlenen herhangi bir nesne öğesinde parametresiz oluşturucuyu genellikle çağırmalıdır ve buna nesne öğeleri olarak biçimlendirme uzantısı sınıfları dahildir. Gelişmiş senaryolar için, sınıflar için varsayılan olmayan oluşturma yolları tanımlayabilirsiniz. (Daha fazla bilgi için bkz. [X:FactoryMethod yönergesi](x-factorymethod-directive.md).) Bununla birlikte, biçimlendirme uzantısı için bu desenleri kullanmamalısınız çünkü bu, hem tasarımcılar hem de ham biçimlendirme kullanıcıları için kullanım desenini bulmayı çok daha zor hale getirir.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Özel bir Işaretleme uzantısı için Attributing  
 Hem tasarım ortamlarını hem de belirli XAML nesne yazıcısı senaryolarını desteklemek için, birkaç CLR özniteliğiyle bir biçimlendirme uzantısı destek türüne sahip olmanız gerekir. Bu öznitelikler, istenen biçimlendirme uzantısı kullanımını raporlar.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>döndürennesne<xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> türü bilgilerini raporlar. <xref:System.Type> Saf imzasına göre, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürür. <xref:System.Object> Ancak çeşitli tüketiciler daha kesin dönüş türü bilgileri isteyebilir. Şunları içerir:  
  
- Tasarımcılar ve Ides, biçimlendirme uzantısı kullanımları için tür duyarlı destek sağlayabilecek.  
  
- Hedef sınıflarda `SetMarkupExtension` işleyicilerin gelişmiş uygulamaları, bir biçimlendirme uzantısının, ada göre bilinen <xref:System.Windows.Markup.MarkupExtension> belirli uygulamalarda dallanması yerine bir işaretleme uzantısının dönüş türünü tespit etmek için yansıma üzerinde güvenebilen.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Biçimlendirme Uzantısı kullanımlarının serileştirilmesi  
 Bir xaml nesne yazıcısı bir biçimlendirme uzantısı kullanımını ve çağrılarını <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>işlediğinde, daha önce biçimlendirme uzantısı kullanımı olan bağlam xaml düğüm akışında devam ediyor ancak nesne grafiğinde yok. Nesne grafiğinde yalnızca değer korunur. Özgün biçimlendirme uzantısı kullanımını serileştirilmiş çıkışa kalıcı hale getirmeniz için tasarım senaryolarınız veya başka nedenleriniz varsa, biçimlendirme uzantısı kullanımlarını, yük yolu XAML düğüm akışından izlemek için kendi altyapınızı tasarlamanız gerekir. Yük yolundan düğüm akışının öğelerini yeniden oluşturmak ve bunları, düğüm akışının uygun konumundaki değeri yerine kaydetme yolunda serileştirme için XAML yazıcılarında geri oynatmak üzere bir davranış uygulayabilirsiniz.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğüm akışındaki biçimlendirme uzantıları  
 Yükleme yolunda bir XAML düğüm akışı ile çalışıyorsanız, düğüm akışında bir nesne olarak biçimlendirme uzantısı kullanımı görüntülenir.  
  
 Biçimlendirme uzantısı kullanımı Konumsal bağımsız değişkenler kullanıyorsa, başlatma değeri olan bir başlangıç nesnesi olarak temsil edilir. Kaba bir metin temsili olarak düğüm akışı aşağıdakine benzer:  
  
 `StartObject`(<xref:System.Xaml.XamlType> biçimlendirme uzantısının, dönüş türü değil, tanım türüdür)  
  
 `StartMember`( <xref:System.Xaml.XamlMember> öğesinin`_InitializationText`adı)  
  
 `Value`(değer, yer değişkenleri, araya giren sınırlayıcıları içeren bir dize olarak bulunur)  
  
 `EndMember`  
  
 `EndObject`  
  
 Adlandırılmış bağımsız değişkenlerle bir biçimlendirme uzantısı kullanımı, her biri metin dizesi değerleriyle ayarlanan ilgili adların üyelerine sahip bir nesne olarak temsil edilir.  
  
 Bir biçimlendirme uzantısının `ProvideValue` uygulanmasını gerçekten çağırmak xaml şeması bağlamını gerektirir çünkü bu, tür eşleme gerektirir ve bir işaretleme uzantısı destek türü örneği oluşturur. Bu, biçimlendirme uzantısı kullanımlarının varsayılan .NET Framework XAML Hizmetleri düğüm akışlarında bu şekilde korunmasının bir nedenidir-bir yükleme yolunun okuyucu bölümünde genellikle gerekli XAML şeması bağlamı kullanılabilir değildir.  
  
 Kaydetme yolunda bir xaml düğüm akışı ile çalışıyorsanız, genellikle seri hale getirilecek nesnenin ilk olarak bir biçimlendirme uzantısı kullanımı ve `ProvideValue` sonuç tarafından sağlandığını bildiren bir nesne grafiği gösteriminde bir şey yoktur. Biçimlendirme Uzantısı kullanımlarının gidiş dönüşü için sürdürülmesi gereken senaryolar, nesne grafiğindeki diğer değişiklikleri de yakalayan, özgün XAML girişinden biçimlendirme uzantısı kullanımı bilgisini korumak için kendi tekniklerini kullanmalıdır. Örneğin, biçimlendirme uzantısı kullanımlarını geri yüklemek için, biçimlendirme uzantısı kullanımlarını geri yüklemek için kayıt yolundaki düğüm akışıyla çalışmanız veya orijinal XAML ile yuvarlak daire içinde bir tür birleştirme gerçekleştirmeniz gerekebilir. WPF gibi bazı XAML uygulayan çerçeveler, biçimlendirme uzantısı kullanımlarının değerlerinin sağlandığı durumları temsil etmenize yardımcı olmak için ara türler (ifadeler) kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
