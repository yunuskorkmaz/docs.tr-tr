---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: c3c69aebacd140a14e74545d601c0207cb8de681
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071635"
---
# <a name="overview-of-type-converters-for-xaml"></a>XAML için tür dönüştürücüler genel bakış

XAML biçimlendirmesindeki bir dizeden nesne grafiğindeki belirli nesnelere dönüştüren bir nesne yazarı için tür dönüştürücüler mantığı kaynağı. .NET XAML Hizmetleri'nde, tür <xref:System.ComponentModel.TypeConverter>dönüştürücü. Bazı dönüştürücüler ayrıca XAML kaydet yolunu destekler ve bir nesneyi serileştirme biçimlendirmesinde dize formuna seri hale getirmek için kullanılabilir. Bu konu, XAML'deki tür dönüştürücülerin nasıl ve ne zaman çağrıldığını <xref:System.ComponentModel.TypeConverter>açıklar ve yöntem geçersiz kılmaları için uygulama önerileri sağlar.

## <a name="type-conversion-concepts"></a>Tür Dönüştürme Kavramları

Aşağıdaki bölümlerde XAML'nin dizeleri nasıl kullandığı ve .NET XAML Services'daki nesne yazarlarının xaml kaynağında karşılaşılan dize değerlerinden bazılarını işlemek için tür dönüştürücülerini nasıl kullandıkları hakkındaki temel kavramları açıklanır.

### <a name="xaml-and-string-values"></a>XAML ve Dize Değerleri

Bir XAML dosyasında öznitelik değeri ayarladığınızda, bu değerin ilk türü genel anlamda bir dize ve XML anlamında bir dize özniteliği değeridir. XAML işlemcinin <xref:System.Double> başlangıçta dizeleri gibi diğer ilkel ler bile vardır.

Çoğu durumda, bir XAML işlemci bir öznitelik değerini işlemek için iki parça bilgiye ihtiyaç duyar. İlk bilgi parçası, ayarlanan özelliğin değer türüdür. Bir öznitelik değeri tanımlayan ve XAML'de işlenen herhangi bir dize sonuçta dönüştürülmelidir veya bu tür bir değere çözülmelidir. Değer XAML parlayıcı (sayısal değer gibi) tarafından anlaşılan ilkel bir ise, dize doğrudan dönüştürme denenir. Öznitelik değeri bir numaralandırmaya başvuruyorsa, sağlanan dize, bu numaralandırmada adlandırılmış bir sabitle eşleşen bir ad için işaretlenir. Değer, ayrıştırıcı tarafından anlaşılmış bir ilkel veya numaralandırmadan sabit bir ad değilse, ilgili tür dönüştürülmüş bir dizeyi temel alan bir değer veya başvuru sağlayabilmelidir.

> [!NOTE]
> XAML dil yönergeleri tür dönüştürücüleri kullanmaz.

### <a name="type-converters-and-markup-extensions"></a>Tür Dönüştürücüler ve Biçimlendirme Uzantıları

Biçimlendirme uzantısı kullanımları, özellik türünü ve diğer hususları kontrol etmeden önce bir XAML işlemci tarafından işlenmelidir. Örneğin, öznitelik olarak ayarlanan bir özelliğin normalde bir tür dönüştürmesi varsa, ancak belirli bir durumda biçimlendirme uzantısı kullanımı tarafından ayarlanırsa, önce biçimlendirme uzantısı davranışı işler. Biçimlendirme uzantısı gerekli olan yaygın bir durum, zaten var olan bir nesneye başvuruda bulunmaktır. Bu senaryo için, durum verişsiz bir tür dönüştürücü yalnızca istenmeyen yeni bir örnek oluşturabilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.

### <a name="native-type-converters"></a>Yerli Tip Dönüştürücüler

