---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 6e78210178fda65bb3baad0d24eb3a20cd6f2a3e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540119"
---
# <a name="overview-of-type-converters-for-xaml"></a>XAML için tür Dönüştürücülerine genel bakış

Tür dönüştürücüler, XAML biçimlendirme içindeki bir dizeden bir nesne grafiğinde belirli nesnelere dönüştüren bir nesne yazıcı için arz mantığı sağlar. .NET XAML hizmetlerinde tür dönüştürücüsü öğesinden türetilen bir sınıf olmalıdır <xref:System.ComponentModel.TypeConverter> . Bazı dönüştürücüler XAML kayıt yolunu da destekler ve serileştirme biçimlendirmesinde bir nesneyi dize biçiminde seri hale getirmek için kullanılabilir. Bu konu, XAML 'deki tür dönüştürücülerinin nasıl ve ne zaman çağrılacağını açıklar ve metot geçersiz kılmaları için uygulama önerisi sağlar <xref:System.ComponentModel.TypeConverter> .

## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları

Aşağıdaki bölümlerde, XAML 'nin dizeleri nasıl kullandığı hakkında temel kavramlar ve .NET XAML Hizmetleri 'ndeki nesne yazıcılarının bir XAML kaynağında karşılaşılan bazı dize değerlerini işlemek için tür dönüştürücülerinin nasıl kullanıldığı açıklanmaktadır.

### <a name="xaml-and-string-values"></a>XAML ve dize değerleri

XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin başlangıç türü genel anlamda bir dize ve bir XML anlamda dize özniteliği değeri olur. Gibi diğer temel öğeler de <xref:System.Double> BIR XAML işlemcisine ilk olarak dizelerdir.

Çoğu durumda, bir XAML işlemcisinin bir öznitelik değerini işlemek için iki bilgi parçasına ihtiyacı vardır. İlk bilgi parçası, ayarlanmakta olan özelliğin değer türüdür. Bir öznitelik değerini tanımlayan ve XAML 'de işlenen herhangi bir dize, sonunda, son olarak o türdeki bir değere dönüştürülmelidir veya çözümlenmelidir. Değer, XAML ayrıştırıcısı (sayısal değer gibi) tarafından anlaşılan bir temel ise, dizenin doğrudan dönüştürülmesine denenir. Özniteliğin değeri bir numaralandırmaya başvuruyorsa, sağlanan dize, bu Numaralandırmadaki adlandırılmış bir sabit ile bir ad eşleşmesi için denetlenir. Değer, ayrıştırıcının anlamış bir temel veya sabit bir ad numaralandırmasından değilse, uygulanabilir tür, dönüştürülmüş bir dizeye dayalı bir değer veya başvuru sağlayabilmelidir.

> [!NOTE]
> XAML dil yönergeleri tür dönüştürücülerini kullanmaz.

### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüler ve biçimlendirme uzantıları

Biçimlendirme uzantısı kullanımları, özellik türünü ve diğer konuları kontrol etmeden önce bir XAML işlemcisi tarafından işlenmelidir. Örneğin, normalde bir öznitelik olarak ayarlanan bir özelliğin tür dönüştürmesi varsa, ancak belirli bir durumda biçimlendirme uzantısı kullanımı ile ayarlanırsa, biçimlendirme uzantısı davranışı önce işlenir. Biçimlendirme uzantısının gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuru yapmak. Bu senaryo için, durum bilgisi olmayan bir tür dönüştürücüsü yalnızca yeni bir örnek oluşturabilir ve bu, istenmeyebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-overview.md).

### <a name="native-type-converters"></a>Yerel tür dönüştürücüler

