---
title: .NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071859"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>.NET XAML Hizmetleri ile kullanılmak üzere özel türleri tanımlayın

İş nesneleri olan veya belirli çerçevelere bağımlı olmayan türler olan özel türleri tanımladığınızda, XAML için izleyebileceğiniz belirli en iyi uygulamalar vardır. Bu uygulamaları izlerseniz, .NET XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları türün XAML özelliklerini keşfedebilir ve XAML türü sistemini kullanarak bir XAML düğüm akışında uygun gösterim sağlayabilir. Bu konu, tür tanımları, üye tanımları ve CLR türleri veya üyelerin atflanması için en iyi uygulamaları açıklar.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML için Yapıcı Desenler ve Tip Tanımları

XAML'de bir nesne öğesi olarak anlık olarak atılabilmesi için, özel bir sınıfın aşağıdaki gereksinimleri karşılaması gerekir:

- Özel sınıf ortak olmalı ve parametresiz bir ortak oluşturucu ortaya çıkarmalıdır. (Yapılarla ilgili notlar için aşağıdaki bölüme bakın.)

- Özel sınıf iç içe sınıf olmamalıdır. Tam ad yolundaki ekstra "nokta" sınıf ad alanı bölümünü belirsiz hale getirir ve ekli özellikler gibi diğer XAML özelliklerini bozar.
Bir nesne nesne öğesi olarak anında oluşturulabilirse, oluşturulan nesne, nesneyi alttaki türü olarak alan tüm özelliklerin özellik öğesi formunu doldurabilir.

