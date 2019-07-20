---
title: .NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: e563c0d7e5113d55d4b942fb1d175a64f5b71abc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364300"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
İş nesneleri olan veya belirli çerçevelere bağımlılığı olmayan türler olan özel türler tanımladığınızda, kullanabileceğiniz XAML için bazı en iyi uygulamalar vardır. Bu yöntemleri izlerseniz .NET Framework XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları, bu türün XAML özelliklerini bulabilir ve xaml tür sistemini kullanarak XAML düğüm akışında uygun gösterimi verebilir. Bu konuda tür tanımları, üye tanımları ve tür veya üyelerin CLR Attributing için en iyi yöntemler açıklanmaktadır.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML için Oluşturucu desenleri ve tür tanımları  
 XAML 'de bir nesne öğesi olarak örneklendirmak için, özel bir sınıf aşağıdaki gereksinimleri karşılamalıdır:  
  
- Özel sınıf ortak olmalıdır ve varsayılan (parametresiz) bir ortak Oluşturucu kullanıma sunmalıdır. (Yapılar hakkında notlar için aşağıdaki bölüme bakın.)  
  
- Özel sınıf iç içe geçmiş bir sınıf olmamalıdır. Tam ad yolundaki fazladan "nokta", sınıf ad alanı bölümünün belirsizleşmesini sağlar ve ekli özellikler gibi diğer XAML özellikleriyle kesintiye uğratır.  
  
 Bir nesne bir nesne öğesi olarak örneklenebilir, oluşturulan nesne nesneyi temel alınan türü olarak alan özelliklerin özellik öğesi biçimini doldurabilir.  
  
 Değer dönüştürücüsünü etkinleştirirseniz, bu kriterleri karşılamayan türler için nesne değerleri de sağlayabilirsiniz. Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Yapılar  
 Yapılar, CLR tanımına göre her zaman XAML 'de oluşturulabilir. Bunun nedeni, bir CLR derleyicisinin bir yapı için örtük olarak parametresiz bir Oluşturucu oluşturmasıdır. Bu Oluşturucu tüm özellik değerlerini varsayılan değerlerine başlatır.  
  
 Bazı durumlarda, bir yapı için varsayılan yapım davranışı istenmez. Bunun nedeni, yapının değerleri birleşim olarak kavramsal bir şekilde doldurmasını amaçladığı bir durum olabilir. Birleşim olarak, içerilen değerler birbirini dışlayan yorumlayıcıya sahip olabilir ve bu nedenle, özelliklerinden hiçbiri ayarlanabilir değildir. WPF sözlüğbir <xref:System.Windows.GridLength>yapısına örnek olarak. Bu tür yapılar, değerlerin öznitelik biçiminde ifade edilmesi için, farklı yorumlamalar veya yapı değerlerinin modlarını oluşturan dize kurallarını kullanarak bir tür dönüştürücüsü uygulamalıdır. Yapı Ayrıca, parametresiz bir Oluşturucu aracılığıyla kod oluşturma için benzer davranışları kullanıma sunmalıdır.  
  
### <a name="interfaces"></a>Arabirimler  
 Arabirimler, temel üye türleri olarak kullanılabilir. XAML tür sistemi atanabilir listeyi denetler ve değer olarak belirtilen nesnenin arabirime atanabileceği bekliyor. İlgili atanabilir bir tür XAML oluşturma gereksinimlerini desteklediği sürece, arabirimin XAML türü olarak nasıl sunulması gerektiği konusunda bir kavram yoktur.  
  
### <a name="factory-methods"></a>Fabrika yöntemleri  
 Fabrika yöntemleri bir XAML 2009 özelliğidir. Nesneler parametresiz oluşturuculara sahip olması gereken XAML ilkesini değiştirir. Bu konuda Fabrika yöntemleri açıklanmamıştır. Bkz. [X:FactoryMethod yönergesi](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Numaralandırmalar XAML yerel tür dönüştürme davranışına sahiptir. XAML 'de belirtilen sabit listesi sabit adları, temeldeki numaralandırma türüne göre çözümlenir ve sabit listesi değerini bir XAML nesne yazıcısına döndürür.  
  
 XAML, <xref:System.FlagsAttribute> uygulanan Numaralandırmalar için bir bayraklar stili kullanımını destekler. Daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../wpf/advanced/xaml-syntax-in-detail.md). ([Ayrıntılı XAML SÖZDIZIMI](../wpf/advanced/xaml-syntax-in-detail.md) WPF hedef kitlesi için yazılmıştır, ancak bu konudaki bilgilerin çoğu, belirli bir uygulama çerçevesine özgü olmayan XAML için geçerlidir.)  
  
