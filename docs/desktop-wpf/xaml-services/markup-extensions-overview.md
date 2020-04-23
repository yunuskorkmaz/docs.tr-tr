---
title: XAML Biçimlendirme Uzantılarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: c0ca8e7d0d68d4730173385540cbcec66c7bf03a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071719"
---
# <a name="overview-of-markup-extensions-for-xaml"></a>XAML için biçimlendirme uzantılarına genel bakış

Biçimlendirme uzantıları, ilkel veya belirli bir XAML türü olmayan bir değer elde etmek için bir XAML tekniğidir. Öznitelik kullanımı için biçimlendirme uzantıları, biçimlendirme uzantısı kapsamını `{` girmek için bir açılış kıvırcık ayracının bilinen karakter dizisini ve çıkmak için kapanış kıvırcık ayracını `}` kullanır. .NET XAML Hizmetlerini kullanırken, System.Xaml derlemesinden önceden tanımlanmış XAML dil biçimlendirme uzantılarından bazılarını kullanabilirsiniz. System.Xaml'da <xref:System.Windows.Markup.MarkupExtension> tanımlanan sınıftan alt sınıf alabilirsiniz ve kendi biçimlendirme uzantılarınızı tanımlayabilirsiniz. Veya bu çerçeveye zaten başvuruyorsanız, belirli bir çerçeve tarafından tanımlanan biçimlendirme uzantılarını kullanabilirsiniz.

Biçimlendirme uzantısı kullanımına erişildiğinde, XAML nesne yazarı geçersiz kılmadaki <xref:System.Windows.Markup.MarkupExtension> <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> bir servis bağlantı noktası aracılığıyla özel bir sınıfa hizmet sağlayabilir. Hizmetler, nesne yazarının kullanımı, belirli yetenekleri, XAML şeması bağlamı ve benzeri bağlamları elde etmek için kullanılabilir.

## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları

XAML dil desteği için .NET XAML Services tarafından çeşitli biçimlendirme uzantıları uygulanır. Bu biçimlendirme uzantıları, dil olarak XAML belirtiminin bazı bölümlerine karşılık gelir. Bunlar genellikle sık kullanımda görüldüğü gibi `x:` sözdiziminde önek tarafından tanımlanabilir. .NET XAML Hizmetleri bu XAML dil öğeleri için <xref:System.Windows.Markup.MarkupExtension> tüm taban sınıftan türetilmiştir.

> [!NOTE]
> Önek, `x:` XAML üretiminin kök öğesinde, XAML dil ad alanının tipik XAML ad alanı eşlemi için kullanılır. Örneğin, çeşitli özel çerçeveler için Visual Studio projesi ve sayfa şablonları `x:` bu eşlemi kullanarak bir XAML dosyası başlatır. Kendi XAML ad alanı eşlemenizde farklı bir önek belirteci seçebilirsiniz, ancak bu belge, belirli bir çerçevenin varsayılan XAML ad alanı veya diğer rasgele CLR veya XML ad alanlarının aksine, XAML dilixaml ad alanının tanımlı bir parçası olan varlıkları tanımlama aracı olarak varsayılan `x:` eşlemeyi varsayar.

### <a name="xtype"></a>x:Tür

`x:Type`<xref:System.Type> adlı tür için nesne sağlar. Bu işlevsellik en sık bir gruplama takma veya tanımlayıcı olarak altta yatan CLR türü ve tür türtevi kullanan erteleme mekanizmaları kullanılır. WPF stilleri ve şablonları ve `TargetType` bunların özelliklerinin kullanımı belirli bir örnektir. Daha fazla bilgi için [bkz: X:Tip Biçimlendirme Uzantısı.](xtype-markup-extension.md)

### <a name="xstatic"></a>x:Statik

`x:Static`doğrudan bir özelliğin değeri türü olmayan, ancak bu türe göre değerlendirilebilen değer türü kod varlıklarından statik değerler üretir. Bu, bir tür tanımında zaten iyi bilinen sabitler olarak zaten var olan değerleri belirtmek için yararlıdır. Daha fazla bilgi için [bkz: x:Statik Biçimlendirme Uzantısı.](xstatic-markup-extension.md)

