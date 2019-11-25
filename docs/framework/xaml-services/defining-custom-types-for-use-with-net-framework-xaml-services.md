---
title: .NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 7437add6795c1bb7f8a59807ebfc51dc2d0f987f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972017"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
İş nesneleri olan veya belirli çerçevelere bağımlılığı olmayan türler olan özel türler tanımladığınızda, kullanabileceğiniz XAML için bazı en iyi uygulamalar vardır. Bu yöntemleri izlerseniz .NET Framework XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları, bu türün XAML özelliklerini bulabilir ve xaml tür sistemini kullanarak XAML düğüm akışında uygun gösterimi verebilir. Bu konuda tür tanımları, üye tanımları ve tür veya üyelerin CLR Attributing için en iyi yöntemler açıklanmaktadır.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML için Oluşturucu desenleri ve tür tanımları  
 XAML 'de bir nesne öğesi olarak örneklendirmak için, özel bir sınıf aşağıdaki gereksinimleri karşılamalıdır:  
  
- Özel sınıf ortak olmalıdır ve parametresiz bir ortak oluşturucuyu kullanıma sunmalıdır. (Yapılar hakkında notlar için aşağıdaki bölüme bakın.)  
  
- Özel sınıf iç içe geçmiş bir sınıf olmamalıdır. Tam ad yolundaki fazladan "nokta", sınıf ad alanı bölümünün belirsizleşmesini sağlar ve ekli özellikler gibi diğer XAML özellikleriyle kesintiye uğratır.  
  
 Bir nesne bir nesne öğesi olarak örneklenebilir, oluşturulan nesne nesneyi temel alınan türü olarak alan özelliklerin özellik öğesi biçimini doldurabilir.  
  
 Değer dönüştürücüsünü etkinleştirirseniz, bu kriterleri karşılamayan türler için nesne değerleri de sağlayabilirsiniz. Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Yapılar  
 Yapılar, CLR tanımına göre her zaman XAML 'de oluşturulabilir. Bunun nedeni, bir CLR derleyicisinin bir yapı için örtük olarak parametresiz bir Oluşturucu oluşturmasıdır. Bu Oluşturucu tüm özellik değerlerini varsayılan değerlerine başlatır.  
  
 Bazı durumlarda, bir yapı için varsayılan yapım davranışı istenmez. Bunun nedeni, yapının değerleri birleşim olarak kavramsal bir şekilde doldurmasını amaçladığı bir durum olabilir. Birleşim olarak, içerilen değerler birbirini dışlayan yorumlayıcıya sahip olabilir ve bu nedenle, özelliklerinden hiçbiri ayarlanabilir değildir. WPF sözlüğbir yapısına bir örnek <xref:System.Windows.GridLength>. Bu tür yapılar, değerlerin öznitelik biçiminde ifade edilmesi için, farklı yorumlamalar veya yapı değerlerinin modlarını oluşturan dize kurallarını kullanarak bir tür dönüştürücüsü uygulamalıdır. Yapı Ayrıca, parametresiz bir Oluşturucu aracılığıyla kod oluşturma için benzer davranışları kullanıma sunmalıdır.  
  
### <a name="interfaces"></a>Arabirimler  
 Arabirimler, temel üye türleri olarak kullanılabilir. XAML tür sistemi atanabilir listeyi denetler ve değer olarak belirtilen nesnenin arabirime atanabileceği bekliyor. İlgili atanabilir bir tür XAML oluşturma gereksinimlerini desteklediği sürece, arabirimin XAML türü olarak nasıl sunulması gerektiği konusunda bir kavram yoktur.  
  
### <a name="factory-methods"></a>Fabrika yöntemleri  
 Fabrika yöntemleri bir XAML 2009 özelliğidir. Nesneler parametresiz oluşturuculara sahip olması gereken XAML ilkesini değiştirir. Bu konuda Fabrika yöntemleri açıklanmamıştır. Bkz. [X:FactoryMethod yönergesi](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Numaralandırmalar XAML yerel tür dönüştürme davranışına sahiptir. XAML 'de belirtilen sabit listesi sabit adları, temeldeki numaralandırma türüne göre çözümlenir ve sabit listesi değerini bir XAML nesne yazıcısına döndürür.  
  
 XAML, <xref:System.FlagsAttribute> uygulanmış Numaralandırmalar için flags stili kullanımı destekler. Daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../wpf/advanced/xaml-syntax-in-detail.md). ([Ayrıntılı XAML SÖZDIZIMI](../wpf/advanced/xaml-syntax-in-detail.md) WPF hedef kitlesi için yazılmıştır, ancak bu konudaki bilgilerin çoğu, belirli bir uygulama çerçevesine özgü olmayan XAML için geçerlidir.)  
  