Windows Sunu Temeli (WPF) ve .NET XAML hizmet uygulamalarında, yerel tür dönüştürme işleme sada sahip belirli CLR türleri vardır. Ancak, bu CLR türleri geleneksel olarak ilkel olarak düşünülmez. Böyle bir tür bir <xref:System.DateTime>örnek . Bunun bir nedeni .NET Framework mimarisinin nasıl <xref:System.DateTime> çalıştığıdır: türü .NET'teki en temel kitaplık olan mscorlib'de tanımlanır. <xref:System.DateTime>bağımlılık<xref:System.ComponentModel.TypeConverterAttribute> (Sistem'den) tanıtan başka bir derlemeden gelen bir öznitelik ile atfedilmesine izin verilmez. Bu nedenle, atfederek olağan tür dönüştürücü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı yerel işleme gerektiren türlerin bir listesi vardır ve bu tür gerçek ilkel işlenme şekline benzer işler. Durumunda <xref:System.DateTime>, Bu işleme için bir <xref:System.DateTime.Parse%2A>çağrı içerir .

## <a name="implementing-a-type-converter"></a>Tür Dönüştürücü Uygulama

Aşağıdaki bölümlerde sınıfın API'si <xref:System.ComponentModel.TypeConverter> tartışılır.

### <a name="typeconverter"></a>TypeConverter

.NET XAML Hizmetleri altında, XAML amaçları için kullanılan tüm tür dönüştürücüler <xref:System.ComponentModel.TypeConverter>taban sınıftan türeyen sınıflardır. Sınıf <xref:System.ComponentModel.TypeConverter> XAML var önce .NET Framework sürümlerinde vardı; orijinal <xref:System.ComponentModel.TypeConverter> senaryolardan biri görsel tasarımcılar özellik düzenleyicileri için dize dönüştürme sağlamak oldu.

XAML için rolü <xref:System.ComponentModel.TypeConverter> genişletilir. XAML amaçları <xref:System.ComponentModel.TypeConverter> için, belirli dize ve dize dönüşümleri için destek sağlamak için temel sınıftır. From-string, XAML'den bir dize özniteliği değerini ayrıştamayı sağlar. To-string, belirli bir nesne özelliğinin çalışma zamanı değerinin serileştirme için XAML'deki bir özniteliğe yeniden işlenmesine olanak sağlayabilir.

<xref:System.ComponentModel.TypeConverter>XAML işleme amaçları için dize ve ipten dönüştürme yle ilgili dört üye tanımlar:

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Bu üyelerden en önemli <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>yöntem, giriş dizesini gerekli nesne türüne dönüştüren yöntemdir. Yöntem, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> daha geniş bir tür aralığını dönüştürücünün hedeflenen hedef türüne dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüşümlerini desteklemek gibi XAML'nin ötesine uzanan amaçlara hizmet edebilir. Ancak, XAML kullanımı için, yalnızca bir <xref:System.String> girişi işleyebilir kod yolu önemlidir.

İkinci en önemli yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama biçimlendirme gösterimine dönüştürülürse (örneğin, dosya olarak XAML'ye kaydediliyorsa), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme gösterimi oluşturmak için xaml metin yazarının daha büyük senaryosunda yer almaktadır. Bu durumda, XAML için önemli kod yolu, `destinationType` arayanın bir ' den ' in ''yi <xref:System.String>geçirmesidir.

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamanın yeteneklerini sorguladığında kullanılan destek yöntemleridir. Dönüştürücünüzdesteğinin eşdeğer `true` dönüştürme yöntemlerinin türüne özgü durumlar için döndürmek için bu yöntemleri uygulamanız gerekir. XAML amaçları için, bu <xref:System.String> genellikle türü anlamına gelir.

### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için Kültür Bilgileri ve Tip Dönüştürücüler

Her <xref:System.ComponentModel.TypeConverter> uygulama, bir dönüşüm için geçerli bir dize yi benzersiz bir şekilde yorumlayabilir ve parametre olarak geçirilen tür açıklamasını da kullanabilir veya yok sayabilir. Kültür ve XAML türü dönüştürme için önemli bir husus şunlardır: öznitelik değerleri olarak yerelleştirilebilir dizeleri kullanarak XAML tarafından desteklenen olsa da, belirli kültür gereksinimleri ile tür dönüştürücü girişi olarak bu yerelleştirilebilir dizeleri kullanamazsınız. Bu sınırlama, XAML öznitelik değerleri için tür dönüştürücüler kültür kullanan `en-US` mutlaka sabit dil XAML işleme davranışı içermesidir. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimi[\[(MS-XAML)\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))veya [WPF Genellaştırma ve Yerelleştirme Genel Bakış'a](../../framework/wpf/advanced/wpf-globalization-and-localization-overview.md)bakın.

Kültürün bir sorun olabileceği bir örnek olarak, bazı kültürler dize şeklindeki sayılar için ondalık nokta delimiter olarak bir dönem yerine virgül kullanır. Bu kullanım, varolan birçok tür dönüştürücünün sahip olduğu davranışla çarpışır, bu da virgülü sınırlayıcı olarak kullanmaktır. Çevredeki XAML'de bir kültürün geçmesi `xml:lang` sorunu çözmez.

### <a name="implementing-convertfrom"></a>ConvertFrom'ı Uygulama

XAML destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> olması için, bu dönüştürücü için `value` yöntem parametre olarak bir dize kabul etmelidir. Dize geçerli bir biçimdeyse ve <xref:System.ComponentModel.TypeConverter> uygulama tarafından dönüştürülebiliyorsa, döndürülen nesnenin bir dökümü özellik tarafından beklenen türe desteklemesi gerekir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama `null`döndürmelidir.

Her <xref:System.ComponentModel.TypeConverter> uygulama, bir dönüşüm için geçerli bir dize oluşturan şeyi benzersiz bir şekilde yorumlayabilir ve parametre olarak geçirilen tür açıklamasını veya kültür bağlamlarını da kullanabilir veya yok sayabilir. Ancak, WPF XAML işleme değerleri tüm durumlarda tür açıklaması bağlamına geçiremeyebilir `xml:lang`ve ayrıca kültüre dayalı olarak geçemeyebilir.

> [!NOTE]
> Ayraçları ( ),{}özellikle açılış ayracını ({), dize biçiminizin bir öğesi olarak kullanmayın. Bu karakterler, biçimlendirme uzantısı dizisi için giriş ve çıkış olarak ayrılmıştır.

Türü dönüştürücünüz .NET XAML Services nesne yazarından bir XAML hizmetine erişebiliyorsa, ancak içeriğe karşı yapılan <xref:System.IServiceProvider.GetService%2A> çağrı bu hizmeti döndürmezse, bir özel durum atmak uygundur.

### <a name="implementing-convertto"></a>ConvertTo'nun Uygulanması

<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>serileştirme desteği için kullanılabilir. Özel türüve <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> türü dönüştürücü için serileştirme desteği mutlak bir gereklilik değildir. Ancak, bir denetim uyguluyorsanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>serileştirme kullanıyorsanız, uygulamanız gerekir.

XAML destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> olması için, bu dönüştürücü için yöntem `value` parametre olarak desteklenen tür (veya değer) bir örnek kabul etmelidir. `destinationType` Parametre türünde <xref:System.String>olduğunda, döndürülen nesne '' olarak <xref:System.String>atılabilir. Döndürülen dize, `value`'nin serileştirilmiş değerini temsil etmelidir. İdeal olarak, seçtiğiniz serileştirme biçimi, önemli miktarda bilgi kaybı olmadan, bu <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> dize aynı dönüştürücünün uygulamasına geçmiş gibi aynı değeri oluşturabilmelidir.

Değer serileştirilemiyorsa veya dönüştürücü serileştirmeyi <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> desteklemiyorsa, uygulama döndürülmeli `null` ve bir özel durum atabilir. Ancak, özel durumlar atarsanız, özel durumları önlemek için <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> önce kontrol etme en iyi uygulamanın desteklenmesi için bu dönüşümü uygulamanızın bir parçası olarak kullanamamayı bildirmeniz gerekir.

`destinationType` Parametre türünde <xref:System.String>değilse, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, temel uygulama işleme, temel <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> olarak belirli bir özel durum yükseltir geri dönersiniz.

Türü dönüştürücünüz .NET XAML Services nesne yazarından bir XAML hizmetine erişebiliyorsa, ancak içeriğe karşı yapılan <xref:System.IServiceProvider.GetService%2A> çağrı bu hizmeti döndürmezse, bir özel durum atmak uygundur.

### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama

Uygulamanız <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> türü `true` <xref:System.String> `sourceType` için geri dönmeli ve aksi takdirde temel uygulamaya ertelenmelidir. 'den <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>istisnalar atmayın.

### <a name="implementing-canconvertto"></a>CanConvertTo'nun Uygulanması

Uygulamanız <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> türü `true` <xref:System.String> `destinationType` için geri dönmeli ve aksi takdirde temel uygulamaya ertelenmelidir. 'den <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>istisnalar atmayın.

## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulama

.NET XAML Services tarafından özel bir sınıf için etki leyici türü dönüştürücü olarak kullanılabilmesi için sınıf <xref:System.ComponentModel.TypeConverterAttribute> tanımına uygulamanız gerekir. Öznitelik aracılığıyla belirttiğiniz şey, <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> özel tür dönüştürücünüzün tür adı olmalıdır. Bu özniteliği uygularsanız, bir XAML işlemci özellik türünün özel sınıf türünüzü kullandığı değerleri işlerse, dizeleri giriş yapabilir ve nesne örneklerini döndürebilir.

Ayrıca, özellik başına bazda bir tür dönüştürücü de sağlayabilirsiniz. Sınıf tanımına <xref:System.ComponentModel.TypeConverterAttribute> a uygulamak yerine, bunu bir özellik tanımına (içindeki `get` / `set` uygulamalar değil, ana tanım) uygulayın. Özelliğin türü, özel tür dönüştürücünüz tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemci bu özelliğin değerlerini işlerse, giriş dizeleri işleyebilir ve nesne örneklerini döndürebilir. Özellik başına tür dönüştürücü tekniği, Microsoft .NET Framework'den veya sınıf tanımını denetleyemediğiniz ve orada uygulayamadığınız başka bir <xref:System.ComponentModel.TypeConverterAttribute> kitaplıktan bir özellik türü kullanmayı seçerseniz yararlıdır.

Özel bağlı bir üye için tür dönüştürme <xref:System.ComponentModel.TypeConverterAttribute> davranışı `Get` sağlamak için, bağlı üye için uygulama deseninin erişimyöntemine uygulayın.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Biçimlendirme Uzantısı Uygulamasından Hizmet Sağlayıcı Bağlamına Erişim

Kullanılabilir hizmetler herhangi bir değer dönüştürücü için aynıdır. Fark, her değer dönüştürücüsü hizmet bağlamını nasıl aldığıdır. Hizmetlere ve mevcut hizmetlere erişim, [XAML için Type Converters ve Markup Uzantıları](type-converters-and-markup-extensions.md)konusunda belgelenmiştir.

## <a name="type-converters-in-the-xaml-node-stream"></a>XAML Düğüm Akışında Tür Dönüştürücüler

Bir XAML düğüm akışıyla çalışıyorsanız, bir tür dönüştürücünün eylem veya sonuç sonucu henüz yürütülmez. Bir yük yolunda, yüklemek için sonunda türe dönüştürülmesi gereken öznitelik dizesi, başlangıç üyesi ve bitiş üyesi içinde metin değeri olarak kalır. Sonunda bu işlem için gerekli olan tür dönüştürücü <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> özelliği kullanılarak belirlenebilir. Ancak, geçerli bir değer <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> elde etmek, bu tür bilgilere temel üye aracılığıyla erişebilen bir XAML şeması bağlamına veya üyenin kullandığı nesne değerinin türüne dayanır. Tür dönüştürme davranışının çağırılması, tür eşleme ve dönüştürücü örneği oluşturma gerektirdiğinden XAML şema bağlamını da gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverterAttribute>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