## <a name="member-definitions"></a>Üye tanımları  
 Türler, XAML kullanımı için üyeleri tanımlayabilir. Söz konusu tür XAML ile kullanılabilir olmasa bile XAML ile kullanılabilen üyeleri tanımlayan türler mümkündür. Bu, CLR devralımı nedeniyle mümkündür. Bu nedenle, üyeyi devralan bir tür bir tür olarak XAML kullanımını desteklediğinden ve üye temel alınan türü için XAML kullanımını desteklediğinde ya da kullanılabilir yerel XAML sözdizimi varsa, bu üye XAML ile kullanılabilir.  
  
### <a name="properties"></a>Özellikler  
 Tipik CLR `get` ve `set` erişimci düzenlerini ve dile uygun KeySize özelliğini kullanarak özellikleri genel bir CLR özelliği olarak tanımlarsanız, XAML tür sistemi, <xref:System.Xaml.XamlMember> ve<xref:System.Xaml.XamlMember.IsWritePublic%2A>gibiözellikler. <xref:System.Xaml.XamlMember.IsReadPublic%2A>  
  
 Belirli özellikler, bir metin söz dizimini uygulayarak <xref:System.ComponentModel.TypeConverterAttribute>etkinleştirebilir. Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions-for-xaml.md).  
  
 Bir metin sözdizimi veya yerel xaml dönüştürmesi yokluğunda ve biçimlendirme uzantısı kullanımı gibi daha fazla yöneltme yokluğunda, bir özelliğin türü (<xref:System.Xaml.XamlMember.TargetType%2A> xaml tür sisteminde) t 'yi düşünerek bir xaml nesne yazıcısında bir örnek döndürebilmelidir bir CLR türü olarak arget türü.  
  
 XAML 2009 kullanıyorsanız, önceki noktalara uyulmazsa değer sağlamak için [X:Reference Işaretleme uzantısı](x-reference-markup-extension.md) kullanılabilir; Ancak, bir tür tanımı sorunundan daha fazla kullanım sorunu vardır.  
  
### <a name="events"></a>Olaylar  
 Olayları ortak bir clr olayı olarak tanımlarsanız, XAML tür sistemi olayı <xref:System.Xaml.XamlMember.IsEvent%2A> olarak `true`bir üye olarak rapor edebilir. Bağlantı, olay işleyicilerinin .NET Framework XAML Hizmetleri özellikleri kapsamında değildir; Bu, belirli çerçeveler ve uygulamalar için bırakılır.  
  
### <a name="methods"></a>Yöntemler  
 Metotlar için satır içi kod varsayılan XAML özelliği değildir. Çoğu durumda, XAML 'den Yöntem üyelerine doğrudan başvurmayın ve XAML içindeki yöntemlerin rolü yalnızca belirli XAML desenleri için destek sağlamaktır. [X:FactoryMethod yönergesi](x-factorymethod-directive.md) özel bir durumdur.  
  
### <a name="fields"></a>Alanlar  
 CLR tasarım yönergeleri statik olmayan alanları önleyin. Statik alanlar için yalnızca [X:static biçimlendirme uzantısı](x-static-markup-extension.md)aracılığıyla statik alan değerlerine erişebilirsiniz; Bu durumda, [X:static](x-static-markup-extension.md) kullanımlar için bir alan sunmak üzere clr tanımında özel bir şey yapmamanız gerekir.  
  
