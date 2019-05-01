---
title: .NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: be9c0e26574a15279ce89af2c7862abaa8713360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971957"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
İş nesneler özel türleri tanımlama ya da bir bağımlılık belirli çerçeveler sahip olmayan türleri izleyebilirsiniz XAML için bazı en iyi yöntemler vardır. Bu uygulamaları izlerseniz, .NET Framework XAML hizmetlerinde ve XAML okuyucular ve yazıcılar XAML türünüz XAML özelliklerini bulabilir ve XAML tür sistemi kullanarak XAML düğüm akış uygun gösterimi verin. Bu konu için tür tanımları, üye tanımları ve CLR türleri veya üyeleri öznitelik atanıyor en iyi uygulamaları açıklar.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Oluşturucu desenler ve XAML için tür tanımları  
 Bir XAML nesne öğesi olarak örneği için özel bir sınıf aşağıdaki gereksinimleri karşılamalıdır:  
  
- Özel bir sınıf, ortak olmalıdır ve bir varsayılan (parametresiz) ortak oluşturucu kullanıma açmalıdır. (Aşağıdaki bölümde yapıları ile ilgili notlar için bkz.)  
  
- Özel bir sınıf, iç içe geçmiş bir sınıf olmalıdır. Tam ad yolunda "dot" ekstra sınıf ad alanı bölme belirsiz hale getirir ve iliştirilmiş özellikler gibi diğer XAML özelliklerle uğratır.  
  
 Bir nesne bir nesne öğesi olarak oluşturulabilir, oluşturulan nesne nesnesi olarak temel alan herhangi bir özelliği özellik öğesi biçiminin doldurabilirsiniz.  
  
 Yine de bir değer dönüştürücü etkinleştirirseniz, bu ölçütleri karşılamayan türleri için nesne değerleri sağlayabilirsiniz. Daha fazla bilgi için [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Yapılar  
 Yapıları her zaman XAML içinde CLR tanımı tarafından oluşturulması olanağına sahip olursunuz. Bu durum, CLR derleyici örtük olarak bir yapı için varsayılan bir oluşturucu oluşturur çünkü. Bu oluşturucu, tüm özellik değerlerini varsayılanlarına başlatır.  
  
 Bazı durumlarda, bir yapı için varsayılan yapı davranış arzu değil. Bu yapı, değerleri ve işlevi bir birleşimi olarak kavramsal olarak doldurmak için tasarlandığından olabilir. Bir birleşimi olarak içerdiği değerlerin birbirini dışlayan yorumlaması olabilir ve bu nedenle, özelliklerini hiçbiri ayarlanabilir. Böyle bir yapı içinde WPF sözlüğü örneğidir <xref:System.Windows.GridLength>. Böylece değerleri öznitelik formunda yapısı değerlerinin modları ve farklı ınterpretations oluşturma dize kurallarını kullanarak ifade edilebilir bir tür dönüştürücüsü gibi yapıları uygulamalıdır. Yapısı, varsayılan olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer bir davranış da sunmalıdır.  
  
### <a name="interfaces"></a>Arabirimler  
 Arabirimleri, temel alınan üye türleri olarak kullanılabilir. XAML tür sistemi atanabilir listenin denetler ve değeri olarak sağlanan nesne arabirimine atanabilir bekliyor. XAML yapı gereksinimleri ilgili atanabilir bir tür desteklediği sürece, arabirimi XAML türü olarak nasıl sunulmalıdır konsepti yoktur.  
  
### <a name="factory-methods"></a>Fabrika yöntemleri  
 Fabrika yöntemleri bir XAML 2009 özelliğidir. Bunlar, nesneler varsayılan oluşturucular olmalıdır XAML ilkesini değiştirin. Bu konu başlığında, Fabrika yöntemleri belgelenmemiştir. Bkz: [x: FactoryMethod yönergesi](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Numaralandırmaların XAML yerel tür dönüştürme davranışı. XAML içinde belirtilen numaralandırma sabit adları, temel alınan numaralandırma türüne göre çözümlenir ve bir XAML nesne yazıcısı numaralandırma değerini döndürür.  
  
 XAML ile numaralandırmalar bayrakları stili kullanım desteği <xref:System.FlagsAttribute> uygulanır. Daha fazla bilgi için [içinde XAML söz dizimi ayrıntı](../wpf/advanced/xaml-syntax-in-detail.md). ([İçinde XAML söz dizimi ayrıntı](../wpf/advanced/xaml-syntax-in-detail.md) WPF izleyiciler için yazılmıştır ancak çoğu bu konu başlığı altındaki bilgiler, ilgili belirli bir uygulama çerçevesine özgü olmayan XAML.)  
  
## <a name="member-definitions"></a>Üye tanımları  
 Tür üyeleri için XAML kullanım tanımlayabilirsiniz. Bu işlem, bu türdeki XAML kullanılabilir olsa bile, XAML kullanılabilir üyeler tanımlayan türler için de mümkündür. Bu, CLR devralma nedeniyle mümkün olur. Üye devralınan tür XAML kullanım türü olarak destekler ve üye, temel alınan türü için XAML kullanım destekler veya bir yerel XAML sözdizimi sürece bu XAML kullanılabilir bir üyesidir.  
  
### <a name="properties"></a>Özellikler  
 Özellikleri tipik CLR kullanarak genel bir CLR özelliği olarak tanımlarsanız `get` ve `set` erişimci desenleri ve uygun dilde keywording, XAML tür sistemi rapor özelliği uygun bilgilerle bir üyesi olarak sağlanan için <xref:System.Xaml.XamlMember> özellikleri gibi <xref:System.Xaml.XamlMember.IsReadPublic%2A> ve <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Belirli özellikler, bir metin söz dizimi uygulayarak etkinleştirebilir <xref:System.ComponentModel.TypeConverterAttribute>. Daha fazla bilgi için [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Bir metin sözdizimi veya yerel XAML dönüştürme ve biçimlendirme uzantısı kullanımı, bir özelliğin türünü gibi daha fazla yöneltme olmaması (<xref:System.Xaml.XamlMember.TargetType%2A> XAML içinde tür sistemi) bir örnek t düşünerek bir XAML nesne yazıcısı geri olmalıdır Hedef türü bir CLR türü.  
  
 XAML 2009 kullanıyorsanız [x: Reference işaretleme uzantısı](x-reference-markup-extension.md) önceki konuları karşılanmazsa değerlerini sağlamak için kullanılabilir; ancak, bu tür tanımı sorunu daha kullanım sorunu daha fazla bilgi.  
  
### <a name="events"></a>Olaylar  
 Olaylar genel bir CLR olay olarak tanımlarsanız, XAML tür sistemi olay sahip bir üye olarak bildirebilirsiniz <xref:System.Xaml.XamlMember.IsEvent%2A> olarak `true`. Olay işleyicileri bağlama .NET Framework XAML hizmetlerinde özellikleri kapsamında değildir; Bu, uygulamaları ve belirli çerçeveleri ile bırakılır.  
  
### <a name="methods"></a>Yöntemler  
 Satır içi kod yöntemleri için bir varsayılan XAML özelliği değil. Çoğu durumda doğrudan yöntem üyeleri XAML başvuru değildir ve XAML yöntemleri yalnızca belirli XAML desenleri için destek sağlamak için rolüdür. [x: FactoryMethod yönergesi](x-factorymethod-directive.md) bir özel durumdur.  
  
### <a name="fields"></a>Alanlar  
 CLR tasarım yönergeleri statik olmayan alanları önleyin. Statik alanlar için statik alan değerlerini erişebileceğiniz yalnızca aracılığıyla [x: Static işaretleme uzantısı](x-static-markup-extension.md); bu durumda, özel bir alan için kullanıma sunmak için CLR tanımındaki herhangi bir şey yapmakta olduğunuz değil [x: Static](x-static-markup-extension.md) kullanımları.  
  
## <a name="attachable-members"></a>İliştirilebilir üyeleri  
 İliştirilebilir üyeleri için XAML, bir erişimci yöntemi deseni tanımlayan bir türe göre aracılığıyla sunulur. Tanımlama türü XAML-kullanışlı bir nesne olarak olması gerekmez. Aslında, bir hizmet sınıfı, rol bildirmek için yaygın bir düzen olduğunu iliştirilebilir üye kendi ve ilgili davranışları uygulayın, ancak kullanıcı Arabirimi gösterimi gibi diğer bir işlev hizmet. Aşağıdaki bölümler, yer tutucu *PropertyName* iliştirilebilir, üyenin adını temsil eder. Bu ad geçerli [XamlName Dilbilgisi](xamlname-grammar.md).  
  
 Bu desenleri ve bir türün diğer yöntemleri arasındaki ad çakışmalarının dikkatli olun. Desenlerden biriyle eşleşen bir üye zaten varsa, amacınız değildi olsa bile, bir iliştirilebilir üye kullanım yol XAML işlemcisi tarafından yorumlanabilir.  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName erişimcisi  
 İmzası `Get` *PropertyName* erişimcisi olmalıdır:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
- `target` Nesnesi, uygulamanızdaki daha belirli bir tür olarak belirtilebilir. İliştirilebilir üyelik kullanımını kapsamını belirlemek için kullanabilirsiniz; hedeflenen Kapsamınız dışında kullanımları, ardından bir XAML ayrıştırma hatası ortaya çıkmış geçersiz dönüştürme özel durumlar. Parametre adı `target` bir gereksinim değildir, ancak adlı `target` çoğu uygulamalarında kural tarafından.  
  
- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Desteklemek için bir <xref:System.ComponentModel.TypeConverter> öznitelik kullanımı iliştirilebilir üyesi için etkin metin sözdizimi geçerli <xref:System.ComponentModel.TypeConverterAttribute> için `Get` *PropertyName* erişimcisi. Uygulama `get` yerine `set` nonintuitive; görünebilir ancak bu kavramı destekler, seri hale getirilebilir salt okunur iliştirilebilir üyesi, olan Tasarımcı senaryolarda yararlıdır.  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName erişimcisi  
 Küme için imza*PropertyName* erişimcisi olmalıdır:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
- `target` Nesne belirtilebilir, uygulamanızda aynı mantığı ve sonuçları daha belirli bir tür olarak önceki bölümde açıklandığı gibi.  
  
- `value` Nesnesi, uygulamanızdaki daha belirli bir tür olarak belirtilebilir.  
  
 Bu yöntem değeri öznitelik formunda genellikle XAML kullanım gelen giriş olduğunu unutmayın. Öznitelik formunda olmalıdır değer dönüştürücü metin söz dizimi desteğini ve şirket özniteliğini `Get` *PropertyName* erişimcisi.  
  
### <a name="attachable-member-stores"></a>İliştirilebilir üye depoları  
 Erişimci metotlarını genellikle bir nesne grafiğine iliştirilebilir üye değerlerinin yerleştirileceği veya Nesne grafiğini değerleri almak ve bunları düzgün bir şekilde serileştirmek için bir yol sağlamak yeterli değildir. Bu işlevselliği sağlayacak şekilde `target` önceki erişimci imzalarında nesneleri değerleri depolayabilen özelliğine sahip olmalıdır. Depolama mekanizmasını tutarlı iliştirilebilir üye üye listesinde olduğu hedeflere iliştirilebilir bir üyesidir iliştirilebilir üye ilkesine sahip olması gerekir. .NET framework XAML hizmetlerinde iliştirilebilir üye API'ler aracılığıyla depolayan bir uygulama teknik sağlar <xref:System.Xaml.IAttachedPropertyStore> ve <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> Mağaza uygulamasını bulmak için XAML yazarlar tarafından kullanılır ve olan tür uygulanması gereken `target` erişimcileri. Statik <xref:System.Xaml.AttachablePropertyServices> API'leri erişimcileri gövdesi içinde kullanılır ve iliştirilebilir üyesi tarafından bakın, <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>XAML ilişkili CLR öznitelikleri  
 Doğru türleri, üyeleri ve derlemeleri öznitelik atanıyor, .NET Framework XAML hizmetlerinde XAML tür sistem bilgileri rapor sırada önemlidir. Bu, türlerinizi .NET Framework XAML Hizmetleri XAML okuyucular ve yazıcılar XAML doğrudan göre XAML sistemleri ile kullanmak istiyorsanız veya tanımlayın veya bu XAML okuyucular ve yazıcılar XAML tabanlı ve XAML kullanan bir framework kullanıyorsanız geçerlidir.  
  
 XAML özel türlerinizi desteği ile ilgili her XAML ile ilgili bir öznitelik listesi için bkz. [özel türler ve Kitaplıkar için CLR öznitelikleri XAML-Related](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Kullanım  
 Özel türleri kullanım, biçimlendirme Yazar özel türü içeren derlemeyi ve CLR ad alanı için bir önek gerekir eşlemenizi gerektirir. Bu yordam, bu konudaki belgelenmemiştir.  
  
## <a name="access-level"></a>Erişim düzeyi  
 XAML yükleme ve türleri oluşturmak için bir yol sağlayan bir `internal` erişim düzeyi. Bu özellik, kullanıcı kodu kendi türlerini tanımlayın ve ardından bu sınıflardan de aynı kullanıcı kod kapsamı parçası biçimlendirme örneği sağlanmıştır.  
  
 Kullanıcı kodu tanımlar zaman wpf'den bir örnek olduğuna bir <xref:System.Windows.Controls.UserControl> bir kullanıcı Arabirimi davranışı yeniden düzenlemenin yolu, ancak değil destekleyici sınıf ile bildirerek örtük herhangi bir olası uzantı mekanizması bir parçası olarak hedeflenen `public` erişim düzeyi. Böyle bir <xref:System.Windows.Controls.UserControl> ile bildirilen `internal` erişmeye içinden, başvurulan bir XAML türü olarak aynı derlemenin yedekleme kod derlenir.  
  
 XAML tam güven altında yükler ve kullanan bir uygulama için <xref:System.Xaml.XamlObjectWriter>, sınıflarla yüklenirken `internal` erişim düzeyi her zaman etkindir.  
  
 Kısmi güven altında XAML yükleyen bir uygulama için erişim düzeyi özellikleri kullanarak denetleyebilirsiniz <xref:System.Xaml.Permissions.XamlAccessLevel> API. Ayrıca, (örneğin, WPF şablonu sistemi) erteleme mekanizmaları herhangi bir erişim düzeyi izinleri yayar ve bunları korumak için son çalışma zamanı değerlendirmeleri olması gerekir; Bu geçirerek dahili olarak işlenir <xref:System.Xaml.Permissions.XamlAccessLevel> bilgileri.  
  
### <a name="wpf-implementation"></a>WPF uygulaması  
 WPF XAML kullanan bir kısmi güven erişim modeli kısmi güven altında BAML yüklenirse, erişimin sınırlı olduğu <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> BAML kaynağı derleme. WPF erteleme için kullandığı <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> erişim düzeyi bilgileri geçirmek için bir mekanizma olarak.  
  
 WPF XAML terminolojisinde, bir *iç tür* başvuruda bulunan bir XAML de içeren aynı derleme tarafından tanımlanan bir tür. Böyle bir türü derleme kasıtlı olarak atlar XAML ad alanı eşlenebilir bir eşleme, örneğin, bir kısmını = `xmlns:local="clr-namespace:WPFApplication1"`.  BAML iç tür başvuruyorsa ve türü olduğunu `internal` erişim düzeyi, bu işlem oluşturur. bir `GeneratedInternalTypeHelper` derleme için sınıf. Kaçınmak istiyorsanız `GeneratedInternalTypeHelper`, ya da kullanmalısınız `public` erişim düzeyi, veya ayrı bir derleme içine ilgili sınıfı faktörü ve bu derlemeye bağımlı olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Türler ve Kitaplıklar İçin XAML İlişkili CLR Öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Hizmetleri](index.md)
