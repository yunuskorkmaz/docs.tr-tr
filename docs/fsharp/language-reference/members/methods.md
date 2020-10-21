---
title: Yöntemler
description: 'Bir F # yönteminin, nesnelerin ve türlerin işlevlerini ve davranışlarını göstermek ve uygulamak için kullanılan bir türle ilişkili bir işlev olduğunu öğrenin.'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224101"
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

Yöntemler işaretlenebilir `inline` . Hakkında bilgi için `inline` bkz. [satır içi işlevler](../functions/inline-functions.md).

Satır içi olmayan yöntemler, türü içinde yinelemeli olarak kullanılabilir; anahtar sözcüğünü açıkça kullanmaya gerek yoktur `rec` .

## <a name="instance-methods"></a>Örnek yöntemleri

Örnek yöntemleri, `member` anahtar sözcüğü ve bir *kendinden tanımlayıcı*ile, ardından bir nokta (.) ve Yöntem adı ve parametreleri ile birlikte bildirilmiştir. `let`Bağlamalarda olduğu gibi, *parametre listesi* bir kalıp olabilir. Genellikle, yöntem parametrelerini parantez içinde, diğer .NET Framework dillerde oluşturulduklarında F # içinde görünme yöntemi olan bir tanımlama grubu formunda çevreedersiniz. Ancak, curried formu (boşluklarla ayrılmış parametreler) de ortaktır ve diğer desenler de desteklenir.

Aşağıdaki örnek Özet olmayan bir örnek yönteminin tanımını ve kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Örnek yöntemleri içinde, Let bağlamaları kullanılarak tanımlanan alanlara erişmek için kendi kendine tanımlayıcıyı kullanmayın. Diğer üyelere ve özelliklere erişirken kendi kendine tanımlayıcıyı kullanın.

## <a name="static-methods"></a>Statik yöntemler

Anahtar sözcüğü, `static` bir yöntemin bir örnek olmadan çağrılabilecek olduğunu ve bir nesne örneğiyle ilişkilendirilmediği belirtmek için kullanılır. Aksi halde Yöntemler örnek yöntemlerdir.

Sonraki bölümde yer alan örnek, anahtar sözcükle belirtilen `let` özellik üyeleri ve anahtar sözcüğüyle belirtilen `member` statik bir yöntem ile tanımlanan alanları gösterir `static` .

Aşağıdaki örnek, statik yöntemlerin tanımını ve kullanımını gösterir. Bu yöntem tanımlarının `SomeType` önceki bölümdeki sınıfında olduğunu varsayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemler

Anahtar sözcüğü, `abstract` bir yöntemin sanal bir dağıtım yuvasına sahip olduğunu ve sınıfta tanımına sahip olabileceğini gösterir. *Sanal dağıtım yuvası* , bir nesne odaklı türdeki sanal işlev çağrılarını aramak için çalışma zamanında kullanılan, dahili olarak tutulan işlevlerin bir girişi olan bir giriştir. Sanal dağıtım mekanizması, nesne odaklı bir Programlamanın önemli bir özelliği olan çok *biçimlilik*uygulayan bir mekanizmadır. Tanımı olmayan en az bir soyut metoda sahip bir sınıf *soyut bir sınıftır*ve bu sınıfın hiçbir örneği oluşturulamadığını gösterir. Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut sınıflar](../abstract-classes.md).

Soyut yöntem bildirimleri bir yöntem gövdesi içermez. Bunun yerine, yöntemin adı iki nokta üst üste gelir (:) ve yöntemi için bir tür imzası. Bir yöntemin tür imzası, fare işaretçisini parametre adları hariç Visual Studio Code düzenleyicisinde bir yöntem adı üzerinde duraklatdığınızda IntelliSense tarafından gösterilenle aynı olur. Tür imzaları Ayrıca, etkileşimli olarak çalışırken fsi.exe yorumlayıcı tarafından da görüntülenir. Bir yöntemin tür imzası, parametre türleri ve ardından dönüş türü, uygun ayırıcı sembolleri ile eklenerek oluşturulur. Curried parametreleri ile ayrılır `->` ve demet parametreleri ile ayrılır `*` . Dönüş değeri her zaman bağımsız değişkenlerden bir sembol ile ayrılır `->` . Parantezler, bir işlev türü parametre olduğunda ya da bir kayıt düzeninin iki parametre yerine tek bir parametre olarak ele alındığı zaman göstermek için, karmaşık parametreleri gruplandırmak için kullanılabilir.

Ayrıca `default` , bu konudaki Sözdizimi bloğunda gösterildiği gibi, tanımı sınıfa ekleyerek ve anahtar sözcüğünü kullanarak soyut yöntemlere varsayılan tanımlamalar da verebilirsiniz. Aynı sınıfta bir tanımı olan soyut bir yöntem, diğer .NET Framework dillerdeki sanal bir yönteme eşdeğerdir. Bir tanım olup olmadığı, `abstract` anahtar sözcüğü sınıfı için sanal işlev tablosunda yeni bir dağıtım yuvası oluşturur.

Bir temel sınıfın soyut yöntemlerini uygulayıp uygulamamasından bağımsız olarak, türetilmiş sınıflar soyut yöntemler için uygulamalar sağlayabilir. Türetilmiş bir sınıfta soyut bir yöntem uygulamak için, türetilmiş sınıfta aynı ada ve imzaya sahip bir yöntemi tanımlayın, `override` or `default` anahtar sözcüğünü kullanın ve Yöntem gövdesini sağlayın. Anahtar sözcükler `override` ve `default` tam olarak aynı şey anlamına gelir. `override`Yeni yöntem bir temel sınıf uygulamasını geçersiz kıldığında kullanın; `default` özgün soyut bildirimle aynı sınıfta bir uygulama oluşturduğunuzda kullanın. `abstract`Temel sınıfta soyut olarak tanımlanan yöntemi uygulayan yöntemde anahtar sözcüğünü kullanmayın.

Aşağıdaki örnek `Rotate` , bir .NET Framework sanal yönteminin eşdeğeri olan varsayılan bir uygulamaya sahip olan soyut bir yöntemi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılan türetilmiş bir sınıfı gösterir. Bu durumda, geçersiz kılma yöntemi, yöntemin hiçbir şey yapabilmesi için davranışı değiştirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Aşırı Yüklenmiş Yöntemler

Aşırı yüklenmiş yöntemler, belirli bir tür içinde özdeş adlara sahip ancak farklı bağımsız değişkenleri olan yöntemlerdir. F # ' da, isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır. Ancak, bağımsız değişkenlerin bir curried form değil, tanımlama grubu biçiminde olması şartıyla, dilde aşırı yüklenmiş yöntemlere izin verilir.

## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler

F # 4,1 ile başlayarak, metotlarda varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenlere de sahip olabilirsiniz.  Bu, C# kodu ile birlikte çalışabilirliği kolaylaştırmaya yardımcı olur.  Aşağıdaki örnek söz dizimini göstermektedir:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

İçin geçirilen değerin `DefaultParameterValue` giriş türüyle eşleşmesi gerektiğini unutmayın.  Yukarıdaki örnekte, bir `int` .  Tamsayı olmayan bir değeri ' a geçirmeye çalışmak `DefaultParameterValue` , derleme hatasına neden olur.

## <a name="example-properties-and-methods"></a>Örnek: Özellikler ve Yöntemler

Aşağıdaki örnek, alan, özel işlevler, Özellikler ve statik bir yöntem örnekleri içeren bir tür içerir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
