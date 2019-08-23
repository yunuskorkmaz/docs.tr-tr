---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: a94f1f358a2d0fbfd489ac3d34375b6f883dd4fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965451"
---
# <a name="type-converters-for-xaml-overview"></a>XAML Tür Dönüştürücülerine Genel Bakış
Tür dönüştürücüler, XAML biçimlendirme içindeki bir dizeden bir nesne grafiğinde belirli nesnelere dönüştüren bir nesne yazıcı için arz mantığı sağlar. .NET Framework XAML hizmetlerinde, tür dönüştürücüsü öğesinden <xref:System.ComponentModel.TypeConverter>türetilen bir sınıf olmalıdır. Bazı dönüştürücüler XAML kayıt yolunu da destekler ve serileştirme biçimlendirmesinde bir nesneyi dize biçiminde seri hale getirmek için kullanılabilir. Bu konu, XAML 'deki tür dönüştürücülerinin nasıl ve ne zaman çağrılacağını açıklar ve metot geçersiz kılmaları <xref:System.ComponentModel.TypeConverter>için uygulama önerisi sağlar.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
 Aşağıdaki bölümlerde, XAML 'nin dizeleri nasıl kullandığı hakkında temel kavramlar ve .NET Framework XAML hizmetlerindeki nesne yazıcılarının bir XAML kaynağında karşılaşılan bazı dize değerlerini işlemek için tür dönüştürücülerinin nasıl kullanıldığı açıklanmaktadır.  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin başlangıç türü genel anlamda bir dize ve bir XML anlamda dize özniteliği değeri olur. Gibi diğer temel öğeler <xref:System.Double> de bir XAML işlemcisine ilk olarak dizelerdir.  
  
 Çoğu durumda, bir XAML işlemcisinin bir öznitelik değerini işlemek için iki bilgi parçasına ihtiyacı vardır. İlk bilgi parçası, ayarlanmakta olan özelliğin değer türüdür. Bir öznitelik değerini tanımlayan ve XAML 'de işlenen herhangi bir dize, sonunda, son olarak o türdeki bir değere dönüştürülmelidir veya çözümlenmelidir. Değer, XAML ayrıştırıcısı (sayısal değer gibi) tarafından anlaşılan bir temel ise, dizenin doğrudan dönüştürülmesine denenir. Özniteliğin değeri bir numaralandırmaya başvuruyorsa, sağlanan dize, bu Numaralandırmadaki adlandırılmış bir sabit ile bir ad eşleşmesi için denetlenir. Değer, ayrıştırıcının anlaşılmaz veya numaralandırmadan sabit bir ad değilse, uygulanabilir tür, dönüştürülmüş bir dizeye dayalı bir değer veya başvuru sağlayabilmelidir.  
  
> [!NOTE]
> XAML dil yönergeleri tür dönüştürücülerini kullanmaz.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüler ve biçimlendirme uzantıları  
 Biçimlendirme uzantısı kullanımları, özellik türünü ve diğer konuları kontrol etmeden önce bir XAML işlemcisi tarafından işlenmelidir. Örneğin, normalde bir öznitelik olarak ayarlanan bir özelliğin tür dönüştürmesi varsa, ancak belirli bir durumda biçimlendirme uzantısı kullanımı ile ayarlanırsa, biçimlendirme uzantısı davranışı önce işlenir. Biçimlendirme uzantısının gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuru yapmak. Bu senaryo için, durum bilgisi olmayan bir tür dönüştürücüsü yalnızca yeni bir örnek oluşturabilir ve bu, istenmeyebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüler  
 WPF ve .NET XAML Hizmetleri uygulamalarında, yerel tür dönüştürme işlemesi olan bazı CLR türleri vardır, ancak bu CLR türleri temel öğeler olarak genel olarak düşünülmez. Bu tür bir örnek vardır <xref:System.DateTime>. Bunun bir nedeni .NET Framework mimarinin nasıl çalıştığına yöneliktir: tür <xref:System.DateTime> , .net 'teki en temel kitaplık olan mscorlib 'de tanımlanmıştır. <xref:System.DateTime>, bir bağımlılığı (<xref:System.ComponentModel.TypeConverterAttribute> sistemden) tanıtan başka bir derlemeden gelen özniteliğiyle ilişkilendirilemez. bu nedenle, Attributing tarafından sunulan her zamanki tür dönüştürücüsü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı yerel işleme ihtiyacı olan türlerin bir listesini içerir ve bu türleri gerçek temel elemanların işlenme biçimine benzer şekilde işler. Bu durumda <xref:System.DateTime>, bu işlem öğesine <xref:System.DateTime.Parse%2A>bir çağrı içerir.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür Dönüştürücüsü uygulama  
 Aşağıdaki bölümlerde <xref:System.ComponentModel.TypeConverter> sınıfının API 'si ele alınmaktadır.  
  