## <a name="attachable-members"></a>Eklenebilir Üyeler  
 Eklenebilir Üyeler, tanımlama türündeki bir erişimci yöntemi düzeniyle XAML 'ye sunulur. Tanımlama türünün kendisi bir nesne olarak kullanılabilir olması gerekmez. Aslında ortak bir model, rolü eklenebilir üyeye sahip olan bir hizmet sınıfı bildirmek ve ilgili davranışları uygulamaktır, ancak kullanıcı arabirimi gösterimi gibi başka bir işlev sunmaz. Aşağıdaki bölümlerde yer tutucu *PropertyName* , eklenebilir üyenin adını temsil eder. Bu ad, [XamlName dilbilgisinde](xamlname-grammar.md)geçerli olmalıdır.  
  
 Bu desenler ve bir türün diğer yöntemleri arasındaki ad çarpışmalarının dikkatli olun. Desenlerden biriyle eşleşen bir üye varsa, sizin amacınız olmasa bile bir XAML işlemcisi tarafından eklenebilir üye kullanım patika olarak yorumlanamaz.  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName erişimcisi  
 `Get` *PropertyName* erişimcisi için imza şu olmalıdır:  
  
 `public static object Get`*PropertyName* `(object``target`  `)`  
  
- Nesne `target` , uygulamanızda daha belirli bir tür olarak belirtilebilir. Bunu, eklenebilir üyenin kullanımını kapsam için kullanabilirsiniz; hedeflenen kapsamınız dışında kullanımlar, daha sonra bir XAML ayrıştırma hatası ile ortaya çıkacak geçersiz atama özel durumları oluşturur. Parametre adı `target` bir gereksinim değildir, ancak çoğu uygulamada kuralına göre `target` adlandırılır.  
  
- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Eklenebilir üyenin öznitelik <xref:System.ComponentModel.TypeConverter> kullanımı için etkin bir metin sözdizimini desteklemek için *PropertyName* erişimcisine uygulayın <xref:System.ComponentModel.TypeConverterAttribute>. `Get` `get` Yerine`set` öğesine uygulamak, sezgisel olmayan görünebilir; ancak, bu kural, tasarımcı senaryolarında yararlı olan, seri hale getirilebilir olan salt okunurdur eklenebilir Üyeler kavramını destekleyebilir.  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName erişimcisi  
 Set*PropertyName* erişimcisinin imzası şu olmalıdır:  
  
 `public static void Set`*PropertyName* `(object``target` `, object``value`    `)`  
  
- `target` Nesnesi, uygulamanızda, önceki bölümde açıklandığı gibi aynı mantık ve sonuçlarla daha belirli bir tür olarak belirtilebilir.  
  
- Nesne `value` , uygulamanızda daha belirli bir tür olarak belirtilebilir.  
  
 Bu yöntemin değerinin, genellikle öznitelik biçiminde XAML kullanımının geldiği giriş olduğunu unutmayın. Öznitelik formunda, bir metin sözdizimi için değer Dönüştürücüsü desteği ve `Get` *PropertyName* erişimcisinde özniteliği olmalıdır.  
  
### <a name="attachable-member-stores"></a>Eklenebilir üye depoları  
 Erişimci yöntemleri genellikle, eklenebilir üye değerlerinin bir nesne grafiğine yerleştirileceği veya nesne grafiğinin dışına değer alıp bunları doğru şekilde serileştirmek için bir yol sağlamak üzere yeterli değildir. Bu işlevi sağlamak için, `target` önceki erişimci imzalarındaki nesnelerin değerleri depolaması yeterli olmalıdır. Depolama mekanizması, eklenebilir üyenin üye listesinde olmadığı yerde, üyenin iliştirilebildiği üye ilkesiyle tutarlı olması gerekir. .NET Framework xaml Hizmetleri, API 'ler <xref:System.Xaml.IAttachedPropertyStore> ve <xref:System.Xaml.AttachablePropertyServices>aracılığıyla eklenebilir üye depoları için bir uygulama tekniği sağlar. <xref:System.Xaml.IAttachedPropertyStore>, bir mağaza uygulamasını keşfetmesi için XAML yazarları tarafından kullanılır ve erişimcilerinin bir türü `target` üzerinde uygulanmalıdır. Statik <xref:System.Xaml.AttachablePropertyServices> API 'ler erişimcilerinin gövdesinde kullanılır ve eklenebilir üyeye <xref:System.Xaml.AttachableMemberIdentifier>öğesine başvurur.  
  