## <a name="member-definitions"></a>Üye tanımları  
 Türler, XAML kullanımı için üyeleri tanımlayabilir. Söz konusu tür XAML ile kullanılabilir olmasa bile XAML ile kullanılabilen üyeleri tanımlayan türler mümkündür. Bu, CLR devralımı nedeniyle mümkündür. Bu nedenle, üyeyi devralan bir tür bir tür olarak XAML kullanımını desteklediğinden ve üye temel alınan türü için XAML kullanımını desteklediğinde ya da kullanılabilir yerel XAML sözdizimi varsa, bu üye XAML ile kullanılabilir.  
  
### <a name="properties"></a>Özellikler  
 Özellikleri tipik CLR `get` ve `set` erişimci düzenlerini ve dile uygun KeySize kullanarak genel bir CLR özelliği olarak tanımlarsanız, XAML tür sistemi, <xref:System.Xaml.XamlMember.IsReadPublic%2A> ve <xref:System.Xaml.XamlMember.IsWritePublic%2A>gibi <xref:System.Xaml.XamlMember> özellikler için belirtilen uygun bilgileri içeren bir üye olarak özelliği rapor edebilir.  
  
 Belirli özellikler, <xref:System.ComponentModel.TypeConverterAttribute>uygulayarak bir metin söz dizimini etkinleştirebilir. Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).  
  
 Bir metin sözdizimi veya yerel XAML dönüştürmesi yokluğunda ve biçimlendirme uzantısı kullanımı gibi daha fazla yöneltme yokluğunda, bir özelliğin türü (XAML türü sisteminde<xref:System.Xaml.XamlMember.TargetType%2A>), hedef türü CLR türü olarak davranarak XAML nesne yazıcısına bir örnek döndürebilmelidir.  
  
 XAML 2009 kullanıyorsanız, önceki noktalara uyulmazsa değer sağlamak için [X:Reference Işaretleme uzantısı](x-reference-markup-extension.md) kullanılabilir; Ancak, bir tür tanımı sorunundan daha fazla kullanım sorunu vardır.  
  
### <a name="events"></a>Olaylar  
 Olayları ortak bir CLR olayı olarak tanımlarsanız XAML tür sistemi, `true`olarak <xref:System.Xaml.XamlMember.IsEvent%2A> bir üye olarak rapor verebilir. Bağlantı, olay işleyicilerinin .NET Framework XAML Hizmetleri özellikleri kapsamında değildir; Bu, belirli çerçeveler ve uygulamalar için bırakılır.  
  
### <a name="methods"></a>Yöntemler  
 Metotlar için satır içi kod varsayılan XAML özelliği değildir. Çoğu durumda, XAML 'den Yöntem üyelerine doğrudan başvurmayın ve XAML içindeki yöntemlerin rolü yalnızca belirli XAML desenleri için destek sağlamaktır. [X:FactoryMethod yönergesi](x-factorymethod-directive.md) özel bir durumdur.  
  
### <a name="fields"></a>Alanlar  
 CLR tasarım yönergeleri statik olmayan alanları önleyin. Statik alanlar için yalnızca [X:static biçimlendirme uzantısı](x-static-markup-extension.md)aracılığıyla statik alan değerlerine erişebilirsiniz; Bu durumda, [X:static](x-static-markup-extension.md) kullanımlar için bir alan sunmak üzere clr tanımında özel bir şey yapmamanız gerekir.  
  
