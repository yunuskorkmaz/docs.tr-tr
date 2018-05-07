---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: df6b7f212a60d8d51bb684891055de7e285ddf4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-converters-for-xaml-overview"></a>XAML Tür Dönüştürücülerine Genel Bakış
XAML biçimlendirme içinde bir dizeden bir nesne grafiğinin belirli nesneleri dönüştürür bir nesne yazıcısı için tür dönüştürücüleri tedarik mantığı. .NET Framework XAML hizmetlerinde tür dönüştürücüsünü türeyen bir sınıf olmalıdır <xref:System.ComponentModel.TypeConverter>. Bazı dönüştürücüler ayrıca kaydetme yolu XAML destekler ve Serileştirme biçimlendirmede dize forma bir nesne seri hale getirmek için kullanılabilir. Bu konuda nasıl ve ne zaman tür dönüştürücüleri XAML'de çağrılır ve yöntemini geçersiz kılar, uygulama önerileri sağlar açıklanmaktadır <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
 Aşağıdaki bölümlerde, XAML dizeleri nasıl kullandığı ve .NET Framework XAML hizmetlerinde nesne yazıcılarının bazı XAML kaynağında karşılaşılan dize değerleri işlemek için tür dönüştürücüleri kullanımı hakkında temel kavramlarını açıklar.  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 XAML dosyası içinde bir öznitelik değeri ayarladığınızda, bu değerin ilk türü genel bir fikir dizesinde ve bir XML anlamlı bir dize öznitelik değeri ' dir. Hatta başka ilkel gibi <xref:System.Double> başlangıçta XAML işlemci dizelerdir.  
  
 Çoğu durumda, bir XAML işlemci iki ayrı bir öznitelik değeri işlemek için bilgi gerekiyor. İlk ayarlı özellik değeri türü bilgidir. Bir öznitelik değeri tanımlar ve XAML'de işlenen herhangi bir dize sonuçta dönüştürülen veya gerekir bu türde bir değer çözümlendi. Değer (örneğin, bir sayısal değer) XAML ayrıştırıcısı tarafından anlaşılan basit bir tür ise, dizenin doğrudan dönüştürme denenir. Öznitelik değeri numaralandırma başvuruyorsa, sağlanan dize Bu numaralandırma adlandırılmış bir sabite ad eşleştirmesi için denetlenir. Değer bir ayrıştırıcı anladım temel ne numaralandırma sabit adı ise, geçerli bir değer veya bir dönüştürülen dizesine dayalı başvuru sağlayabilir türünden olmalıdır.  
  
> [!NOTE]
>  XAML dil yönergeleri tür dönüştürücüleri kullanmayın.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüleri ve İşaretleme uzantıları  
 Özellik türü ve diğer konular için denetlemeden önce biçimlendirme uzantısı kullanımları XAML işlemcisi tarafından işlenen gerekir. Öznitelik bir tür dönüştürme normalde olduğu gibi ancak belirli bir durumda ayarlanan bir özelliği bir biçimlendirme uzantısı kullanımı tarafından ayarlanırsa, örneğin, ardından biçimlendirme uzantısı davranışı ilk işler. Biçimlendirme uzantısı gerekli olduğu bir ortak zaten bir nesneye başvuru yapmak için bir durumdur. Bu senaryo için durum bilgisiz tür dönüştürücüsünü arzu olmayabilir yeni bir örneği yalnızca oluşturabilir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüleri  
 WPF ve .NET XAML Hizmetleri uygulamalarında yerel tür dönüştürme işleme belirli CLR türleri vardır, ancak bu CLR Türleri işleme, genel temelleri düşünülen değil. Bu tür bir türü örneği <xref:System.DateTime>. Bunun bir nedeni olan .NET Framework mimari nasıl çalıştığı: türü <xref:System.DateTime> mscorlib, .NET en temel kitaplıkta tanımlanır. <xref:System.DateTime> bir bağımlılık tanıtır başka bir derlemeden gelen özniteliğine sahip öznitelikli izin verilmiyor (<xref:System.ComponentModel.TypeConverterAttribute> sistemden olduğu); bu nedenle, öznitelik atanıyor tarafından her zamanki türü dönüştürücü bulma mekanizmasından desteklenemez. Bunun yerine, yerel işleme gerek türlerinin bir listesini XAML ayrıştırıcısı vardır ve bu tür true temelleri nasıl işlendiği için benzer işler. Durumunda <xref:System.DateTime>, bu işlem için bir çağrı içerir <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür dönüştürücüsünü uygulama  
 Aşağıdaki bölümlerde API'si açıklanmaktadır <xref:System.ComponentModel.TypeConverter> sınıfı.  
  
