---
title: XAML Biçimlendirme Uzantılarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 68c03589294bcc8b58f1142331d4a889f0f18a3b
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736490"
---
# <a name="markup-extensions-for-xaml-overview"></a>XAML Biçimlendirme Uzantılarına Genel Bakış

Biçimlendirme uzantıları, temel olmayan veya belirli bir XAML türü olmayan bir değer elde etmek için XAML tekniğidir. Biçimlendirme uzantıları, öznitelik kullanımı için, biçimlendirme uzantısı kapsamını girmek için `{` bir açma küme ayracı bilinen karakter dizisini ve çıkış için bir kapanış küme `}` ayracı kullanır. .NET Framework XAML hizmetlerini kullanırken, System. Xaml derlemesinden önceden tanımlanmış XAML dili biçimlendirme genişletmelerini kullanabilirsiniz. Ayrıca, System. xaml içinde tanımlanan <xref:System.Windows.Markup.MarkupExtension> sınıfından alt sınıf oluşturabilir ve kendi biçimlendirme uzantılarınızı tanımlayabilirsiniz. Ya da söz konusu çerçeveye zaten başvuruyordıysanız belirli bir Framework tarafından tanımlanan biçimlendirme uzantılarını kullanabilirsiniz.

Biçimlendirme Uzantısı kullanımına erişildiğinde, XAML nesne yazıcısı, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> geçersiz kılma içindeki bir hizmet bağlantı noktası aracılığıyla özel bir <xref:System.Windows.Markup.MarkupExtension> sınıfına hizmet sağlayabilir. Hizmetler, nesne yazıcısının kullanımı, belirli özellikleri, XAML şeması bağlamı vb. için bağlam elde etmek üzere kullanılabilir.

<a name="XAML_Defined_Markup_Extensions"></a>
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları

Çeşitli biçimlendirme uzantıları XAML dil desteği için .NET Framework XAML Hizmetleri tarafından uygulanır. Bu biçimlendirme uzantıları, XAML belirtiminin bir dil olarak belirtilerinin bölümlerine karşılık gelir. Bunlar genellikle yaygın kullanımda görülen sözdiziminde `x:` ön ekine göre tanımlanabilir. Bu XAML dil öğeleri için .NET Framework XAML Hizmetleri uygulamaları, <xref:System.Windows.Markup.MarkupExtension> temel sınıfından türetilir.

> [!NOTE]
> `x:` ön eki, XAML üretiminin kök öğesinde XAML dili ad alanının tipik XAML ad alanı eşlemesi için kullanılır. Örneğin, çeşitli belirli çerçeveler için Visual Studio projesi ve sayfa şablonları bu `x:` eşlemesini kullanarak bir XAML dosyası başlatır. Kendi XAML ad alanı eşlemesinde farklı bir ön ek belirteci seçebilirsiniz, ancak bu belge varsayılan `x:` eşlemeyi, XAML dilinin varsayılan XAML ad alanı veya diğer rasgele CLR veya XML ad alanları yerine XAML Language XAML ad alanının tanımlı bir parçası olan varlıkları tanımlama yöntemi olarak varsayacaktır.

### <a name="xtype"></a>x:Type

`x:Type`, adlandırılmış tür için <xref:System.Type> nesnesi sağlar. Bu işlevsellik, temel alınan clr türü ve bir gruplama adı veya tanımlayıcı olarak tür Türetmenin kullanıldığı erteleme mekanizmalarındaki en sık kullanılır. WPF stilleri ve şablonları ve `TargetType` özelliklerinin kullanımları belirli bir örnektir. Daha fazla bilgi için bkz. [X:Type Işaretleme uzantısı](x-type-markup-extension.md).

### <a name="xstatic"></a>x:Static

`x:Static`, doğrudan bir özelliğin değerinin türü olmayan değer türü kod varlıklarından statik değerler üretir, ancak bu tür için değerlendirilebilirler. Bu, bir tür tanımında tanınmış sabitler olarak zaten var olan değerleri belirtmek için yararlıdır. Daha fazla bilgi için bkz. [X:static Işaretleme uzantısı](x-static-markup-extension.md).

### <a name="xnull"></a>x:Null

