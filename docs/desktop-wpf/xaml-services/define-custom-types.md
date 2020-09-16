---
title: .NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 2c0578b5397172814c708706173c69ef69f91b2a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551784"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>.NET XAML Hizmetleri ile kullanılacak özel türleri tanımlama

İş nesneleri olan veya belirli çerçevelere bağımlılığı olmayan türler olan özel türler tanımladığınızda, kullanabileceğiniz XAML için bazı en iyi uygulamalar vardır. Bu uygulamaları izlerseniz, .NET XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları, bu türden XAML özelliklerini bulabilir ve xaml tür sistemini kullanarak XAML düğüm akışında uygun gösterimi verebilir. Bu konuda tür tanımları, üye tanımları ve tür veya üyelerin CLR Attributing için en iyi yöntemler açıklanmaktadır.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML için Oluşturucu desenleri ve tür tanımları

XAML 'de bir nesne öğesi olarak örneklendirmak için, özel bir sınıf aşağıdaki gereksinimleri karşılamalıdır:

- Özel sınıf ortak olmalıdır ve parametresiz bir ortak oluşturucuyu kullanıma sunmalıdır. (Yapılar hakkında notlar için aşağıdaki bölüme bakın.)

- Özel sınıf iç içe geçmiş bir sınıf olmamalıdır. Tam ad yolundaki fazladan "nokta", sınıf ad alanı bölümünün belirsizleşmesini sağlar ve ekli özellikler gibi diğer XAML özellikleriyle kesintiye uğratır.
Bir nesne bir nesne öğesi olarak örneklenebilir, oluşturulan nesne nesneyi temel alınan türü olarak alan özelliklerin özellik öğesi biçimini doldurabilir.

Değer dönüştürücüsünü etkinleştirirseniz, bu kriterleri karşılamayan türler için nesne değerleri de sağlayabilirsiniz. Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Yapılar

Yapılar, CLR tanımına göre her zaman XAML 'de oluşturulabilir. Bunun nedeni, bir CLR derleyicisinin bir yapı için örtük olarak parametresiz bir Oluşturucu oluşturmasıdır. Bu Oluşturucu tüm özellik değerlerini varsayılan değerlerine başlatır.

Bazı durumlarda, bir yapı için varsayılan yapım davranışı istenmez. Bunun nedeni, yapının değerleri birleşim olarak kavramsal bir şekilde doldurmasını amaçladığı bir durum olabilir. Birleşim olarak, içerilen değerler birbirini dışlayan yorumlayıcıya sahip olabilir ve bu nedenle, özelliklerinden hiçbiri ayarlanabilir değildir. WPF sözlüğbir yapısına örnek olarak <xref:System.Windows.GridLength> . Bu tür yapılar, değerlerin öznitelik biçiminde ifade edilmesi için, farklı yorumlamalar veya yapı değerlerinin modlarını oluşturan dize kurallarını kullanarak bir tür dönüştürücüsü uygulamalıdır. Yapı Ayrıca, parametresiz bir Oluşturucu aracılığıyla kod oluşturma için benzer davranışları kullanıma sunmalıdır.

### <a name="interfaces"></a>Arabirimler

Arabirimler, temel üye türleri olarak kullanılabilir. XAML tür sistemi atanabilir listeyi denetler ve değer olarak belirtilen nesnenin arabirime atanabileceği bekliyor. İlgili atanabilir bir tür XAML oluşturma gereksinimlerini desteklediği sürece, arabirimin XAML türü olarak nasıl sunulması gerektiği konusunda bir kavram yoktur.

### <a name="factory-methods"></a>Fabrika yöntemleri

Fabrika yöntemleri bir XAML 2009 özelliğidir. Nesneler parametresiz oluşturuculara sahip olması gereken XAML ilkesini değiştirir. Bu makalede Fabrika yöntemleri açıklanmamıştır. Bkz. [X:FactoryMethod yönergesi](xfactorymethod-directive.md).

## <a name="enumerations"></a>Listelemeler

Numaralandırmalar XAML yerel tür dönüştürme davranışına sahiptir. XAML 'de belirtilen sabit listesi sabit adları, temeldeki numaralandırma türüne göre çözümlenir ve sabit listesi değerini bir XAML nesne yazıcısına döndürür.

