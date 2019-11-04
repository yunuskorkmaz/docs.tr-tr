---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: b54731cc1aba1a47ed6b11f2bff5c596a53fd4b5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458514"
---
# <a name="type-converters-for-xaml-overview"></a>XAML Tür Dönüştürücülerine Genel Bakış
Tür dönüştürücüler, XAML biçimlendirme içindeki bir dizeden bir nesne grafiğinde belirli nesnelere dönüştüren bir nesne yazıcı için arz mantığı sağlar. .NET Framework XAML hizmetlerinde, tür dönüştürücüsü <xref:System.ComponentModel.TypeConverter>türeten bir sınıf olmalıdır. Bazı dönüştürücüler XAML kayıt yolunu da destekler ve serileştirme biçimlendirmesinde bir nesneyi dize biçiminde seri hale getirmek için kullanılabilir. Bu konu, XAML 'deki tür dönüştürücülerinin nasıl ve ne zaman çağrılacağını açıklar ve <xref:System.ComponentModel.TypeConverter>metot geçersiz kılmaları için uygulama önerisi sağlar.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
 Aşağıdaki bölümlerde, XAML 'nin dizeleri nasıl kullandığı hakkında temel kavramlar ve .NET Framework XAML hizmetlerindeki nesne yazıcılarının bir XAML kaynağında karşılaşılan bazı dize değerlerini işlemek için tür dönüştürücülerinin nasıl kullanıldığı açıklanmaktadır.  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin başlangıç türü genel anlamda bir dize ve bir XML anlamda dize özniteliği değeri olur. <xref:System.Double> gibi diğer temel öğeler, başlangıçta XAML işlemcisine dizelerdir.  
  
 Çoğu durumda, bir XAML işlemcisinin bir öznitelik değerini işlemek için iki bilgi parçasına ihtiyacı vardır. İlk bilgi parçası, ayarlanmakta olan özelliğin değer türüdür. Bir öznitelik değerini tanımlayan ve XAML 'de işlenen herhangi bir dize, sonunda, son olarak o türdeki bir değere dönüştürülmelidir veya çözümlenmelidir. Değer, XAML ayrıştırıcısı (sayısal değer gibi) tarafından anlaşılan bir temel ise, dizenin doğrudan dönüştürülmesine denenir. Özniteliğin değeri bir numaralandırmaya başvuruyorsa, sağlanan dize, bu Numaralandırmadaki adlandırılmış bir sabit ile bir ad eşleşmesi için denetlenir. Değer, ayrıştırıcının anlaşılmaz veya numaralandırmadan sabit bir ad değilse, uygulanabilir tür, dönüştürülmüş bir dizeye dayalı bir değer veya başvuru sağlayabilmelidir.  
  
> [!NOTE]
> XAML dil yönergeleri tür dönüştürücülerini kullanmaz.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüler ve biçimlendirme uzantıları  
 Biçimlendirme uzantısı kullanımları, özellik türünü ve diğer konuları kontrol etmeden önce bir XAML işlemcisi tarafından işlenmelidir. Örneğin, normalde bir öznitelik olarak ayarlanan bir özelliğin tür dönüştürmesi varsa, ancak belirli bir durumda biçimlendirme uzantısı kullanımı ile ayarlanırsa, biçimlendirme uzantısı davranışı önce işlenir. Biçimlendirme uzantısının gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuru yapmak. Bu senaryo için, durum bilgisi olmayan bir tür dönüştürücüsü yalnızca yeni bir örnek oluşturabilir ve bu, istenmeyebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüler  
 WPF ve .NET XAML Hizmetleri uygulamalarında, yerel tür dönüştürme işlemesi olan bazı CLR türleri vardır, ancak bu CLR türleri temel öğeler olarak genel olarak düşünülmez. Bu tür bir örnek <xref:System.DateTime>. Bunun bir nedeni .NET Framework mimarinin çalışmadır: tür <xref:System.DateTime>, .NET 'teki en temel kitaplık olan mscorlib 'de tanımlanmıştır. <xref:System.DateTime>, bağımlılığı tanıtan başka bir derlemeden gelen bir öznitelikle ilişkilendirilememesine izin verilmez (<xref:System.ComponentModel.TypeConverterAttribute> sistemden); Bu nedenle, Attributing tarafından her zamanki tür dönüştürücüsü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı yerel işleme ihtiyacı olan türlerin bir listesini içerir ve bu türleri gerçek temel elemanların işlenme biçimine benzer şekilde işler. <xref:System.DateTime>söz konusu olduğunda, bu işlem <xref:System.DateTime.Parse%2A>bir çağrı içerir.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür Dönüştürücüsü uygulama  
 Aşağıdaki bölümlerde <xref:System.ComponentModel.TypeConverter> sınıfının API 'SI ele alınmaktadır.  
  
