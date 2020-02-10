---
title: TypeConverters ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 6b8b58228e94ed12557e97406e55cc4165753076
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095092"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters ve XAML
Bu konu, dizeden Genel XAML dil özelliği olarak tür dönüştürme amacını tanıtır. .NET Framework, <xref:System.ComponentModel.TypeConverter> sınıfı, XAML öznitelik kullanımında Özellik değeri olarak kullanılabilecek yönetilen bir özel sınıf için uygulamanın bir parçası olarak belirli bir amaca hizmet eder. Özel bir sınıf yazarsanız ve sınıfınızın örneklerinin XAML ayarlanabilir öznitelik değerleri olarak kullanılabilir olmasını istiyorsanız, sınıfınıza bir <xref:System.ComponentModel.TypeConverterAttribute> uygulamanız, özel bir <xref:System.ComponentModel.TypeConverter> sınıfı yazmanız veya her ikisi de yapmanız gerekebilir.  

## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin başlangıç türü, saf metindeki bir dizedir. <xref:System.Double> gibi diğer temel öğeler, başlangıçta XAML işlemcisine metin dizeleridir.  
  
 XAML işlemcisi, bir öznitelik değerini işlemek için iki bilgi parçasına ihtiyaç duyuyor. İlk bilgi parçası, ayarlanmakta olan özelliğin değer türüdür. Bir öznitelik değerini tanımlayan ve XAML 'de işlenen herhangi bir dize, sonunda, son olarak o türdeki bir değere dönüştürülmelidir veya çözümlenmelidir. Değer, XAML ayrıştırıcısı (sayısal değer gibi) tarafından anlaşılan bir temel ise, dizenin doğrudan dönüştürülmesine denenir. Değer bir sabit listesi ise, dize söz konusu Numaralandırmadaki adlandırılmış bir sabityle bir ad eşleşmesi denetlemek için kullanılır. Değer, ayrıştırıcının anlaşılmaz veya bir numaralandırma değilse, söz konusu tür, dönüştürülmüş bir dizeye göre türün bir örneğini veya bir değerini sağlayabilmelidir. Bu, bir tür dönüştürücü sınıfı belirterek yapılır. Tür dönüştürücüsü etkin bir şekilde başka bir sınıfın değerlerini sağlamak için, hem XAML senaryosu hem de .NET kodundaki kod çağrıları için bir yardımcı sınıftır.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML 'de varolan tür dönüştürme davranışını kullanma  
 Temel alınan XAML kavramlarıyla ilgili olarak, temel uygulama XAML 'de tür dönüştürme davranışını gerçekleştirmeden önce bu yöntemi zaten kullanıyor olabilirsiniz. Örneğin, WPF <xref:System.Windows.Point>türünde bir değer alan, yüzlerce yüzlerce özelliği tanımlar. <xref:System.Windows.Point>, iki boyutlu koordinat alanındaki bir koordinatı tanımlayan bir değerdir ve aslında yalnızca iki önemli özelliğe sahiptir: <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A>. XAML 'de bir nokta belirttiğinizde, bunu sağladığınız <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A> değerleri arasında sınırlayıcı (genellikle virgül) olan bir dize olarak belirtirsiniz. Örneğin: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Bu basit <xref:System.Windows.Point> türü ve XAML 'de basit kullanımı, bir tür dönüştürücüyü içerir. Bu durumda, sınıfı <xref:System.Windows.PointConverter>.  
  
 Sınıf düzeyinde tanımlanan <xref:System.Windows.Point> için tür dönüştürücüsü, <xref:System.Windows.Point>olan tüm özelliklerin biçimlendirme kullanımlarını basitleştirir. Burada bir tür dönüştürücüsü olmadan, daha önce gösterilen örnek için aşağıdaki çok daha ayrıntılı biçimlendirme gerekir:  

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
  
 Tür dönüştürme dizesinin mi yoksa daha ayrıntılı bir eşdeğer sözdiziminin mi kullanılacağı genellikle kodlama stili seçimidir. XAML araç iş akışınız, değerlerin nasıl ayarlandığını da etkileyebilir. Bazı XAML araçları, tasarımcı görünümlerine veya kendi serileştirme mekanizmasına daha kolay dönmek için biçimlendirmenin en ayrıntılı biçimini yaymaya eğilimlidir.  
  
 Varolan tür dönüştürücüler, uygulanan bir <xref:System.ComponentModel.TypeConverterAttribute>varlığı için bir sınıf (veya özellik) denetleyerek genellikle WPF ve .NET Framework türlerinde bulunabilir. Bu öznitelik, bu türün değerleri için destekleme türü Dönüştürücüsü olan sınıfı, XAML amaçları ve potansiyel olarak başka amaçlar için olarak adlandırın.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüler ve biçimlendirme uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüler, XAML işlemci davranışı ve uygulandıkları senaryolar bakımından dikgen rolleri doldurur. Bağlam biçimlendirme uzantısı kullanımları için kullanılabilir olsa da, biçimlendirme uzantısının bir değer sağladığı özelliklerin dönüştürme davranışı genellikle biçimlendirme uzantısı uygulamalarında denetlenmez. Diğer bir deyişle, biçimlendirme uzantısı `ProvideValue` çıktısı olarak bir metin dizesi döndürse bile, bu dizeye belirli bir özelliğe uygulanan veya özellik değeri türüne uygulanan şekilde tür dönüştürme davranışı çağrılmaz, genellikle bir biçimlendirme uzantısının amacı bir dizeyi işlemek ve herhangi bir tür dönüştürücüsü olmadan bir nesne döndürmek olur.  
  
 Bir tür dönüştürücüsü yerine bir biçimlendirme uzantısının gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuru yapmak olur. En iyi durum bilgisi olmayan tür dönüştürücüsü yalnızca yeni bir örnek oluşturabilir, bu da istenmeyebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüler  
 WPF ve XAML ayrıştırıcısının .NET Framework uygulamasında, yerel tür dönüştürme işlemesi olan belirli türler vardır, ancak temel olarak genel olarak olabilecek türler değildir. Bu tür bir örnek <xref:System.DateTime>. Bunun nedeni, .NET Framework mimarisinin nasıl çalıştığına bağlıdır: tür <xref:System.DateTime>, .NET 'teki en temel kitaplık olan mscorlib içinde tanımlanır. <xref:System.DateTime>, bağımlılık kullanan başka bir derlemeden gelen bir öznitelikle ilişkilendirilemez (<xref:System.ComponentModel.TypeConverterAttribute> sistemdir), bu nedenle olağan tür dönüştürücüsü bulma mekanizması Attributing tarafından desteklenmez. Bunun yerine, XAML ayrıştırıcısı böyle bir yerel işleme ihtiyacı olan türlerin bir listesini içerir ve bunları doğru temel elemanların işlenme şekli gibi işler. (<xref:System.DateTime> durumunda bu, <xref:System.DateTime.Parse%2A>çağrısını içerir.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür Dönüştürücüsü uygulama  
  