### <a name="xnull"></a>x:Null

`x:Null`bir XAML üyesi için bir değer olarak belirtir. `null` Belirli türlerin tasarımına veya daha büyük çerçeve `null` kavramlarına bağlı olarak, bir özellik için varsayılan değer veya boş bir dize özniteliğinin zımni değeri her zaman değildir. Daha fazla bilgi için [bkz: x:Null Biçimlendirme Uzantısı.](xnull-markup-extension.md)

### <a name="xarray"></a>x:Dizi

`x:Array`Temel elemanlar ve denetim modelleri tarafından sağlanan toplama desteğinin kasıtlı olarak kullanılmadığı durumlarda XAML sözdiziminde genel dizilerin oluşturulmasını destekler. Daha fazla bilgi için [bkz: x:Dizi Biçimlendirme Uzantısı.](xarray-markup-extension.md) Özellikle XAML 2009'da dizilere uzantı olarak değil, dil ilkelleri olarak erişilir. Daha fazla bilgi için [Bkz. XAML 2009 Dil Özellikleri.](xaml-2009-language-features.md)

### <a name="xreference"></a>x:Başvuru

`x:Reference`XAML 2009, orijinal (2006) dil kümesinin bir uzantısı bir parçasıdır. `x:Reference`nesne grafiğindeki başka bir varolan nesneye başvurutemsil eder. Bu nesne onun `x:Name`. Daha fazla bilgi için [bkz: X:Reference Markup Extension](xreference-markup-extension.md).

### <a name="other-x-constructs"></a>Diğer x: Yapılar

XAML dil özelliklerini destekleyen diğer `x:` yapılar vardır, ancak bunlar biçimlendirme uzantıları olarak uygulanmaz. Daha fazla bilgi için [Bkz. XAML Namespace (x:) Dil Özellikleri](namespace-language-features.md).

## <a name="the-markupextension-base-class"></a>Biçimlendirme Taban Sınıfı

System.Xaml'daki XAML okuyucularının ve XAML yazarlarının varsayılan uygulamalarıyla etkileşime girebilen özel bir <xref:System.Windows.Markup.MarkupExtension> biçimlendirme uzantısı tanımlamak için, soyut sınıftan bir sınıf türedersiniz. Bu sınıfın geçersiz kılmak için bir <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>yöntemi vardır. Ayrıca, biçimlendirme uzantısı kullanımı ve eşleşen ayarlanabilir özellikleri bağımsız değişkenleri desteklemek için ek oluşturucular tanımlamanız gerekebilir.