`x:Null` XAML üyesi için değer olarak `null` belirtir. Belirli türlerin tasarımına veya daha büyük çerçeve kavramına bağlı olarak, `null` her zaman bir özellik için varsayılan değer veya boş bir dize özniteliğinin ima edilen değeri değildir. Daha fazla bilgi için bkz. [X:null Işaretleme uzantısı](x-null-markup-extension.md).

### <a name="xarray"></a>x:Array

`x:Array`, temel öğeler ve denetim modelleri tarafından sağlanmış olan koleksiyon desteğinin kasıtlı olarak kullanıldığı durumlarda XAML sözdiziminde genel diziler oluşturulmasını destekler. Daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](x-array-markup-extension.md). XAML 2009 ' de özellikle, dizilere uzantı olarak değil dil temelleri olarak erişilir. Daha fazla bilgi için bkz. [XAML 2009 dil özellikleri](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Reference

`x:Reference`, özgün (2006) dil kümesinin bir uzantısı olan XAML 2009 ' in bir parçasıdır. `x:Reference` bir nesne grafiğinde varolan başka bir nesnenin başvurusunu temsil eder. Bu nesne `x:Name`tarafından tanımlanır. Daha fazla bilgi için bkz. [X:Reference Işaretleme uzantısı](x-reference-markup-extension.md).

### <a name="other-x-constructs"></a>Diğer x: yapılar

XAML dil özelliklerini desteklemeye yönelik diğer `x:` yapıları mevcuttur, ancak bunlar biçimlendirme uzantıları olarak uygulanmaz. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri](xaml-namespace-x-language-features.md).

<a name="the_markupextension_base_class"></a>

## <a name="the-markupextension-base-class"></a>MarkupExtension temel sınıfı

System. xaml 'de XAML okuyucuları ve XAML yazıcılarının varsayılan uygulamalarıyla etkileşime girebilen özel bir işaretleme uzantısı tanımlamak için soyut <xref:System.Windows.Markup.MarkupExtension> sınıfından bir sınıf türetirsiniz. Bu sınıfın, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>geçersiz kılmak için bir yöntemi vardır. Ayrıca, biçimlendirme uzantısı kullanımının bağımsız değişkenlerini desteklemek için ek oluşturucular tanımlamanız ve ayarlanabilir özelliklerle eşleşmesi gerekebilir.

<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, özel bir biçimlendirme uzantısının, biçimlendirme uzantısının gerçekten XAML işlemcisi tarafından çağrıldığı ortamı raporlayan bir hizmet bağlamına erişimi vardır. Yükleme yolunda bu genellikle bir <xref:System.Xaml.XamlObjectWriter>. Kayıt yolunda bu genellikle bir <xref:System.Xaml.XamlXmlWriter>. Her biri hizmet bağlamını bir hizmet sağlayıcı kalıbı uygulayan bir iç XAML hizmeti sağlayıcısı bağlam sınıfı olarak bildirir. Kullanılabilir hizmetler ve neleri temsil ettikleri hakkında daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).

Biçimlendirme Uzantısı sınıfınız ortak erişim düzeyi kullanmalıdır; XAML işlemcileri, hizmetlerini kullanmak için her zaman işaretleme uzantısının destek sınıfını örnekleyemez.

<a name="naming_the_support_type"></a>
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Özel bir Işaretleme uzantısı için destek türünü tanımlama

.NET Framework XAML Hizmetleri üzerinde yapı .NET Framework XAML Hizmetleri veya çerçeveler kullandığınızda, biçimlendirme uzantısı destek türünü adlandırma hakkında iki seçeneğiniz vardır. Tür adı, XAML nesne yazıcılarının XAML 'de biçimlendirme uzantısı kullanımıyla karşılaştıklarında biçimlendirme uzantısı destek türüne erişme ve çağırma ile ilgilidir. Aşağıdaki adlandırma stratejilerinden birini kullanın:

- Tür adını XAML biçimlendirme kullanım belirtecine tam eşleşme olacak şekilde adlandırın. Örneğin, bir `{Collate ...}` uzantısı kullanımını desteklemek için, `Collate`destek türünü adlandırın.
- Tür adını kullanım dizesi belirteci ve sonek `Extension`olarak adlandırın. Örneğin, bir `{Collate ...}` uzantısı kullanımını desteklemek için, `CollateExtension`destek türünü adlandırın.

