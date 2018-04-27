---
title: XAML İşaretleme Uzantılarına Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
caps.latest.revision: 14
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 464c5f547089d47906f2e227effe821357196c16
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="markup-extensions-for-xaml-overview"></a>XAML İşaretleme Uzantılarına Genel Bakış
Biçimlendirme uzantıları türünün bir temel veya de belirli XAML türü olan bir değer almak için bir XAML teknik yer almaktadır. Öznitelik kullanımı için bir parantezinden bilinen karakter dizisi biçimlendirme uzantıları kullanmak `{` biçimlendirme uzantısı kapsamı ve kapanış kuşak girmek için `}` çıkmak için. .NET Framework XAML hizmetlerinde kullanırken, önceden tanımlanmış XAML dil biçimlendirme uzantıları System.Xaml derlemesinden bazıları kullanabilirsiniz. Gelen bir alt kullanabileceğiniz <xref:System.Windows.Markup.MarkupExtension> sınıfı, System.Xaml içinde tanımlanan ve kendi biçimlendirme uzantıları tanımlayın. Veya zaten bu framework başvurduğunuzdan, belirli bir çerçevesi tarafından tanımlanan biçimlendirme uzantıları kullanabilirsiniz.  
  
 Biçimlendirme uzantısı kullanımı erişildiğinde XAML nesne yazıcısı özel hizmetleri sağlayabilir <xref:System.Windows.Markup.MarkupExtension> sınıfı aracılığıyla bir hizmet bağlantı noktası <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> geçersiz kılar. Hizmetlerin kullanımı hakkında bağlam, nesne yazıcısı, XAML şema içeriği ve benzeri belirli özelliklerini almak için kullanılabilir.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlanan biçimlendirme uzantıları  
 Birkaç biçimlendirme uzantıları, XAML dili desteği için .NET Framework XAML Hizmetleri tarafından uygulanır. Bu biçimlendirme uzantıları XAML belirtimi dili olarak bölümlerini karşılık gelir. Bunlar genellikle adlarıyla `x:` ortak kullanım görülen sözdiziminde öneki. Tüm türetilen bu XAML dil öğeleri için .NET Framework XAML hizmetlerinde uygulamaları <xref:System.Windows.Markup.MarkupExtension> temel sınıfı.  
  
> [!NOTE]
>  `x:` Öneki, XAML dili ad uzayı XAML üretim kök öğesinin tipik XAML ad alanı eşlemesi için kullanılır. Örneğin, bunu kullanan XAML dosyası çeşitli belirli çerçeveler için Visual Studio Proje ve sayfa şablonları başlatmak `x:` eşleme. Kendi XAML ad alanı eşlemesi farklı önek belirteci seçebilir, ancak bu belgeleri varsayılan varsayacak `x:` tersine XAML dili XAML ad uzayı, tanımlı bir parçası olan bu varlıkların tanımlamak için bir araç olarak eşleme bir belirli framework'ün varsayılan XAML ad uzayı veya diğer rasgele CLR veya XML ad alanları.  
  