## <a name="attachable-members"></a>Eklenebilir Üyeler  
 Eklenebilir Üyeler, tanımlama türündeki bir erişimci yöntemi düzeniyle XAML 'ye sunulur. Tanımlama türünün kendisi bir nesne olarak kullanılabilir olması gerekmez. Aslında ortak bir model, rolü eklenebilir üyeye sahip olan bir hizmet sınıfı bildirmek ve ilgili davranışları uygulamaktır, ancak kullanıcı arabirimi gösterimi gibi başka bir işlev sunmaz. Aşağıdaki bölümlerde yer tutucu *PropertyName* , eklenebilir üyenin adını temsil eder. Bu ad, [XamlName dilbilgisinde](xamlname-grammar.md)geçerli olmalıdır.  
  
 Bu desenler ve bir türün diğer yöntemleri arasındaki ad çarpışmalarının dikkatli olun. Desenlerden biriyle eşleşen bir üye varsa, sizin amacınız olmasa bile bir XAML işlemcisi tarafından eklenebilir üye kullanım patika olarak yorumlanamaz.  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName erişimcisi  
 `Get`*PropertyName* erişimcisi için imza şu olmalıdır:  
  
 `public static object Get` *PropertyName* `(object``target` `)`  
  
- `target` nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Bunu, eklenebilir üyenin kullanımını kapsam için kullanabilirsiniz; hedeflenen kapsamınız dışında kullanımlar, daha sonra bir XAML ayrıştırma hatası ile ortaya çıkacak geçersiz atama özel durumları oluşturur. `target` parametre adı bir gereksinim değildir, ancak çoğu uygulamada kuralına göre `target` olarak adlandırılır.  
  
- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Eklenebilir üyenin öznitelik kullanımı için <xref:System.ComponentModel.TypeConverter> etkin bir metin sözdizimini desteklemek için, `Get`*PropertyName* erişimcisine <xref:System.ComponentModel.TypeConverterAttribute> uygulayın. `set` yerine `get` uygulamak, sezgisel olmayan görünebilir; Ancak, bu kural, tasarımcı senaryolarında yararlı olan, seri hale getirilebilen salt okunurdur eklenebilir Üyeler kavramını destekleyebilir.  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName erişimcisi  
 Set*PropertyName* erişimcisinin imzası şu olmalıdır:  
  
 `public static void Set` *PropertyName* `(object``target` `, object``value` `)`  
  
- `target` nesnesi, uygulamanızda, önceki bölümde açıklandığı gibi aynı mantık ve sonuçlarla daha belirli bir tür olarak belirtilebilir.  
  
- `value` nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Bu yöntemin değerinin, genellikle öznitelik biçiminde XAML kullanımının geldiği giriş olduğunu unutmayın. Öznitelik formunda, bir metin sözdizimi için değer Dönüştürücüsü desteği ve `Get`*PropertyName* erişimcisinde özniteliği olmalıdır.  
  
### <a name="attachable-member-stores"></a>Eklenebilir üye depoları  
 Erişimci yöntemleri genellikle, eklenebilir üye değerlerinin bir nesne grafiğine yerleştirileceği veya nesne grafiğinin dışına değer alıp bunları doğru şekilde serileştirmek için bir yol sağlamak üzere yeterli değildir. Bu işlevi sağlamak için, önceki erişimci imzalarındaki `target` nesnelerinin değerleri depoladığını bilme özelliği olmalıdır. Depolama mekanizması, eklenebilir üyenin üye listesinde olmadığı yerde, üyenin iliştirilebildiği üye ilkesiyle tutarlı olması gerekir. .NET Framework XAML Hizmetleri, <xref:System.Xaml.IAttachedPropertyStore> ve <xref:System.Xaml.AttachablePropertyServices>API 'Leri aracılığıyla eklenebilir üye depoları için bir uygulama tekniği sağlar. <xref:System.Xaml.IAttachedPropertyStore>, mağaza uygulamasını keşfetmesi için XAML yazarları tarafından kullanılır ve erişimcilerinin `target` bir tür üzerinde uygulanmalıdır. Statik <xref:System.Xaml.AttachablePropertyServices> API 'Leri erişimcilerinin gövdesinde kullanılır ve <xref:System.Xaml.AttachableMemberIdentifier>tarafından eklenebilir üyeye başvurur.  
  