Arama sırası, önce `Extension`-sonsabit sınıf adını aramak ve ardından `Extension` soneki olmadan sınıf adını arayıyoruz.
  
Biçimlendirme kullanım perspektifinden, kullanım kapsamında `Extension` soneki de dahil olmak üzere geçerli olur. Ancak bu, `Extension` sınıf adının gerçekten bir parçası olduğu gibi davranır ve destek sınıfı `Extension` sonekine sahip değilse XAML nesne yazarları bu kullanım için bir işaretleme uzantısı destek sınıfını çözemeyebilir.

### <a name="the-parameterless-constructor"></a>Parametresiz Oluşturucu

Tüm biçimlendirme uzantısı destek türleri için ortak parametresiz bir Oluşturucu kullanıma sunmalısınız. Parametresiz bir Oluşturucu, bir XAML nesne yazıcısının bir nesne öğesi kullanımındaki biçimlendirme uzantısını örneklemesinin oluşturulduğu herhangi bir durumda gereklidir. Destekleyici nesne öğesi kullanımı, özellikle serileştirme için bir işaretleme uzantısı için bir beklentidir. Ancak, yalnızca biçimlendirme uzantısının öznitelik kullanımlarını desteklemek istiyorsanız, bir ortak Oluşturucu olmadan bir işaretleme uzantısı uygulayabilirsiniz.  

Biçimlendirme Uzantısı kullanımınızın bağımsız değişkeni yoksa, kullanımı desteklemek için parametresiz Oluşturucu gereklidir.

<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Özel bir Işaretleme uzantısı için Oluşturucu desenleri ve Konumsal bağımsız değişkenler

Bağımsız değişken kullanımı amaçlanan bir işaretleme uzantısı için, ortak oluşturucuların amaçlanan kullanım modlarına karşılık gelmesi gerekir. Diğer bir deyişle, biçimlendirme uzantınız geçerli kullanım olarak bir Konumsal bağımsız değişken gerektirecek şekilde tasarlanmışsa, konum bağımsız değişkenini alan bir giriş parametresiyle ortak bir oluşturucuyu desteklemeniz gerekir.

Örneğin, `Collate` biçimlendirme uzantısının yalnızca modunu temsil eden bir konum bağımsız değişkeni olan ve `CollationMode` bir numaralandırma sabiti olarak belirtilen bir modu desteklemeye yönelik olduğunu varsayalım. Bu durumda, aşağıdaki biçimde bir oluşturucu olmalıdır:

```csharp
public Collate(CollationMode collationMode) {...}
```

Temel düzeyde, biçimlendirme uzantısına geçirilen bağımsız değişkenler, biçimlendirmenin öznitelik değerlerinden iletileceği için bir dizedir. Bağımsız değişken Dizelerinizin tümünü yapabilir ve bu düzeyde giriş ile çalışabilirsiniz. Ancak, biçimlendirme uzantısı bağımsız değişkenleri destek sınıfına geçirilmeden önce gerçekleşen belirli işleme erişiminiz vardır.

İşleme, biçimlendirme uzantısı oluşturulacak bir nesne olup, sonra üye değerleri ayarlanmış gibi kavramsal olarak çalışacaktır. Ayarlanacak her bir özellik, XAML ayrıştırıldığında oluşturulan bir nesnede belirtilen üyenin nasıl ayarlanıladığına benzer şekilde değerlendirilir. İki önemli fark vardır:
  
- Daha önce belirtildiği gibi, biçimlendirme uzantısı destek türünün XAML 'de örneklendirmenin parametresiz oluşturucusu olması gerekmez. Nesne oluşturma, metin sözdiziminde olası bağımsız değişkenlerin simgeleştirilmesine ve Konumsal ya da adlandırılmış bağımsız değişkenler olarak değerlendirilene kadar ertelenir ve uygun Oluşturucu o anda çağırılır.
- Biçimlendirme uzantıları kullanımları iç içe olabilir. En içteki biçimlendirme uzantısı ilk olarak değerlendirilir. Bu nedenle, bu tür bir kullanımı varsayabilir ve oluşturma parametrelerinden birini bir değer Dönüştürücüsü (örneğin, biçimlendirme uzantısı) gerektiren bir tür olacak şekilde bildirebilirsiniz.