Bir değer dönüştürücü etkinleştiriyorsanız, bu ölçütleri karşılamayan türler için nesne değerleri sağlamaya devam edebilirsiniz. Daha fazla bilgi için [XAML için Tür Dönüştürücüler ve Biçimlendirme Uzantıları'na](type-converters-and-markup-extensions.md)bakın.

### <a name="structures"></a>Yapılar

Yapılar her zaman ClR tanımı ile XAML inşa edilebilir. Bunun nedeni, CLR derleyicinin örtülü olarak bir yapı için parametresiz bir oluşturucu oluşturmasıdır. Bu oluşturucu, tüm özellik değerlerini varsayılanlarına göre başlar.

Bazı durumlarda, bir yapı için varsayılan yapı davranışı istenmez. Bunun nedeni, yapının değerleri doldurmak ve kavramsal olarak birleşim olarak işlev görmek için tasarlanmış olması olabilir. Bir birlik olarak, içerdiği değerler birbirini dışlayan yorumlara sahip olabilir ve bu nedenle, özelliklerinin hiçbiri ayarlanabilir değildir. WPF sözlüğünde böyle bir yapıya <xref:System.Windows.GridLength>örnek olarak . Bu tür yapılar, yapıların farklı yorumlarını veya modlarını oluşturan dize kuralları nı kullanarak, değerlerin öznitelik formunda ifade edilebilmeleri için bir tür dönüştürücü uygulamalıdır. Yapı da parametresiz olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer davranış ortaya çıkarmalıdır.

### <a name="interfaces"></a>Arabirimler

Arabirimler, altta yatan üye türleri olarak kullanılabilir. XAML türü sistemi devredilebilir listeyi denetler ve değer olarak sağlanan nesnenin arabirime atanmasını bekler. İlgili bir devratlanabilir tür XAML yapı gereksinimlerini desteklediği sürece arabirimin XAML türü olarak nasıl sunulması gerektiği ne anlama geliyor?

### <a name="factory-methods"></a>Fabrika Yöntemleri

Fabrika yöntemleri bir XAML 2009 özelliğidir. Nesnelerin parametresiz oluşturucuları olması gerektiği XAML ilkesini değiştirirler. Fabrika yöntemleri bu makalede belgelenmemiştir. Bkz. [x:FactoryMethod Direktifi](xfactorymethod-directive.md).

## <a name="enumerations"></a>Numaralandırmalar

Tümumerations XAML yerel türü dönüştürme davranışı vardır. XAML'de belirtilen numaralandırma sabit adları, temel numaralandırma türüne göre çözülür ve numaralandırma değerini bir XAML nesne yazarına döndürür.

XAML <xref:System.FlagsAttribute> uygulanan sayısallaştırmalar için bayrak stili kullanımını destekler. Daha fazla bilgi için Bkz. [Ayrıntılı Olarak XAML Sözdizimi.](../../framework/wpf/advanced/xaml-syntax-in-detail.md) ([XAML Sözdizimi Ayrıntılı](../../framework/wpf/advanced/xaml-syntax-in-detail.md) olarak WPF hedef kitlesi için yazılmıştır, ancak bu konudaki bilgilerin çoğu belirli bir uygulama çerçevesine özgü olmayan XAML için önemlidir.)

## <a name="member-definitions"></a>Üye Tanımları

Türleri XAML kullanımı için üye tanımlayabilir. Bu tür XAML-kullanılabilir olmasa bile XAML kullanılabilir üyeleri tanımlamak için türleri mümkündür. Bu CLR kalıtım nedeniyle mümkündür. Üyeyi devralan bazı tür, XAML kullanımını bir tür olarak desteklediği ve üyenin xaml kullanımını temel türü için desteklediği veya yerel bir XAML sözdizimi bulunduğu sürece, bu üye XAML tarafından kullanılabilir.

### <a name="properties"></a>Özellikler

`get` Özellikleri, tipik CLR ve erişimci desenleri `set` ve dile uygun anahtar kelime kullanarak ortak bir CLR özelliği olarak tanımlarsanız, XAML türü sistemi, özellikleri için <xref:System.Xaml.XamlMember> sağlanan uygun bilgilere sahip bir üye olarak özelliği <xref:System.Xaml.XamlMember.IsReadPublic%2A> bildirebilir. <xref:System.Xaml.XamlMember.IsWritePublic%2A>

Belirli özellikler uygulayarak <xref:System.ComponentModel.TypeConverterAttribute>bir metin sözdizimini etkinleştirebilir. Daha fazla bilgi için [XAML için Tür Dönüştürücüler ve Biçimlendirme Uzantıları'na](type-converters-and-markup-extensions.md)bakın.

Metin sözdizimi veya yerel XAML dönüştürme yokluğunda ve biçimlendirme uzantısı kullanımı gibi daha fazla yönlendirme yokluğunda,<xref:System.Xaml.XamlMember.TargetType%2A> bir özellik türü (XAML türü sisteminde) bir xaml nesne spesiiiyacıiçin bir CLR türü olarak ele alarak bir örnek döndürmek gerekir.

XAML 2009 kullanıyorsanız, [x:Reference Markup Extension](xreference-markup-extension.md) önceki hususlar karşılanmazsa değerleri sağlamak için kullanılabilir; ancak, bu bir tür tanımı sorunu daha bir kullanım sorunu daha fazladır.

### <a name="events"></a>Olaylar

Olayları herkese açık bir CLR olayı olarak tanımlarsanız, XAML türü <xref:System.Xaml.XamlMember.IsEvent%2A> sistemi `true`olayı üye olarak bildirebilir. Olay işleyicilerinin kablolama .NET XAML Hizmetleri yetenekleri kapsamında değildir; kablolama belirli çerçevelere ve uygulamalara bırakılır.

### <a name="methods"></a>Yöntemler

Yöntemler için satır kodu varsayılan bir XAML özelliği değildir. Çoğu durumda, xaml doğrudan yöntem üyeleri başvuru yok ve XAML yöntemlerin rolü sadece belirli XAML desenleri için destek sağlamaktır. [x:FactoryMethod Direktifi](xfactorymethod-directive.md) bir istisnadır.

### <a name="fields"></a>Alanlar

CLR tasarım yönergeleri statik olmayan alanların cesaretini kırar. Statik alanlar için statik alan değerlerine yalnızca [x:Static Markup Extension](xstatic-markup-extension.md)üzerinden erişebilirsiniz; bu durumda [x:Static](xstatic-markup-extension.md) kullanımları için bir alanı ortaya çıkarmak için CLR tanımında özel bir şey yapmıyorsunuz.

## <a name="attachable-members"></a>Eklenebilir Üyeler

Takılabilir üyeler tanımlayıcı bir tür üzerinde bir erişimci yöntemi deseni aracılığıyla XAML maruz kalırlar. Tanımlayıcı türün kendisi bir nesne olarak XAML kullanılabilir olması gerekmez. Aslında, ortak bir desen olan rolü takılabilir üye sahibi ve ilgili davranışları uygulamak için bir hizmet sınıfı bildirmek, ancak bir UI gösterimi gibi başka bir işlev hizmet etmektir. Aşağıdaki bölümlerde yer tutucu *PropertyName,* eklenebilir üyenizin adını temsil eder. Bu ad [XamlName Dilbilgisi](xamlname-grammar.md)geçerli olmalıdır.

Bu desenler ve bir türün diğer yöntemleri arasındaki ad çakışmalarına karşı dikkatli olun. Desenlerden biriyle eşleşen bir üye varsa, niyetiniz bu olmasa bile xaml işlemci tarafından takılabilir bir üye kullanım yolu olarak yorumlanabilir.

#### <a name="the-getpropertyname-accessor"></a>GetPropertyName Erişimcisi

Erişime erişimin `GetPropertyName` imzası aşağıdaki olmalıdır:

`public static object GetPropertyName(object target)`

- Nesne, `target` uygulamanızda daha özel bir tür olarak belirtilebilir. Bunu, eklenebilir üyenizin kullanımını kapsamak için kullanabilirsiniz; amaçlanan kapsam dışındaki kullanımlar, xaml ayrıştırım hatasıyla su yüzüne çıkan geçersiz döküm özel durumları oluşturur. Parametre adı `target` bir gereklilik değildir, `target` ancak çoğu uygulamada kural olarak adlandırılır.

- İade değeri, uygulamanızda daha özel bir tür olarak belirtilebilir.

Eklenebilir <xref:System.ComponentModel.TypeConverter> üyenin öznitelik kullanımı için etkin leştirilmiş bir <xref:System.ComponentModel.TypeConverterAttribute> metin `GetPropertyName` sözdizimini desteklemek için, erişime başvurana uygulayın. `get` Yerine `set` uygulamak sezgisel olmayabilir; ancak, bu kural, tasarımcı senaryolarında yararlı olan, serileştirilebilir salt okunur eklenebilir üyeler kavramını destekleyebilir.

#### <a name="the-setpropertyname-accessor"></a>SetPropertyName Erişimcisi

Erişime erişimin `SetPropertyName` imzası aşağıdaki olmalıdır:

`public static void SetPropertyName(object target, object value)`

- Nesne, `target` önceki bölümde açıklandığı gibi aynı mantık ve sonuçlarla, uygulamanızda daha özel bir tür olarak belirtilebilir.

- Nesne, `value` uygulamanızda daha özel bir tür olarak belirtilebilir.

Bu yöntemin değerinin genellikle öznitelik formunda olan XAML kullanımından gelen giriş olduğunu unutmayın. Öznitelik formundan bir metin sözdizimi için değer dönüştürücü desteği `GetPropertyName`olmalıdır ve siz de s erişimedayalıda öznitelik verirsiniz.

### <a name="attachable-member-stores"></a>Takılabilir Üye Mağazaları

Erişimci yöntemler genellikle eklenebilir üye değerleri nesne grafiğine yerleştirmek veya nesneleri nesne grafiğinden alıp düzgün bir şekilde seri hale getirmek için yeterli değildir. Bu işlevselliği sağlamak `target` için, önceki erişimci imzadaki nesnelerin değerleri depolama yeteneğine sahip olması gerekir. Depolama mekanizması, üyenin üye listesinde olmayan hedeflere eklenebilir olduğu ilkesiyle tutarlı olmalıdır. .NET XAML Hizmetleri, API'ler <xref:System.Xaml.IAttachedPropertyStore> aracılığıyla eklenebilir <xref:System.Xaml.AttachablePropertyServices>üye mağazalar için bir uygulama tekniği sağlar ve. <xref:System.Xaml.IAttachedPropertyStore>xaml yazarlar tarafından mağaza uygulamasını keşfetmek için kullanılır ve erişenlerin türü `target` üzerinde uygulanmalıdır. Statik <xref:System.Xaml.AttachablePropertyServices> API'ler, eriştirenlerin gövdesi içinde kullanılır ve takılabilir <xref:System.Xaml.AttachableMemberIdentifier>üyeye .

## <a name="xaml-related-clr-attributes"></a>XAML ile ilgili CLR Öznitelikleri

XAML türü sistem bilgilerini .NET XAML Hizmetleri'ne bildirmek için türlerinizi, üyelerinizi ve derlemelerinizi doğru bir şekilde atfetmek önemlidir. Aşağıdaki durumlardan biri geçerliyse XAML türü sistem bilgilerinin raporlanması önemlidir:

- Doğrudan .NET XAML Hizmetleri XAML okuyucularına ve XAML yazarlarını temel alan XAML sistemlerinde kullanım için türünüzü niyetindesiniz.
- Bu XAML okuyucuları ve XAML yazarlarını temel alan XAML kullanan bir çerçeve tanımlar veya kullanırsınız.

Özel türlerinizin XAML desteğiyle alakalı her XAML ile ilgili özniteliğin listesi [için, Özel Türler ve Kitaplıklar için XAML ile ilgili CLR Öznitelikleri'ne](clr-attributes-with-custom-types-and-libraries.md)bakın.

## <a name="usage"></a>Kullanım

Özel türlerin kullanımı, biçimlendirme yazarının özel türü içeren derleme ve CLR ad alanı için bir önek eşlemesini gerektirir. Bu yordam bu konuda belgelenmemiştir.

## <a name="access-level"></a>Erişim Düzeyi

XAML, erişim düzeyine sahip türleri yüklemek ve `internal` anlık olarak yüklemek için bir araç sağlar. Bu özellik, kullanıcı kodunun kendi türlerini tanımlayabilmesi ve ardından aynı kullanıcı kodu kapsamının bir parçası olan biçimlendirmeden bu sınıfları anında atabilmesi için sağlanır.

WPF'den bir örnek, kullanıcı kodu, kullanıcı arabirimi davranışını yeniden düzenlemenin bir yolu olarak tasarlanmış bir kullanıcı kodu tanımladığı, <xref:System.Windows.Controls.UserControl> ancak destek `public` çisi sini erişim düzeyiyle beyan ederek ima edilebilen olası uzantı mekanizmasının bir parçası olarak tanımlanmamasıdır. Destek <xref:System.Windows.Controls.UserControl> kodu XAML türü olarak başvurulmulan aynı derleme içine derlenirse, böyle bir erişim ile `internal` bildirilebilir.

XAML'yi tam güven altında yükleyen ve <xref:System.Xaml.XamlObjectWriter> `internal` kullanan bir uygulama için, erişim düzeyine sahip yükleme sınıfları her zaman etkinleştirilir.

XAML'yi kısmi güven altında yükleyen bir uygulama için, <xref:System.Xaml.Permissions.XamlAccessLevel> API'yi kullanarak erişim düzeyi özelliklerini denetleyebilirsiniz. Ayrıca, erteleme mekanizmaları (WPF şablon sistemi gibi) herhangi bir erişim düzeyi izinleri yaymak ve nihai çalışma süresi değerlendirmeleri için bunları korumak gerekir; bu <xref:System.Xaml.Permissions.XamlAccessLevel> bilgi geçirerek dahili olarak ele alınır.

### <a name="wpf-implementation"></a>WPF Uygulaması

WPF XAML, BAML kısmi güven altında yüklenirse, erişimin <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> BAML kaynağı olan derlemeyle sınırlı olduğu kısmi güven erişim modeli kullanır. Erteleme için WPF, <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> erişim düzeyi bilgilerini aktarmak için bir mekanizma olarak kullanır.

WPF XAML terminolojisinde, dahili bir *tür,* xaml referansını da içeren aynı derleme tarafından tanımlanan bir türdür. Böyle bir tür, örneğin, bir eşlemenin derleme= bölümünü kasten atlayan bir XAML `xmlns:local="clr-namespace:WPFApplication1"`ad alanı üzerinden eşlenebilir. BAML bir iç türe başvuruyorsa ve bu tür erişim düzeyine sahipse, `internal` bu derleme için bir `GeneratedInternalTypeHelper` sınıf oluşturur. Kaçınmak `GeneratedInternalTypeHelper`istiyorsanız, erişim düzeyini kullanmanız `public` veya ilgili sınıfı ayrı bir derlemeye dahil etmeniz ve bu derlemeyi bağımlı hale getirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri](clr-attributes-with-custom-types-and-libraries.md)
- [XAML Hizmetleri](../../../api/index.md)
