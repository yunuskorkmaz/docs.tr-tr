---
title: Yöntemler
description: Bir F# yöntemin, nesnelerin ve türlerin işlevlerini ve davranışlarını göstermek ve uygulamak için kullanılan bir türle ilişkili bir işlev olduğunu öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976644"
---
# <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir türle ilişkili bir işlevdir. Nesne odaklı programlamada Yöntemler, nesnelerin ve türlerin işlevlerini ve davranışını göstermek ve uygulamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, yöntem bildirimlerinin ve tanımlarının çeşitli biçimlerini görebilirsiniz. Daha uzun Yöntem gövdelerinde, bir satır sonu eşittir işareti (=) ve tüm Yöntem gövdesi girintilenir.

Öznitelikler, herhangi bir yöntem bildirimine uygulanabilir. Bir yöntem tanımı için sözdiziminin önüne ve genellikle ayrı bir satırda listelenir. Daha fazla bilgi için bkz. [öznitelikler](../attributes.md).

Yöntemler `inline`olarak işaretlenebilir. `inline`hakkında bilgi için bkz. [Inline Functions](../functions/inline-functions.md).

Satır içi olmayan yöntemler, türü içinde yinelemeli olarak kullanılabilir; `rec` anahtar sözcüğünü açıkça kullanmaya gerek yoktur.

## <a name="instance-methods"></a>Örnek yöntemleri

Örnek yöntemleri, bir nokta (.) ve Yöntem adı ve parametreleri tarafından izlenen `member` anahtar sözcüğü ve bir *kendinden tanımlayıcı*ile tanımlanır. `let` bağlamalarda olduğu gibi, *parametre listesi* bir kalıp olabilir. Genellikle, yöntem parametrelerini parantez içinde, yöntemlerin diğer .NET Framework dillerde F# oluşturulduklarında görünme yöntemi olan bir demet formunda çevreleolursunuz. Ancak, curried formu (boşluklarla ayrılmış parametreler) de ortaktır ve diğer desenler de desteklenir.

Aşağıdaki örnek Özet olmayan bir örnek yönteminin tanımını ve kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Örnek yöntemleri içinde, Let bağlamaları kullanılarak tanımlanan alanlara erişmek için kendi kendine tanımlayıcıyı kullanmayın. Diğer üyelere ve özelliklere erişirken kendi kendine tanımlayıcıyı kullanın.

## <a name="static-methods"></a>Statik yöntemler

Anahtar sözcüğü `static`, bir yöntemin bir örnek olmadan çağrılabilecek olduğunu ve bir nesne örneğiyle ilişkilendirilmediği belirtmek için kullanılır. Aksi halde Yöntemler örnek yöntemlerdir.

Sonraki bölümde yer alan örnek, `let` anahtar sözcüğü, `member` anahtar sözcüğüyle belirtilen özellik üyeleri ve `static` anahtar sözcüğüyle belirtilen statik bir yöntem ile belirtilen alanları gösterir.

Aşağıdaki örnek, statik yöntemlerin tanımını ve kullanımını gösterir. Bu yöntem tanımlarının önceki bölümde `SomeType` sınıfında olduğunu varsayalım.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemler

Anahtar sözcüğü `abstract` bir yöntemin sanal bir dağıtım yuvasına sahip olduğunu ve sınıfta bir tanımı olabileceğini gösterir. *Sanal dağıtım yuvası* , bir nesne odaklı türdeki sanal işlev çağrılarını aramak için çalışma zamanında kullanılan, dahili olarak tutulan işlevlerin bir girişi olan bir giriştir. Sanal dağıtım mekanizması, nesne odaklı bir Programlamanın önemli bir özelliği olan çok *biçimlilik*uygulayan bir mekanizmadır. Tanımı olmayan en az bir soyut metoda sahip bir sınıf *soyut bir sınıftır*ve bu sınıfın hiçbir örneği oluşturulamadığını gösterir. Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut sınıflar](../abstract-classes.md).