Bu tür bir işlem, önceki örnekte gösterilmemiştir. .NET Framework XAML Hizmetleri XAML nesne yazıcı, sabit listesi sabit adlarını yerel düzeyde numaralandırılmış değerlerle işler.

Bir işaretleme uzantısı konumsal parametresinin metin sözdizimi işleme, oluşturma bağımsız değişkeninde bulunan türle ilişkili bir tür dönüştürücüde de olabilir.

Kullanımdaki belirteçlerin karşılaştığı sıra, atandıkları Oluşturucu parametresinin konumsal sırasına karşılık gelen bağımsız değişkenler Konumsal bağımsız değişkenler olarak adlandırılır. Örneğin, aşağıdaki Oluşturucu imzasını göz önünde bulundurun:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

XAML işlemcisi, bu biçimlendirme uzantısı için iki Konumsal bağımsız değişken bekliyor. Kullanım `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` belirteci ilk parametreye gönderilir ve sabit adlı bir `CollationMode` numaralandırması olarak değerlendirilir. İç `x:Reference` sonucu ikinci parametreye gönderilir ve bir nesne olarak değerlendirilir.

Biçimlendirme uzantısı sözdizimi ve işleme için XAML tarafından belirtilen kurallarda, bu bağımsız değişkenlerin Konumsal bağımsız değişkenler veya adlandırılmış bağımsız değişkenler olup olmadığı bağımsız değişkenler arasındaki sınırlayıcı virgüldür.

### <a name="duplicate-arity-of-positional-arguments"></a>Yinelenen sayıda Konumsal bağımsız değişken

XAML nesne yazarı, Konumsal bağımsız değişkenlerle bir biçimlendirme uzantısı kullanımıyla karşılaşırsa ve bu sayıda bağımsız değişken (yinelenen parametre sayısı) alan birden çok Oluşturucu bağımsız değişkeni varsa, bu bir hata olması gerekmez. Davranış, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>özelleştirilebilir XAML şeması bağlam ayarına bağlıdır. <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `true`, bir XAML nesne yazıcısı yalnızca yinelenen parametre sayısı nedeniyle özel durum oluşturmaz. Bu noktanın ötesinde davranış kesin olarak tanımlanmamıştır. Temel tasarım varsayımına, şema bağlamının belirli parametrelere ait tür bilgilerine sahip olması ve hangi imzanın en iyi eşleşme olabileceğini görmek için yinelenen adaylara uyan açık yayınları deneyebileceği anlamına gelir. Bir XAML nesne yazıcısında çalışan belirli şema bağlamı tarafından uygulanan testleri geçemezse bir özel durum yine de oluşturulabilir.

<xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>, varsayılan olarak, .NET Framework XAML Hizmetleri için CLR tabanlı <xref:System.Xaml.XamlSchemaContext> `false`. Bu nedenle, varsayılan <xref:System.Xaml.XamlObjectWriter>, bir biçimlendirme uzantısı kullanımı ile karşılaştığında, yedekleme türünün oluşturucularında yinelenen parametre sayısı olduğunda özel durumlar oluşturur.

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
## <a name="attributing-for-a-custom-markup-extension"></a>Özel bir işaretleme uzantısı için Attributing

Hem tasarım ortamlarını hem de belirli XAML nesne yazıcısı senaryolarını desteklemek için, birkaç CLR özniteliğiyle bir biçimlendirme uzantısı destek türüne sahip olmanız gerekir. Bu öznitelikler, istenen biçimlendirme uzantısı kullanımını raporlar.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürdüğü nesne türü için <xref:System.Type> bilgilerini raporlar. Saf imzasına göre, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> <xref:System.Object>döndürür. Ancak çeşitli tüketiciler daha kesin dönüş türü bilgileri isteyebilir. Şunları içerir:

- Tasarımcılar ve Ides, biçimlendirme uzantısı kullanımları için tür duyarlı destek sağlayabilecek.
- Hedef sınıflarda `SetMarkupExtension` işleyicilerinin gelişmiş uygulamaları, belirli bir ada göre bilinen <xref:System.Windows.Markup.MarkupExtension> uygulamalarında dallandırma yerine bir işaretleme uzantısının dönüş türünü tespit etmek için yansıma üzerinde güvenebilirler.