### <a name="typeconverter"></a>TypeConverter  
 .NET Framework XAML Hizmetleri ' nin altında, XAML için kullanılan tüm tür dönüştürücüler taban sınıftan türetilen sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> sınıfı, XAML var olan .NET Framework sürümlerinde vardı; özgün <xref:System.ComponentModel.TypeConverter> senaryolarından biri, Visual tasarýmcýlarındaki Özellik düzenleyicilerinde dize dönüştürme sağlamaktır.  
  
 XAML için <xref:System.ComponentModel.TypeConverter> rolü genişletilir. XAML amaçları için <xref:System.ComponentModel.TypeConverter>, belirli-dize ve dize dönüştürmelerinde destek sağlamak için temel sınıftır. From-String, XAML 'den bir dize özniteliği değeri ayrıştırmayı mümkün. -String, belirli bir nesne özelliğinin çalışma zamanı değerini seri hale getirme için XAML içindeki bir özniteliğe geri işlemeye olanak sağlayabilir.  
  
 <xref:System.ComponentModel.TypeConverter>, XAML işleme amaçları için-String ve from-String ' i dönüştürmeye uygun dört üyeyi tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu üyelerin en önemli yöntemi, giriş dizesini gereken nesne türüne dönüştüren <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi, daha geniş bir tür türü dönüştürücünün amaçlanan hedef türüne dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüştürmelerini destekleme gibi XAML 'in ötesine genişleyen amaçlar sunabilir. Ancak, XAML kullanımı için yalnızca bir <xref:System.String> girişi işleyecede kod yolu önemlidir.  
  
 En önemli ikinci yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama biçimlendirme gösterimine dönüştürülürse (örneğin, XAML 'ye bir dosya olarak kaydedilirse), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> XAML metin yazıcılarının daha büyük senaryosunda bir biçimlendirme temsili oluşturur. Bu durumda,, çağıran bir <xref:System.String>`destinationType` geçtiğinde, XAML için önemli kod yolu.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>, bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamasının yeteneklerini sorguladığında kullanılan destek yöntemleridir. Bu yöntemleri, dönüştürücünün eşit dönüştürme yöntemlerinin desteklediği türe özgü durumlar için `true` döndürmek üzere uygulamanız gerekir. XAML amaçları için bu genellikle <xref:System.String> türü anlamına gelir.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için kültür bilgileri ve tür dönüştürücüler  
 Her bir <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize olduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklamasını kullanabilir veya yoksayabilir. Kültür ve XAML türü dönüştürme için önemli bir göz önünde bulundurmanız gerekenler şunlardır: öznitelik değerleri olarak yerelleştirilebilir dizeler kullanılması XAML tarafından desteklenmekle birlikte, bu yerelleştirilebilir dizeleri belirli kültür gereksinimlerine sahip tür dönüştürücüsü girişi olarak kullanamazsınız. Bu sınırlama, XAML öznitelik değerleri için tür dönüştürücülerinin, `en-US` kültür kullanan sabit dil XAML işleme davranışına sahip olması gerektiğini içerir. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için bkz. XAML dil belirtimi ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) veya [WPF Genelleştirme ve yerelleştirme genel bakış](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Kültüre bir sorun olabilecek bir örnek olarak, bazı kültürler dize biçimindeki sayılar için ondalık nokta sınırlayıcısı olarak bir nokta yerine virgül kullanır. Bu kullanım, çok sayıda mevcut tür dönüştürücülerinin sahip olduğu ve sınırlayıcı olarak virgül kullanmanın olduğu davranış ile çakışıyor. Bir kültürü çevreleyen XAML 'de `xml:lang` aracılığıyla geçirmek sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 XAML 'yi destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi `value` parametresi olarak bir dizeyi kabul etmelidir. Dize geçerli bir biçimeyse ve <xref:System.ComponentModel.TypeConverter> uygulamayla dönüştürülemiyorsa, döndürülen nesne, özellik tarafından beklenen türe bir tür dönüştürmeyi desteklemelidir. Aksi takdirde <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama `null`döndürmelidir.  
  
 Her bir <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize oluşturduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklaması veya kültür bağlamlarını kullanabilir veya yoksayabilir. Ancak WPF XAML işleme değerleri her durumda tür açıklaması bağlamına geçirmeyebilir ve ayrıca `xml:lang`göre kültür geçirmeyebilir.  
  
> [!NOTE]
> Parantez ({}), özellikle de açma küme ayracı ({), dize biçiminizdeki bir öğe olarak kullanmayın. Bu karakterler bir işaretleme uzantısı sırası için giriş ve çıkış olarak ayrılmıştır.  
  
 Tür dönüştürücüsünün .NET Framework XAML Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak bağlamda gerçekleştirilen <xref:System.IServiceProvider.GetService%2A> çağrısı bu hizmeti döndürmez.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>, serileştirme desteği için büyük olasılıkla kullanılır. Özel tür ve tür Dönüştürücüsü için <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> aracılığıyla serileştirme desteği mutlak bir gereksinim değildir. Ancak, bir denetim uyguladıysanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak serileştirilmesi kullanıyorsanız, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>uygulamanız gerekir.  
  
 XAML 'yi destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> yöntemi, `value` parametresi olarak desteklenen tür (veya bir değer) örneğini kabul etmelidir. `destinationType` parametresi <xref:System.String>türünde olduğunda, döndürülen nesnenin <xref:System.String>olarak yayınlanamayacak olması gerekir. Döndürülen dize, seri hale getirilmiş bir `value`değerini temsil etmelidir. İdeal olarak, seçtiğiniz serileştirme biçimi, bu dizenin aynı dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamasına geçirilmesiyle aynı değeri, önemli ölçüde bilgi kaybı olmadan oluşturabilmelidir.  
  
 Değer seri hale getirilemez veya dönüştürücü Serileştirmeyi desteklemiyorsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama `null` döndürmelidir ve bir özel durum oluşturabilir. Ancak, özel durum throw yaparsanız, özel durumların önüne geçmek için en iyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> kontrol altına almanız için <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanızın bir parçası olarak bu dönüştürmeyi kullanmayı bildirmelisiniz.  
  
 `destinationType` parametresi <xref:System.String>türünde değilse, kendi dönüştürücü işleme seçeneğini belirleyebilirsiniz. Genellikle, temel <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> özel bir özel durum harekete geçirirse temel uygulama işlemeye döndürüleolursunuz.  
  
 Tür dönüştürücüsünün .NET Framework XAML Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak bağlamda gerçekleştirilen <xref:System.IServiceProvider.GetService%2A> çağrısı bu hizmeti döndürmez.  
  
### <a name="implementing-canconvertfrom"></a>Canconvertuygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> uygulamanız <xref:System.String> türü `sourceType` için `true` döndürmelidir; Aksi takdirde temel uygulamaya erteleyin. <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>özel durumlar atamayın.  
  
### <a name="implementing-canconvertto"></a>Canconvertuygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanız <xref:System.String>türü `destinationType` için `true` döndürmelidir ve başka bir deyişle temel uygulamaya ertelemelidir. <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>özel durumlar atamayın.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Özel tür dönüştürücüsünün .NET Framework XAML Hizmetleri tarafından özel bir sınıf için davranan tür dönüştürücüsü olarak kullanılabilmesi için, <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımınıza uygulamanız gerekir. Özniteliği aracılığıyla belirttiğiniz <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A>, özel tür dönüştürücünün tür adı olmalıdır. Bu özniteliği uygularsanız, bir XAML işlemcisi, özellik türünün özel sınıf türünü kullandığı değerleri işlediğinde, dizeleri belirtebilir ve nesne örnekleri döndürebilir.  
  
 Ayrıca özellik başına bir tür dönüştürücüsü sağlayabilirsiniz. Sınıf tanımına bir <xref:System.ComponentModel.TypeConverterAttribute> uygulamak yerine, bunu bir özellik tanımına (`get`/`set` uygulamalar değil) uygulayın. Özelliğin türü, özel tür dönüştürücülü tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemcisi bu özelliğin değerlerini işlediğinde, giriş dizelerini işleyebilir ve nesne örnekleri döndürebilir. Özellik başına tür dönüştürücüsü tekniği, Microsoft .NET çerçevesinden veya sınıf tanımını denetleyemeyip bir <xref:System.ComponentModel.TypeConverterAttribute> uygulayabileceğiniz diğer bir kitaplıktan Özellik türünü kullanmayı tercih ediyorsanız özellikle yararlıdır.  
  
 Özel bir ekli üye için tür dönüştürme davranışı sağlamak için, ekli üye için uygulama deseninin `Get` erişimci metoduna <xref:System.ComponentModel.TypeConverterAttribute> uygulayın.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı uygulamasından hizmet sağlayıcı bağlamına erişme  
 Kullanılabilir hizmetler herhangi bir değer Dönüştürücüsü için aynıdır. Fark, her bir değer dönüştürücünün hizmet bağlamını nasıl aldığına ilişkin farktır. Hizmetlere ve kullanılabilir hizmetlere erişme, [xaml Için biçimlendirme uzantıları ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md)konu başlığı altında belgelenmiştir.  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akışında tür dönüştürücüler  
 XAML düğüm akışıyla çalışıyorsanız, bir tür dönüştürücüsünün eylemi veya nihai sonucu henüz yürütülmemiştir. Yükleme yolunda, son olarak, yüklenecek öznitelik dizesinin bir başlangıç üyesi ve bitiş üyesi içinde metin değeri olarak kalması gerekir. Bu işlem için sonunda gereken tür dönüştürücüsü <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> özelliği kullanılarak belirlenebilir. Ancak <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> geçerli bir değer elde etmek, temel alınan üye veya üyenin kullandığı nesne değerinin türü ile ilgili bilgilere erişebilen bir XAML şeması bağlamına sahip olmaya bağlıdır. Tür dönüştürme davranışının çağrılması, tür eşlemesi gerektirdiğinden ve bir dönüştürücü örneği oluştururken XAML şeması bağlamını de gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverterAttribute>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
