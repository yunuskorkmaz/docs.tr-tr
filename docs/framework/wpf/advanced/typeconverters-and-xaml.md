---
title: TypeConverters ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 8c39fe75eea5042657cab533a0a557d966802a1b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169019"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters ve XAML
Bu konu, dizeden Genel XAML dil özelliği olarak tür dönüştürme amacını tanıtır. .NET Framework, <xref:System.ComponentModel.TypeConverter> sınıfı, xaml öznitelik kullanımında Özellik değeri olarak kullanılabilecek yönetilen özel sınıf için uygulamanın bir parçası olarak belirli bir amaca hizmet eder. Özel bir sınıf yazarsanız ve sınıfınızın örneklerinin xaml ayarlanabilir öznitelik değerleri olarak kullanılabilir olmasını istiyorsanız, sınıfınıza bir <xref:System.ComponentModel.TypeConverterAttribute> uygulama uygulamanız, özel <xref:System.ComponentModel.TypeConverter> bir sınıf yazmanız veya her ikisini de yapmanız gerekebilir.  

## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin başlangıç türü, saf metindeki bir dizedir. Gibi diğer temel öğeler <xref:System.Double> , bir XAML işlemcisine başlangıçta metin dizeleridir.  
  
 XAML işlemcisi, bir öznitelik değerini işlemek için iki bilgi parçasına ihtiyaç duyuyor. İlk bilgi parçası, ayarlanmakta olan özelliğin değer türüdür. Bir öznitelik değerini tanımlayan ve XAML 'de işlenen herhangi bir dize, sonunda, son olarak o türdeki bir değere dönüştürülmelidir veya çözümlenmelidir. Değer, XAML ayrıştırıcısı (sayısal değer gibi) tarafından anlaşılan bir temel ise, dizenin doğrudan dönüştürülmesine denenir. Değer bir sabit listesi ise, dize söz konusu Numaralandırmadaki adlandırılmış bir sabityle bir ad eşleşmesi denetlemek için kullanılır. Değer, ayrıştırıcının anlaşılmaz veya bir numaralandırma değilse, söz konusu tür, dönüştürülmüş bir dizeye göre türün bir örneğini veya bir değerini sağlayabilmelidir. Bu, bir tür dönüştürücü sınıfı belirterek yapılır. Tür dönüştürücüsü etkin bir şekilde başka bir sınıfın değerlerini sağlamak için, hem XAML senaryosu hem de .NET kodundaki kod çağrıları için bir yardımcı sınıftır.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML 'de varolan tür dönüştürme davranışını kullanma  
 Temel alınan XAML kavramlarıyla ilgili olarak, temel uygulama XAML 'de tür dönüştürme davranışını gerçekleştirmeden önce bu yöntemi zaten kullanıyor olabilirsiniz. Örneğin, WPF, türünde <xref:System.Windows.Point>bir değer alan, yüzlerce yüzlerce özelliği tanımlar. , İki boyutlu koordinat alanında bir koordinatı tanımlayan bir değerdir ve aslında yalnızca iki önemli özelliğe sahiptir: <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A>. <xref:System.Windows.Point> XAML 'de bir nokta belirttiğinizde, bunu sağladığınız <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A> değerleri arasında sınırlayıcı (genellikle virgül) olan bir dize olarak belirtirsiniz. Örneğin: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`  
  
 XAML 'de bu basit türü <xref:System.Windows.Point> ve basit kullanımı bile bir tür Dönüştürücüsü içerir. Bu durumda, sınıfı <xref:System.Windows.PointConverter>.  
  
 Sınıf düzeyinde <xref:System.Windows.Point> tanımlanan tür dönüştürücüsü, tüm özelliklerin <xref:System.Windows.Point>biçimlendirme kullanımlarını basitleştirir. Burada bir tür dönüştürücüsü olmadan, daha önce gösterilen örnek için aşağıdaki çok daha ayrıntılı biçimlendirme gerekir:  

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
  
 Varolan tür dönüştürücüler, uygulanan <xref:System.ComponentModel.TypeConverterAttribute>varlık için bir sınıf (veya özellik) denetleyerek genellikle WPF ve .NET Framework türlerinde bulunabilir. Bu öznitelik, bu türün değerleri için destekleme türü Dönüştürücüsü olan sınıfı, XAML amaçları ve potansiyel olarak başka amaçlar için olarak adlandırın.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüler ve biçimlendirme uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüler, XAML işlemci davranışı ve uygulandıkları senaryolar bakımından dikgen rolleri doldurur. Bağlam biçimlendirme uzantısı kullanımları için kullanılabilir olsa da, biçimlendirme uzantısının bir değer sağladığı özelliklerin dönüştürme davranışı genellikle biçimlendirme uzantısı uygulamalarında denetlenmez. Diğer bir deyişle, bir biçimlendirme uzantısı `ProvideValue` çıkış olarak bir metin dizesi döndürse bile, belirli bir özelliğe uygulanan veya özellik değeri türü çağrılmayan Bu dizeye tür dönüştürme davranışı, genellikle bir biçimlendirme uzantısının amacı bir String ve herhangi bir tür dönüştürücüsü olmadan bir nesne döndürür.  
  
 Bir tür dönüştürücüsü yerine bir biçimlendirme uzantısının gerekli olduğu yaygın bir durum, zaten var olan bir nesneye başvuru yapmak olur. En iyi durum bilgisi olmayan tür dönüştürücüsü yalnızca yeni bir örnek oluşturabilir, bu da istenmeyebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüler  
 WPF ve XAML ayrıştırıcısının .NET Framework uygulamasında, yerel tür dönüştürme işlemesi olan belirli türler vardır, ancak temel olarak genel olarak olabilecek türler değildir. Bu tür bir örnek vardır <xref:System.DateTime>. Bunun nedeni, .NET Framework mimarisinin nasıl çalıştığına bağlıdır: tür <xref:System.DateTime> , .net 'teki en temel kitaplık olan mscorlib 'te tanımlanmıştır. <xref:System.DateTime>, bağımlılık tanıtan başka bir derlemeden gelen bir öznitelikle ilişkilendirilemez (<xref:System.ComponentModel.TypeConverterAttribute> sistemdir), bu nedenle, Attributing tarafından her zamanki tür dönüştürücüsü bulma mekanizması desteklenemez. Bunun yerine, XAML ayrıştırıcısı böyle bir yerel işleme ihtiyacı olan türlerin bir listesini içerir ve bunları doğru temel elemanların işlenme şekli gibi işler. ( <xref:System.DateTime> Bu durum durumunda öğesine <xref:System.DateTime.Parse%2A>bir çağrı içerir.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür Dönüştürücüsü uygulama  
  
### <a name="typeconverter"></a>TypeConverter  
 Daha önce verilen <xref:System.Windows.PointConverter> örnekte, sınıfı bahsedildi. <xref:System.Windows.Point> XAML .NET uygulamaları için XAML için kullanılan tüm tür dönüştürücüler, temel sınıftan <xref:System.ComponentModel.TypeConverter>türetilen sınıflardır. <xref:System.ComponentModel.TypeConverter> Sınıf, xaml varlığını önündeki .NET Framework sürümlerinde vardı; özgün kullanımlarından biri, Visual Designer 'daki Özellik iletişimleri için dize dönüştürmesi sağlamaktır. XAML için, rolü <xref:System.ComponentModel.TypeConverter> bir dize özniteliği değerini ayrıştırmayı sağlayan-String ve from-String dönüştürmeleri için temel sınıf olacak şekilde genişletilir ve büyük olasılıkla belirli bir nesne özelliğinin çalışma zamanı değerini bir dizeye geri doğru olarak işliyor öznitelik olarak serileştirme.  
  
 <xref:System.ComponentModel.TypeConverter>XAML işleme amaçları için dizeden ve dizeden dönüştürmeye uygun dört üyeyi tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu, en önemli Yöntem ' dir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Bu yöntem, giriş dizesini gereken nesne türüne dönüştürür. Kesinlikle konuşuyor, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntem çok daha geniş bir tür türü dönüştürücünün amaçlanan hedef türüne dönüştürmek için uygulanabilir ve bu nedenle, çalışma zamanı dönüştürmeleri destekleme gibi XAML 'in ötesine genişleyen, ancak xaml amaçları için bir amaç sunar yalnızca önemli bir <xref:System.String> girişi işleyecede kod yoludur.  
  
 En önemli bir sonraki Yöntem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama, biçimlendirme gösterimine dönüştürülürse (örneğin, XAML 'ye bir dosya olarak kaydedilirse), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme temsili üretilmekten sorumludur. Bu durumda, XAML için önemli olan kod yolu, bir `destinationType` <xref:System.String> ' ı geçirdiğinizde olur.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> , bir hizmet <xref:System.ComponentModel.TypeConverter> uygulamanın yeteneklerini sorguladığında kullanılan destek yöntemleridir. Bu yöntemleri, dönüştürücünün eşit dönüştürme yöntemlerinin `true` desteklediği türe özgü durumlar için döndürmek üzere uygulamalısınız. XAML amaçları için bu genellikle <xref:System.String> tür anlamına gelir.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML için kültür bilgileri ve tür dönüştürücüler  
 Her <xref:System.ComponentModel.TypeConverter> uygulamanın, dönüştürme için geçerli bir dize oluşturduğunu belirlemek için kendi yorumu olabilir ve ayrıca parametre olarak geçirilen tür açıklaması ' nı kullanabilir veya yoksayabilir. Kültür ve XAML türü dönüşümle ilgili önemli bir göz vardır. Öznitelik değerleri olarak yerelleştirilebilir dizelerin kullanılması XAML tarafından tamamen desteklenir. Ancak, xaml öznitelik değerleri için tür dönüştürücülerinin, kültür kullanılarak `en-US` sabit dil ayrıştırma davranışı içerdiğinden, bu yerelleştirilebilir dizenin tür dönüştürücüsü girdisi olarak kullanılması desteklenmez. Bu kısıtlamanın tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimine ([\[ms-xaml\]](https://go.microsoft.com/fwlink/?LinkId=114525)) başvurmalısınız.  
  
 Kültüre bir sorun olabilecek bir örnek olarak, bazı kültürler sayılar için ondalık nokta sınırlayıcıları olarak virgül kullanır. Bu, WPF XAML tür dönüştürücülerinin çoğunun sahip olduğu davranışla çakışır. Bu, bir sınırlayıcı olarak virgül (ortak X, Y formu veya virgülle ayrılmış listeler gibi geçmiş etkileyenler temelinde) kullanır. Kapsayıcı xaml içindeki bir kültürü ( `Language` veya `xml:lang` `sl-SI` kültürü, bu şekilde ondalık için bir virgül kullanan bir kültür örneği) bile, sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 XAML <xref:System.ComponentModel.TypeConverter> 'yidestekleyen`value` bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün yöntemiparametreolarakbirdizekabuletmelidir.<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Dize geçerli biçimeyse ve <xref:System.ComponentModel.TypeConverter> uygulama tarafından dönüştürülebileceğinden döndürülen nesne, özellik tarafından beklenen türe bir tür dönüştürmeyi desteklemelidir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamanın dönmesi `null`gerekir.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulamanın, bir dönüştürme için geçerli bir dize oluşturduğunu belirlemek için kendi yorumu olabilir ve ayrıca parametre olarak geçirilen tür açıklaması ya da kültür bağlamlarını kullanabilir veya yoksayabilir. Ancak, WPF XAML işleme değerleri her durumda tür açıklaması bağlamına geçirmeyebilir ve ayrıca, temelinde `xml:lang`kültürü geçirmeyebilir.  
  
> [!NOTE]
> Dize biçiminizdeki olası bir öğe olarak, özellikle {, küme ayracı karakterlerini kullanmayın. Bu karakterler bir işaretleme uzantısı sırası için giriş ve çıkış olarak ayrılmıştır.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>, serileştirme desteği için büyük olasılıkla kullanılıyor. Özel tür ve <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> tür Dönüştürücüsü için serileştirme desteği, mutlak bir gereksinim değildir. Ancak, bir denetim uyguladıysanız veya sınıfınızın özelliklerinin veya tasarımının bir parçası olarak serileştirilmesi kullanıyorsanız, uygulamanız <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>gerekir.  
  
 XAML <xref:System.ComponentModel.TypeConverter> 'yidestekleyen`value` bir uygulama olarak kullanılabilmesi için, bu dönüştürücünün yöntemiparametreolarakdesteklenmekteolantürün(veyabirdeğerin)birörneğinikabuletmelidir.<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Parametre türü <xref:System.String>olduğunda, döndürülen nesnenin olarak <xref:System.String>yayınlanamayacak olması gerekir. `destinationType` Döndürülen dize, seri hale getirilmiş bir değeri `value`temsil etmelidir. İdeal olarak, seçtiğiniz seri hale getirme biçimi, bu dizenin aynı dönüştürücünün <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulamasına geçirilmesi durumunda, önemli bir bilgi kaybı olmadan aynı değeri üretmeye sahip olmalıdır.  
  
 Değer seri hale getirilemez veya dönüştürücü Serileştirmeyi <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> desteklemiyorsa, uygulamanın dönmesi `null`gerekir ve bu durumda bir özel durum oluşturulmasına izin verilir. Ancak özel durumlar oluşturuyorsanız, bu dönüştürmeyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulamanızın bir parçası olarak kullanmayı bildirmelisiniz, böylelikle özel durumların önüne geçmek için en iyi şekilde <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> kontrol altına almanız gerekir.  
  
 `destinationType` Parametre türü<xref:System.String>değilse, kendi dönüştürücü işleme seçeneğini belirleyebilirsiniz. Genellikle, temelde <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durumu oluşturan temel uygulama işlemeye dönülür.  
  
### <a name="implementing-canconvertto"></a>Canconvertuygulama  
 Uygulamanız türü `true` içindöndürmelidir`destinationType` , aksi takdirde temel uygulamaya ertelemelidir. <xref:System.String> <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
### <a name="implementing-canconvertfrom"></a>Canconvertuygulama  
 Uygulamanız türü `true` içindöndürmelidir`sourceType` , aksi takdirde temel uygulamaya ertelemelidir. <xref:System.String> <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Özel tür dönüştürücüsünün bir XAML işlemcisi tarafından özel bir sınıf için davranan tür dönüştürücüsü olarak kullanılabilmesi için, <xref:System.ComponentModel.TypeConverterAttribute> öğesini sınıf tanımınıza uygulamanız gerekir. Özniteliği <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> aracılığıyla belirttiğiniz, özel tür dönüştürücünün tür adı olmalıdır. Bu öznitelik uygulandığında, XAML işlemcisi özellik türünün özel sınıf türünü kullandığı değerleri işlediğinde, dizeleri belirtebilir ve nesne örnekleri döndürebilir.  
  
 Ayrıca özellik başına bir tür dönüştürücüsü sağlayabilirsiniz. Sınıf tanımına bir <xref:System.ComponentModel.TypeConverterAttribute> uygulamak yerine, bunu bir özellik tanımına (Ana tanım, içindeki `set` uygulamaları `get` / değil) uygulayın. Özelliğin türü, özel tür dönüştürücülü tarafından işlenen türle eşleşmelidir. Bu öznitelik uygulandığında, bir XAML işlemcisi bu özelliğin değerlerini işlediğinde, giriş dizelerini işleyebilir ve nesne örnekleri döndürebilir. Özellik başına tür dönüştürücüsü tekniği, Microsoft .net çerçevesinden veya sınıf tanımını denetleyemeyip bir başka kitaplıktan bir <xref:System.ComponentModel.TypeConverterAttribute> Özellik türü kullanmayı tercih ediyorsanız özellikle yararlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverter>
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