## <a name="xaml-related-clr-attributes"></a>XAML ile Ilgili CLR öznitelikleri  
 Türler, Üyeler ve derlemeleriniz .NET Framework XAML Hizmetleri için XAML türü sistem bilgilerini raporlamak için önemli Attributing. Bu, türlerinizi .NET Framework XAML Hizmetleri XAML okuyucuları ve XAML yazıcılarında doğrudan temel alan XAML sistemleriyle kullanım için istiyorsanız veya bu XAML okuyucuları ve XAML yazıcılarını temel alan XAML kullanan bir çerçeve tanımladıktan veya kullandıysanız geçerlidir.  
  
 Özel türleriniz için XAML desteğiyle ilgili olan XAML ile ilgili her özniteliğin listelenmesi için bkz. [özel türler ve kitaplıklar Için xaml ıle ılgılı clr öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Kullanım  
 Özel türlerin kullanımı, biçimlendirme yazarının, özel türü içeren derleme ve CLR ad alanı için bir önek eşlemesini gerektirir. Bu yordam, bu konuda açıklanmamıştır.  
  
## <a name="access-level"></a>Erişim düzeyi  
 XAML, `internal` erişim düzeyine sahip türleri yüklemek ve örneklemek için bir yol sağlar. Bu özellik, kullanıcı kodunun kendi türlerini tanımlayabilmesi ve ardından aynı kullanıcı kodu kapsamının bir parçası olan biçimlendirmeden bu sınıfların örneklemesinin sağlanması için sağlanır.  
  
 WPF 'den bir örnek, Kullanıcı kodu, bir UI davranışını yeniden düzenleme yolu olarak tasarlanan, ancak destekleyici sınıfı `public` erişim düzeyiyle belirtilen olası uzantı mekanizmalarının bir parçası olarak değil, bir <xref:System.Windows.Controls.UserControl> tanımlar. Bu tür bir <xref:System.Windows.Controls.UserControl>, yedekleme kodu bir XAML türü olarak başvurulduğu aynı derlemeye derlenirse `internal` erişimiyle birlikte bildirilemez.  
  
 Tam güven altına XAML yükleyen ve <xref:System.Xaml.XamlObjectWriter>kullanan bir uygulama için, `internal` erişim düzeyiyle sınıfları yüklemek her zaman etkindir.  
  
 Kısmi güven altına XAML yükleyen bir uygulama için, <xref:System.Xaml.Permissions.XamlAccessLevel> API 'sini kullanarak erişim düzeyi özelliklerini kontrol edebilirsiniz. Ayrıca, erteleme mekanizmaları (WPF şablon sistemi gibi), herhangi bir erişim düzeyi izni yayabilir ve bunları nihai çalışma süresi değerlendirmelerine karşı koruyabilmelidir; Bu, <xref:System.Xaml.Permissions.XamlAccessLevel> bilgileri geçirerek dahili olarak işlenir.  
  
### <a name="wpf-implementation"></a>WPF uygulama  
 WPF XAML, kısmi güven altında BAML 'nin yüklendiği durumlarda kısmi güven erişim modeli kullanır, bu da BAML kaynağı olan derleme için <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> erişim kısıtlıdır. Deferral için WPF, erişim düzeyi bilgilerinin geçirilmesi için bir mekanizma olarak <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> kullanır.  
  
 WPF XAML terminolojisinde, *dahili bir tür* , başvuran xaml de içeren aynı derleme tarafından tanımlanan bir türdür. Böyle bir tür, bir eşlemenin derleme = bölümünü kasıtlı olarak atuygulayan XAML ad alanı aracılığıyla eşleştirilebilir, örneğin, `xmlns:local="clr-namespace:WPFApplication1"`.  BAML bir iç türe başvuruyorsa ve bu türün `internal` erişim düzeyi varsa, bu derleme için bir `GeneratedInternalTypeHelper` sınıfı oluşturur. `GeneratedInternalTypeHelper`önlemek istiyorsanız, `public` erişim düzeyini kullanmalısınız veya ilgili sınıfı ayrı bir derlemede çarpanlara katmalıdır ve bu derlemeye bağımlı hale gelmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Türler ve Kitaplıklar İçin XAML İlişkili CLR Öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Hizmetleri](index.md)