### <a name="xtype"></a>x: Type  
 `x:Type` sağladığı <xref:System.Type> adlandırılmış türü için nesnesi. Bu işlev, CLR türü kullanan ve bir gruplandırma ad veya tanımlayıcı türetme yazın erteleme mekanizmaları, en sık kullanılır. WPF stilleri, şablonları ve bunların kullanımını `TargetType` özelliklerdir, belirli bir örneği. Daha fazla bilgi için bkz: [x: Type işaretleme uzantısı](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` doğrudan bir özelliğin değerini türünü değildir, ancak bu tür için hesaplanan değer türü kodu varlıkları statik değerlerinden üretir. Bu tür tanımında iyi bilinen sabitleri olarak zaten mevcut değerleri belirtmek için kullanışlıdır. Daha fazla bilgi için bkz: [x: Static işaretleme uzantısı](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### <a name="xnull"></a>x: Null  
 `x:Null` belirtir `null` XAML üyesi için bir değer olarak. Belirli türleri ya da daha büyük framework kavramlarını tasarımına `null` her zaman bir özellik için varsayılan bir değer veya boş dize özniteliğin örtük değeri değil. Daha fazla bilgi için bkz: [x: Null işaretleme uzantısı](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` temel öğeler ve denetim modelleri tarafından sağlanan koleksiyonu desteği kasıtlı olarak değil kullanıldığı durumlarda XAML sözdiziminde genel dizi oluşturmayı destekler. Daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../docs/framework/xaml-services/x-array-markup-extension.md). XAML 2009 dil temelleri yerine bir uzantısı olarak diziler özellikle erişilir. Daha fazla bilgi için bkz: [XAML 2009 dil özellikleri](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` XAML 2009, uzantı özgün (2006) dil kümesinin parçasıdır. `x:Reference` başka bir var olan bir nesne grafiğinin nesneye bir başvurusu temsil eder. Bu nesne tarafından tanımlanan kendi `x:Name`. Daha fazla bilgi için bkz: [x: Reference işaretleme uzantısı](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Diğer x: yapıları  
 Diğer `x:` XAML dil özellikleri desteklemek için yapıları var, ancak bunlar işaretleme uzantıları uygulanmadı. Daha fazla bilgi için bkz: [XAML Namespace (x:) Dil özellikleri](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>MarkupExtension taban sınıfı  
 XAML okuyucuları ve XAML yazıcılarının System.Xaml içinde varsayılan uygulamaları ile etkileşim kurabilen bir özel biçimlendirme uzantısı tanımlamak için bir sınıf Özet türetin <xref:System.Windows.Markup.MarkupExtension> sınıfı. Sınıf olan geçersiz kılmak için bir yöntem olduğunu <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Biçimlendirme uzantısı kullanımı bağımsız değişkenleri desteklemek için ek oluşturucuları tanımlama gerekebilir ve eşleşen ayarlanabilir özellikleri.  
  
 Aracılığıyla <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, özel biçimlendirme uzantısı burada biçimlendirme uzantısı gerçekte çağrılır XAML işlemcisi tarafından ortamı raporları bir hizmet bağlamı erişebilir. Genellikle bu yükleme yolunda olduğundan bir <xref:System.Xaml.XamlObjectWriter>. Kaydetme yolu bu genellikle bir <xref:System.Xaml.XamlXmlWriter>. Her bir hizmet sağlayıcısı deseni uygulayan bir iç XAML hizmet sağlayıcısı bağlamı sınıf Hizmet bağlamı rapor. Kullanılabilir hizmetler ve neyi temsil ettiği hakkında daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Biçimlendirme uzantısı sınıfı genel erişim düzeyini kullanması gerekir; XAML işlemcileri her zaman hizmetlerini kullanmak için işaretleme uzantının destek sınıfının örneği kurabilmesi gerekir.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için destek türü tanımlama  
 .NET Framework XAML Hizmetlerinde veya .NET Framework XAML hizmetlerinde yapı çerçeveleri kullandığınızda, nasıl biçimlendirme uzantısı destek türü adı iki seçeneğiniz vardır. Tür adı nasıl XAML nesne yazıcılarının erişmek ve biçimlendirme uzantısı kullanımı XAML'de karşılaştığınızda biçimlendirme uzantısı destek türü çağırma girişimi için geçerlidir. Aşağıdaki adlandırma stratejiler birini kullanın:  
  
-   XAML biçimlendirme kullanım belirtecine tam bir eşleşme olarak türü adı. Örneğin, desteklemek için bir `{Collate ...}` uzantı kullanımını adı destek türü `Collate`.  
  
-   Kullanım dize belirteci artı soneki olmasını türü adı `Extension`. Örneğin, desteklemek için bir `{Collate ...}` uzantı kullanımını adı destek türü `CollateExtension`.  
  
 Arama aranacak sırasıdır `Extension`-sonekine sınıfı adı ve sınıf adı arayın `Extension` soneki.  
  
 Biçimlendirme kullanım açısından dahil olmak üzere `Extension` soneki kullanım parçası geçerli olduğu gibi. Ancak, bu davranış gibi `Extension` gerçekten sınıf adı bir parçasıdır ve XAML nesne yazıcılarının destek sınıfı yok, bu kullanım için bir biçimlendirme uzantısı destek sınıf çözümlemek başarısız olurdu `Extension` soneki.  
  
### <a name="the-default-constructor"></a>Varsayılan Oluşturucu  
 Tüm biçimlendirme uzantısı için türlerini destekleyen, ortak varsayılan bir oluşturucu maruz bırakmamalısınız. Varsayılan bir oluşturucu olduğu bir nesne öğesi kullanımdan biçimlendirme uzantısı XAML nesne yazıcısı başlatır çalışması için gereklidir. Nesne öğesi kullanımı destekleyen, özellikle Serileştirmenin biçimlendirme uzantısı için eşit bir beklenir. Ancak, yalnızca biçimlendirme uzantısı özniteliği kullanımları desteklemek istiyorsanız, bir ortak oluşturucu olmadan biçimlendirme uzantısı uygulayabilirsiniz.  
  
 Biçimlendirme uzantısı kullanımı bağımsız değişkenler varsa, varsayılan oluşturucu kullanımını desteklemek için gereklidir.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Oluşturucu desenler ve özel biçimlendirme uzantısı konumsal bağımsız değişkenler  
 Hedeflenen bağımsız değişken kullanım ile işaretleme uzantısı için ortak oluşturucu hedeflenen kullanım moduna karşılık gelmelidir. Diğer bir deyişle, biçimlendirme uzantısı konumsal bağımsız değişken olarak geçerli kullanım gerektirecek şekilde tasarlanmıştır, bir ortak oluşturucu konumsal bağımsız değişken bir giriş parametresi desteklemelidir.  
  
 Örneğin, varsayalım `Collate` biçimlendirme uzantısı yalnızca bir modu desteklemek üzere tasarlanmıştır söz konusu olduğunda, modunu temsil eden bir konumsal bağımsız değişkeni olarak belirtilen bir `CollationMode` numaralandırma sabiti. Bu durumda, bir oluşturucu şu biçimde olmalıdır:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 İşaretleme 's öznitelik değerlerinden iletildiği temel düzeyde, biçimlendirme uzantısı için geçirilen bağımsız değişken bir dize olduklarından. Tüm bağımsız değişkenler dizelerini yapın ve düzeyde giriş ile çalışır. Ancak, biçimlendirme uzantısı bağımsız değişkenler için destek sınıfı geçirilmeden önce oluşan belirli işleme erişimi.  
  
 İşaretleme uzantısı oluşturulacak bir nesne ise işleme kavramsal olarak çalışır ve ardından, üye değerlerinin ayarlayın. Ayarlamak için belirtilen her özellik benzer XAML ayrıştırıldığında belirtilen üyenin oluşturulan bir nesne üzerinde ayarlanamaz nasıl değerlendirilir. İki önemli farklılıklar vardır:  
  
-   Daha önce belirtildiği gibi bir biçimlendirme uzantısı destek türü XAML'de örneğinin oluşturulması için varsayılan bir oluşturucu olması gerekmez. Nesne oluşturması olası değişkenlerinin metin sözdiziminde simgeleştirilmiş ve konumsal veya adlandırılmış bağımsız değişkenler olarak değerlendirilir ve uygun oluşturucuyu o anda adlı kadar ertelenir.  
  
-   Biçimlendirme uzantıları kullanımları iç içe. En içteki biçimlendirme uzantısı ilk olarak değerlendirilir. Bu nedenle, bu tür bir kullanım varsayar ve oluşturmak için bir değer dönüştürücüsü (örneğin, bir işaretleme uzantısı) gerektiren bir tür olması için yapım parametrelerden biri bildirin.  
  
 Bu işlem bir bağımlılık önceki örnekte gösterildi. .NET Framework XAML Hizmetleri XAML nesne yazıcısı numaralandırma sabit adları yerel düzeyde Enum değerlerinden işler.  
  
 Metin söz dizimi biçimlendirme uzantısı konumsal parametresinin işleme yapım değişkeninde türüyle ilişkili tür dönüştürücüsünü üzerinde de güvenebilirsiniz.  
  
 İçinde kullanım belirteçlerinde karşılaştı sipariş atanmış olan oluşturucu parametresini konumsal siparişe karşılık olmadığından bağımsız değişkenler konumsal bağımsız olarak adlandırılır. Örneğin, aşağıdaki Oluşturucusu imzası göz önünde bulundurun:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 XAML işlemci bu biçimlendirme uzantısı için iki konuma göre bağımsız değişken bekler. Bir kullanım olduysa `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` belirteci ilk parametre olarak gönderilen ve olarak hesaplanan bir `CollationMode` sabiti adlı numaralandırması. İç sonucunu `x:Reference` ikinci parametresi gönderilen ve bir nesne olarak değerlendirilir.  
  
 XAML biçimlendirme uzantısı sözdizimi ve işleme, virgülle ayrılmış için belirtilen kuralları olup bağımsız değişkenler, bölücüyü konumsal bağımsız değişken veya adlandırılmış bağımsız değişkenler bu bağımsız değişkenler.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Konumsal bağımsız değişken yinelenen kapsamalıdır  
 XAML nesne yazıcısı biçimlendirme uzantısı kullanımı konumsal bağımsız değişkenler ile karşılaştığında, ve bu sayıda bağımsız değişken (yinelenen bir parametre sayısı) ele birden çok oluşturucu bağımsız değişkenleri varsa, mutlaka bir hata değildir. Davranış bir özelleştirilebilir XAML şema içeriği ayarlarına bağlıdır <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Varsa <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> olan `true`, XAML nesne yazıcısı bir özel durum yalnızca nedenlerle yinelenen parametre oluşturmamalıdır. Bu noktadan ötesinde davranışı kesinlikle tanımlı değil. Temel tasarım şema bağlamı türü bilgileri belirli parametreleri için kullanılabilir olan ve imza görmek için yinelenen bir aday eşleşen girişimi açık atamaları en iyi eşleşmeyi olabilir varsayılır. İmza yok XAML nesne yazıcısı üzerinde çalışan bu belirli şema bağlam tarafından uygulanan testleri geçerse bir özel hala durum.  
  
 Varsayılan olarak, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> olan `false` CLR tabanlı <xref:System.Xaml.XamlSchemaContext> .NET Framework XAML Hizmetleri için. Bu nedenle, varsayılan <xref:System.Xaml.XamlObjectWriter> biçimlendirme uzantısı kullanımı karşılaşırsa özel durumları oluşturur yedekleme tür kurucularda yinelenen parametre olduğu.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Adlandırılmış bağımsız değişkenler için özel biçimlendirme uzantısı  
 Biçimlendirme uzantıları XAML belirtildiği gibi kullanım için bir adlandırılmış bağımsız değişkenler form de kullanabilirsiniz. Simgeleştirme ilk düzeyinde metin sözdizimini bağımsız değişkenleriyle ayrılmıştır. İçinde herhangi bir bağımsız değişken bir eşittir işareti (=) varlığını bağımsız değişken adlandırılmış bir bağımsız değişken olarak tanımlar. Bu tür bir bağımsız değişken ayrıca bir ad/değer çifti simgeleştirilmiş. Adı bu durumda biçimlendirme uzantının destek türünde ortak bir ayarlanabilir özellik adları. Adlandırılmış bağımsız değişkeni kullanımını desteklemek istiyorsanız, bu ortak ayarlanabilir özellikleri sağlamalıdır. Ortak kaldığı sürece özellikleri devralınan özellikler olabilir.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Hizmet sağlayıcısı bağlamı bir biçimlendirme uzantısı uygulamasından erişme  
 Kullanılabilir hizmetler hiçbir değer Dönüştürücüsü için aynıdır. Nasıl her değer dönüştürücüsü alan hizmet bağlamı farktır. Hizmetlerine erişimi ve kullanılabilir hizmetler konusunda belgelenmiştir [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Özellik öğesi kullanımı biçimlendirme uzantısı  
 Biçimlendirme uzantısı kullanımlar için senaryolar, genellikle öznitelik kullanımda biçimlendirme uzantısı kullanarak geçici tasarlanmıştır. Ancak, aynı zamanda özellik öğesi kullanımı desteklemek için yedekleme sınıfı tanımlamak büyük olasılıkla mümkündür.  
  
 Özellik öğesi biçimlendirme uzantısı kullanımını desteklemek için ortak varsayılan bir oluşturucu tanımlayın. Bu örnek oluşturucu statik bir oluşturucusu olmalıdır. XAML işlemci genellikle varsayılan kurucu biçimlendirmeden işler herhangi bir nesne öğesi üzerinde çağırmanız gerekir çünkü bu gereklidir ve bu nesne öğeleri olarak işaretleme uzantısı sınıfları içerir. Gelişmiş senaryolar için sınıflar için varsayılan olmayan yapım yolları tanımlayabilirsiniz. (Daha fazla bilgi için bkz: [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md).) Ancak, bu kullanım deseni bulma çok daha zor tasarımcıları hem kullanıcılar ham biçimlendirme yaptığından bu desenleri biçimlendirme uzantısı amacıyla kullanmamalısınız.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için öznitelik atanıyor  
 Tasarım ortamları ve belirli XAML nesne yazan senaryoları desteklemek için bir biçimlendirme uzantısı destek türü ile birkaç CLR öznitelikleri öznitelik. Bu öznitelikler hedeflenen biçimlendirme uzantısı kullanımı bildirin.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> raporları <xref:System.Type> nesne için bilgileri yazın <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürür. Saf imzası tarafından <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürür <xref:System.Object>. Ancak, çeşitli tüketicileri daha kesin dönüş türü bilgileri isteyebilirsiniz. Şunları içerir:  
  
-   Tasarımcılar ve türünü algılayan sağlayabilir olabilir IDE, için biçimlendirme uzantısı kullanımları destekler.  
  
-   Uygulamaları Gelişmiş `SetMarkupExtension` üzerinde belirli bilinen dallanma yerine bir işaretleme uzantının dönüş türü belirlemek için yansıma Bel hedef sınıfları işleyicileri <xref:System.Windows.Markup.MarkupExtension> ada göre uygulamaları.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Biçimlendirme uzantısı kullanımlarından seri hale getirme  
 Biçimlendirme uzantısı kullanımı ve çağrıları XAML nesne yazıcısı işlediğinde <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, XAML düğümü akışı ancak nesne grafiği, daha önce bir biçimlendirme uzantısı kullanımı olan bağlamının devam ettirir. Nesne grafiğinde yalnızca değeri korunur. Tasarım senaryoları veya özgün biçimlendirme uzantısı kullanımı serileştirilmiş çıkış sürdürmek için başka bir nedenle varsa, yükleme yolu XAML düğüm akış biçimlendirme uzantısı kullanımları izlemek için kendi altyapınızı tasarlamanız gerekir. Yükleme yolu düğüm akış öğelerini yeniden oluşturun ve bunları XAML yazıcılarının Kaydet Serileştirmenin için oynatmak için davranış uygulayabilirsiniz düğüm akış uygun konum değeri için değiştirerek, yol.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğümü akışı biçimlendirme uzantıları  
 Yükleme yolu olan bir XAML düğüm akış çalışıyorsanız, biçimlendirme uzantısı kullanımı düğüm akışında bir nesne olarak görünür.  
  
 Biçimlendirme uzantısı kullanımı konumsal bağımsız değişkenleri kullanıyorsa, bir başlatma değeri olan bir başlangıç nesnesi olarak temsil edilir. Kaba metin gösterimi olarak düğümü akışı aşağıdakine benzer:  
  
 `StartObject` (<xref:System.Xaml.XamlType> biçimlendirme uzantının tanım türü, kendi dönüş türü olan)  
  
 `StartMember` (adını <xref:System.Xaml.XamlMember> olan `_InitializationText`)  
  
 `Value` (konumsal bağımsız değişkenleri müdahalede bulunan sınırlayıcıları dahil olmak üzere bir dize olarak değerdir)  
  
 `EndMember`  
  
 `EndObject`  
  
 Biçimlendirme uzantısı kullanımı adlandırılmış bağımsız değişkenler ile temsil edilen üyeleriyle ilgili adları olan bir nesne olarak her metin dizesi değerleri ile ayarlanır.  
  
 Gerçekte çağırma `ProvideValue` biçimlendirme uzantısı uyarlamasını türü eşlemesi gerektirdiği için XAML şema içeriği gerektirir ve bir işaretleme uzantısı destek türü örneği oluşturma. Neden bu yolla varsayılan .NET Framework XAML hizmetlerinde düğümü akışları biçimlendirme uzantısı kullanımları korunur - genellikle bir yükleme yolu okuyucu parçası gerekli XAML şema içeriği kullanılabilir olmayan bir neden de budur.  
  
 Kaydetme işleminde bir XAML düğüm akış ile çalışıyorsanız, yol genellikle bir şey yok serileştirilecek nesnenin biçimlendirme uzantısı kullanımı tarafından başlangıçta sağlandı bilgilendirebilir bir nesne grafik gösterimi bulunan ve bir `ProvideValue` sonucu. Nesne grafiği diğer değişiklikler de yakalama biçimlendirme uzantısı kullanımı orijinal bilgi koruma için kendi teknikleri insanlara gerekir sırada gidiş için işaretleme uzantısı kullanımları kalıcı hale getirmek için gereken senaryoları XAML girin. Örneğin, biçimlendirme uzantısı kullanımları geri yüklemek için düğümü akışı Kaydet çalışmanız gerekebilir biçimlendirme uzantısı kullanımları geri ya da birleştirme özgün XAML arasındaki gidiş dönüş XAML tür gerçekleştirmek amacıyla yolu. WPF gibi bazı XAML uygulama çerçeveleri Ara türleri (ifadeler) biçimlendirme uzantısı kullanımları değerleri nerede sağlanan durumları temsil yardımcı olması için kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Markup.MarkupExtension>  
 [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
