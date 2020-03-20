---
title: TypeConverters ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187292"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters ve XAML
Bu konu, genel bir XAML dil özelliği olarak dize türü dönüştürme amacını tanıtır. .NET Framework'de <xref:System.ComponentModel.TypeConverter> sınıf, XAML öznitelik kullanımında özellik değeri olarak kullanılabilecek yönetilen bir özel sınıf için uygulamanın bir parçası olarak belirli bir amaca hizmet eder. Özel bir sınıf yazarsanız ve sınıfınızın örneklerinin XAML ayarlanabilir öznitelik değerleri olarak kullanılabilir olmasını <xref:System.ComponentModel.TypeConverterAttribute> istiyorsanız, sınıfınıza bir <xref:System.ComponentModel.TypeConverter> sınıf uygulamanız, özel bir sınıf yazmanız veya her ikisini birden yazmanız gerekebilir.  

## <a name="type-conversion-concepts"></a>Tür Dönüştürme Kavramları  
  
### <a name="xaml-and-string-values"></a>XAML ve Dize Değerleri  
 Bir XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin ilk türü saf metindeki bir dizedir. XAML işlemciye <xref:System.Double> başlangıçta metin dizeleri gibi diğer ilkel ler bile vardır.  
  
 Bir XAML işlemci, öznitelik değerini işlemek için iki parça bilgiye ihtiyaç duyar. İlk bilgi parçası, ayarlanan özelliğin değer türüdür. Bir öznitelik değeri tanımlayan ve XAML'de işlenen herhangi bir dize sonuçta dönüştürülmelidir veya bu tür bir değere çözülmelidir. Değer XAML parlayıcı (sayısal değer gibi) tarafından anlaşılan ilkel bir ise, dize doğrudan dönüştürme denenir. Değer numaralandırma ise, dize, bu numaralandırmada adı geçen bir sabitle eşleşen bir ad eşleşmesini denetlemek için kullanılır. Değer ne ayrıştırıcı tarafından anlaşılmış bir ilkel ne de numaralandırma ise, söz konusu tür, dönüştürülmüş bir dize dayalı tür veya bir değer in bir örnek sağlamak gerekir. Bu bir tür dönüştürücü sınıf belirterek yapılır. Tür dönüştürücü, hem XAML senaryosu hem de .NET kodundaki kod çağrıları için başka bir sınıfın değerlerini sağlamak için etkili bir yardımcı sınıftır.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML'de Varolan Tür Dönüştürme Davranışını Kullanma  
 Temel XAML kavramlarına aşinalığınıza bağlı olarak, temel uygulama XAML'de bunu fark etmeden tür dönüştürme davranışı kullanıyor olabilirsiniz. Örneğin, WPF kelimenin tam anlamıyla tür <xref:System.Windows.Point>bir değer alan özellikleri yüzlerce tanımlar. A, <xref:System.Windows.Point> iki boyutlu koordinat uzayında bir koordinatı açıklayan bir değerdir ve gerçekten <xref:System.Windows.Point.X%2A> <xref:System.Windows.Point.Y%2A>sadece iki önemli özelliği vardır: ve. XAML'de bir nokta belirttiğiniz zaman, bunu sağladığınız değerler <xref:System.Windows.Point.X%2A> arasında <xref:System.Windows.Point.Y%2A> sınırlayıcı (genellikle virgül) olan bir dize olarak belirtirsiniz. Örneğin: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 XAML bile <xref:System.Windows.Point> bu basit türü ve basit kullanımı bir tür dönüştürücü içerir. Bu durumda bu sınıftır. <xref:System.Windows.PointConverter>  
  
 Sınıf düzeyinde tanımlanan <xref:System.Windows.Point> tür dönüştürücü, 'yi alan <xref:System.Windows.Point>tüm özelliklerin biçimlendirme kullanımlarını kolaylaştırır. Burada bir tür dönüştürücü olmadan, daha önce gösterilen aynı örnek için aşağıdaki çok daha ayrıntılı biçimlendirme gerekir:  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 Tür dönüştürme dizesi veya daha ayrıntılı eşdeğer sözdizimi kullanmak için genellikle bir kodlama stili seçimdir. XAML takım iş akışınız değerlerin nasıl ayarlanır olduğunu da etkileyebilir. Bazı XAML araçları, tasarımcı görünümlerine veya kendi serileştirme mekanizmasına gidiş-dönüş yapmak daha kolay olduğundan biçimlendirmenin en ayrıntılı biçimini yayışma eğilimindedir.  
  
 Varolan tür dönüştürücüler genellikle WPF ve .NET Framework türlerinde bir sınıfın (veya özelliğin) uygulanmış <xref:System.ComponentModel.TypeConverterAttribute>bir varlığı olup olmayacağını denetleyerek keşfedilebilir. Bu öznitelik, xaml amaçları nın yanı sıra potansiyel olarak diğer amaçlar için, bu tür değerler için destekleyen tür dönüştürücü olan sınıf adlanır.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür Dönüştürücüler ve Biçimlendirme Uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüler XAML işlemci davranışı ve uygulandığı senaryolar açısından ortogonal rolleri doldurun. Biçimlendirme uzantısı kullanımları için bağlam kullanılabilir olsa da, biçimlendirme uzantısı sağlayan özelliklerin tür dönüştürme davranışı genellikle biçimlendirme uzantısı uygulamalarında denetlenmez. Başka bir deyişle, biçimlendirme uzantısı bir metin `ProvideValue` dizesini çıktıolarak döndürse bile, belirli bir özellik veya özellik değeri türüne uygulandığı gibi bu dizedeki dönüşüm davranışı çağrılmaz, genellikle biçimlendirme uzantısının amacı bir dizeyi işlemek ve herhangi bir tür dönüştürücü içermeyen bir nesneyi döndürmektir.  
  
 Tür dönüştürücüyerine biçimlendirme uzantısı nın gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuruda bulunmaktır. En iyi durumda, durum verişsiz bir tür dönüştürücü yalnızca istenmeyen olmayabilir yeni bir örnek oluşturabilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için [bkz.](markup-extensions-and-wpf-xaml.md)  
  