XAML, uygulanan Numaralandırmalar için bir bayraklar stili kullanımını destekler <xref:System.FlagsAttribute> . Daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail). ([Ayrıntılı XAML SÖZDIZIMI](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail) WPF hedef kitlesi için yazılmıştır, ancak bu konudaki bilgilerin çoğu, belirli bir uygulama çerçevesine özgü olmayan XAML için geçerlidir.)

## <a name="member-definitions"></a>Üye tanımları

Türler, XAML kullanımı için üyeleri tanımlayabilir. Türlerin XAML ile kullanılabilir olması, bu tür XAML ile kullanılabilir olmasa bile, XAML ile kullanılabilen üyeleri tanımlamak mümkündür. Bu, CLR devralımı nedeniyle mümkündür. Bu nedenle, üyeyi devralan bir tür bir tür olarak XAML kullanımını desteklediğinden ve üye temel alınan türü için XAML kullanımını desteklediğinde ya da kullanılabilir yerel XAML sözdizimi varsa, bu üye XAML ile kullanılabilir.

### <a name="properties"></a>Özellikler

Tipik CLR ve erişimci düzenlerini ve dile uygun KeySize özelliğini kullanarak genel bir CLR özelliği olarak Özellikler tanımlarsanız `get` `set` , XAML tür sistemi özelliği, ve gibi özellikler için belirtilen uygun bilgileri içeren bir üye olarak rapor edebilir <xref:System.Xaml.XamlMember> <xref:System.Xaml.XamlMember.IsReadPublic%2A> <xref:System.Xaml.XamlMember.IsWritePublic%2A> .

Belirli özellikler, bir metin söz dizimini uygulayarak etkinleştirebilir <xref:System.ComponentModel.TypeConverterAttribute> . Daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions.md).

Bir metin sözdizimi veya yerel XAML dönüştürmesi yokluğunda ve biçimlendirme uzantısı kullanımı gibi daha fazla yöneltme yokluğunda bir özelliğin türü ( <xref:System.Xaml.XamlMember.TargetType%2A> xaml tür sisteminde), hedef türü clr türü olarak davranarak bir ÖRNEĞI xaml nesne yazıcısına döndürebilmelidir.

XAML 2009 kullanıyorsanız, önceki noktalara uyulmazsa değer sağlamak için [X:Reference Işaretleme uzantısı](xreference-markup-extension.md) kullanılabilir; Ancak, bir tür tanımı sorunundan daha fazla kullanım sorunu vardır.

### <a name="events"></a>Ekinlikler

Olayları ortak bir CLR olayı olarak tanımlarsanız, XAML tür sistemi olayı olarak bir üye olarak rapor edebilir <xref:System.Xaml.XamlMember.IsEvent%2A> `true` . Olay işleyicilerinin kablolaması .NET XAML Hizmetleri özellikleri kapsamında değildir; kablolama, belirli çerçeveler ve uygulamalar için bırakılır.

### <a name="methods"></a>Yöntemler

Metotlar için satır içi kod varsayılan XAML özelliği değildir. Çoğu durumda, XAML 'deki Yöntem üyelerine doğrudan başvurmayın ve XAML içindeki yöntemlerin rolü yalnızca belirli XAML desenleri için destek sağlamaktır. [X:FactoryMethod yönergesi](xfactorymethod-directive.md) özel bir durumdur.

### <a name="fields"></a>Alanlar

CLR tasarım yönergeleri statik olmayan alanları önleyin. Statik alanlar için yalnızca [X:static biçimlendirme uzantısı](xstatic-markup-extension.md)aracılığıyla statik alan değerlerine erişebilirsiniz; Bu durumda, [X:static](xstatic-markup-extension.md) kullanımlar için bir alan sunmak üzere clr tanımında özel bir şey yapmamanız gerekir.

## <a name="attachable-members"></a>Eklenebilir Üyeler