### <a name="typeconverter"></a>TypeConverter  
 .NET Framework XAML Hizmetleri ' nin altında, XAML için kullanılan tüm tür dönüştürücüler taban sınıftan <xref:System.ComponentModel.TypeConverter>türetilen sınıflardır. Sınıf <xref:System.ComponentModel.TypeConverter> , XAML silinmeden önce .NET Framework sürümlerinde vardı; özgün <xref:System.ComponentModel.TypeConverter> senaryolardan biri, Visual Designer 'daki Özellik düzenleyicileri için dize dönüştürmesi sağlamaktır.  
  
 XAML için, rolü <xref:System.ComponentModel.TypeConverter> genişletilir. XAML amaçları için, <xref:System.ComponentModel.TypeConverter> belirli-dize ve dize dönüştürmelerinde destek sağlamak için temel sınıftır. From-String, XAML 'den bir dize özniteliği değeri ayrıştırmayı mümkün. -String, belirli bir nesne özelliğinin çalışma zamanı değerini seri hale getirme için XAML içindeki bir özniteliğe geri işlemeye olanak sağlayabilir.  
  
 <xref:System.ComponentModel.TypeConverter>XAML işleme amaçları için-String ve from-String ' i dönüştürmeye uygun dört üyeyi tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu üyelerin en önemli yöntemi, giriş dizesini gereken <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>nesne türüne dönüştüren ' dir. Yöntemi <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , dönüştürücünün amaçlanan hedef türüne daha geniş bir tür dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüştürmelerini destekleme gibi XAML 'in ötesine genişleyen amaçlar sunabilir. Ancak, XAML kullanımı için yalnızca bir <xref:System.String> girişi işleyecede kod yolu önemlidir.  
  
 En önemli ikinci yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama, biçimlendirme gösterimine dönüştürülürse (örneğin, XAML 'ye bir dosya olarak kaydedilirse), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> bir xaml metin yazıcılarının daha büyük senaryoya bir biçimlendirme temsili üretir. Bu durumda, XAML için önemli kod yolu çağıranın bir `destinationType` <xref:System.String>' ı geçirme yoludur.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> , bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamanın yeteneklerini sorguladığında kullanılan destek yöntemleridir. Bu yöntemleri, dönüştürücünün eşit dönüştürme yöntemlerinin `true` desteklediği türe özgü durumlar için döndürmek üzere uygulamalısınız. XAML amaçları için bu genellikle <xref:System.String> tür anlamına gelir.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için kültür bilgileri ve tür dönüştürücüler  
 Her <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize olduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklamasını kullanabilir veya yoksayabilir. Kültür ve XAML türü dönüştürme için önemli bir göz önünde bulundurmanız gerekenler şunlardır: öznitelik değerleri olarak yerelleştirilebilir dizeler kullanılması XAML tarafından desteklenmekle birlikte, bu yerelleştirilebilir dizeleri belirli kültür gereksinimlerine sahip tür dönüştürücüsü girişi olarak kullanamazsınız. Bu sınırlama, xaml öznitelik değerleri için tür dönüştürücülerinin kültür kullanan `en-US` sabit dil xaml işleme davranışına sahip olması gerektiğini içerir. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için bkz. xaml dil belirtimi ([\[ms-xaml\]](https://go.microsoft.com/fwlink/?LinkId=114525)) veya [WPF Genelleştirme ve yerelleştirme genel bakış](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Kültüre bir sorun olabilecek bir örnek olarak, bazı kültürler dize biçimindeki sayılar için ondalık nokta sınırlayıcısı olarak bir nokta yerine virgül kullanır. Bu kullanım, çok sayıda mevcut tür dönüştürücülerinin sahip olduğu ve sınırlayıcı olarak virgül kullanmanın olduğu davranış ile çakışıyor. Bir kültürü `xml:lang` çevreleyen XAML içinde geçirme sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 XAML <xref:System.ComponentModel.TypeConverter> 'yidestekleyen`value` bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün yöntemiparametreolarakbirdizekabuletmelidir.<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Dize geçerli bir biçimeyse ve <xref:System.ComponentModel.TypeConverter> uygulama tarafından dönüştürülemiyorsa, döndürülen nesne, özellik tarafından beklenen türe bir tür dönüştürmeyi desteklemelidir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamanın dönmesi `null`gerekir.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize oluşturduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklaması veya kültür bağlamlarını kullanabilir veya yoksayabilir. Ancak, WPF XAML işleme değerleri her durumda tür açıklaması bağlamına geçirmeyebilir ve ayrıca, temelinde `xml:lang`kültürü geçirmeyebilir.  
  
> [!NOTE]
> Parantez ({}), özellikle de açma küme ayracı ({) dize biçiminizdeki bir öğe olarak kullanmayın. Bu karakterler bir işaretleme uzantısı sırası için giriş ve çıkış olarak ayrılmıştır.  
  
 Tür dönüştürücüsünün .NET Framework xaml Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak <xref:System.IServiceProvider.GetService%2A> bağlamda gerçekleştirilen çağrının bu hizmeti döndürmez.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>, serileştirme desteği için büyük olasılıkla kullanılıyor. Özel tür ve <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> tür Dönüştürücüsü için serileştirme desteği, mutlak bir gereksinim değildir. Ancak, bir denetim uyguladıysanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak serileştirilmesi kullanıyorsanız, uygulamanız <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>gerekir.  
  
 XAML <xref:System.ComponentModel.TypeConverter> 'yidestekleyen`value` bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün yöntemiparametreolarakdesteklenentürün(veyabirdeğerin)birörneğinikabuletmelidir.<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Parametre türü <xref:System.String>olduğunda, döndürülen nesnenin olarak <xref:System.String>yayınlanamayacak olması gerekir. `destinationType` Döndürülen dize, seri hale getirilmiş bir değeri `value`temsil etmelidir. İdeal olarak, seçtiğiniz serileştirme biçimi, bu dizenin aynı dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamasına geçirilmesiyle aynı değeri, önemli ölçüde bilgi kaybı olmadan oluşturabilebilmelidir.  
  
 Değer seri hale getirilemez veya dönüştürücü Serileştirmeyi desteklemiyorsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null` ve bir özel durum oluşturabilir. Ancak, özel durumlar oluşturuyorsanız, bu dönüştürmeyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanızın bir parçası olarak kullanmayı, özel durumların önüne geçmek için en iyi şekilde <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> denetim altına almanız gerektiğini bildirmelisiniz.  
  
 `destinationType` Parametre türü<xref:System.String>değilse, kendi dönüştürücü işleme seçeneğini belirleyebilirsiniz. Genellikle temel uygulama işlemeye döndürürseniz, temel <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> içinde belirli bir özel durum yükseltilir.  
  
 Tür dönüştürücüsünün .NET Framework xaml Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak <xref:System.IServiceProvider.GetService%2A> bağlamda gerçekleştirilen çağrının bu hizmeti döndürmez.  
  
### <a name="implementing-canconvertfrom"></a>Canconvertuygulama  
 Uygulamanız türü `true` içindöndürmelidir`sourceType` , aksi takdirde temel uygulamaya ertelemelidir. <xref:System.String> <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> ' Den <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>özel durumlar atamayın.  
  
### <a name="implementing-canconvertto"></a>Canconvertuygulama  
 Uygulamanız türü `true` içindöndürmelidir`destinationType` , aksi takdirde temel uygulamaya ertelemelidir. <xref:System.String> <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ' Den <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>özel durumlar atamayın.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Özel tür dönüştürücüsünün .NET Framework xaml Hizmetleri tarafından özel bir sınıf için davranan tür dönüştürücüsü olarak kullanılabilmesi için, [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> ' yi sınıf tanımınıza uygulamanız gerekir. Özniteliği <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> aracılığıyla belirttiğiniz, özel tür dönüştürücünün tür adı olmalıdır. Bu özniteliği uygularsanız, bir XAML işlemcisi, özellik türünün özel sınıf türünü kullandığı değerleri işlediğinde, dizeleri belirtebilir ve nesne örnekleri döndürebilir.  
  
 Ayrıca özellik başına bir tür dönüştürücüsü sağlayabilirsiniz. [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] Sınıf tanımına bir `set` / `get` uygulamak yerine, bunu bir özellik tanımına (Ana tanım, içindeki uygulamaları değil) uygulayın. <xref:System.ComponentModel.TypeConverterAttribute> Özelliğin türü, özel tür dönüştürücülü tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemcisi bu özelliğin değerlerini işlediğinde, giriş dizelerini işleyebilir ve nesne örnekleri döndürebilir. Özellik başına tür dönüştürücüsü tekniği, Microsoft .net çerçevesinden veya sınıf tanımını denetleyemeyip bir başka kitaplıktan bir <xref:System.ComponentModel.TypeConverterAttribute> Özellik türü kullanmayı tercih ediyorsanız özellikle yararlıdır.  
  
 Özel bir ekli üye için tür dönüştürme davranışı sağlamak için, ekli üye <xref:System.ComponentModel.TypeConverterAttribute> için uygulama `Get` deseninin erişimci metoduna uygulayın.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı uygulamasından hizmet sağlayıcı bağlamına erişme  
 Kullanılabilir hizmetler herhangi bir değer Dönüştürücüsü için aynıdır. Fark, her bir değer dönüştürücünün hizmet bağlamını nasıl aldığına ilişkin farktır. Hizmetlere ve kullanılabilir hizmetlere erişme, [xaml Için biçimlendirme uzantıları ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md)konu başlığı altında belgelenmiştir.  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akışında tür dönüştürücüler  
 XAML düğüm akışıyla çalışıyorsanız, bir tür dönüştürücüsünün eylemi veya nihai sonucu henüz yürütülmemiştir. Yükleme yolunda, son olarak, yüklenecek öznitelik dizesinin bir başlangıç üyesi ve bitiş üyesi içinde metin değeri olarak kalması gerekir. Bu işlem için sonunda gereken tür dönüştürücüsü, <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> özelliği kullanılarak belirlenebilir. Ancak, öğesinden <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> geçerli bir değer elde etmek, bu tür bilgilere temel üye aracılığıyla erişebilen veya üyenin kullandığı nesne değerinin türü olan xaml şema bağlamına sahip olur. Tür dönüştürme davranışının çağrılması, tür eşlemesi gerektirdiğinden ve bir dönüştürücü örneği oluştururken XAML şeması bağlamını de gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverterAttribute>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