Windows Presentation Foundation (WPF) ve .NET XAML Hizmetleri uygulamalarında, yerel tür dönüştürme işlemesi olan belirli CLR türleri vardır. Ancak, bu CLR türleri temel öğeler olarak genel olarak düşünülmez. Bu tür bir örnek vardır <xref:System.DateTime> . Bunun bir nedeni .NET Framework mimarinin nasıl çalıştığına yöneliktir: tür, <xref:System.DateTime> .net 'teki en temel kitaplık olan mscorlib 'de tanımlanmıştır. <xref:System.DateTime> bağımlılık tanıtan başka bir derlemeden gelen bir öznitelikle ilişkilendirilememesine izin verilmez ( <xref:System.ComponentModel.TypeConverterAttribute> sistem). Bu nedenle, Attributing tarafından her zamanki tür dönüştürücüsü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı yerel işleme ihtiyacı olan türlerin bir listesini içerir ve bu türleri gerçek temel elemanların işlenme biçimine benzer şekilde işler. <xref:System.DateTime>Bu durumda, bu işlem öğesine bir çağrı içerir <xref:System.DateTime.Parse%2A> .

## <a name="implementing-a-type-converter"></a>Tür Dönüştürücüsü uygulama

Aşağıdaki bölümlerde sınıfının API 'SI ele alınmaktadır <xref:System.ComponentModel.TypeConverter> .

### <a name="typeconverter"></a>TypeConverter

.NET XAML Hizmetleri ' nin altında, XAML için kullanılan tüm tür dönüştürücüler taban sınıftan türetilen sınıflardır <xref:System.ComponentModel.TypeConverter> . <xref:System.ComponentModel.TypeConverter>Sınıf, XAML silinmeden önce .NET Framework sürümlerinde vardı; özgün senaryolardan biri, <xref:System.ComponentModel.TypeConverter> Visual Designer 'daki Özellik düzenleyicileri için dize dönüştürmesi sağlamaktır.

XAML için, rolü <xref:System.ComponentModel.TypeConverter> genişletilir. XAML amaçları için, <xref:System.ComponentModel.TypeConverter> belirli-dize ve dize dönüştürmelerinde destek sağlamak için temel sınıftır. From-String, XAML 'den bir dize özniteliği değeri ayrıştırmayı mümkün. -String, belirli bir nesne özelliğinin çalışma zamanı değerini seri hale getirme için XAML içindeki bir özniteliğe geri işlemeye olanak sağlayabilir.

<xref:System.ComponentModel.TypeConverter> XAML işleme amaçları için-String ve from-String ' i dönüştürmeye uygun dört üyeyi tanımlar:

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Bu üyelerin en önemli yöntemi, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> giriş dizesini gereken nesne türüne dönüştüren ' dir. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>Yöntemi, dönüştürücünün amaçlanan hedef türüne daha geniş bir tür dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüştürmelerini destekleme gibi XAML 'in ötesine genişleyen amaçlar sunabilir. Ancak, XAML kullanımı için yalnızca bir girişi işleyecede kod yolu <xref:System.String> önemlidir.