### <a name="typeconverter"></a>TypeConverter  
 Daha önce verilen <xref:System.Windows.Point> örnekte, sınıf <xref:System.Windows.PointConverter> bahsedildi. XAML .NET uygulamaları için, XAML için kullanılan tüm tür dönüştürücüler taban sınıftan türetilen sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> sınıfı, XAML varlığını önündeki .NET Framework sürümlerinde vardı; özgün kullanımlarından biri, Visual Designer 'daki Özellik iletişimleri için dize dönüştürmesi sağlamaktır. XAML için <xref:System.ComponentModel.TypeConverter> rolü, dize özniteliği değerini ayrıştırmayı sağlayan-String ve from-String dönüştürmeleri için temel sınıf olacak şekilde genişletilir ve muhtemelen bir öznitelik olarak serileştirme için belirli bir nesne özelliğinin çalışma zamanı değerini bir dizeye geri işliyor.  
  
 <xref:System.ComponentModel.TypeConverter> XAML işleme amaçları için dizeden ve dizeden dönüştürmeye uygun dört üyeyi tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu, en önemli Yöntem <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Bu yöntem, giriş dizesini gereken nesne türüne dönüştürür. Kesinlikle konuşurken <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi, dönüştürücünün amaçlanan hedef türüne çok daha geniş bir tür dönüştürmek için uygulanabilir ve bu nedenle çalışma zamanı dönüştürmelerini destekleme gibi XAML 'in ötesine genişleyen, ancak XAML amacıyla, yalnızca önemli bir <xref:System.String> girişi işleyebilen kod yoludur.  
  
 En önemli bir sonraki Yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama biçimlendirme gösterimine dönüştürülürse (örneğin, XAML 'ye bir dosya olarak kaydedilirse), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme temsili üretilmeden sorumludur. Bu durumda, XAML için önemli olan kod yolu <xref:System.String> `destinationType` geçirdiğinizde olur.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>, bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamasının yeteneklerini sorguladığında kullanılan destek yöntemleridir. Bu yöntemleri, dönüştürücünün eşit dönüştürme yöntemlerinin desteklediği türe özgü durumlar için `true` döndürmek üzere uygulamanız gerekir. XAML amaçları için bu genellikle <xref:System.String> türü anlamına gelir.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için kültür bilgileri ve tür dönüştürücüler  

 Her bir <xref:System.ComponentModel.TypeConverter> uygulamasının, dönüştürme için geçerli bir dize oluşturduğunu belirlemek için kendi yorumu bulunabilir ve ayrıca parametre olarak geçirilen tür açıklamasını kullanabilir veya yoksayabilir. Kültür ve XAML türü dönüşümle ilgili önemli bir göz vardır. Öznitelik değerleri olarak yerelleştirilebilir dizelerin kullanılması XAML tarafından tamamen desteklenir. Ancak, XAML öznitelik değerleri için tür dönüştürücülerinin, `en-US` kültür kullanılarak sabit dil ayrıştırma davranışı içerdiğinden, bu yerelleştirilebilir dizenin tür dönüştürücüsü girdisi olarak kullanılması desteklenmez. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimine ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)başvurmalısınız.  
  
 Kültüre bir sorun olabilecek bir örnek olarak, bazı kültürler sayılar için ondalık nokta sınırlayıcıları olarak virgül kullanır. Bu, WPF XAML tür dönüştürücülerinin çoğunun sahip olduğu davranışla çakışır. Bu, bir sınırlayıcı olarak virgül (ortak X, Y formu veya virgülle ayrılmış listeler gibi geçmiş etkileyenler temelinde) kullanır. Aynı XAML içindeki bir kültürü (`Language` veya `xml:lang` `sl-SI` kültürüne geçirerek, bu şekilde ondalık için virgül kullanan bir kültür örneği) sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 XAML 'yi destekleyen <xref:System.ComponentModel.TypeConverter> bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi `value` parametresi olarak bir dizeyi kabul etmelidir. Dize geçerli biçimeyse ve <xref:System.ComponentModel.TypeConverter> uygulamayla dönüştürülebileceğinden, döndürülen nesne, özellik tarafından beklenen türe bir tür dönüştürmeyi desteklemelidir. Aksi takdirde <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama `null`döndürmelidir.  
  
 Her bir <xref:System.ComponentModel.TypeConverter> uygulamasının, dönüştürme için geçerli bir dize oluşturduğunu belirlemek için kendi yorumu olabilir ve ayrıca parametre olarak geçirilen tür açıklaması ya da kültür bağlamlarını kullanabilir ya da yoksayabilir. Ancak WPF XAML işlemi, değerleri her durumda tür açıklaması bağlamına geçirmeyebilir ve ayrıca `xml:lang`göre kültür geçirmeyebilir.  
  
