---
title: TypeConverters ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: ec6eaadae1dd7a7db84538c24e396a14db1a65a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164997"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters ve XAML
Bu konu, genel XAML dil özelliği olarak dizeden tür dönüştürme amacı tanıtır. .NET Framework'teki <xref:System.ComponentModel.TypeConverter> sınıfı XAML öznitelik kullanımı bir özellik değeri olarak kullanılabilecek özel bir yönetilen sınıf uygulamasını bir parçası olarak belirli bir amaca hizmet. Özel bir sınıf yazma ve XAML ayarlanabilir öznitelik değeri olarak kullanılabilmesi için bir sınıfın örneklerini istiyorsanız uygulamak ihtiyacınız olabilecek bir <xref:System.ComponentModel.TypeConverterAttribute> sınıfınıza, özel bir yazma <xref:System.ComponentModel.TypeConverter> sınıfı veya her ikisini de.  

## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 Bir XAML dosyasında bir öznitelik değeri ayarladığınızda, ilk değeri bir dize içinde salt metin türüdür. Hatta diğer ilkel gibi <xref:System.Double> başlangıçta metin dizelerdir XAML işlemci için.  
  
 XAML işlemci bir öznitelik değeri işlemek için iki parça bilgi gerekir. Bilgi ilk parçasını ayarlanan özelliğin bir değer türüdür. XAML içinde işlenir ve bir öznitelik değeri tanımlayan herhangi bir dize olmalıdır sonuçta dönüştürülecek veya o türün değerine çözümlendi. Değer (örneğin, sayısal bir değer) XAML ayrıştırıcı tarafından anlaşılan basit bir tür ise, dize doğrudan dönüştürme denenir. Bir sabit listesi değeri ise, dize, numaralandırma, adlandırılmış bir sabit bir adı eşleşme olup olmadığını denetlemek için kullanılır. Değer ne ayrıştırıcı anlaşılan bir temel ya da bir numaralandırma sonra söz konusu türü ise sağlayabilir veya bir dönüştürülmüş dizesine dayalı bir değer türü örneği olmalıdır. Bu, bir tür dönüştürücüsü sınıfı belirterek gerçekleştirilir. Tür dönüştürücüsünü etkili bir şekilde kod içinde .NET kodda çağırır XAML senaryosu için hem de başka bir sınıf değerlerini sağlamak için bir yardımcı sınıftır.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML içinde mevcut türü dönüştürme davranışını kullanarak  
 Temel XAML kavramları, aşinalık bağlı olarak, zaten türü dönüştürme davranışını temel uygulama XAML fark etmeden kullanıyor olabilir. Örneğin, WPF türünde bir değer alan özellikleri yüzlerce tanımlar <xref:System.Windows.Point>. A <xref:System.Windows.Point> iki boyutlu bir koordinat alanında bir koordinat açıklayan bir değerdir ve aslında iki önemli özellikleri vardır: <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A>. XAML içinde bir noktaya belirttiğinizde, (genellikle bir virgül) sınırlayıcı bir dize olarak arasında belirtmeden <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A> sağladığınız değerler. Örneğin: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`  
  
 Bu basit tür bile <xref:System.Windows.Point> ve basit kullanımını XAML içinde bir tür dönüştürücüsü içerir. Bu durumda, sınıf, <xref:System.Windows.PointConverter>.  
  
 Tür dönüştürücü <xref:System.Windows.Point> Süren tüm özellikleri biçimlendirme kullanımları sınıf düzeyinde ölçeklendirerek tanımlanan <xref:System.Windows.Point>. Bir tür dönüştürücüsü Burada, aşağıdakiler gerekir. daha önce gösterilen aynı örneği için çok daha ayrıntılı biçimlendirmesini:  

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
  
 Tür dönüştürme dize veya daha ayrıntılı bir eşdeğer sözdizimi kullanmak için genellikle bir kodlama stili bir seçimdir. XAML araçları akışınız, değerlerin nasıl ayarlanacağı da etkileyebilir. Bazı XAML araçları gidiş dönüş Tasarımcı görünümleri ya da kendi seri hale getirme mekanizması için daha kolay olduğundan, en ayrıntılı form biçimlendirme yayma eğilimindedir.  
  
 Var olan tür dönüştürücüleri genellikle bulunması WPF ve .NET Framework türleri üzerinde bir sınıf (ya da özellik) uygulanan bir varlığını denetleyerek <xref:System.ComponentModel.TypeConverterAttribute>. Bu öznitelik, XAML amacıyla hem de büyük olasılıkla diğer amaçlar için bu türü değerlerinin destekleyen tür dönüştürücüsünü sınıfı adını vereceğiz.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüleri ve İşaretleme uzantıları  
 İşaretleme uzantıları ve tür dönüştürücüleri XAML işlemci davranışı ve uygulanacak olan senaryoları açısından dikgen rolleri doldurun. Bağlam için işaretleme uzantısı kullanımları kullanılabilir olsa da, burada bir değerdir genellikle bir işaretleme uzantısı sağlar. özellikleri türü dönüştürme davranışını işaretleme uzantısı uygulamalarında işaretlenmemiştir. Diğer bir deyişle, bile bir işaretleme uzantısı bir metin dizesi olarak döndürür, `ProvideValue` çıkışı, belirli özellik ya da özellik değeri türü uygulanan olarak bu dize türü dönüştürme davranışını değil çağrılır, genellikle, bir işaretleme uzantısı amacı işlemidir bir dize ve ilgili herhangi bir tür dönüştürücüsü olmadan bir nesne döndürür.  
  
 İşaretleme uzantısı yerine bir tür dönüştürücüsü gerekli olduğu bir yaygın durum zaten var. bir nesneye bir başvuru sağlamaktır. En iyi durum bilgisi olmayan bir tür dönüştürücüsü yalnızca istenen olmayabilir yeni bir örneği oluşturabilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüleri  
 WPF ve .NET Framework uygulamasında XAML ayrıştırıcı, henüz genel temel olarak zorlayıcı olabilir türleri değil, yerel bir tür dönüştürme işleme sahip bazı türleri vardır. Böyle bir türü örneğidir <xref:System.DateTime>. Bunun nedeni, .NET Framework mimarisini nasıl çalıştığını temel alır: türü <xref:System.DateTime> mscorlib, .NET en temel kitaplığında tanımlanır. <xref:System.DateTime> bir bağımlılık tanıtan başka bir bütünleştirilmiş koddan gelen bir öznitelik ile öznitelikli izin verilmiyor (<xref:System.ComponentModel.TypeConverterAttribute> sisteminden alınmıştır) normal türü dönüştürücü bulma mekanizmasından'öznitelik atanıyor tarafından desteklenebilmesi için. Bunun yerine, XAML ayrıştırıcı gibi yerel işlenmesi gereken türlerinin bir listesi vardır ve bunlar true temelleri nasıl işlendiği için benzer şekilde işler. (Durumunda <xref:System.DateTime> bu bir çağrı içerir <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür dönüştürücü uygulama  
  
### <a name="typeconverter"></a>TypeConverter  
 İçinde <xref:System.Windows.Point> sınıfı daha önce verilen örnek <xref:System.Windows.PointConverter> bahsedilen. XAML .NET uygulamaları için XAML amaçlarıyla kullanılan tüm tür dönüştürücüleri temel sınıfından türetilir sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Sınıfı XAML varlığını önünde .NET Framework sürümleri içinde vardı; kendi özgün kullanımlarından dize dönüştürme için görsel tasarımcılar özelliği iletişim kutularında sağlamak için. XAML, rolü için <xref:System.ComponentModel.TypeConverter> öznitelik dize ayrıştırma ve büyük olasılıkla bir dize halinde geri belirli nesne özelliği çalışma zamanı değerini işleme-dize ve dize öğesinden dönüştürme için temel sınıfı olan içerecek şekilde genişletilmiş özniteliği olarak seri hale getirme.  
  
 <xref:System.ComponentModel.TypeConverter> ve dizeleri XAML işleme amacıyla bu nesnelerden dönüştürme için uygun olan dört üyeleri tanımlar:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu en önemli yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Bu yöntem, Giriş dizesinin gerekli nesne türüne dönüştürür. NET olarak söylemek gerekirse, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yönteminin çok geniş bir tür Dönüştürücüsü'nın hedeflenen hedef türüne dönüştürün ve bu nedenle çalışma zamanı dönüştürmeleri destekleyen gibi ancak XAML amacıyla XAML genişletmek amacıyla hizmet uygulanmasını işleyebilen kod yolu olan bir <xref:System.String> önemli giriş.  
  
 Sonraki en önemli yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. (Örneğin, XAML dosyası olarak kaydedilir) bir uygulama için bir biçimlendirme gösterimi dönüştürülür varsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme gösterimi üretmek için sorumludur. XAML için önemli kod yolu geçirdiğinizde bu durumda olduğu bir `destinationType` , <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> yeteneklerini hizmet sorgu oluştururken kullanılan destek yöntemleri <xref:System.ComponentModel.TypeConverter> uygulaması. Döndürmek için bu yöntemleri uygulamalıdır `true` , türe özgü durumda, dönüştürücü eşdeğer dönüştürme yöntemleri destekler. XAML amacıyla, bu genellikle anlamına gelir <xref:System.String> türü.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Kültür bilgilerini ve XAML için tür dönüştürücüleri  
 Her <xref:System.ComponentModel.TypeConverter> uygulama bir dönüştürme için geçerli bir dize nelerden kendi yorumlama sahip ve ayrıca kullanın veya parametre olarak geçirilen türü açıklaması yoksay. Kültür ve XAML tür dönüştürme ile ilgili önemli bir husus vardır. Yerelleştirilebilir Dize öznitelik değerleri kullanılarak, tamamen XAML tarafından desteklenir. Ancak, belirli bir kültürün gereksinimleri ile dönüştürücü giriş türü desteklenmediğinden bu yerelleştirilebilir dize kullanarak XAML öznitelik değerleri için tür dönüştürücüleri mutlaka sabit dil ayrıştırma davranışı hatalarıyla ilgili olduğundan, kullanarak `en-US` kültür. Bu kısıtlama tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimi danışmalıdır ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Burada kültür bir sorun olabilir örneğin, bazı kültürlerde sayılar için ondalık ayırıcı olarak virgül kullanın. Bu, ayırıcı olarak virgül WPF XAML tür dönüştürücüleri çoğunu içeren davranış birbiriyle çakışır (Geçmiş Etkileyenler gibi ortak X bağlı olarak, Y form veya virgülle ayrılmış listeleri). Bir kültür çevreleyen XAML içinde bile geçirme (ayar `Language` veya `xml:lang` için `sl-SI` kültür, virgül, ondalık bu şekilde kullanımları bir kültür örneği) sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 Olarak kullanılabilir bir <xref:System.ComponentModel.TypeConverter> XAML, destekleyen bir uygulama <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi Bu dönüştürücü için bir dize olarak kabul etmelisiniz `value` parametresi. Dize geçerli biçimlendirmek ve tarafından dönüştürülebilir olup olmadığını <xref:System.ComponentModel.TypeConverter> uygulama sonra döndürülen nesne bir özellik tarafından beklenen türe dönüştürme desteklemesi gerekir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama döndürmelidir `null`.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulama bir dönüştürme için geçerli bir dize nelerden kendi yorumlama sahip ve ayrıca kullanın veya parametre olarak geçirilen tür açıklaması veya kültür bağlamı yoksay. Ancak, işleme WPF XAML değerleri türü açıklaması içeriği tüm durumlarda geçebilir değil ve kültüre göre de geçirmemesi `xml:lang`.  
  
> [!NOTE]
>  Küme ayracı karakterleri özellikle kullanmayın {, dize biçiminiz olası öğesi olarak. Bu karakterler, giriş ve çıkış bir işaretleme uzantısı sırası olarak ayrılmıştır.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Potansiyel olarak seri hale getirme desteği için kullanılır. Serileştirme desteğini <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> özel türünüzü ve kendi türü için dönüştürücü mutlak bir gereksinim değildir. Ancak, bir denetimi uygulamak veya tasarım sınıfınızın veya özellikleri bir parçası serileştirilmesi kullanarak, uygulamalıdır <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Olarak kullanılabilir bir <xref:System.ComponentModel.TypeConverter> XAML, destekleyen bir uygulama <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> yöntemi Bu dönüştürücü için kabul etmelisiniz desteklenmekte türü (veya bir değer) örneği olarak `value` parametresi. Zaman `destinationType` parametre türüdür <xref:System.String>, döndürülen nesne olarak yayınlanması gereken sonra <xref:System.String>. Döndürülen dize bir seri hale getirilmiş değerini temsil etmelidir `value`. İdeal olarak, seçtiğiniz serileştirme biçimi bu dize geçirilmiş aynı değeri oluşturma yeteneği olmalıdır <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> önemli bilgi kaybı olmadan aynı dönüştürücü uygulamasıdır.  
  
 Değeri serileştirilemez veya seri hale getirme, dönüştürücü desteklemiyor <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null`ve bu durumda bir özel durum oluşturmasına izin verilir. Ancak özel durumlar ise bir parçası olarak bu dönüştürme kullanılacak yükleyememesine raporlamalıdır, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulama böylece ile denetimi en iyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ilk özel durumları engellemek için desteklenir.  
  
 Varsa `destinationType` parametresi türü değil <xref:System.String>, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, işleme, hangi basemost temel uygulamaya geri <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum oluşturur.  
  
