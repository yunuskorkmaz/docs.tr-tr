---
title: XAML Biçimlendirme Uzantılarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 41fe3cb368bed12ccb2dbe9bd31f95fd556e3968
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224929"
---
# <a name="markup-extensions-for-xaml-overview"></a>XAML Biçimlendirme Uzantılarına Genel Bakış
Biçimlendirme uzantıları, basit bir tür ya da özel bir XAML türü bir değer almak için bir XAML tekniğidir. Öznitelik kullanımı için biçimlendirme uzantıları açılış kaşlı ayracından bilinen karakter dizisini kullanın. `{` işaretleme uzantısı kapsamı ve bir kapanış küme ayracını girmek için `}` çıkmak için. .NET Framework XAML hizmetlerinde kullanırken bazı System.Xaml derlemesinden önceden tanımlanmış XAML dil biçimlendirme uzantıları kullanabilirsiniz. Alt sınıfı ayrıca <xref:System.Windows.Markup.MarkupExtension> sınıfı System.Xaml içinde tanımlanan ve kendi biçimlendirme uzantılarını tanımlayın. Veya zaten bu çerçeve başvurduğunuz, belirli bir framework tarafından tanımlanan biçimlendirme uzantıları kullanabilirsiniz.  
  
 Biçimlendirme uzantısı kullanımı erişildiğinde XAML nesne yazan bir özel hizmet sunabilir <xref:System.Windows.Markup.MarkupExtension> sınıfı aracılığıyla bir hizmet bağlantı noktası <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> geçersiz kılar. Hizmetlerin kullanımıyla ilgili bağlam, nesne yazıcısı, XAML şema içeriği ve benzeri belirli özelliklerini almak için kullanılabilir.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML tanımlı biçimlendirme uzantıları  
 Çeşitli biçimlendirme uzantıları, XAML dil desteği için .NET Framework XAML hizmetlerinde tarafından uygulanır. Bu işaretleme uzantıları XAML belirtimi dili olarak bölümlerini karşılık gelir. Bunlar genellikle adlarıyla `x:` sözdiziminde ortak kullanım görüldüğü gibi önek. Tüm türetilen bu XAML dil öğeleri için .NET Framework XAML hizmetlerinde uygulamaları <xref:System.Windows.Markup.MarkupExtension> temel sınıfı.  
  
> [!NOTE]
>  `x:` Tipik XAML ad alanı eşlemesi XAML dil ad alanı bir XAML üretim kök öğesi için kullanılan önek. Örneğin, çeşitli belirli çerçeveler için Visual Studio projeyi ve sayfa şablonları kullanan bir XAML dosyası başlatmak `x:` eşleme. Kendi XAML ad alanı eşlemesi, farklı ön ek belirteç seçebilir, ancak bu belgeleri varsayılan kabul edecek `x:` başlangıcı yerine sonundan XAML dil XAML ad alanı, tanımlanmış bir parçası olan bu varlıklar tanımlayan bir yol olarak eşleme bir belirli framework'ün varsayılan XAML ad alanı veya diğer rastgele CLR veya XML ad alanı.  
  
