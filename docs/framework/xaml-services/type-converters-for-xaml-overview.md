---
title: XAML Tür Dönüştürücülerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: cf9eda484d184b9be70a02bac7ced5b85a2dd211
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617214"
---
# <a name="type-converters-for-xaml-overview"></a>XAML Tür Dönüştürücülerine Genel Bakış
XAML biçimlendirmede bir dizeden belirli nesneleri bir nesne grafiğinin dönüştürür bir nesne yazıcısı için tür dönüştürücüleri tedarik mantığı. .NET Framework XAML hizmetlerinde tür dönüştürücüsünü türetildiği bir sınıf olmalıdır <xref:System.ComponentModel.TypeConverter>. Bazı dönüştürücüler ayrıca XAML kaydetme yolu desteklemek ve Serileştirme biçimlendirme dizesi forma bir nesneyi serileştirmek için kullanılan. Bu konu nasıl ve ne zaman XAML içinde tür dönüştürücüleri çağrılır ve, metot geçersiz kılmaları uygulama önerileri sağlar açıklar <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Tür dönüştürme kavramları  
 Aşağıdaki bölümlerde, XAML dizeleri nasıl kullandığı ve .NET Framework XAML hizmetlerinde nesne yazıcılarının XAML kaynakta karşılaşılan dize değerlerden bazıları işlemek için tür dönüştürücüleri kullanma ilgili temel kavramlar açıklanmaktadır.  
  
### <a name="xaml-and-string-values"></a>XAML ve dize değerleri  
 Bir XAML dosyasında bir öznitelik değeri ayarladığınızda, bu değerin ilk türü genel anlamda bir dize ve dize öznitelik değeri bir XML anlamında ' dir. Hatta diğer ilkel gibi <xref:System.Double> başta XAML işlemci dizelerdir.  
  
 Çoğu durumda, bir öznitelik değeri işlemek için bilgilerin iki parça XAML işlemci gerekir. Bilgi ilk parçasını ayarlanan özelliğin bir değer türüdür. XAML içinde işlenir ve bir öznitelik değeri tanımlayan herhangi bir dize olmalıdır sonuçta dönüştürülecek veya o türün değerine çözümlendi. Değer (örneğin, sayısal bir değer) XAML ayrıştırıcı tarafından anlaşılan basit bir tür ise, dize doğrudan dönüştürme denenir. Özniteliğinin değeri bir sabit listesi başvuruyorsa, sağlanan dize adı eşleşme, numaralandırma, adlandırılmış bir sabite denetlenir. Değer ayrıştırıcısı anlaşılan bir temel ya da sabit bir sabit listesi adı ise, geçerli bir değer ya da bir dönüştürülmüş dizesine dayalı başvuru sağlayabilir türünde olmalıdır.  
  
> [!NOTE]
>  XAML dil yönergeleri tür dönüştürücüleri kullanmayın.  
  