Özel <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>biçimlendirme uzantısı aracılığıyla, biçimlendirme uzantısının bir XAML işlemci tarafından çağrıldığı ortamı bildiren bir hizmet bağlamına erişimi vardır. Yük yolunda, bu genellikle bir <xref:System.Xaml.XamlObjectWriter>. Kaydet yolunda bu genellikle <xref:System.Xaml.XamlXmlWriter>bir . Her rapor bir hizmet sağlayıcı deseni uygulayan bir iç XAML hizmet sağlayıcısı bağlam ıstırmayı olarak hizmet bağlamı. Kullanılabilir hizmetler ve neyi temsil ettikleri hakkında daha fazla bilgi için [XAML için Type Converters ve Markup Uzantıları'na](type-converters-and-markup-extensions.md)bakın.

Biçimlendirme uzantısı sınıfınız herkese açık erişim düzeyini kullanmalıdır; XAML işlemciler, hizmetlerini kullanabilmek için biçimlendirme uzantısı destek sınıfını her zaman anında kullanabilmeli.

## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Özel Biçimlendirme Uzantısı için Destek Türünü Tanımlama

.NET XAML Hizmetleri veya .NET XAML Hizmetleri üzerine inşa edilen çerçeveleri kullandığınızda, biçimlendirme uzantısı destek türünü adlandırmak için iki seçeneğiniz vardır. Tür adı, XAML nesne yazarlarının XAML'de biçimlendirme uzantısı kullanımıyla karşılaştıklarında biçimlendirme uzantısı destek türüne nasıl erişmeye ve çağrıda bulunmaya çalıştıklarıyla ilgilidir. Aşağıdaki adlandırma stratejilerinden birini kullanın:

- XAML biçimlendirme kullanım belirteciyle tam eşleşecek şekilde tür adını adlandırın. Örneğin, bir `{Collate ...}` uzantı kullanımını desteklemek için `Collate`destek türünü adlandırın.
- Kullanım dizesi belirteci artı sonek `Extension`olacak tür adını adlandırın. Örneğin, bir `{Collate ...}` uzantı kullanımını desteklemek için `CollateExtension`destek türünü adlandırın.

Arama sırası önce `Extension`-sonefixed sınıf adını aramak ve daha sonra `Extension` sonek olmadan sınıf adını aramaktır.

Biçimlendirme kullanım açısından bakıldığında, `Extension` kullanım parçası olarak sonek de dahil olmak üzere geçerlidir. Ancak, bu gerçekten sınıf `Extension` adının bir parçası gibi olur ve XAML nesne yazarları destek sınıfı `Extension` sonek yoksa bu kullanım için bir biçimlendirme uzantısı destek sınıfı çözmek için başarısız olur.

### <a name="the-parameterless-constructor"></a>Parametresiz yapıcı

Tüm biçimlendirme uzantısı destek türleri için, ortak parametresiz bir oluşturucu sunmalısınız. Bir XAML nesne yazarının biçimlendirme uzantısını nesne öğesi kullanımından anında aldığı her durum için parametresiz bir oluşturucu gereklidir. Nesne öğesi kullanımını desteklemek, özellikle serileştirme için bir biçimlendirme uzantısı için adil bir beklentidir. Ancak, yalnızca biçimlendirme uzantısı öznitelik kullanımlarını desteklemek istiyorsanız, ortak bir oluşturucu olmadan bir biçimlendirme uzantısı uygulayabilirsiniz.

Biçimlendirme uzantısı kullanımınızda bağımsız değişken yoksa, kullanımı desteklemek için parametresiz oluşturucu gereklidir.

## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Özel Biçimlendirme Uzantısı Için Oluşturucu Desenleri ve Konumsal Bağımsız Değişkenler

Amaçlanan bağımsız değişken kullanımıyla bir biçimlendirme uzantısı için, ortak oluşturucuların amaçlanan kullanım modlarına karşılık vermesi gerekir. Başka bir deyişle, biçimlendirme uzantınız geçerli bir kullanım olarak bir konumsal bağımsız değişken gerektirecek şekilde tasarlandıysa, konumsal bağımsız değişkeni alan tek bir giriş parametresi olan bir ortak oluşturucuyu desteklemeniz gerekir.

Örneğin, `Collate` biçimlendirme uzantısıyalnızca kendi modunu temsil eden ve numaralandırma sabiti olarak belirtilen `CollationMode` bir konumsal bağımsız değişkenin olduğu bir modu desteklemek için tasarlandığını varsayalım. Bu durumda, aşağıdaki forma sahip bir oluşturucu olmalıdır:

```csharp
public Collate(CollationMode collationMode) {...}
```

Temel düzeyde, biçimlendirme uzantısına geçirilen bağımsız değişkenler, biçimlendirmenin öznitelik değerlerinden iledildiği için bir dizedir. Tüm bağımsız değişkenlerinizi dizeleri yapabilir ve bu düzeyde giriş ile çalışabilirsiniz. Ancak, biçimlendirme uzantısı bağımsız değişkenleri destek sınıfına geçirilmeden önce oluşan belirli işleme erişiminiz vardır.

İşlem, biçimlendirme uzantısı oluşturulacak bir nesne gibi kavramsal olarak çalışır ve üye değerleri ayarlanır. Ayarlanacak her belirtilen özellik, XAML ayrıştırıldığında, belirli bir üyenin oluşturulan bir nesne üzerinde nasıl ayarlanabildiğiyle benzer şekilde değerlendirilir. İki önemli fark vardır:

- Daha önce de belirtildiği gibi, xaml anında olması için bir biçimlendirme uzantısı destek türü parametresiz bir oluşturucu olması gerekmez. Nesne yapısı, metin sözdiziminde olası bağımsız değişkenleri belirtilene ve konumsal veya adlandırılmış bağımsız değişkenler olarak değerlendirilene ve uygun oluşturucu o anda çağrılana kadar ertelenir.
- Biçimlendirme uzantıları kullanımları iç içe olabilir. Önce en içteki biçimlendirme uzantısı değerlendirilir. Bu nedenle, böyle bir kullanımı varsayabilir ve yapı parametrelerinden birini üretmek için değer dönüştürücü (biçimlendirme uzantısı gibi) gerektiren bir tür olarak bildirebilirsiniz.

Önceki örnekte bu tür işlemlere güven gösterilmiştir. .NET XAML Services XAML nesne yazarı, sabit adları yerel düzeyde numaralandırılmış değerlere numaralandırma yı işler.

Biçimlendirme uzantısı konumel parametresinin metin sözdizimini işleme, yapı bağımsız değişkenindeki türle ilişkili bir tür dönüştürücüse de güvenebilir.

Kullanımdaki belirteçlerin karşılaşıldığı sıra, atandıkları kurucu parametrenin konumsal sırasına karşılık geldiği için bağımsız değişkenlere konumsal bağımsız değişkenler denir. Örneğin, aşağıdaki oluşturucu imzayı göz önünde bulundurun:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Bir XAML işlemci bu biçimlendirme uzantısı için iki konumsal bağımsız değişken bekler. Bir kullanım `{Collate AlphaUp,{x:Reference circularFile}}`varsa, `AlphaUp` belirteç ilk parametreye gönderilir ve `CollationMode` sabit adlı numaralandırma olarak değerlendirilir. İç sonucu `x:Reference` ikinci parametreye gönderilir ve nesne olarak değerlendirilir.

XAML'de biçimlendirme uzantısı sözdizimi ve işleme için belirtilen kurallarda, virgül, bu bağımsız değişkenlerin konumsal bağımsız değişkenler mi yoksa adlandırılmış bağımsız değişkenler mi olduğu bağımsız değişkenler arasındaki sınır layıcıdır.

### <a name="duplicate-arity-of-positional-arguments"></a>Konumsal bağımsız değişkenlerin yinelenen arityonu

Bir XAML nesne swriter konumsal bağımsız değişkenler ile bir biçimlendirme uzantısı kullanımı karşılaşırsa ve bu sayıda bağımsız değişken (yinelenen arity) almak birden çok oluşturucu bağımsız değişkenler varsa, bu mutlaka bir hata değildir. Davranış, özelleştirilebilir bir XAML şema bağlam <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>ayarına bağlıdır. <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> Ise, `true`bir XAML nesne yazar yinelenen arity nedenlerle yalnızca bir özel durum atmamalıdır. Bu noktanın ötesindeki davranışlar kesinlikle tanımlanmamıştır. Temel tasarım varsayımı, şema bağlamında belirli parametreler için tür bilgileri ne kadar kullanılabilir ve hangi imzanın en iyi eşleşme olabileceğini görmek için yinelenen adaylarla eşleşen açık dökümler deneyebilir. XAML nesne yazarı üzerinde çalışan belirli şema bağlamı tarafından dayatılan testleri hiçbir imza geçemezse, yine de bir özel durum atılabilir.

Varsayılan <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> olarak, `false` .NET XAML Hizmetleri için CLR tabanlıdır. <xref:System.Xaml.XamlSchemaContext> Bu nedenle, <xref:System.Xaml.XamlObjectWriter> varsayılan, destek türü oluşturucularında yinelenen arity'nin olduğu bir biçimlendirme uzantısı kullanımıyla karşılaşırsa özel durumlar oluşturur.

## <a name="named-arguments-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için adlandırılmış bağımsız değişkenler

XAML tarafından belirtilen biçimlendirme uzantıları da kullanım için adlandırılmış bağımsız değişkenler formu kullanabilirsiniz. Belirteçleştirmenin ilk düzeyinde, metin sözdizimi bağımsız değişkenlere ayrılır. Herhangi bir bağımsız değişkeniçinde eşitler işareti (=) varlığı bir bağımsız değişkeni adlandırılmış bir bağımsız değişken olarak tanımlar. Böyle bir bağımsız değişken de bir ad/değer çiftine dönüştürülebilir. Bu durumda ad, biçimlendirme uzantısı destek türünün ortak ayarlanan özelliğini adlandırır. Adlandırılmış bağımsız değişken kullanımını desteklemek istiyorsanız, bu ortak ayarlanan özellikleri sağlamanız gerekir. Mülkler, ortak oldukları sürece devralınabilir.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı Uygulamasından Hizmet Sağlayıcı Bağlamına Erişim

Kullanılabilir hizmetler herhangi bir değer dönüştürücü için aynıdır. Fark, her değer dönüştürücüsü hizmet bağlamını nasıl aldığıdır. Hizmetlere ve mevcut hizmetlere erişim, [XAML için Type Converters ve Markup Uzantıları](type-converters-and-markup-extensions.md)konusunda belgelenmiştir.

## <a name="property-element-usage-of-a-markup-extension"></a>Biçimlendirme uzantısı özellik öğesi kullanımı

Biçimlendirme uzantısı kullanımları için senaryolar genellikle öznitelik kullanımında biçimlendirme uzantısı kullanılarak tasarlanmıştır. Ancak, özellik öğesi kullanımını desteklemek için destek sınıfını tanımlamak da mümkündür.

Biçimlendirme uzantınızın özellik öğesi kullanımını desteklemek için, ortak parametresiz bir oluşturucu tanımlayın. Bu statik bir yapıcı değil, bir örnek oluşturucu olmalıdır. Bir XAML işlemci genellikle biçimlendirme den işlediği herhangi bir nesne öğesi üzerinde parametresiz oluşturucu çağırmak gerekir ve bu nesne öğeleri olarak biçimlendirme uzantısı sınıfları içerir, çünkü bu gereklidir. Gelişmiş senaryolar için sınıflar için varsayılan olmayan yapı yolları tanımlayabilirsiniz. (Daha fazla bilgi için [bkz: X:FactoryMethod Direktifi.)](xfactorymethod-directive.md) Ancak, bu durum hem tasarımcılar hem de ham biçimlendirme kullanıcıları için kullanım deseninin keşfini çok daha zor hale getirir olduğundan, bu desenleri biçimlendirme uzantısı amaçları için kullanmamalısınız.

## <a name="attributing-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için atfetme

Hem tasarım ortamlarını hem de belirli XAML nesne yazar senaryolarını desteklemek için, birkaç CLR öznitelikleriiçeren bir biçimlendirme uzantısı destek türü atfetmeniz gerekir. Bu öznitelikler, amaçlanan biçimlendirme uzantısı kullanımını rapor eder.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>döndüren <xref:System.Type> <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> nesne türüne ait bilgileri raporlar. Saf imzasıyla, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> <xref:System.Object>geri döner. Ancak çeşitli tüketiciler daha kesin iade türü bilgileri isteyebilir. Buna aşağıdakiler dahildir:

- Biçimlendirme uzantısı kullanımları için tür duyarlı destek sağlayabilecek tasarımcılar ve IID'ler.
- Hedef sınıflardaki `SetMarkupExtension` işleyicilerin gelişmiş uygulamaları, belirli bilinen <xref:System.Windows.Markup.MarkupExtension> uygulamaları ada göre dallandırmak yerine biçimlendirme uzantısının dönüş türünü belirlemek için yansımaya güvenebilir.

## <a name="serialization-of-markup-extension-usages"></a>Biçimlendirme uzantısı kullanımlarının serileştirilmesi

Bir XAML nesne swriter bir biçimlendirme <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>uzantısı kullanımını işler ve çağırır , daha önce bir biçimlendirme uzantısı kullanımı xaml düğüm akışı nda kalır, ancak nesne grafiğinde değil. Nesne grafiğinde yalnızca değer korunur. Özgün biçimlendirme uzantısı kullanımını seri haline getirilmiş çıktıda kalıcı hale getirebiliyorsanız, yükleme yolu XAML düğüm akışından biçimlendirme uzantısı kullanımlarını izlemek için kendi altyapınızı tasarlamanız gerekir. Düğüm akışının öğelerini yük yolundan yeniden oluşturmak ve düğüm akışının uygun konumundaki değeryerine kaydet yolunda serileştirme için XAML yazarlarına oynatmak için davranışı uygulayabilirsiniz.

## <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğüm akışındaki biçimlendirme uzantıları

Yük yolunda bir XAML düğümü akışıyla çalışıyorsanız, düğüm akışında nesne olarak biçimlendirme uzantısı görüntülenir.

Biçimlendirme uzantısı kullanımı konumsal bağımsız değişkenler kullanıyorsa, başlatma değeri olan bir başlangıç nesnesi olarak temsil edilir. Kaba metin gösterimi olarak düğüm akışı aşağıdakileri benzer:

`StartObject`(<xref:System.Xaml.XamlType> biçimlendirme uzantısının tanım türüdür, dönüş türüdür)

`StartMember`<xref:System.Xaml.XamlMember> (is `_InitializationText`adı )

`Value`(değer, araya giren sınırlayıcıları da içeren bir dize olarak konumsal bağımsız değişkendir)

`EndMember`

`EndObject`

Adlandırılmış bağımsız değişkenler içeren biçimlendirme uzantısı kullanımı, her biri metin dize değerleriyle birlikte ayarlanan ilgili adların üyeleriyle birlikte bir nesne olarak temsil edilir.

Aslında bir biçimlendirme uzantısı `ProvideValue` uygulanması nı çağırmak XAML şema bağlamı gerektirir, çünkü bu tür eşleme ve biçimlendirme uzantısı destek türü örneği oluşturmagerektirir. Biçimlendirme uzantısı kullanımlarının varsayılan .NET XAML Hizmetleri düğüm akışlarında bu şekilde korunmasının bir nedeni de budur - yükleme yolunun okuyucu bölümü genellikle gerekli XAML şeması bağlamına sahip değildir.

Kaydet yolunda bir XAML düğüm akışıyla çalışıyorsanız, serihale getirmek için nesnenin başlangıçta bir biçimlendirme uzantısı kullanımı ve bir `ProvideValue` sonuç tarafından sağlandığını size bildirebilecek bir nesne grafiği gösteriminde genellikle hiçbir şey yoktur. Nesne grafiğindeki diğer değişiklikleri yakalarken yuvarlama uzantısı kullanımlarını devam ettirmesi gereken senaryolar, özgün XAML girişinden biçimlendirme uzantısı kullanımının bilgisini korumak için kendi tekniklerini geliştirmelidir. Örneğin, biçimlendirme uzantısı kullanımlarını geri yüklemek için, biçimlendirme uzantısı kullanımlarını geri yüklemek için kaydet yolundaki düğüm akışıyla çalışmanız veya özgün XAML ile geri dönüşen XAML arasında bir tür birleştirme gerçekleştirmeniz gerekebilir. WPF gibi bazı XAML uygulayan çerçeveler, biçimlendirme uzantısı kullanımlarının değerleri sağladığı durumları temsil etmeye yardımcı olmak için ara türler (ifadeler) kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions.md)
- [Biçimlendirme Uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