### <a name="xtype"></a>x: Type  
 `x:Type` Kaynakları <xref:System.Type> adlandırılmış bir türün nesnesi. Bu işlev, temel alınan CLR türü kullanan ve bir gruplandırma bilinen adı veya tanımlayıcısı olarak türetme türü erteleme mekanizmaları en sık kullanılıyor. WPF stilleri ve şablonları ve bunların kullanımını `TargetType` özelliklerdir, belirli bir örneği. Daha fazla bilgi için [x: Type işaretleme uzantısı](x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` doğrudan bir özelliğin değerinin türü değildir, ancak bu türe hesaplanan değer türü kodu varlıkları statik değerlerini üretir. Bu, bir tür tanımı iyi bilinen sabitleri olarak zaten mevcut değerleri belirtmek için kullanışlıdır. Daha fazla bilgi için [x: Static işaretleme uzantısı](x-static-markup-extension.md).  
  
### <a name="xnull"></a>x:Null  
 `x:Null` Belirtir `null` XAML üyesi için bir değer olarak. Belirli türlerini ya da daha büyük framework kavramlarını tasarımına `null` her zaman bir özellik için varsayılan değer veya zımni bir boş dize özniteliğinin değerini değil. Daha fazla bilgi için [x: Null işaretleme uzantısı](x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` XAML söz dizimi temel öğeleri ve denetim modelleri tarafından sağlanan koleksiyon desteğiyle kasıtlı olarak değil kullanıldığı durumlarda genel diziler oluşturulmasını destekler. Daha fazla bilgi için [x: Array işaretleme uzantısı](x-array-markup-extension.md). XAML 2009 dil temelleri yerine bir uzantısı olarak diziler özellikle erişilir. Daha fazla bilgi için [XAML 2009 dil özellikleri](xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` XAML 2009, uzantı özgün (2006) dil kümesinin parçasıdır. `x:Reference` başka bir var olan bir nesne grafiğinin nesnesinde bir başvuruyu temsil eder. Bu nesne tarafından tanımlanan kendi `x:Name`. Daha fazla bilgi için [x: Reference işaretleme uzantısı](x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Diğer x: Yapıları  
 Diğer `x:` yapıları, XAML dili özelliklerini desteklemek için mevcut, ancak bunlar biçimlendirme uzantıları uygulanmadı. Daha fazla bilgi için [XAML Namespace (x:) Dil özellikleri](xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>MarkupExtension temel sınıfı  
 XAML okuyucular ve XAML yazıcılarının System.Xaml varsayılan uygulamaları ile etkileşime özel biçimlendirme uzantısı tanımlamak için bir sınıf soyut türetilen <xref:System.Windows.Markup.MarkupExtension> sınıfı. Sınıfı, geçersiz kılmak için bir yöntem olduğunu <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Bağımsız değişken biçimlendirme uzantısı kullanımı desteklemek için ek yapıcıları tanımlayın gerekebilir ve ayarlanabilir özelliklerin eşleştirme.  
  
 Aracılığıyla <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, özel biçimlendirme uzantısı raporları nereye işaretleme uzantısı gerçekten çağrıldığında bir XAML işlemcisi tarafından ortam bir hizmet bağlamı erişebilir. Yükleme yolu bu genellikle, bir <xref:System.Xaml.XamlObjectWriter>. Kaydetme yolu Bu, genellikle bir <xref:System.Xaml.XamlXmlWriter>. Rapor her bir hizmet sağlayıcısı deseni uygulayan bir iç XAML hizmet sağlayıcısı bağlamı sınıf olarak hizmet bağlamı. Kullanılabilir hizmetleri ve neyi gösterdikleri hakkında daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Genel erişim düzeyi, işaretleme uzantısı sınıfı kullanmanız gerekir; XAML işlemci her zaman hizmetlerini kullanmak için işaretleme uzantının destek sınıfının örneği mümkün olması gerekir.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Destek türü için özel biçimlendirme uzantısı tanımlama  
 .NET Framework XAML Hizmetlerinde veya .NET Framework XAML hizmetlerinde yapı çerçeveleri kullandığınızda, biçimlendirme uzantısı destek türü adını öğrenmek için iki seçeneğiniz vardır. Tür adı, erişim ve bunların XAML, biçimlendirme uzantısı kullanımı karşılaştığınızda bir işaretleme uzantısı destek türü çağırmak nasıl XAML nesne yazıcılar girişiminde uygundur. Adlandırma aşağıdaki stratejilerden birini kullanın:  
  
-   XAML işaretleme kullanım belirtecine tam bir eşleşme olması için tür adı. Örneğin, destek için bir `{Collate ...}` uzantısı kullanımı, destek türü adı `Collate`.  
  
-   Kullanım dize belirteci ve son olarak türü adı `Extension`. Örneğin, destek için bir `{Collate ...}` uzantısı kullanımı, destek türü adı `CollateExtension`.  
  
 Aramak için arama sırası olduğundan `Extension`-sonekli sınıf adı ve sınıf adı bulun `Extension` soneki.  
  
 Biçimlendirme kullanım açısından da dahil olmak üzere `Extension` kullanım parçası geçerli olduğu soneki. Ancak, bu davranış gibi `Extension` sınıf adı gerçek anlamda parçasıdır ve XAML nesne yazıcılar destek sınıfı yok, bu kullanım için bir işaretleme uzantısı desteği sınıfı çözümlemek başarısız olurdu `Extension` soneki.  
  
### <a name="the-default-constructor"></a>Varsayılan Oluşturucu  
 Türleri tüm işaretleme uzantısı için destek, genel bir varsayılan oluşturucu sunmalıdır. Burada bir nesne öğesi kullanımı biçimlendirme uzantısından XAML nesne yazıcısı başlatır herhangi bir durumu için varsayılan bir oluşturucu gereklidir. Nesne öğesi kullanımı destekleyen, seri hale getirme için özellikle bir işaretleme uzantısı için adil bir beklenir. Ancak yalnızca işaretleme uzantısı özniteliği kullanımları desteklemek istiyorsanız, bir işaretleme uzantısı Genel oluşturucu olmadan uygulayabilirsiniz.  
  
 Biçimlendirme uzantısı kullanımı, hiçbir bağımsız değişken varsa, varsayılan oluşturucu kullanım desteklemek için gereklidir.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Oluşturucu desenler ve özel biçimlendirme uzantısı için konumsal bağımsız değişkenler  
 Hedeflenen bağımsız değişkeni kullanımı ile bir işaretleme uzantısı için genel oluşturucular hedeflenen kullanım moduna karşılık gelmelidir. Diğer bir deyişle, işaretleme uzantısı konumsal bağımsız değişken olarak geçerli kullanım gerektirecek şekilde tasarlanmışsa, konumsal bağımsız değişkenini alan bir giriş parametresi içeren bir genel oluşturucuya desteklemelidir.  
  
 Örneğin, varsayalım `Collate` işaretleme uzantısı yalnızca bir modu desteklemek için tasarlanmıştır, modunu temsil eden bir konumsal bağımsız değişken olduğunda, belirtilen bir `CollationMode` numaralandırma sabiti. Bu durumda, bir oluşturucuyla aşağıdaki biçimde olmalıdır:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 İşaretleme ait öznitelik değerleri iletildiği çünkü temel düzeyde, bir dize bir işaretleme uzantısı için geçirilen bağımsız değişkenler. Tüm bağımsız değişkenler dizelerinizi ve o seviyede giriş ile çalışır. Ancak, biçimlendirme uzantısı bağımsız değişkenler için destek sınıfı geçirilmeden önce gerçekleşen belirli bir işleme erişimi.  
  
 İşaretleme uzantısı oluşturulacak bir nesne ise gibi işleme kavramsal olarak çalışır ve ardından, bu üye değerlerinin ayarlanır. Ayarlamak için her belirtilen özellik benzer XAML ayrıştırıldığında, belirtilen üyenin üzerinde oluşturulan bir nesneye nasıl ayarlanabilir şekilde değerlendirilir. İki önemli farklar vardır:  
  
-   Daha önce belirtildiği gibi bir işaretleme uzantısı destek türü XAML içinde örneği için varsayılan bir oluşturucusu olması gerekmez. Kendi nesne oluşturmayı mümkün bağımsız değişkenlerinden biri içinde metin sözdiziminde simgeleştirilmiş ve konumsal veya adlandırılmış bağımsız değişkenler değerlendirilen ve o anda uygun Oluşturucu çağrılır kadar ertelenir.  
  
-   İşaretleme uzantıları kullanımları yuvalanabilir. En içteki işaretleme uzantısı, ilk olarak değerlendirilir. Bu nedenle, böyle bir kullanım varsayılır ve yapı parametrelerden biri üretmek için bir değer dönüştürücü (örneğin, bir işaretleme uzantısı) gerektiren bir türü bildirin.  
  
 Önceki örnekte gösterildiği gibi işleme güvenme. .NET Framework XAML Hizmetleri XAML nesne yazıcısı numaralandırma sabit adları yerel düzeyde listelenmiş değerler olarak işler.  
  
 Metin sözdiziminin bir işaretleme uzantısı konumsal parametrenin işleme yapım bağımsız değişken türü ile ilişkili olan bir tür dönüştürücüsü üzerinde de güvenebilirsiniz.  
  
 Kullanım belirteçlerinde karşılaşıldığında sırasını konumsal sırasını atanmış olan oluşturucu parametresi için karşılık gelen için bağımsız değişkenler konumsal bağımsız değişkenler olarak adlandırılır. Örneğin, aşağıdaki Oluşturucu imzası göz önünde bulundurun:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 XAML işlemci bu işaretleme uzantısının iki konumsal bağımsız değişken bekliyor. Bir kullanım olduysa `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` belirteci ilk parametre olarak gönderilen ve olarak değerlendirilen bir `CollationMode` sabiti adlı sabit listesi. İç sonucunu `x:Reference` ikinci parametresi gönderilen ve nesneyi değerlendirilir.  
  
 XAML içinde belirtilen kuralları için biçimlendirme uzantısı sözdizimi ve işleme, virgülle ayrılmış olup bağımsız bölücüyü konumsal bağımsız değişkenler veya adlandırılmış bağımsız değişkenler bu bağımsız değişkenler.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Konumsal bağımsız değişkenlere yinelenen parametre sayısı  
 XAML nesne yazıcısı konumsal bağımsız değişken biçimlendirme uzantısı kullanımı karşılaşır ve söz konusu sayıda bağımsız değişken (Yinelenen parametre) birden çok oluşturucu bağımsız değişkeni vardır, bu mutlaka bir hata değil. Davranışı bir özelleştirilebilir XAML şema içeriği ayarlarına bağlıdır <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Varsa <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> olduğu `true`, XAML nesne yazıcısı yinelenen parametre, yalnızca nedenleriyle bir özel durum oluşturmamalıdır. Bu noktanın ötesinde davranışı kesin olarak tanımlanmamış. Temel tasarım şema içeriği türü bilgilerini belirli parametreler için kullanılabilir olan ve yinelenen adayları imza görmek için eşleşen girişimi açık yayınları en iyi eşleşmeyi olabilir varsayılır. İmza yok XAML nesne yazıcısı üzerinde çalışan, belirli bir şema içeriği tarafından uygulanan tüm testleri geçerse bir özel durum yine de durum.  
  
 Varsayılan olarak, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> olduğu `false` CLR tabanlı <xref:System.Xaml.XamlSchemaContext> .NET Framework XAML hizmetlerinde için. Bu nedenle, varsayılan <xref:System.Xaml.XamlObjectWriter> biçimlendirme uzantısı kullanımı karşılaşırsa, istisnalar fırlatıyorsa yedekleme türün oluşturucularda yinelenen parametre olduğu.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Adlandırılmış bağımsız değişkenler için özel biçimlendirme uzantısı  
 Biçimlendirme uzantıları XAML belirtildiği gibi adlandırılmış bağımsız değişkenler form kullanımı için de kullanabilirsiniz. Simgeleştirme ilk düzeyinde metin sözdizimi bağımsız değişkenleriyle ayrılmıştır. Herhangi bir bağımsız değişkeni içinde eşittir işareti (=) varlığını adlandırılmış bağımsız değişken olarak bir bağımsız değişken tanımlar. Böyle bir bağımsız değişken, bir ad/değer çifti de simgeleştirilmiş. Ad, bu durumda biçimlendirme uzantının destek türünün ortak bir ayarlanabilir özelliği adları. Adlandırılmış bağımsız değişken kullanımını desteklemek istiyorsanız, bu genel ayarlanabilir özelliklerin sağlamanız gerekir. Bunlar genel kaldığı sürece özelliklerini devralınan özellikler olabilir.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Hizmet sağlayıcısı bağlamı bir işaretleme uzantısı uygulamasından erişme  
 Kullanılabilen hizmetler, herhangi bir değer dönüştürücü için aynıdır. Nasıl her değer dönüştürücü alan hizmet bağlamı farktır. Hizmetlerine erişimi ve hizmetler konusunda belgelenir [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Özellik öğesi kullanımı bir işaretleme uzantısı  
 Biçimlendirme uzantısı kullanımı için senaryoları, genellikle öznitelik kullanımında da işaretleme uzantısı kullanarak geçici olarak tasarlanmıştır. Ancak, aynı zamanda özellik öğesi kullanımı desteklemek için yedekleme sınıfını tanımlamak potansiyel olarak mümkündür.  
  
 Özellik öğesi kullanımı, biçimlendirme uzantısı desteklemek için genel varsayılan oluşturucu tanımlayın. Bu, bir statik Oluşturucu örnek oluşturucusu olmalıdır. Bu gereklidir çünkü bir XAML işlemci genellikle biçimlendirmeden işler herhangi bir nesne öğe varsayılan oluşturucu çağırmanız gerekir ve bu nesne öğesi olarak işaretleme uzantısı sınıfları içerir. Gelişmiş senaryolar için sınıflar için varsayılan olmayan oluşturma yolları tanımlayabilirsiniz. (Daha fazla bilgi için [x: FactoryMethod yönergesi](x-factorymethod-directive.md).) Ancak, bu kullanım deseninin bulma çok daha zor hem tasarımcıları ve kullanıcılar ham biçimlendirme sağlar çünkü bu desenleri işaretleme uzantısı amacıyla kullanmamalısınız.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Özel biçimlendirme uzantısı için öznitelik atanıyor  
 Tasarım ortamları hem belirli XAML nesne yazıcı senaryoları desteklemek için bir işaretleme uzantısı destek türü ile birden çok CLR öznitelikleri özniteliği. Bu öznitelikler, hedeflenen biçimlendirme uzantısı kullanımı bildirin.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> raporları <xref:System.Type> nesne için bilgi türü <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürür. Saf imzası tarafından <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> döndürür <xref:System.Object>. Ancak, çeşitli tüketicileri daha kesin bir dönüş türü bilgi isteyebilirsiniz. Şunları içerir:  
  
-   Tasarımcılar ve türünü algılayan sağlamak mümkün olabilir IDE'ler, biçimlendirme uzantısı kullanımı için destek.  
  
-   Uygulamaları Gelişmiş `SetMarkupExtension` üzerinde belirli bilinen dallanma yerine, dönüş türü bir işaretleme uzantının belirlemek için yansıma dayanan hedef sınıflarını işleyicileri <xref:System.Windows.Markup.MarkupExtension> ada göre uygulamaları.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Biçimlendirme uzantısı kullanımı serileştirilmesi  
 Biçimlendirme uzantısı kullanımı ve aramalar XAML nesne yazıcısı işlediğinde <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, XAML düğüm akış ancak nesne grafiği, daha önce bir biçimlendirme uzantısı kullanımı olan bağlamı sürdürür. Nesne grafiğinde, yalnızca değeri korunur. Tasarım senaryoları veya diğer nedenlerle serileştirilmiş çıkış özgün biçimlendirme uzantısı kullanımı kalıcı hale getirmeniz için varsa, yük yolu XAML düğüm akış biçimlendirme uzantısı kullanımı izlemek için kendi altyapınızı tasarlamanız gerekir. Yükleme yolu düğümü akıştan öğelerini yeniden oluşturun ve bunları XAML yazıcılar Kaydet Serileştirmenin kayıttan yürütme için davranış uygulayabilirsiniz değeri uygun düğümü akışı konumunu değiştirme yolu.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğümü Stream biçimlendirme uzantıları  
 Yükleme yolunda bir XAML düğümü akışı ile çalışıyorsanız, biçimlendirme uzantısı kullanımı düğüm akışında bir nesne olarak görünür.  
  
 Biçimlendirme uzantısı kullanımı konumsal bağımsız değişkenlere kullanıyorsa, bir başlatma değeri olan bir başlangıç nesnesi olarak temsil edilir. Bir kaba metin temsili düğümü akışı aşağıdakine benzer:  
  
 `StartObject` (<xref:System.Xaml.XamlType> biçimlendirme uzantının tanım türü, kendi dönüş türü olan)  
  
 `StartMember` (adı <xref:System.Xaml.XamlMember> olan `_InitializationText`)  
  
 `Value` (konumsal bağımsız değişkenler müdahalede bulunan sınırlayıcıları dahil olmak üzere bir dize olarak değerdir)  
  
 `EndMember`  
  
 `EndObject`  
  
 Biçimlendirme uzantısı kullanımı adlandırılmış bağımsız değişkenler ile temsil edilen üyelerle ilgili adların bir nesne olarak, her ayarla metin dizesi değerleri ile.  
  
 Aslında çağırma `ProvideValue` bir işaretleme uzantısı uygulaması tür eşlemesi gerektirdiği için XAML şema içeriği gerektirir ve bir işaretleme uzantısı destek türü örneği oluşturma. Neden bu yolla varsayılan .NET Framework XAML hizmetlerinde düğümü akışları biçimlendirme uzantısı kullanımı korunur - okuyucu yolun bir bölümünü Yük genellikle gerekli XAML şema içeriği kullanılabilir olmayan bir nedeni budur.  
  
 XAML düğümü akışı ile kaydetme üzerinde çalışıyorsanız yolu, genellikle bir şey yok seri hale getirilecek nesne biçimlendirme uzantısı kullanımı tarafından başlangıçta sağlanan konusunda bilgilendiren bir nesne grafiği gösterimi mevcut ve bir `ProvideValue` sonucu. Ayrıca diğer değişiklikler Nesne grafiği yakalama orijinal biçimlendirme uzantısı kullanımı bilgisi koruma için kendi teknikleri bulmanız gerekir ancak gidiş dönüşü için işaretleme uzantısı kullanımları kalıcı hale getirmek için gereken senaryolarda XAML girin. Örneğin, biçimlendirme uzantısı kullanımı geri yüklemek için Kaydet düğümü akışı ile çalışmak ihtiyacınız biçimlendirme uzantısı kullanımı geri yükleyin veya birleştirme özgün XAML gidiş dönüşlü XAML arasındaki herhangi bir türde gerçekleştirmek için yol. Bazı WPF XAML uygulama çerçevelerini Ara türler (ifadeler) burada biçimlendirme uzantısı kullanımı değerleri sağlanan durumları temsil etmek için kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