### <a name="implementing-canconvertto"></a>CanConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> Uygulamasına dönmesi gerektiğini `true` için `destinationType` türü <xref:System.String>ve aksi için temel uygulama erteleyin.  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> Uygulamasına dönmesi gerektiğini `true` için `sourceType` türü <xref:System.String>ve aksi için temel uygulama erteleyin.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Sırayla olarak görev yapan kullanılmak üzere kendi özel tür dönüştürücü için tür dönüştürücüsünü bir XAML işlemcisi tarafından özel bir sınıf için uygulamalısınız [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımı. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Özniteliğiyle belirtin, özel bir tür dönüştürücüsü türü adı olması gerekir. Bu özniteliği uygulandı, ile XAML işlemci değerleri nerede özellik türü, özel bir sınıf türünü kullanan işlediğinde, bu giriş dizeleri ve nesne örneği döndürür.  
  
 Özellik başına temelinde bir tür dönüştürücüsü de sağlayabilirsiniz. Uygulama yerine bir [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> isteğe bağlı olarak sınıf tanımının bir özellik tanımı için geçerlidir (ana tanım değil `get` / `set` içindeki uygulamaları). Özelliğin türü, özel bir tür dönüştürücüsü tarafından işlenen türüyle eşleşmelidir. Bu özniteliği uygulandı, ile bir XAMLprocessor bu özellik değerlerini işlediğinde, bu işlem giriş dizesi ve nesne örneği döndürür. Özellik başına türü dönüştürücü özellik türü Microsoft .NET Framework veya sınıf tanımı kontrol ve uygulanamıyor burada bazı diğer kitaplığı kullanmayı tercih ederseniz özellikle kullanışlı bir tekniktir bir <xref:System.ComponentModel.TypeConverterAttribute> vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverter>
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