> [!NOTE]
> Dize biçiminizdeki olası bir öğe olarak, özellikle {, küme ayracı karakterlerini kullanmayın. Bu karakterler bir işaretleme uzantısı sırası için giriş ve çıkış olarak ayrılmıştır.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>, serileştirme desteği için büyük olasılıkla kullanılır. Özel tür ve tür Dönüştürücüsü için <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> aracılığıyla serileştirme desteği mutlak bir gereksinim değildir. Ancak, bir denetim uyguladıysanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak serileştirilmesi kullanıyorsanız, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>uygulamanız gerekir.  
  
 XAML 'yi destekleyen bir <xref:System.ComponentModel.TypeConverter> uygulama olarak kullanılabilmesi için, bu dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> yöntemi, `value` parametresi olarak desteklenmekte olan türün (veya bir değerin) bir örneğini kabul etmelidir. `destinationType` parametre <xref:System.String>tür olduğunda, döndürülen nesnenin <xref:System.String>olarak yayınlanamayacak olması gerekir. Döndürülen dize, seri hale getirilmiş bir `value`değerini temsil etmelidir. İdeal olarak, seçtiğiniz serileştirme biçimi, bu dizenin aynı dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamasına geçirilmesi durumunda, önemli ölçüde bilgi kaybı olmadan aynı değeri üretmeye sahip olmalıdır.  
  
 Değer seri hale getirilemez veya dönüştürücü Serileştirmeyi desteklemiyorsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama `null`döndürmelidir ve bu durumda bir özel durum oluşturulmasına izin verilir. Ancak, özel durumlar oluşturmamak için bu dönüştürmeyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanızın bir parçası olarak kullanmayı bildirmelisiniz. böylece, özel durumların önlenmesi için en iyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> kontrol altına almanız gerekir.  
  
 `destinationType` parametre <xref:System.String>türünde değilse, kendi dönüştürücü işleme seçeneğini belirleyebilirsiniz. Genellikle, temel uygulama işlemeye döndürülerek, en çok <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum oluşturur.  
  
### <a name="implementing-canconvertto"></a>Canconvertuygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanız <xref:System.String>türü `destinationType` için `true` döndürmelidir ve başka bir deyişle temel uygulamaya ertelemelidir.  
  
### <a name="implementing-canconvertfrom"></a>Canconvertuygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> uygulamanız <xref:System.String>türü `sourceType` için `true` döndürmelidir ve başka bir deyişle temel uygulamaya ertelemelidir.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Özel tür dönüştürücüsünün bir XAML işlemcisi tarafından özel bir sınıf için davranan tür dönüştürücüsü olarak kullanılabilmesi için, <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımınıza uygulamanız gerekir. Özniteliği aracılığıyla belirttiğiniz <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A>, özel tür dönüştürücünün tür adı olmalıdır. Bu öznitelik uygulandığında, XAML işlemcisi özellik türünün özel sınıf türünü kullandığı değerleri işlediğinde, dizeleri belirtebilir ve nesne örnekleri döndürebilir.  
  
 Ayrıca özellik başına bir tür dönüştürücüsü sağlayabilirsiniz. Sınıf tanımına bir <xref:System.ComponentModel.TypeConverterAttribute> uygulamak yerine, bunu bir özellik tanımına (`get`/`set` uygulamalar değil) uygulayın. Özelliğin türü, özel tür dönüştürücülü tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemcisi bu özelliğin değerlerini işlediğinde, giriş dizelerini işleyebilir ve nesne örnekleri döndürebilir. Özellik başına tür dönüştürücüsü tekniği, Microsoft .NET çerçevesinden veya sınıf tanımını denetleyemeyip bir <xref:System.ComponentModel.TypeConverterAttribute> uygulayabileceğiniz diğer bir kitaplıktan Özellik türünü kullanmayı tercih ediyorsanız özellikle yararlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverter>
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
