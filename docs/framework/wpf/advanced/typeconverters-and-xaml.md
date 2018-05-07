---
title: TypeConverters ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: a6d41b5ad519302016ed7fa1d6a103af0f4f14d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="typeconverters-and-xaml"></a>TypeConverters ve XAML
Bu konu, bir genel XAML dil özellik olarak dizesinden tür dönüştürme amacı tanıtır. .NET Framework'teki <xref:System.ComponentModel.TypeConverter> sınıfı XAML öznitelik kullanımı özellik değeri olarak kullanılabilecek özel bir yönetilen sınıf uygulamasını bir parçası olarak belirli bir amaca hizmet. Özel bir sınıf yazma ve XAML ayarlanabilir öznitelik değerleri kullanılabilmesi için sınıf örneklerinin istiyorsanız uygulamak gerekebilecek bir <xref:System.ComponentModel.TypeConverterAttribute> sınıfınıza, özel bir yazma <xref:System.ComponentModel.TypeConverter> sınıfı ya da her ikisini de.  
  

  
## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyası içinde bir öznitelik değeri ayarladığınızda, ilk değer bir dize saf metinde türüdür. Hatta başka ilkel gibi <xref:System.Double> başlangıçta metin dizesinin bir XAML işlemciye olup.  
  
 XAML işlemci bir öznitelik değeri işlemek için iki parça bilgi gerekir. İlk ayarlı özellik değeri türü bilgidir. Bir öznitelik değeri tanımlar ve XAML'de işlenen herhangi bir dize sonuçta dönüştürülen veya gerekir bu türde bir değer çözümlendi. Değer (örneğin, bir sayısal değer) XAML ayrıştırıcısı tarafından anlaşılan basit bir tür ise, dizenin doğrudan dönüştürme denenir. Numaralandırma değeri geçerliyse dize adı eşleşir, numaralandırma adlandırılmış bir sabite denetlemek için kullanılır. Değer ne ayrıştırıcı anladım ilkel veya numaralandırma, söz konusu türü ise örneği türü veya dönüştürülmüş dizesini temel alan bir değer sağlayabilir olmalıdır. Bu tür dönüştürücü sınıfı belirtilerek gerçekleştirilir. Tür dönüştürücüsünü etkili bir şekilde kod .NET kodda çağırır için XAML senaryo hem de büyük olasılıkla başka bir sınıf değerlerini sağlamak için bir yardımcı sınıfıdır.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Var olan tür dönüştürme davranışı XAML içinde kullanma  
 Temel alınan XAML kavramları, benzerlik bağlı olarak, tür dönüştürme davranışını temel uygulamada XAML kullanıldıklarını olmadan kullanıyor olabilir. Örneğin, WPF türünde bir değer olması özellikleri yüzlerce tanımlar <xref:System.Windows.Point>. A <xref:System.Windows.Point> koordinat iki boyutlu koordinat alanında açıklayan bir değerdir ve gerçekten yalnızca iki önemli özelliklere sahiptir: <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A>. XAML'de bir noktası belirttiğinizde, bir sınırlayıcı (genellikle bir virgül) ile bir dize olarak arasında belirtmeden <xref:System.Windows.Point.X%2A> ve <xref:System.Windows.Point.Y%2A> sağladığınız değerleri. Örneğin: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`.  
  
 Bu basit tür bile <xref:System.Windows.Point> ve basit kullanım XAML'de tür dönüştürücüsünü içerir. Bu durumda, sınıftır <xref:System.Windows.PointConverter>.  
  
 İçin tür dönüştürücüsünü <xref:System.Windows.Point> sınıf düzeyinde ölçeklendirerek ele tüm özelliklerin biçimlendirme kullanımları tanımlanan <xref:System.Windows.Point>. Tür dönüştürücüsünü Burada, aşağıdaki gerekir daha önce gösterilen aynı örneği için çok daha ayrıntılı biçimlendirme:  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 Tür dönüştürme dize ya da daha ayrıntılı bir eşdeğer sözdizimi kullanıp kullanmayacağınızı genellikle bir kodlama stili seçimdir. XAML araç akışınızı ayrıca değerleri nasıl ayarlanacağını etkileyebilir. Bazı XAML Araçlar gidiş Tasarımcı görünümleri ya da kendi seri hale getirme mekanizmasını daha kolay olduğundan en ayrıntılı formun biçimlendirme yayma eğilimindedir.  
  
 Var olan tür dönüştürücüleri genellikle keşfedilecek WPF ve .NET Framework türlerinde sınıfı (veya özelliği) bir uygulanmış olup olmadığını kontrol ederek <xref:System.ComponentModel.TypeConverterAttribute>. Bu öznitelik XAML amacıyla yanı sıra potansiyel olarak diğer amaçlar için bu türü değerleri için destekleyici türü dönüştürücü sınıfı adı.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüleri ve İşaretleme uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüleri XAML işlemci davranışı ve bunlar uygulanır senaryolar açısından resme rolleri doldurun. Bağlam için işaretleme uzantısı kullanımları kullanılabilir olsa da, burada biçimlendirme uzantısı genellikle değerdir sağlar özellikleri türü dönüştürme davranışını biçimlendirme uzantısı uygulamalarında işaretlenmemiştir. Diğer bir deyişle, biçimlendirme uzantısı bir metin dizesi olarak döndürür olsa bile, `ProvideValue` çıkışı, belirli özellik ya da özellik değeri türü uygulanan olarak bu dize türü dönüştürme davranışını değil çağrıldığında, genellikle, bir işaretleme uzantısı amacı işlemdir bir dize ve dönüş türü dönüştürücünün söz konusu olmadan bir nesne.  
  
 Biçimlendirme uzantısı yerine tür dönüştürücüsünü gerekli olduğu bir ortak zaten bir nesneye başvuru yapmak için bir durumdur. En iyi durum bilgisiz tür dönüştürücüsünü yalnızca arzu olmayabilir yeni bir örneği üretebilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüleri  
 XAML ayrıştırıcısı WPF ve .NET Framework uygulamasında henüz işleme, genel temelleri düşünülen türleri değil, yerel tür dönüştürme işleme sahip belirli türü vardır. Bu tür bir türü örneği <xref:System.DateTime>. Bunun nedeni, .NET Framework mimari nasıl çalıştığı hakkında temel alır: türü <xref:System.DateTime> mscorlib, .NET en temel kitaplıkta tanımlanır. <xref:System.DateTime> bir bağımlılık tanıtır başka bir derlemeden gelen özniteliğine sahip öznitelikli izin verilmiyor (<xref:System.ComponentModel.TypeConverterAttribute> sistemden olduğu) öznitelik atanıyor tarafından her zamanki türü dönüştürücü bulma mekanizmasından desteklenemez şekilde. Bunun yerine, XAML ayrıştırıcısı gibi yerel işleme gerek türlerinin bir listesi vardır ve bunlar true temelleri nasıl işlendiği benzer şekilde işler. (Durumunda <xref:System.DateTime> bu yapılan bir çağrı içerir <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür dönüştürücüsünü uygulama  
  
### <a name="typeconverter"></a>TypeConverter  
 İçinde <xref:System.Windows.Point> sınıfı daha önce verilen örnek <xref:System.Windows.PointConverter> değinilen. XAML .NET uygulamaları için XAML amacıyla kullanılan tüm tür dönüştürücüleri temel sınıfından türetilen sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Sınıfı XAML varlığını koyun .NET Framework sürümleri içinde vardı; kendi özgün kullanımlarından özelliği iletişim kutularında görsel tasarımcılar dize dönüştürme sağlamak için. XAML, rolü <xref:System.ComponentModel.TypeConverter> bir dize öznitelik değeri ayrıştırma ve büyük olasılıkla bir dize uygulamasına geri belirli nesne özelliğinin bir çalışma zamanı değeri işleme etkinleştirmek için dize ve dize öğesinden dönüştürmeleri için temel sınıfı olan içerecek şekilde genişletilmiş Serileştirme özniteliği olarak.  
  
 <xref:System.ComponentModel.TypeConverter> XAML işleme amacıyla dizeleri gelen ve giden dönüştürmek için uygun olan dört üyeleri tanımlar:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu, en önemli bir yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Bu yöntem giriş dizesini gerekli nesne türüne dönüştürür. NET olarak söylemek <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemin çok geniş bir türü dönüştürücü 's hedeflenen hedef türüne dönüştürün ve böylece çalışma zamanı dönüşümleri destekleme gibi ancak XAML amacıyla XAML genişletmek amaca hizmet eder yalnızca işleyebilir kod yolu olan bir <xref:System.String> önemli giriş.  
  
 Sonraki en önemli yöntemi <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. (Örneğin, XAML dosyası olarak kaydedilir) bir uygulama bir biçimlendirme gösterimine dönüştürülür varsa, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> biçimlendirme gösterimi oluşturmaktan sorumludur. Geçirdiğiniz bu durumda, XAML için önemli kod yolu olduğunda bir `destinationType` , <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> hizmet özelliklerini sorguladığında kullanılan destek yöntemleri <xref:System.ComponentModel.TypeConverter> uygulaması. Döndürmek için bu yöntemleri uygulamalıdır `true` türüne özgü durumlarda, dönüştürücü eşdeğer dönüştürme yöntemleri desteği. XAML amacıyla, bu genellikle anlamına gelir <xref:System.String> türü.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Kültür bilgilerini ve XAML için tür dönüştürücüleri  
 Her <xref:System.ComponentModel.TypeConverter> uygulaması bir dönüştürme için geçerli bir dize nelerin oluşturduğunu kendi yorumlama sahip ve ayrıca kullanın veya parametre olarak geçirilen türü açıklaması yoksay. Kültür ve XAML tür dönüştürme açısından önemli bir konu yoktur. Öznitelik değerleri yerelleştirilebilir dizeleriyle XAML tarafından tamamen desteklenir. Ancak türü dönüştürücü giriş kültürü gereksinimleriyle desteklenmediği XAML öznitelik değerleri için tür dönüştürücüleri mutlaka sabit dil ayrıştırma davranışı içerdiğinden bu yerelleştirilebilir dize kullanmak, kullanarak `en-US` kültür. Bu kısıtlama tasarım nedenleri hakkında daha fazla bilgi için XAML dil belirtimi danışmalısınız ([\[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Burada, kültür bir sorun olabilir örnek olarak, bazı kültürler sayılar için kendi ondalık ayırıcı olarak virgül kullanın. Bu, ayırıcı olarak virgül kullanılacak olan birçok WPF XAML tür dönüştürücüleri olan davranışı birbiriyle çakışır (ortak X gibi geçmiş Etkileyenler bağlı olarak, Y form veya virgülle ayrılmış listesi). Bile bir kültür çevresindeki XAML'de geçirme (ayar `Language` veya `xml:lang` için `sl-SI` kültür, bu şekilde ondalık virgül kullanımları bir kültür örneği) sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 Olarak kullanılabilmesi için bir <xref:System.ComponentModel.TypeConverter> XAML destekleyen uygulama <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi Bu dönüştürücü için bir dize olarak kabul etmelisiniz `value` parametresi. Dize geçerli biçimlendirmek ve tarafından dönüştürülebilir olup olmadığını <xref:System.ComponentModel.TypeConverter> uygulama daha sonra döndürülen nesne bir özellik tarafından beklenen türe dönüştürme desteklemesi gerekir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama döndürmelidir `null`.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulama bir dönüştürme için geçerli bir dize nelerin oluşturduğunu kendi yorumlama sahip ve ayrıca kullanın veya parametre olarak geçirilen türü açıklama veya kültüre içerikler yoksay. Ancak, işleme WPF XAML değerleri türü açıklaması bağlamını tüm durumlarda geçebilir değil ve ayrıca göre kültür geçebilir değil `xml:lang`.  
  
> [!NOTE]
>  Süslü ayraç karakterleri özellikle kullanmayın {, dize biçim olası bir öğe olarak. Bu karakterleri olarak giriş ve çıkış biçimlendirme uzantısı sırası için ayrılmıştır.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> büyük olasılıkla seri hale getirme desteği için kullanılır. Seri hale getirme desteğini <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> özel türünüz ve onun türü için dönüştürücü kesin bir gereklilik değildir. Bir denetimi uygulamak veya özelliklerin bir kısmı veya sınıfınızın tasarım serileştirmek kullanarak, ancak uygulamalıdır <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Olarak kullanılabilmesi için bir <xref:System.ComponentModel.TypeConverter> XAML destekleyen uygulama <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> yöntemi Bu dönüştürücü için kabul etmelisiniz desteklenmekte olan türü (veya bir değer) örneği olarak `value` parametresi. Zaman `destinationType` parametredir türü <xref:System.String>, döndürülen nesne olarak cast mümkün sonra <xref:System.String>. Döndürülen dize serileştirilmiş değerini temsil etmelidir `value`. İdeal olarak, seçtiğiniz seri hale getirme biçimi için bu dizeyi geçirilmiş varsa aynı değeri oluşturma yeteneği olmalıdır <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> önemli bilgi kaybı olmadan aynı dönüştürücü uygulamasıdır.  
  
 Değer seri hale getirilemez veya dönüştürücü serileştirme, desteklemiyor <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null`, bu durumda bir özel durum erişmesine izin. Ancak özel durumlar oluşturma, bir parçası olarak bu dönüştürme kullanamama bildirmelisiniz, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulama böylece ile denetimi en iyi uygulama olarak <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ilk özel durumları önlemek için desteklenir.  
  
 Varsa `destinationType` parametresi türü değil <xref:System.String>, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, işleme, hangi basemost temel uygulamasına geri <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum oluşturur.  
  
### <a name="implementing-canconvertto"></a>CanConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> Uygulama döndürmelidir `true` için `destinationType` türü <xref:System.String>ve aksi durumda temel uygulamayı erteleneceği.  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> Uygulama döndürmelidir `true` için `sourceType` türü <xref:System.String>ve aksi durumda temel uygulamayı erteleneceği.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulama  
 Sırayla gibi davranan kullanılması için özel tür dönüştürücü için XAML işlemcisi tarafından özel bir sınıf için tür dönüştürücüsünü, uygulamalısınız [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımı. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Özniteliğiyle belirttiğiniz özel tür dönüştürücü türü adı olması gerekir. Uygulanan, bu öznitelik ile XAML işlemci değerleri nerede özellik türü, özel bir sınıf türü kullanan işlediğinde, bu giriş dizeleri ve nesne örneklerini döndürür.  
  
 Ayrıca bir özelliği başına temelinde tür dönüştürücüsünü sağlayabilir. Uygulama yerine bir [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> bir özellik tanımını uygulayan sınıf tanımına (ana tanımı değil `get` / `set` içindeki uygulamaları). Özelliğinin türü, özel tür dönüştürücü tarafından işlenen türü eşleşmelidir. Uygulanan, bu öznitelik ile bu özelliğin değerleri, bir XAMLprocessor işlediğinde, bu işlem giriş dizelerini ve dönüş nesne örnekleri. Özellik başına türü dönüştürücü teknik bir özellik türü Microsoft .NET Framework veya burada sınıf tanımını denetleyemezsiniz ve uygulanamıyor bazı diğer kitaplığı kullanmayı tercih ederseniz özellikle yararlıdır bir <xref:System.ComponentModel.TypeConverterAttribute> vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.TypeConverter>  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