### <a name="type-converters-and-markup-extensions"></a>Tür dönüştürücüleri ve İşaretleme uzantıları  
 Özellik türü ve diğer konular için iade etmeden önce biçimlendirme uzantısı kullanımı XAML işlemcisi tarafından işlenen gerekir. Öznitelik bir tür dönüştürme normalde olduğu gibi ancak belirli bir durumda ayarlanan bir özelliği biçimlendirme uzantısı kullanımı ayarlarsanız, örneğin, ardından biçimlendirme uzantısı davranışı ilk işler. İşaretleme uzantısı gerekli olduğu bir yaygın durum zaten var. bir nesneye bir başvuru sağlamaktır. Bu senaryo için bir durum bilgisi olmayan bir tür dönüştürücüsü yalnızca istenen olmayabilir yeni bir örneği oluşturur. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [genel XAML işaretleme uzantılarına](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Yerel tür dönüştürücüleri  
 WPF ve .NET XAML Hizmetleri uygulamalarında, ancak CLR türlerine genel temel olarak zorlayıcı değil, yerel bir tür dönüştürme işleme sahip belirli CLR türleri vardır. Böyle bir türü örneğidir <xref:System.DateTime>. Bunun bir nedeni olan .NET Framework mimarisini işleyişi: türü <xref:System.DateTime> mscorlib, .NET en temel kitaplığında tanımlanır. <xref:System.DateTime> bir bağımlılık tanıtan başka bir bütünleştirilmiş koddan gelen bir öznitelik ile öznitelikli izin verilmiyor (<xref:System.ComponentModel.TypeConverterAttribute> sisteminden alınmıştır); bu nedenle, her zamanki türü dönüştürücü bulma mekanizmasından'öznitelik atanıyor tarafından desteklenemiyor. Bunun yerine, XAML ayrıştırıcı yerel işlenmesi gereken türlerinin bir listesi vardır ve bu tür true temelleri nasıl işlendiği için benzer işler. Durumunda, <xref:System.DateTime>, bu işlem için bir çağrı içerir <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Tür dönüştürücü uygulama  
 Aşağıdaki bölümlerde API'si <xref:System.ComponentModel.TypeConverter> sınıfı.  
  
### <a name="typeconverter"></a>TypeConverter  
 .NET Framework XAML hizmetlerinde altında XAML amaçlarıyla kullanılan tüm tür dönüştürücüleri temel sınıfından türetilir sınıflardır <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Sınıfı XAML varolan önce; .NET Framework sürümlerinde mevcut olan özgün birini <xref:System.ComponentModel.TypeConverter> senaryoları olan görsel tasarımcılar düzenleyicilerde özelliği için dize dönüştürme sağlamak için.  
  
 XAML, rolü için <xref:System.ComponentModel.TypeConverter> genişletilir. XAML amacıyla <xref:System.ComponentModel.TypeConverter> belirli-dize ve dize öğesinden dönüştürme desteği sağlamak için temel sınıftır. Gelen dize, dize özniteliği değerinden XAML ayrıştırma sağlar. Serileştirme için XAML içinde bir öznitelik uygulamasına geri belirli nesne özelliği çalışma zamanı değerini işleme-dize sağlar.  
  
 <xref:System.ComponentModel.TypeConverter> dize için ve gelen dize XAML işleme amacıyla dönüştürmek için uygun olan dört üyeleri tanımlar:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Bu üyeleri, en önemli yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, gerekli nesne türü için Giriş dizesinin dönüştürür. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Yöntemi, geniş bir tür dönüştürücüsü hedeflenen hedef türü dönüştürmek için uygulanabilir. Bu nedenle, çalışma zamanı dönüştürmeleri destekleyen gibi XAML genişletmek amacıyla hizmet verebilir. Ancak, XAML kullanmak, işleyebileceği kod yolu için bir <xref:System.String> giriş önemlidir.  
  
 İkinci en önemli yöntemdir <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Bir uygulama (örneğin XAML dosyası olarak kaydedilmişse,), bir biçimlendirme gösterimi dönüştürülürse <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> XAML metni yazıcılar üretim biçimlendirme gösterimi büyük senaryoda karmaşıktır. Çağıranın geçtiğinde bu durumda, XAML için önemli kod yolu olan bir `destinationType` , <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ve <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> yeteneklerini hizmet sorgu oluştururken kullanılan destek yöntemleri <xref:System.ComponentModel.TypeConverter> uygulaması. Döndürmek için bu yöntemleri uygulamalıdır `true` , türe özgü durumda, dönüştürücü eşdeğer dönüştürme yöntemleri destekler. XAML amacıyla, bu genellikle anlamına gelir <xref:System.String> türü.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Kültür bilgilerini ve XAML için tür dönüştürücüleri  
 Her <xref:System.ComponentModel.TypeConverter> uygulama benzersiz olarak yorumlamak dönüştürme için geçerli bir dize nedir ve bunu ayrıca kullanın veya parametre olarak geçirilen türü açıklaması yoksay. Kültür ve XAML tür dönüştürme için önemli bir konu aşağıda verilmiştir: yerelleştirilebilir dize öznitelik değerleri kullanarak XAML tarafından desteklenir, ama belirli bir kültürün gereksinimleriyle türü dönüştürücü girdi olarak bu yerelleştirilebilir dize kullanamazsınız. XAML öznitelik değerleri için tür dönüştürücüleri kullanan bir mutlaka sabit dil XAML işleme davranışını içerdiğinden bu sınırlamasıdır `en-US` kültür. Bu kısıtlama için tasarım nedenleri hakkında daha fazla bilgi için bkz. XAML dil belirtimi ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) veya [WPF genelleştirmesi ve yerelleştirmesine genel bakış](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Burada kültür bir sorun olabilir örneğin, bazı kültürlerde, ondalık ayırıcı olarak bir dönem yerine dize biçiminde sayılar için virgül kullanın. Bu, ayırıcı olarak virgül olan mevcut birçok tür dönüştürücüleri olan davranışı ile çakışıyor. Aracılığıyla bir kültür geçirme `xml:lang` çevreleyen XAML içinde sorunu çözmez.  
  
### <a name="implementing-convertfrom"></a>ConvertFrom uygulama  
 Olarak kullanılabilir bir <xref:System.ComponentModel.TypeConverter> XAML, destekleyen bir uygulama <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> yöntemi Bu dönüştürücü için bir dize olarak kabul etmelisiniz `value` parametresi. Dize geçerli bir biçimde ve tarafından dönüştürülebilir <xref:System.ComponentModel.TypeConverter> uygulama, döndürülen nesne bir özellik tarafından beklenen türüne dönüştürme desteklemelidir. Aksi takdirde, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> uygulama döndürmelidir `null`.  
  
 Her <xref:System.ComponentModel.TypeConverter> uygulama benzersiz olarak yorumlamak dönüştürme için geçerli bir dize nelerden ve bunu ayrıca kullanın veya parametre olarak geçirilen tür açıklama veya kültür bağlamları yoksay. Ancak, işleme WPF XAML değerleri türü açıklaması içeriği tüm durumlarda geçebilir değil ve ayrıca kültüre göre geçebilir değil `xml:lang`.  
  
> [!NOTE]
>  Küme ayraçları kullanmayın ({}), özellikle açılış ayracı ({}) öğesi olarak, dize biçimi. Bu karakterler, giriş ve çıkış bir işaretleme uzantısı sırası olarak ayrılmıştır.  
  
 Bir tür dönüştürücüsü erişimi .NET Framework XAML hizmetlerinde nesne yazıcıdan bir XAML hizmetine olmalıdır, bir özel durum uygundur ancak <xref:System.IServiceProvider.GetService%2A> bağlam karşı yapılan çağrı, hizmeti döndürmez.  
  
### <a name="implementing-convertto"></a>ConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> Potansiyel olarak seri hale getirme desteği için kullanılır. Serileştirme desteğini <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> özel türünüzü ve kendi türü için dönüştürücü mutlak bir gereksinim değildir. Ancak, bir denetimi uygulamak veya tasarım sınıfınızın veya özellikleri bir parçası serileştirilmesi kullanarak, uygulamalıdır <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Olarak kullanılabilir bir <xref:System.ComponentModel.TypeConverter> XAML, destekleyen bir uygulama <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> yöntemi Bu dönüştürücünün örneği türü (veya bir değer) olarak desteklenen kabul etmelisiniz `value` parametresi. Zaman `destinationType` parametre türüdür <xref:System.String>, döndürülen nesne olarak yayınlanması gereken <xref:System.String>. Döndürülen dize bir seri hale getirilmiş değerini temsil etmelidir `value`. İdeal olarak, seçtiğiniz serileştirme biçimi için bu dize geçirilmiş gibi aynı değeri oluşturmak kullanılabilecek <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> önemli bilgi kaybı olmadan aynı dönüştürücü uygulamasıdır.  
  
 Değeri serileştirilemez veya seri hale getirme, dönüştürücü desteklemiyor <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uygulama döndürmelidir `null` ve bir durum oluşturabilir. Ancak, özel durumlar, bir parçası olarak bu dönüştürme kullanılacak yükleyememesine bildirmelisiniz, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> uygulama böylece ile denetimi en iyi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> ilk özel durumları engellemek için desteklenir.  
  
 Varsa `destinationType` parametresi türü değil <xref:System.String>, kendi dönüştürücü işleme seçebilirsiniz. Genellikle, işleme, temel, temel uygulamaya geri <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> belirli bir özel durum oluşturur.  
  
 Bir tür dönüştürücüsü erişimi .NET Framework XAML hizmetlerinde nesne yazıcıdan bir XAML hizmetine olmalıdır, bir özel durum uygundur ancak <xref:System.IServiceProvider.GetService%2A> bağlam karşı yapılan çağrı, hizmeti döndürmez.  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> Uygulamasına dönmesi gerektiğini `true` için `sourceType` türü <xref:System.String> ve aksi takdirde, temel bir uygulama için erteleyin. Özel durumlar oluşturmayın <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>CanConvertTo uygulama  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> Uygulamasına dönmesi gerektiğini `true` için `destinationType` türü <xref:System.String>ve aksi için temel uygulama erteleyin. Özel durumlar oluşturmayın <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute uygulanıyor  
 Olarak görev yapan kullanılmak üzere kendi özel tür dönüştürücü için tür dönüştürücüsü .NET Framework XAML hizmetlerinde tarafından özel bir sınıf için uygulamalısınız [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> sınıf tanımı. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Özniteliğiyle belirtin, özel bir tür dönüştürücüsü türü adı olması gerekir. Burada özellik türü, özel bir sınıf türünü kullanan XAML işlemci değerleri işlediğinde, bu öznitelik uygularsanız, bu dizeleri giriş ve nesne örneği döndürür.  
  
 Özellik başına temelinde bir tür dönüştürücüsü de sağlayabilirsiniz. Uygulama yerine bir [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> isteğe bağlı olarak sınıf tanımının bir özellik tanımı için geçerlidir (ana tanım değil `get` / `set` içindeki uygulamaları). Özelliğin türü, özel bir tür dönüştürücüsü tarafından işlenen türüyle eşleşmelidir. Bu özniteliği uygulandı, ile XAML işlemci bu özellik değerlerini işlediğinde, bu işlem giriş dizesi ve nesne örneği döndürür. Özellik başına türü dönüştürücü özellik türü Microsoft .NET Framework veya sınıf tanımı kontrol ve uygulanamıyor burada bazı diğer kitaplığı kullanmayı tercih ederseniz özellikle kullanışlı bir tekniktir bir <xref:System.ComponentModel.TypeConverterAttribute> vardır.  
  
 Özel ekli üyesi için bir tür dönüştürme davranışı sağlamak için uygulama <xref:System.ComponentModel.TypeConverterAttribute> için `Get` uygulama modeli erişimci yöntemi için eklenen üye.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Hizmet sağlayıcısı bağlamı bir işaretleme uzantısı uygulamasından erişme  
 Kullanılabilir hizmetlerin herhangi bir değer dönüştürücü için aynıdır. Nasıl her değer dönüştürücü alan hizmet bağlamı farktır. Hizmetlerine erişimi ve hizmetler konusunda belgelenir [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğümü Stream içinde tür dönüştürücüleri  
 XAML düğümü akışı ile çalışıyorsanız, bir tür dönüştürücüsü nihai sonucu ve eylem henüz yürütülmez. Bir yükleme yolu sonunda yüklemek için türüne dönüştürülmesi gereken öznitelik dizesini bir metin değerinin başlangıç üyesi ve son üye olarak kalır. Bu işlemi kullanarak belirlenebilir için sonuçta gerekli tür dönüştürücüsünü <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> özelliği. Ancak, geçerli bir değer elde etme <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> açık olması gibi bilgileri temel alınan üye veya üyeyi kullanan nesne değeri türü erişebileceğiniz bir XAML şema içeriği kullanır. Tür dönüştürme davranışını çağırma ayrıca gerektirir XAML şema içeriği tür eşlemesi gerektirdiği için ve bir dönüştürücü örneği oluşturma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.TypeConverterAttribute>
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