<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Biçimlendirme Uzantısı kullanımlarının serileştirilmesi

XAML nesne yazıcısı bir biçimlendirme uzantısı kullanımını işlediğinde ve <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>çağırdığında, daha önce biçimlendirme uzantısı kullanımı olan bağlam XAML düğüm akışında devam ediyor ancak nesne grafiğinde kullanılamaz. Nesne grafiğinde yalnızca değer korunur. Özgün biçimlendirme uzantısı kullanımını serileştirilmiş çıkışa kalıcı hale getirmeniz için tasarım senaryolarınız veya başka nedenleriniz varsa, biçimlendirme uzantısı kullanımlarını, yük yolu XAML düğüm akışından izlemek için kendi altyapınızı tasarlamanız gerekir. Yük yolundan düğüm akışının öğelerini yeniden oluşturmak ve bunları, düğüm akışının uygun konumundaki değeri yerine kaydetme yolunda serileştirme için XAML yazıcılarında geri oynatmak üzere bir davranış uygulayabilirsiniz.

<a name="markup_extensions_in_the_xaml_node_stream"></a>
## <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğüm akışındaki biçimlendirme uzantıları

Yükleme yolunda bir XAML düğüm akışı ile çalışıyorsanız, düğüm akışında bir nesne olarak biçimlendirme uzantısı kullanımı görüntülenir.

Biçimlendirme uzantısı kullanımı Konumsal bağımsız değişkenler kullanıyorsa, başlatma değeri olan bir başlangıç nesnesi olarak temsil edilir. Kaba bir metin temsili olarak düğüm akışı aşağıdakine benzer:

 `StartObject` (<xref:System.Xaml.XamlType>, dönüş türü değil, biçimlendirme uzantısının tanım türüdür)

 `StartMember` (<xref:System.Xaml.XamlMember> adı `_InitializationText`)

 `Value` (değer, yer değişkenleri, araya giren sınırlayıcıları içeren bir dize olarak bulunur)

 `EndMember`

 `EndObject`

Adlandırılmış bağımsız değişkenlerle bir biçimlendirme uzantısı kullanımı, her biri metin dizesi değerleriyle ayarlanan ilgili adların üyelerine sahip bir nesne olarak temsil edilir.

Bir biçimlendirme uzantısının `ProvideValue` uygulamasını çağırmak için XAML şeması bağlamı gereklidir çünkü bu, tür eşleme gerektirir ve bir işaretleme uzantısı destek türü örneği oluşturur. Bu, biçimlendirme uzantısı kullanımlarının varsayılan .NET Framework XAML Hizmetleri düğüm akışlarında bu şekilde korunmasının bir nedenidir-bir yükleme yolunun okuyucu bölümünde genellikle gerekli XAML şeması bağlamı kullanılabilir değildir.

Kaydetme yolunda bir XAML düğüm akışı ile çalışıyorsanız, genellikle seri hale getirilecek nesnenin ilk olarak bir biçimlendirme uzantısı kullanımı ve bir `ProvideValue` sonucu tarafından sağlandığını bildiren bir nesne grafiği gösteriminde hiçbir şey yok. Biçimlendirme Uzantısı kullanımlarının gidiş dönüşü için sürdürülmesi gereken senaryolar, nesne grafiğindeki diğer değişiklikleri de yakalayan, özgün XAML girişinden biçimlendirme uzantısı kullanımı bilgisini korumak için kendi tekniklerini kullanmalıdır. Örneğin, biçimlendirme uzantısı kullanımlarını geri yüklemek için, biçimlendirme uzantısı kullanımlarını geri yüklemek için kayıt yolundaki düğüm akışıyla çalışmanız veya orijinal XAML ile yuvarlak daire içinde bir tür birleştirme gerçekleştirmeniz gerekebilir. WPF gibi bazı XAML uygulayan çerçeveler, biçimlendirme uzantısı kullanımlarının değerlerinin sağlandığı durumları temsil etmenize yardımcı olmak için ara türler (ifadeler) kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