### <a name="typeconverter"></a>TypeConverter  
 .NET Framework XAML Hizmetleri altında XAML amacıyla kullanılan tüm tür dönüştürücüleri temel sınıfından türetilen sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Sınıfı XAML var önce; .NET Framework'ün sürümlerinde var özgün birini <xref:System.ComponentModel.TypeConverter> senaryoları olan görsel tasarımcılar özelliği düzenleyicilerde dize dönüştürme sağlamak için.  
  
 XAML, rolü <xref:System.ComponentModel.TypeConverter> genişletilir. XAML amacıyla <xref:System.ComponentModel.TypeConverter> belirli dize için ve dize öğesinden dönüştürmeleri için destek sağlamak için temel sınıftır. Dize öğesinden XAML dize öznitelik değerinden ayrıştırma sağlar. Dize için XAML özniteliğin serileştirme için uygulamasına geri belirli nesne özelliğinin bir çalışma zamanı değeri işleme etkinleştirebilir.  
  
 <xref:System.ComponentModel.TypeConverter> dize için ve gelen-dize XAML işleme amacıyla dönüştürmek için uygun olan dört üyeleri tanımlar:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu üyeleri en önemli yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, gerekli nesne türü giriş dizesi dönüştürür. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Yöntemi, geniş bir türleri dönüştürücü hedeflenen hedef türüne dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüşümleri destekleme gibi XAML genişletmek amacıyla hizmet verebilir. Ancak, XAML kullanmak, yalnızca işleyebilir kod yolu için bir <xref:System.String> giriş önemlidir.  
  
 İkinci en önemli yöntemi <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama (örneğin XAML dosyası olarak kaydedilir,), bir işaretleme gösterimi dönüştürülürse <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> XAML metin yazıcılarının ürettiği biçimlendirme gösterim büyük senaryoda karmaşıktır. Arayan geçtiğinde bu durumda, önemli kod XAML yoludur bir `destinationType` , <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> hizmet özelliklerini sorguladığında kullanılan destek yöntemleri <xref:System.ComponentModel.TypeConverter> uygulaması. Döndürmek için bu yöntemleri uygulamalıdır `true` türüne özgü durumlarda, dönüştürücü eşdeğer dönüştürme yöntemleri desteği. XAML amacıyla, bu genellikle anlamına gelir <xref:System.String> türü.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Kültür bilgilerini ve XAML için tür dönüştürücüleri  
 Her <xref:System.ComponentModel.TypeConverter> uygulaması, dönüştürme için geçerli bir dize nedir benzersiz olarak yorumlayabilir ve bu da kullanabilir veya parametre olarak geçirilen türü açıklaması yoksay. Kültür ve XAML dönüştürme türü için önemli bir konu aşağıdadır: öznitelik değerleri yerelleştirilebilir dizeleriyle XAML tarafından desteklenmesine karşın, belirli kültür gereksinimleriyle türü dönüştürücü girdi olarak bu yerelleştirilebilir dizeler kullanamazsınız. XAML öznitelik değerleri için tür dönüştürücüleri kullanan bir mutlaka sabit dil XAML işleme davranışını içerdiğinden bu kısıtlamadır `en-US` kültür. Bu kısıtlama tasarım nedenlerle hakkında daha fazla bilgi için bkz: XAML dil belirtimi ([\[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)) veya [WPF Genelleştirme ve yerelleştirme genel bakış](../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Burada, kültür bir sorun olabilir örnek olarak, bazı kültürler, ondalık ayırıcısı olarak nokta yerine dize formunda numaraları için virgül kullanın. Bu kullanım ayırıcı olarak virgül kullanılacak olan birçok mevcut tür dönüştürücüleri olan davranışı ile çakışıyor. Aracılığıyla bir kültür geçirme `xml:lang` çevresindeki XAML'de sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 Olarak kullanılabilmesi için bir <xref:System.ComponentModel.TypeConverter> XAML destekleyen uygulama <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi Bu dönüştürücü için bir dize olarak kabul etmelisiniz `value` parametresi. Dize biçimi geçerli değil ve tarafından dönüştürülebilir ise <xref:System.ComponentModel.TypeConverter> uygulaması, döndürülen nesne bir özellik tarafından beklenen türüne dönüştürme desteklemelidir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama döndürmelidir `null`.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulaması, dönüştürme için geçerli bir dize nelerin oluşturduğunu benzersiz olarak yorumlayabilir ve bu da kullanabilir veya parametre olarak geçirilen türü açıklama veya kültüre içerikler yoksay. Ancak, işleme WPF XAML değerleri türü açıklaması bağlamını tüm durumlarda geçebilir değil ve ayrıca göre kültür geçebilir değil `xml:lang`.  
  
> [!NOTE]
>  Küme ayraçları kullanmayın ({}), özellikle açılış ayracı ({}), bir öğe, dize biçimi. Bu karakterleri olarak giriş ve çıkış biçimlendirme uzantısı sırası için ayrılmıştır.  
  
 Tür dönüştürücü bir XAML hizmet .NET Framework XAML hizmetlerinde nesne yazıcıdan erişiminiz olmalıdır, bir özel durum uygundur ancak <xref:System.IServiceProvider.GetService%2A> karşı bağlam yapılan çağrı, bu hizmet döndürmez.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> büyük olasılıkla seri hale getirme desteği için kullanılır. Seri hale getirme desteğini <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> özel türünüz ve onun türü için dönüştürücü kesin bir gereklilik değildir. Bir denetimi uygulamak veya özelliklerin bir kısmı veya sınıfınızın tasarım serileştirmek kullanarak, ancak uygulamalıdır <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Olarak kullanılabilmesi için bir <xref:System.ComponentModel.TypeConverter> XAML destekleyen uygulama <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Bu dönüştürücü için yöntemi olarak desteklenen bir tür örneği (veya bir değer) kabul etmelisiniz `value` parametresi. Zaman `destinationType` parametredir türü <xref:System.String>, döndürülen nesne olarak cast mümkün <xref:System.String>. Döndürülen dize serileştirilmiş değerini temsil etmelidir `value`. İdeal olarak, seçtiğiniz seri hale getirme biçimi için bu dizeyi geçirilmiş gibi aynı değeri oluşturmak üzere gerekir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> önemli bilgi kaybı olmadan aynı dönüştürücü uygulamasıdır.  
  
 Değer seri hale getirilemez veya dönüştürücü serileştirme, desteklemiyor <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null` ve bir özel durum. Ancak, özel durumlar oluşturma, bir parçası olarak bu dönüştürme kullanamama rapor, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulama böylece ile denetimi en iyi uygulama olarak <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ilk özel durumları önlemek için desteklenir.  
  
 Varsa `destinationType` parametresi türü değil <xref:System.String>, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, işleme, hangi Base temel uygulamasına geri <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum oluşturur.  
  
 Tür dönüştürücü bir XAML hizmet .NET Framework XAML hizmetlerinde nesne yazıcıdan erişiminiz olmalıdır, bir özel durum uygundur ancak <xref:System.IServiceProvider.GetService%2A> karşı bağlam yapılan çağrı, bu hizmet döndürmez.  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> Uygulama döndürmelidir `true` için `sourceType` türü <xref:System.String> ve aksi durumda, temel uygulamayı erteler. Özel durumlar oluşturmayın <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>CanConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> Uygulama döndürmelidir `true` için `destinationType` türü <xref:System.String>ve aksi durumda temel uygulamayı erteleneceği. Özel durumlar oluşturmayın <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulama  
 Gibi davranan kullanılması için özel tür dönüştürücü için .NET Framework XAML Hizmetleri tarafından özel bir sınıf için tür dönüştürücüsünü, uygulamalısınız [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımı. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Özniteliğiyle belirttiğiniz özel tür dönüştürücü türü adı olması gerekir. Burada özellik türü, özel bir sınıf türü kullanan bir XAML işlemci değerleri işlediğinde, bu öznitelik uygularsanız, onu dizeleri giriş ve nesne örneklerini döndürür.  
  
 Ayrıca bir özelliği başına temelinde tür dönüştürücüsünü sağlayabilir. Uygulama yerine bir [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> bir özellik tanımını uygulayan sınıf tanımına (ana tanımı değil `get` / `set` içindeki uygulamaları). Özelliğinin türü, özel tür dönüştürücü tarafından işlenen türü eşleşmelidir. Uygulanan, bu öznitelik ile XAML işlemci bu özelliğin değerleri, işlediğinde, bu işlem giriş dizelerini ve dönüş nesne örnekleri. Özellik başına türü dönüştürücü teknik bir özellik türü Microsoft .NET Framework veya burada sınıf tanımını denetleyemezsiniz ve uygulanamıyor bazı diğer kitaplığı kullanmayı tercih ederseniz özellikle yararlıdır bir <xref:System.ComponentModel.TypeConverterAttribute> vardır.  
  
 Özel ekli üyesi için bir tür dönüştürme davranışı sağlamak için uygulama <xref:System.ComponentModel.TypeConverterAttribute> için `Get` uygulama modeli erişimci yöntemi eklenen üye.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Hizmet sağlayıcısı bağlamı bir biçimlendirme uzantısı uygulamasından erişme  
 Kullanılabilir hizmetler hiçbir değer Dönüştürücüsü için aynıdır. Nasıl her değer dönüştürücüsü alan hizmet bağlamı farktır. Hizmetlerine erişimi ve kullanılabilir hizmetler konusunda belgelenmiştir [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akış tür dönüştürücüleri  
 XAML düğümü akışı ile çalışıyorsanız, eylem veya sonuç türü dönüştürücünün henüz yürütülemiyor. Bir yükleme yolu sonunda yüklemek için türü dönüştürülmesi olması gereken öznitelik dizesini başlangıç üye ve end üyesi içinde metin değeri olarak kalır. Bu işlemi kullanarak belirlenebilir için sonunda gerekli tür dönüştürücüsünü <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> özelliği. Ancak, geçerli bir değer alma <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> gibi bilgileri temel üye veya üyeyi kullanan nesne değeri türü üzerinden erişebilirsiniz XAML şema içeriği sahip kullanır. Tür dönüştürme davranışını çağırma de gerektirir XAML şema içeriği türü eşlemesi gerektiren olduğundan ve bir dönüştürücü örneği oluşturma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