### <a name="native-type-converters"></a>Yerli Tip Dönüştürücüler  
 XAML ayrıştırıcısının WPF ve .NET Framework uygulamasında, yerel tür dönüştürme işlemeye sahip belirli türler vardır, ancak geleneksel olarak ilkel olarak düşünülebilecek türler değildir. Böyle bir tür bir <xref:System.DateTime>örnek . Bunun nedeni .NET Framework mimarisinin nasıl çalıştığına <xref:System.DateTime> bağlıdır: türü .NET'teki en temel kitaplık olan mscorlib'de tanımlanır. <xref:System.DateTime>bağımlılık<xref:System.ComponentModel.TypeConverterAttribute> (Sistem'den) tanıtan başka bir derlemeden gelen bir öznitelik ile atfedilmesine izin verilmez, bu nedenle atfederek olağan tür dönüştürücü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı, bu tür yerel işleme gerektiren türlerin bir listesine sahiptir ve bunları gerçek ilkellerin nasıl işlendiğine benzer şekilde işler. <xref:System.DateTime> (Bu durumda bir çağrı içerir <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>Tür Dönüştürücü Uygulama  
  
### <a name="typeconverter"></a>TypeConverter  
 Daha <xref:System.Windows.Point> önce verilen örnekte, <xref:System.Windows.PointConverter> sınıf belirtilmiştir. XAML'nin .NET uygulamaları için, XAML amaçları için kullanılan tüm tür dönüştürücüler <xref:System.ComponentModel.TypeConverter>taban sınıftan türeyen sınıflardır. Sınıf <xref:System.ComponentModel.TypeConverter> XAML varlığından önce .NET Framework sürümlerinde vardı; orijinal kullanımlarından biri görsel tasarımcılarda özellik iletişim leri için dize dönüştürme sağlamakoldu. XAML için rolü, <xref:System.ComponentModel.TypeConverter> dize öznitelik değerini ayrıştırmayı sağlayan dize ve dize dönüşümleri için taban sınıf olmayı ve büyük olasılıkla belirli bir nesne özelliğinin çalışma zamanı değerini bir öznitelik olarak serileştirme için bir dize olarak yeniden işlemeyi içerecek şekilde genişletilir.  
  
 <xref:System.ComponentModel.TypeConverter>XAML işleme amaçları için dizeleri dönüştürme ve dizeleri ile ilgili dört üye tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bunlardan en önemli yöntem <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Bu yöntem, giriş dizesini gerekli nesne türüne dönüştürür. Açıkçası, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntem dönüştürücünün hedef türüne çok daha geniş bir tür aralığı dönüştürmek için uygulanabilir ve böylece çalışma zamanı dönüşümleri destekleyen gibi XAML ötesine uzanan amaçlara hizmet, <xref:System.String> ancak XAML amaçları için sadece önemli bir giriş işleyebilir kod yoludur.  
  
 Sonraki en önemli <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>yöntem . Bir uygulama biçimlendirme gösterimine dönüştürülürse (örneğin, dosya olarak XAML'ye kaydedilirse), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme gösterimi üretmekten sorumludur. Bu durumda, XAML için önemli olan kod yolu `destinationType` <xref:System.String> bir ' den geçtiğiniz zaman  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamanın yeteneklerini sorguladığında kullanılan destek yöntemleridir. Dönüştürücünüzdesteğinin eşdeğer `true` dönüştürme yöntemlerinin türüne özgü durumlar için döndürmek için bu yöntemleri uygulamanız gerekir. XAML amaçları için, bu <xref:System.String> genellikle türü anlamına gelir.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için Kültür Bilgileri ve Tip Dönüştürücüler  

 Her <xref:System.ComponentModel.TypeConverter> uygulama, bir dönüşüm için geçerli bir dize oluşturan şeyin kendi yorumuna sahip olabilir ve parametre olarak geçirilen tür açıklamasını da kullanabilir veya yok sayabilir. Kültür ve XAML türü dönüştürme ile ilgili önemli bir husus vardır. Öznitelik değerleri olarak yerelleştirilebilir dizeleri kullanarak tamamen XAML tarafından desteklenir. Ancak, xaml öznitelik değerleri için tür dönüştürücüler kültür kullanarak mutlaka sabit dil ayrıştırma davranışı içerdiğinden, belirli kültür gereksinimleri `en-US` ile tür dönüştürücü girişi olarak bu yerelleştirilebilir dize kullanılması desteklenmez. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimine[\[(MS-XAML)\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)başvurmalısınız.  
  
 Kültürün bir sorun olabileceği bir örnek olarak, bazı kültürler sayılar için ondalık nokta sınırlayıcı olarak virgül kullanırlar. Bu, WPF XAML türü dönüştürücülerin çoğunun sahip olduğu davranışla çakışacaktır, bu da virgülbir delimiter olarak kullanmaktır (ortak X,Y formu veya virgül delimited listeleri gibi tarihsel örneklere dayalı). Hatta çevreleyen XAML (ayarı `Language` veya `xml:lang` `sl-SI` kültür, bu şekilde ondalık için virgül kullanan bir kültür örneği) bir kültür geçen sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom'ı Uygulama  
 XAML destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> olması için, bu dönüştürücü için `value` yöntem parametre olarak bir dize kabul etmelidir. Dize geçerli biçimindeyse ve <xref:System.ComponentModel.TypeConverter> uygulama tarafından dönüştürülebiliyorsa, döndürülen nesnenin bir dökümü özellik tarafından beklenen türe desteklemesi gerekir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama `null`döndürmelidir.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulama, bir dönüşüm için geçerli bir dize oluşturan şeyin kendi yorumuna sahip olabilir ve parametre olarak geçirilen tür açıklamasını veya kültür bağlamlarını kullanabilir veya yok sayabilir. Ancak, WPF XAML işleme değerleri tüm durumlarda tür açıklaması bağlamına geçiremeyebilir `xml:lang`ve ayrıca kültüre dayalı olarak geçemeyebilir.  
  
> [!NOTE]
> Dize biçiminizin olası bir öğesi olarak özellikle {kıvırcık ayraç karakterlerini kullanmayın. Bu karakterler, biçimlendirme uzantısı dizisi için giriş ve çıkış olarak ayrılmıştır.  
  
### <a name="implementing-convertto"></a>ConvertTo'nun Uygulanması  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>serileştirme desteği için kullanılabilir. Özel türüve <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> türü dönüştürücü için serileştirme desteği mutlak bir gereklilik değildir. Ancak, bir denetim uyguluyorsanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>serileştirme kullanıyorsanız, uygulamanız gerekir.  
  
 XAML'yi <xref:System.ComponentModel.TypeConverter> destekleyen bir uygulama olarak <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> kullanılabilir olması için, bu dönüştürücüiçin yöntemin `value` parametre olarak desteklenen tür (veya değer) örneğini kabul etmesi gerekir. `destinationType` Parametre türü <xref:System.String>olduğunda, döndürülen nesne '' olarak <xref:System.String>atılabilir. Döndürülen dize, `value`'nin serileştirilmiş değerini temsil etmelidir. İdeal olarak, seçtiğiniz serileştirme biçimi, bu dize önemli bilgi kaybı olmadan <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> aynı dönüştürücü nün uygulamasına geçtiyse aynı değeri oluşturma yeteneğine sahip olmalıdır.  
  
 Değer serileştirilemiyorsa veya dönüştürücü serileştirmeyi desteklemiyorsa, uygulama döndürülmelidir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> `null`ve bu durumda bir özel durum atmasına izin verilir. Ancak özel durumlar atarsanız, özel durumları önlemek için <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> önce kontrol etme uygulamasının en iyi şekilde desteklenmesi için bu dönüşümü uygulamanızın bir parçası olarak kullanamamayı bildirmelisiniz.  
  
 `destinationType` Parametre türünde <xref:System.String>değilse, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, taban uygulama işleme, taban da <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum yükseltir dönmek istiyorsunuz.  
  
### <a name="implementing-canconvertto"></a>CanConvertTo'nun Uygulanması  
 Uygulamanız <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> türü `true` <xref:System.String> `destinationType` için geri dönmeli ve aksi takdirde temel uygulamaya ertelenmelidir.  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama  
 Uygulamanız <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> türü `true` <xref:System.String> `sourceType` için geri dönmeli ve aksi takdirde temel uygulamaya ertelenmelidir.  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulama  
 Özel tür dönüştürücünüzün xaml işlemci tarafından özel bir sınıf için etki leyici tür dönüştürücü olarak kullanılabilmesi için sınıf <xref:System.ComponentModel.TypeConverterAttribute> tanımına uygulamanız gerekir. Öznitelik aracılığıyla belirttiğiniz şey, <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> özel tür dönüştürücünüzün tür adı olmalıdır. Bu öznitelik uygulandığında, bir XAML işlemci özellik türü özel sınıf türü kullanır değerleri işler, dizeleri giriş ve nesne örnekleri döndürebilir.  
  
 Ayrıca, özellik başına bazda bir tür dönüştürücü de sağlayabilirsiniz. Sınıf tanımına <xref:System.ComponentModel.TypeConverterAttribute> a uygulamak yerine, bunu bir özellik tanımına (içindeki `get` / `set` uygulamalar değil, ana tanım) uygulayın. Özelliğin türü, özel tür dönüştürücünüz tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemci bu özelliğin değerlerini işlerse, giriş dizeleri işleyebilir ve nesne örneklerini döndürebilir. Özellik başına tür dönüştürücü tekniği, Microsoft .NET Framework'den veya sınıf tanımını denetleyemediğiniz ve orada uygulayamadığınız <xref:System.ComponentModel.TypeConverterAttribute> başka bir kitaplıktan bir özellik türü kullanmayı seçerseniz özellikle yararlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverter>
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
