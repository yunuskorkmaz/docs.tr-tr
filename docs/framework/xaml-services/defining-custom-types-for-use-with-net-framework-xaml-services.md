---
title: .NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 9edc7baa1a540a71997cf5b1ed010ad5c7960d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566502"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
İş nesneleri özel türler tanımlamak ya da bir bağımlılık belirli çerçevesinde yok türleri, izleyebilirsiniz XAML için bazı en iyi yöntemler vardır. Bu yöntemler, .NET Framework XAML hizmetlerinde izleyin ve kendi XAML okuyucuları ve XAML yazıcıları türünüz XAML özelliklerini bulmak ve XAML tür sistemi kullanarak bir XAML düğüm akış uygun gösterimi vermek istiyorsanız. Bu konu için tür tanımları, üye tanımları ve CLR türleri veya üyeleri öznitelik atanıyor en iyi uygulamaları açıklar.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Oluşturucu desenler ve XAML için tür tanımları  
 XAML'de object öğesi olarak örneğinin oluşturulması için özel bir sınıf aşağıdaki gereksinimleri karşılamalıdır:  
  
-   Özel bir sınıf genel olmalıdır ve bir varsayılan (parametresiz) ortak oluşturucu kullanıma gerekir. (Bölüm yapıları ilgili notları aşağıdaki bakın.)  
  
-   Özel bir sınıf, bir iç içe geçmiş sınıf olması gerekir. Tam ad yolundaki "nokta" ek sınıfı-namespace bölme belirsiz yapar ve ekli özellikler gibi diğer XAML özellikleriyle uğratır.  
  
 Bir nesne bir nesne öğesi olarak oluşturulabilir, oluşturulan nesnesi nesneyi kendi temel alınan türü olarak ele herhangi bir özellik özellik öğesi formunu doldurabilirsiniz.  
  
 Değer dönüştürücüsü etkinleştirirseniz, nesne değerleri için bu ölçütü karşılamayan türleri sağlayabilirsiniz. Daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Yapılar  
 Yapıları her zaman XAML'de, CLR tanımı tarafından oluşturulması mümkün olur. Bir CLR derleyici örtük olarak bir yapı için varsayılan bir oluşturucu oluşturmasıdır. Bu oluşturucu, tüm özellik değerlerini varsayılanlarına başlatır.  
  
 Bazı durumlarda, bir yapı için varsayılan yapım davranış arzu değil. Bu yapı değerleri ve işlevi UNION olarak kavramsal olarak doldurmak için tasarlandığından olabilir. Bir birleşim olarak içerilen değerleri dışlayan yorumlar olabilir ve bu nedenle, özelliklerini hiçbiri ayarlanabilir. Böyle bir yapı içinde WPF sözlüğü örneğidir <xref:System.Windows.GridLength>. Böylece farklı yorumlar veya modları yapısı değerlerin oluşturma dize kurallarını kullanarak özniteliği formunda değerleri belirtilebilir böyle yapıları tür dönüştürücüsünü uygulamanız gerekir. Yapı Ayrıca varsayılan olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer davranış maruz bırakmamalısınız.  
  
### <a name="interfaces"></a>Arabirimler  
 Arabirim üyeleri temel türleri olarak kullanılabilir. XAML tür sistemi atanabilir listesini denetler ve değeri olarak sağlanan nesne arabirimine atanabilir bekliyor. XAML yapı gereksinimleri ilgili atanabilir tür desteklediği sürece arabirimi XAML türü olarak nasıl sunulmalıdır hiçbir kavramı yoktur.  
  