İkinci en önemli Yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> . Bir uygulama, biçimlendirme gösterimine dönüştürülürse (örneğin, XAML 'ye bir dosya olarak kaydedilirse), bir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> xaml metin yazıcısının bir biçimlendirme temsili oluşturmak için daha büyük senaryoya dahil edilir. Bu durumda, XAML için önemli kod yolu çağıranın bir ' ı geçirme yoludur `destinationType` <xref:System.String> .

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve, <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> bir hizmet uygulamanın yeteneklerini sorguladığında kullanılan destek yöntemleridir <xref:System.ComponentModel.TypeConverter> . Bu yöntemleri, `true` dönüştürücünün eşit dönüştürme yöntemlerinin desteklediği türe özgü durumlar için döndürmek üzere uygulamalısınız. XAML amaçları için bu genellikle tür anlamına gelir <xref:System.String> .

### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için kültür bilgileri ve tür dönüştürücüler

Her <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize olduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklamasını kullanabilir veya yoksayabilir. Kültür ve XAML türü dönüştürme için önemli bir göz önünde bulundurmanız gerekenler şunlardır: öznitelik değerleri olarak yerelleştirilebilir dizeler kullanılması XAML tarafından desteklenmekle birlikte, bu yerelleştirilebilir dizeleri belirli kültür gereksinimlerine sahip tür dönüştürücüsü girişi olarak kullanamazsınız. Bu sınırlama, XAML öznitelik değerleri için tür dönüştürücülerinin kültür kullanan sabit dil XAML işleme davranışına sahip olması gerektiğini içerir `en-US` . Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için bkz. XAML dil belirtimi ([ \[ MS-xaml \] ](/previous-versions/msp-n-p/ff650760(v=pandp.10))) veya [WPF Genelleştirme ve yerelleştirme genel bakış](/dotnet/desktop/wpf/advanced/wpf-globalization-and-localization-overview).

Kültüre bir sorun olabilecek bir örnek olarak, bazı kültürler dize biçimindeki sayılar için ondalık nokta sınırlayıcısı olarak bir nokta yerine virgül kullanır. Bu kullanım, çok sayıda mevcut tür dönüştürücülerinin sahip olduğu ve sınırlayıcı olarak virgül kullanmanın olduğu davranış ile çakışıyor. Bir kültürü `xml:lang` çevreleyen XAML içinde geçirme sorunu çözmez.

### <a name="implementing-convertfrom"></a>ConvertFrom uygulama

<xref:System.ComponentModel.TypeConverter>Xaml 'yi destekleyen bir uygulama olarak kullanılabilmesi için, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Bu dönüştürücünün yöntemi parametre olarak bir dize kabul etmelidir `value` . Dize geçerli bir biçimeyse ve uygulama tarafından dönüştürülemiyorsa <xref:System.ComponentModel.TypeConverter> , döndürülen nesne, özellik tarafından beklenen türe bir tür dönüştürmeyi desteklemelidir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamanın dönmesi gerekir `null` .

Her <xref:System.ComponentModel.TypeConverter> uygulama, dönüştürme için geçerli bir dize oluşturduğunu benzersiz bir şekilde yorumlayabilir ve ayrıca parametre olarak geçirilen tür açıklaması veya kültür bağlamlarını kullanabilir veya yoksayabilir. Ancak, WPF XAML işleme değerleri her durumda tür açıklaması bağlamına geçirmeyebilir ve ayrıca, temelinde kültürü geçirmeyebilir `xml:lang` .

> [!NOTE]
> Parantez ( {} ), özellikle de açma küme ayracı ({) dize biçiminizdeki bir öğe olarak kullanmayın. Bu karakterler bir işaretleme uzantısı sırası için giriş ve çıkış olarak ayrılmıştır.

Tür dönüştürücüsünün .NET XAML Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak <xref:System.IServiceProvider.GetService%2A> bağlamda gerçekleştirilen çağrının bu hizmeti döndürmez.

### <a name="implementing-convertto"></a>ConvertTo uygulama

<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> , serileştirme desteği için büyük olasılıkla kullanılıyor. <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>Özel tür ve tür Dönüştürücüsü için serileştirme desteği, mutlak bir gereksinim değildir. Ancak, bir denetim uyguladıysanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak serileştirilmesi kullanıyorsanız, uygulamanız gerekir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> .

<xref:System.ComponentModel.TypeConverter>Xaml 'yi destekleyen bir uygulama olarak kullanılabilmesi için, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Bu dönüştürücünün yöntemi parametre olarak desteklenen türün (veya bir değerin) bir örneğini kabul etmelidir `value` . `destinationType`Parametre türü olduğunda <xref:System.String> , döndürülen nesnenin olarak yayınlanamayacak olması gerekir <xref:System.String> . Döndürülen dize, seri hale getirilmiş bir değeri temsil etmelidir `value` . İdeal olarak, seçtiğiniz serileştirme biçimi, bu dizenin aynı dönüştürücünün uygulamasına geçirilmesiyle aynı değeri <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , önemli ölçüde bilgi kaybı olmadan oluşturabilebilmelidir.

Değer seri hale getirilemez veya dönüştürücü Serileştirmeyi desteklemiyorsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null` ve bir özel durum oluşturabilir. Ancak, özel durumlar oluşturuyorsanız, bu dönüştürmeyi uygulamanızın bir parçası olarak kullanmayı, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> özel durumların önüne geçmek için en iyi şekilde denetim altına almanız gerektiğini bildirmelisiniz <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> .

`destinationType`Parametre türü değilse <xref:System.String> , kendi dönüştürücü işleme seçeneğini belirleyebilirsiniz. Genellikle temel uygulama işlemeye döndürürseniz, temel içinde <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum yükseltilir.

Tür dönüştürücüsünün .NET XAML Hizmetleri nesne yazıcısından bir XAML hizmetine erişimi olması gerektiğinde bir özel durum oluşturmak için uygundur, ancak <xref:System.IServiceProvider.GetService%2A> bağlamda gerçekleştirilen çağrının bu hizmeti döndürmez.

### <a name="implementing-canconvertfrom"></a>Canconvertuygulama

<xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>Uygulamanız `true` türü için döndürmelidir `sourceType` <xref:System.String> , aksi takdirde temel uygulamaya ertelemelidir. ' Den özel durumlar atamayın <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> .

### <a name="implementing-canconvertto"></a>Canconvertuygulama

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>Uygulamanız `true` türü için döndürmelidir `destinationType` <xref:System.String> , aksi takdirde temel uygulamaya ertelemelidir. ' Den özel durumlar atamayın <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> .

## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor

Özel tür dönüştürücüsünün .NET XAML Hizmetleri tarafından özel bir sınıf için davranan tür dönüştürücüsü olarak kullanılması için, ' yi <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımınıza uygulamanız gerekir. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A>Özniteliği aracılığıyla belirttiğiniz, özel tür dönüştürücünün tür adı olmalıdır. Bu özniteliği uygularsanız, bir XAML işlemcisi, özellik türünün özel sınıf türünü kullandığı değerleri işlediğinde, dizeleri belirtebilir ve nesne örnekleri döndürebilir.

Ayrıca özellik başına bir tür dönüştürücüsü sağlayabilirsiniz. Sınıf tanımına bir uygulamak yerine <xref:System.ComponentModel.TypeConverterAttribute> , bunu bir özellik tanımına (Ana tanım, `get` / `set` içindeki uygulamaları değil) uygulayın. Özelliğin türü, özel tür dönüştürücülü tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemcisi bu özelliğin değerlerini işlediğinde, giriş dizelerini işleyebilir ve nesne örnekleri döndürebilir. Özellik başına tür dönüştürücüsü tekniği, Microsoft .NET çerçevesinden veya sınıf tanımını denetleyemeyip bir başka kitaplıktan bir özellik türü kullanmayı tercih ediyorsanız yararlıdır <xref:System.ComponentModel.TypeConverterAttribute> .

Özel bir ekli üye için tür dönüştürme davranışı sağlamak için, <xref:System.ComponentModel.TypeConverterAttribute> `Get` ekli üye için uygulama deseninin erişimci metoduna uygulayın.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı uygulamasından hizmet sağlayıcı bağlamına erişme

Kullanılabilir hizmetler herhangi bir değer Dönüştürücüsü için aynıdır. Fark, her bir değer dönüştürücünün hizmet bağlamını nasıl aldığına ilişkin farktır. Hizmetlere ve kullanılabilir hizmetlere erişme, [xaml Için biçimlendirme uzantıları ve biçimlendirme uzantıları](type-converters-and-markup-extensions.md)konu başlığı altında belgelenmiştir.

## <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akışında tür dönüştürücüler

XAML düğüm akışıyla çalışıyorsanız, bir tür dönüştürücüsünün eylemi veya nihai sonucu henüz yürütülmemiştir. Yükleme yolunda, son olarak, yüklenecek öznitelik dizesinin bir başlangıç üyesi ve bitiş üyesi içinde metin değeri olarak kalması gerekir. Bu işlem için sonunda gereken tür dönüştürücüsü, özelliği kullanılarak belirlenebilir <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> . Ancak, öğesinden geçerli bir değer elde etmek, <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> Bu tür bilgilere temel üye aracılığıyla erişebilen veya üyenin kullandığı nesne değerinin türü olan xaml şema bağlamına sahip olur. Tür dönüştürme davranışının çağrılması, tür eşlemesi gerektirdiğinden ve bir dönüştürücü örneği oluştururken XAML şeması bağlamını de gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverterAttribute>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