Eklenebilir Üyeler, tanımlama türündeki bir erişimci yöntemi düzeniyle XAML 'ye sunulur. Tanımlama türünün kendisi bir nesne olarak kullanılabilir olması gerekmez. Aslında ortak bir model, rolü eklenebilir üyeye sahip olan bir hizmet sınıfı bildirmek ve ilgili davranışları uygulamaktır, ancak kullanıcı arabirimi gösterimi gibi başka bir işlev sunmaz. Aşağıdaki bölümlerde yer tutucu *PropertyName* , eklenebilir üyenin adını temsil eder. Bu ad, [XamlName dilbilgisinde](xamlname-grammar.md)geçerli olmalıdır.

Bu desenler ve bir türün diğer yöntemleri arasındaki ad çarpışmalarının dikkatli olun. Desenlerden biriyle eşleşen bir üye varsa, sizin amacınız olmasa bile bir XAML işlemcisi tarafından eklenebilir üye kullanım patika olarak yorumlanamaz.

#### <a name="the-getpropertyname-accessor"></a>GetPropertyName erişimcisi

Erişimcinin imzası şu olmalıdır `GetPropertyName` :

`public static object GetPropertyName(object target)`

- `target`Nesne, uygulamanızda daha belirli bir tür olarak belirtilebilir. Bunu, eklenebilir üyenin kullanımını kapsam için kullanabilirsiniz; hedeflenen kapsamınız dışında kullanımlar, daha sonra bir XAML ayrıştırma hatası ile ortaya çıkacak geçersiz atama özel durumları oluşturur. Parametre adı `target` bir gereksinim değildir, ancak `target` çoğu uygulamada kuralına göre adlandırılır.

- Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir.

<xref:System.ComponentModel.TypeConverter>Eklenebilir üyenin öznitelik kullanımı için etkin bir metin sözdizimini desteklemek için, <xref:System.ComponentModel.TypeConverterAttribute> `GetPropertyName` erişimciye uygulayın. Yerine öğesine uygulamak, `get` `set` sezgisel olmayan görünebilir; ancak, bu kural, tasarımcı senaryolarında yararlı olan, seri hale getirilebilir olan salt okunurdur eklenebilir Üyeler kavramını destekleyebilir.

#### <a name="the-setpropertyname-accessor"></a>SetPropertyName erişimcisi

Erişimcinin imzası şu olmalıdır `SetPropertyName` :

`public static void SetPropertyName(object target, object value)`

- `target`Nesnesi, uygulamanızda, önceki bölümde açıklandığı gibi aynı mantık ve sonuçlarla daha belirli bir tür olarak belirtilebilir.

- `value`Nesne, uygulamanızda daha belirli bir tür olarak belirtilebilir.

Bu yöntemin değerinin, genellikle öznitelik biçiminde XAML kullanımının geldiği giriş olduğunu unutmayın. Öznitelik formunda, bir metin sözdizimi için değer Dönüştürücüsü desteği ve `GetPropertyName` s erişimcisinde özniteliği olmalıdır.

### <a name="attachable-member-stores"></a>Eklenebilir üye depoları

Erişimci yöntemleri genellikle, eklenebilir üye değerlerinin bir nesne grafiğine yerleştirileceği veya nesne grafiğinin dışına değer alıp bunları doğru şekilde serileştirmek için bir yol sağlamak üzere yeterli değildir. Bu işlevi sağlamak için, `target` önceki erişimci imzalarındaki nesnelerin değerleri depolaması yeterli olmalıdır. Depolama mekanizması, eklenebilir üyenin üye listesinde olmadığı yerde, üyenin iliştirilebildiği üye ilkesiyle tutarlı olması gerekir. .NET XAML Hizmetleri, API 'Ler ve aracılığıyla eklenebilir üye depoları için bir uygulama tekniği <xref:System.Xaml.IAttachedPropertyStore> sağlar <xref:System.Xaml.AttachablePropertyServices> . <xref:System.Xaml.IAttachedPropertyStore> , bir mağaza uygulamasını keşfetmesi için XAML yazarları tarafından kullanılır ve erişimcilerinin bir türü üzerinde uygulanmalıdır `target` . Statik <xref:System.Xaml.AttachablePropertyServices> API 'ler erişimcilerinin gövdesinde kullanılır ve eklenebilir üyeye öğesine başvurur <xref:System.Xaml.AttachableMemberIdentifier> .

## <a name="xaml-related-clr-attributes"></a>XAML ile Ilgili CLR öznitelikleri