Soyut yöntem bildirimleri bir yöntem gövdesi içermez. Bunun yerine, yöntemin adı iki nokta üst üste gelir (:) ve yöntemi için bir tür imzası. Bir yöntemin tür imzası, fare işaretçisini parametre adları hariç Visual Studio Code düzenleyicisinde bir yöntem adı üzerinde duraklatdığınızda IntelliSense tarafından gösterilenle aynı olur. Etkileşimli olarak çalışırken tür imzaları, fsi. exe yorumlayıcı tarafından da görüntülenir. Bir yöntemin tür imzası, parametre türleri ve ardından dönüş türü, uygun ayırıcı sembolleri ile eklenerek oluşturulur. Curried parametreleri `->` ile ayrılır ve demet parametreleri `*`ile ayrılır. Dönüş değeri her zaman bağımsız değişkenlerden `->` simgesiyle ayrılır. Parantezler, bir işlev türü parametre olduğunda ya da bir kayıt düzeninin iki parametre yerine tek bir parametre olarak ele alındığı zaman göstermek için, karmaşık parametreleri gruplandırmak için kullanılabilir.

Ayrıca, tanımı sınıfa ekleyerek ve bu konudaki Sözdizimi bloğunda gösterildiği gibi `default` anahtar sözcüğünü kullanarak soyut yöntemlere varsayılan tanımlar verebilirsiniz. Aynı sınıfta bir tanımı olan soyut bir yöntem, diğer .NET Framework dillerdeki sanal bir yönteme eşdeğerdir. Bir tanım olup olmadığı, `abstract` anahtar sözcüğü, sınıfının sanal işlev tablosunda yeni bir dağıtım yuvası oluşturur.

Bir temel sınıfın soyut yöntemlerini uygulayıp uygulamamasından bağımsız olarak, türetilmiş sınıflar soyut yöntemler için uygulamalar sağlayabilir. Türetilmiş bir sınıfta soyut bir yöntem uygulamak için, türetilmiş sınıfta aynı ada ve imzaya sahip olan ve `override` veya `default` anahtar sözcüğünü kullan dışında bir yöntem tanımlayın ve Yöntem gövdesini sağlayın. `override` ve `default` anahtar sözcükleri tam olarak aynı şeyi ifade ederler. Yeni yöntem bir temel sınıf uygulamasını geçersiz kılıyorsa `override` kullanın; özgün soyut bildirimle aynı sınıfta bir uygulama oluşturduğunuzda `default` kullanın. Temel sınıfta soyut olarak tanımlanan yöntemi uygulayan yöntemde `abstract` anahtar sözcüğünü kullanmayın.

Aşağıdaki örnek, bir .NET Framework sanal yönteminin eşdeğeri olan varsayılan bir uygulamaya sahip `Rotate` soyut bir yöntemi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılan türetilmiş bir sınıfı gösterir. Bu durumda, geçersiz kılma yöntemi, yöntemin hiçbir şey yapabilmesi için davranışı değiştirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler

Aşırı yüklenmiş yöntemler, belirli bir tür içinde özdeş adlara sahip ancak farklı bağımsız değişkenleri olan yöntemlerdir. F#' Da, isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır. Ancak, bağımsız değişkenlerin bir curried form değil, tanımlama grubu biçiminde olması şartıyla, dilde aşırı yüklenmiş yöntemlere izin verilir.

## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler

4,1 ile F# başlayarak, metotlarda varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenlere de sahip olabilirsiniz.  Bu, C# kodla birlikte çalışabilirliği kolaylaştırmaya yardımcı olur.  Aşağıdaki örnek söz dizimini göstermektedir:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

`DefaultParameterValue` için geçirilen değerin giriş türüyle eşleşmesi gerektiğini unutmayın.  Yukarıdaki örnekte, bir `int`.  Tamsayı olmayan bir değeri `DefaultParameterValue` 'e geçirmeye çalışmak, derleme hatasına neden olur.

## <a name="example-properties-and-methods"></a>Örnek: Özellikler ve Yöntemler

Aşağıdaki örnek, alan, özel işlevler, Özellikler ve statik bir yöntem örnekleri içeren bir tür içerir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