### <a name="factory-methods"></a>Fabrika yöntemleri  
 Fabrika yöntemleri bir XAML 2009 özelliğidir. Bunlar nesneleri varsayılan oluşturucular olmalıdır XAML ilkesini değiştirin. Fabrika yöntemleri, bu konuda açıklanmamıştır. Bkz: [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Numaralandırmalar XAML yerel tür dönüştürme davranışına sahip. XAML'de belirtilen numaralandırması sabit adları karşı temel numaralandırma türü çözümlenir ve bir XAML nesne yazıcısı numaralandırma değeri döndürür.  
  
 XAML sabit listeleri için bayrakları stili kullanım destekleyen <xref:System.FlagsAttribute> uygulanır. Daha fazla bilgi için bkz: [içinde XAML sözdizimi ayrıntı](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([İçinde XAML sözdizimi ayrıntı](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) WPF kitlesi yazılır, ancak çoğu bu konu başlığı altındaki bilgiler, belirli bir uygulama çerçevesi için belirli değil XAML için ilgili.)  
  
## <a name="member-definitions"></a>Üye tanımları  
 XAML kullanımı için üyeleri türleri tanımlayabilirsiniz. Bu belirli tür XAML kullanılabilir olsa bile, XAML kullanılabilen üyeleri tanımlayan türleri için mümkündür. Bu CLR devralma nedeniyle mümkündür. XAML kullanım türü olarak üye devralan bazı tür destekler ve üye XAML kullanımı temel alınan türü için destekleyen veya kullanılabilir yerel XAML sözdizimine sahip olduğu sürece, bu XAML kullanılabilir bir üyesidir.  
  
### <a name="properties"></a>Özellikler  
 Tipik CLR kullanan ortak bir CLR özellik özellikleri tanımlarsanız `get` ve `set` erişimci desenleri ve dil uygun keywording, XAML tür sistemi raporlama yapabilir özelliği uygun bilgilerle bir üye olarak sağlanan için <xref:System.Xaml.XamlMember> özellikleri gibi <xref:System.Xaml.XamlMember.IsReadPublic%2A> ve <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Belirli özellikler, bir metin sözdizimi uygulayarak etkinleştirebilir <xref:System.ComponentModel.TypeConverterAttribute>. Daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Bir metin sözdizimini veya yerel XAML dönüştürme yokluğu ve biçimlendirme uzantısı kullanımı, bir özellik türü gibi daha fazla yöneltme yokluğu (<xref:System.Xaml.XamlMember.TargetType%2A> XAML'de type system) t düşünerek XAML nesne yazıcısı için bir örnek döndürmeyi kurabiliyor olması gerekir Hedef türü bir CLR türü.  
  
 XAML 2009 kullanıyorsanız [x: Reference işaretleme uzantısı](../../../docs/framework/xaml-services/x-reference-markup-extension.md) önceki konuları karşılanmazsa değerlerini sağlamak için kullanılabilir; ancak, bu kullanım bir sorun türü tanımı sorun'den daha fazla bilgi.  
  
### <a name="events"></a>Olaylar  
 Ortak bir CLR olayı olarak olayları tanımlarsanız, XAML tür sistemi olay sahip bir üye olarak bildirebilirsiniz <xref:System.Xaml.XamlMember.IsEvent%2A> olarak `true`. Olay işleyicileri geriye .NET Framework XAML Hizmetleri özellikleri kapsamında değildir; Bu, belirli çerçeveler ve uygulamaları bırakılır.  
  
### <a name="methods"></a>Yöntemler  
 Satır içi kod yöntemleri için bir varsayılan XAML özelliği değil. Çoğu durumda, doğrudan yöntemi üyeleri referans değil ve XAML yöntemlerinde rolü yalnızca desteği için belirli XAML desenleri sağlamaktır. [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md) bir özel durumdur.  
  
### <a name="fields"></a>Alanlar  
 CLR tasarım yönergeleri statik olmayan alanlar önleyin. Statik alanları için statik alan değerlerini erişebilirsiniz yalnızca aracılığıyla [x: Static işaretleme uzantısı](../../../docs/framework/xaml-services/x-static-markup-extension.md); bu durumda, bir alan için kullanıma sunmak için CLR tanımında özel bir şey yapmakta olduğunuz değil [x: Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) kullanımları.  
  
## <a name="attachable-members"></a>Takılabilir üyeleri  
 Takılabilir üyeleri XAML için bir erişimci yöntemi desen tanımlama türündeki aracılığıyla sunulur. Tanımlayıcı türü XAML-kullanılabilir bir nesne olarak olması gerekmez. Aslında, genel bir desen, rol hizmeti sınıfı bildirmektir takılabilir üye kendi ve ilgili davranışları uygulamak, ancak bir UI gösterimi gibi diğer bir işlev hizmet. Aşağıdaki bölümler, yer tutucu için *PropertyName* takılabilir üyenin adını temsil eder. Bu adı geçerli [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Bu düzenleri ve diğer yöntemleri türünün arasındaki ad çakışma dikkatli olun. Desenler biriyle eşleşen bir üye zaten varsa, amacınız değildi olsa bile, takılabilir üye kullanım izlediğiniz XAML işlemcisi tarafından yorumlanabilir.  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName erişimcisi  
 İmza için `Get` *PropertyName* erişimci olması gerekir:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` Nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Bu, takılabilir üye kullanımını kapsamını belirlemek için kullanabilirsiniz; hedeflenen kapsamı dışında kullanımları sonra bir XAML ayrıştırma hatası ortaya çıkmış geçersiz yayın özel durum atar. Parametre adı `target` zorunlu değildir, ancak adlı `target` çoğu uygulamalarında kural tarafından.  
  
-   Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Desteklemek için bir <xref:System.ComponentModel.TypeConverter> takılabilir üyesinin özniteliği kullanım için etkin metin sözdizimi geçerli <xref:System.ComponentModel.TypeConverterAttribute> için `Get` *PropertyName* erişimcisi. Uygulama `get` yerine `set` nonintuitive; görünebilir ancak, bu kural kavramı destekleyebilir seri hale getirilebilir salt okunur takılabilir üyelerinin, olduğu Tasarımcı senaryolarda kullanışlıdır.  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName erişimcisi  
 İmza kümesi için*PropertyName* erişimci olması gerekir:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` Nesnesi olarak belirtilebilir aynı mantığı ve sonuçları ile uygulamanızda daha belirli bir tür önceki bölümde açıklandığı gibi.  
  
-   `value` Nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Bu yöntem için değerinin XAML kullanımdan özniteliği formunda genellikle gelen giriş olduğunu unutmayın. Öznitelik formundan olmalıdır değer dönüştürücüsü metin sözdizimi desteği ve üzerinde öznitelik `Get` *PropertyName* erişimcisi.  
  
### <a name="attachable-member-stores"></a>Takılabilir üye depolar  
 Erişimci yöntemleri genellikle takılabilir üye değerlerinin bir nesne grafiğinin yerleştirin veya nesne grafiğinin dışında değerleri almak ve düzgün şekilde serileştirmek için bir yol sağlamak yeterli değildir. Bu işlevselliği sağlayacak şekilde `target` önceki erişimcisi imzaları nesneleri değerlerini depolama yeteneğine sahip olmalıdır. Depolama mekanizmasını tutarlı takılabilir üye Üyeler listesinde olduğu hedefleri takılabilir bir üyesidir takılabilir üye ilkesine sahip olmalıdır. .NET framework XAML hizmetleri sağlar. bir uygulama teknik takılabilir üye API'leri aracılığıyla depolar <xref:System.Xaml.IAttachedPropertyStore> ve <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> XAML yazarlar tarafından deposu uygulaması bulmak için kullanılır ve türü üzerinde uygulanmadı `target` erişimciler. Statik <xref:System.Xaml.AttachablePropertyServices> API'leri erişimciler gövdesi içinde kullanılır ve takılabilir üyesi tarafından başvurmak kendi <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>XAML ilişkili CLR öznitelikleri  
 Doğru türleri, üyeleri ve derlemeler öznitelik atanıyor rapor .NET Framework XAML Hizmetleri için XAML tür sistem bilgileri sırada önemlidir. Bu, .NET Framework XAML Hizmetleri XAML okuyucuları ve XAML yazıcılarının doğrudan bağlı XAML sistemleri ile kullanmak için türlerinizi düşünüyorsanız veya tanımlayın veya bu XAML okuyucuları ve XAML yazıcılarının temel XAML kullanılarak bir Framework'te kullanıyorsanız geçerlidir.  
  
 Özel türler XAML desteği için uygun olan her XAML ilişkili bir öznitelik listesi için bkz: [özel türler ve Kitaplıkar için XAML-Related CLR öznitelikleri](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Kullanım  
 Özel türler kullanımını biçimlendirme Yazar özel türü içeren derleme ve CLR ad alanı için bir önek eşlenmelidir gerektirir. Bu yordam, bu konudaki belgelenmemiştir.  
  
## <a name="access-level"></a>Erişim düzeyi  
 XAML yükleme ve türleri örneği için bir yol sağlayan bir `internal` erişim düzeyi. Bu özellik, kullanıcı kodu kendi türlerini tanımlayın ve ardından aynı kullanıcı kod kapsamını parçası olduğunu da biçimlendirme bu sınıflardan örneği sağlanmıştır.  
  
 Kullanıcı kodu tanımlayan her bir örnektir WPF gelen bir <xref:System.Windows.Controls.UserControl> UI davranışı yeniden düzenlemeniz için bir yöntem olarak, ancak destekleyen sınıfı bildirerek kapsanan herhangi bir olası uzantısı mekanizma parçası olarak değil hedeflenen `public` erişim düzeyi. Bu tür bir <xref:System.Windows.Controls.UserControl> ile bildirilen `internal` yedekleme kodunun içinden, başvurulan bir XAML tür olarak aynı bütünleştirilmiş derlenir erişme.  
  
 XAML altında tam güven yükler ve kullanan bir uygulama için <xref:System.Xaml.XamlObjectWriter>, sınıflarıyla yüklenirken `internal` erişim düzeyi her zaman etkindir.  
  
 Kısmi güven altında XAML yükleyen bir uygulama için erişim düzeyi özelliklerini kullanarak denetleyebilirsiniz <xref:System.Xaml.Permissions.XamlAccessLevel> API. Ayrıca, erteleme mekanizmaları (örneğin, WPF şablon sistemi) tüm erişim düzeyi izinleri yaymak ve son çalıştırma değerlendirmeleri için korumak olması gerekir; Bu geçirerek dahili olarak işlenir <xref:System.Xaml.Permissions.XamlAccessLevel> bilgi.  
  
### <a name="wpf-implementation"></a>WPF uygulaması  
 WPF XAML BAML altında kısmi güven yüklerse, erişimin sınırlı olduğu bir kısmi güven erişim modeli kullanan <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> BAML kaynak assembly için. WPF erteleme için kullandığı <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> erişim düzeyi bilgi geçirme için bir mekanizma olarak.  
  
 WPF XAML terminoloji içinde bir *iç tür* de başvuru XAML içeren aynı derlemesi tarafından tanımlanan bir tür. Bu tür bir türü kasıtlı olarak derleme atlar XAML ad uzayı eşlenebilir bir bu gibi bir durumda eşleme kısmı = `xmlns:local="clr-namespace:WPFApplication1"`.  BAML iç tür başvuran varsa ve türü olduğunu `internal` erişim düzeyi, bu oluşturur bir `GeneratedInternalTypeHelper` derleme için sınıf. Önlemek istiyorsanız `GeneratedInternalTypeHelper`, ya da kullanmalıdır `public` erişim düzeyini veya gerekir ilgili sınıfı ayrı bir derleme faktörü ve bu derleme kaynağına bağımlı kılın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Türler ve Kitaplıklar İçin XAML İlişkili CLR Öznitelikleri](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md)