Türler, Üyeler ve derlemeleriniz, XAML türü sistem bilgilerini .NET XAML hizmetlerine raporlamak için önemli Attributing. Aşağıdaki durumlardan biri geçerliyse, raporlama XAML türü sistem bilgileri geçerlidir:

- Türlerinizi, .NET XAML Hizmetleri XAML okuyucuları ve XAML yazıcılarında doğrudan temel alan XAML sistemleri ile kullanım için amaçlamıştınız.
- Bu XAML okuyucuları ve XAML yazıcılarını temel alan XAML kullanan bir çerçeve tanımlar veya kullanırsınız.

Özel türleriniz için XAML desteğiyle ilgili olan XAML ile ilgili her özniteliğin listelenmesi için bkz. [özel türler ve kitaplıklar Için xaml ıle ılgılı clr öznitelikleri](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Kullanım

Özel türlerin kullanımı, biçimlendirme yazarının, özel türü içeren derleme ve CLR ad alanı için bir önek eşlemesini gerektirir. Bu yordam, bu konuda açıklanmamıştır.

## <a name="access-level"></a>Erişim düzeyi

XAML, erişim düzeyi olan türleri yüklemek ve örneklemek için bir yol sağlar `internal` . Bu özellik, kullanıcı kodunun kendi türlerini tanımlayabilmesi ve ardından aynı kullanıcı kodu kapsamının bir parçası olan biçimlendirmeden bu sınıfların örneklemesinin sağlanması için sağlanır.

WPF 'den bir örnek, Kullanıcı kodu, bir <xref:System.Windows.Controls.UserControl> UI davranışını yeniden düzenleme yöntemi olarak tasarlanan, ancak destekleme sınıfı erişim düzeyiyle tanımlanarak ima edilebilir olan herhangi bir uzantı mekanizmalarının bir parçası olarak değil, her ne zaman bir örnektir `public` . Bu tür bir <xref:System.Windows.Controls.UserControl> `internal` , yedekleme kodu bir xaml türü olarak başvurulduğu aynı derlemeye derlenirse erişim ile bildirilemez.

Tam güven ve kullanımları altında XAML yükleyen bir uygulama için <xref:System.Xaml.XamlObjectWriter> , erişim düzeyiyle sınıfları yüklemek `internal` her zaman etkindir.

Kısmi güven altına XAML yükleyen bir uygulama için, API 'yi kullanarak erişim düzeyi özelliklerini kontrol edebilirsiniz <xref:System.Xaml.Permissions.XamlAccessLevel> . Ayrıca, erteleme mekanizmaları (WPF şablon sistemi gibi), herhangi bir erişim düzeyi izni yayabilir ve bunları nihai çalışma süresi değerlendirmelerine karşı koruyabilmelidir; Bu, bilgileri geçirerek dahili olarak işlenir <xref:System.Xaml.Permissions.XamlAccessLevel> .

### <a name="wpf-implementation"></a>WPF uygulama

WPF XAML, kısmi güven altında BAML 'nin yüklendiği durumlarda kısmi güven erişim modeli kullanır, <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> Bu da BAML kaynağı olan derleme için erişim kısıtlıdır. Deferral için WPF, <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> erişim düzeyi bilgilerini geçirmek için bir mekanizma kullanır.

WPF XAML terminolojisinde, *dahili bir tür* , başvuran xaml de içeren aynı derleme tarafından tanımlanan bir türdür. Böyle bir tür, bir eşlemenin derleme = bölümünü (örneğin,) kasıtlı olarak atbir XAML ad alanı aracılığıyla eşlenebilir `xmlns:local="clr-namespace:WPFApplication1"` . BAML bir iç türe başvuruyorsa ve bu türün `internal` erişim düzeyi varsa, bu `GeneratedInternalTypeHelper` derleme için bir sınıf oluşturur. Kaçınmak isterseniz `GeneratedInternalTypeHelper` , erişim düzeyini kullanmanız ya da `public` ilgili sınıfı ayrı bir derlemede çarpanlara katmalıdır ve bu derlemeye bağımlı hale gelmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri](clr-attributes-with-custom-types-and-libraries.md)
- [XAML Hizmetleri](../../../api/index.md)