## <a name="xaml-related-clr-attributes"></a>XAML ile Ilgili CLR öznitelikleri  
 Türler, Üyeler ve derlemeleriniz .NET Framework XAML Hizmetleri için XAML türü sistem bilgilerini raporlamak için önemli Attributing. Bu, türlerinizi .NET Framework XAML Hizmetleri XAML okuyucuları ve XAML yazıcılarında doğrudan temel alan XAML sistemleriyle kullanım için istiyorsanız veya bu XAML okuyucuları ve XAML yazıcılarını temel alan XAML kullanan bir çerçeve tanımladıktan veya kullandıysanız geçerlidir.  
  
 Özel türleriniz için XAML desteğiyle ilgili olan XAML ile ilgili her özniteliğin listelenmesi için bkz. [özel türler ve kitaplıklar Için xaml ıle ılgılı clr öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Kullanım  
 Özel türlerin kullanımı, biçimlendirme yazarının, özel türü içeren derleme ve CLR ad alanı için bir önek eşlemesini gerektirir. Bu yordam, bu konuda açıklanmamıştır.  
  
## <a name="access-level"></a>Erişim düzeyi  
 XAML, `internal` erişim düzeyi olan türleri yüklemek ve örneklemek için bir yol sağlar. Bu özellik, kullanıcı kodunun kendi türlerini tanımlayabilmesi ve ardından aynı kullanıcı kodu kapsamının bir parçası olan biçimlendirmeden bu sınıfların örneklemesinin sağlanması için sağlanır.  
  
 WPF 'den bir örnek, Kullanıcı kodu, bir UI <xref:System.Windows.Controls.UserControl> davranışını yeniden düzenleme yöntemi olarak tasarlanan, ancak destekleme `public` sınıfı erişim düzeyiyle tanımlanarak ima edilebilir olan herhangi bir uzantı mekanizmalarının bir parçası olarak değil, her ne zaman bir örnektir. Bu tür <xref:System.Windows.Controls.UserControl> bir, yedekleme kodu `internal` bir xaml türü olarak başvurulduğu aynı derlemeye derlenirse erişim ile bildirilemez.  
  
 Tam güven ve kullanımları <xref:System.Xaml.XamlObjectWriter>altında xaml yükleyen bir uygulama için, `internal` erişim düzeyiyle sınıfları yüklemek her zaman etkindir.  
  
 Kısmi güven altına xaml yükleyen bir uygulama için, <xref:System.Xaml.Permissions.XamlAccessLevel> API 'yi kullanarak erişim düzeyi özelliklerini kontrol edebilirsiniz. Ayrıca, erteleme mekanizmaları (WPF şablon sistemi gibi), herhangi bir erişim düzeyi izni yayabilir ve bunları nihai çalışma süresi değerlendirmelerine karşı koruyabilmelidir; Bu, <xref:System.Xaml.Permissions.XamlAccessLevel> bilgileri geçirerek dahili olarak işlenir.  
  
### <a name="wpf-implementation"></a>WPF uygulama  
 WPF XAML, kısmi güven altında BAML 'nin yüklendiği durumlarda kısmi güven erişim modeli kullanır, bu da BAML kaynağı olan derleme <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> için erişim kısıtlıdır. Deferral için WPF, erişim <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> düzeyi bilgilerini geçirmek için bir mekanizma kullanır.  
  
 WPF XAML terminolojisinde, *dahili bir tür* , başvuran xaml de içeren aynı derleme tarafından tanımlanan bir türdür. Böyle bir tür, bir eşlemenin derleme = bölümünü (örneğin, `xmlns:local="clr-namespace:WPFApplication1"`) kasıtlı olarak atbir xaml ad alanı aracılığıyla eşlenebilir.  BAML bir iç türe başvuruyorsa ve bu türün `internal` erişim düzeyi varsa, bu derleme için bir `GeneratedInternalTypeHelper` sınıf oluşturur. Kaçınmak `GeneratedInternalTypeHelper`isterseniz, erişim düzeyini kullanmanız `public` ya da ilgili sınıfı ayrı bir derlemede çarpanlara katmalıdır ve bu derlemeye bağımlı hale gelmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Türler ve Kitaplıklar İçin XAML İlişkili CLR Öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Hizmetleri](index.md)
