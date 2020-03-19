---
title: Yöntemler
description: F# yönteminin, nesnelerin ve türlerin işlevselliğini ve davranışını ortaya çıkarmak ve uygulamak için kullanılan bir türle ilişkili bir işlev olduğunu öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400213"
---
# <a name="methods"></a>Yöntemler

*Yöntem,* bir türle ilişkili bir işlevdir. Nesne yönelimli programlamada, nesnelerin ve türlerin işlevselliğini ve davranışını ortaya çıkarmak ve uygulamak için yöntemler kullanılır.

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

Önceki sözdiziminde, yöntem bildirimlerinin ve tanımlarının çeşitli biçimlerini görebilirsiniz. Uzun yöntem gövdelerinde, bir satır sonu eşit işareti (=) izler ve tüm yöntem gövdesi girintilir.

Öznitelikler herhangi bir yöntem bildirimine uygulanabilir. Yöntem tanımı için sözdiziminden önce gelir ler ve genellikle ayrı bir satırda listelenirler. Daha fazla bilgi için [Özniteliklere](../attributes.md)bakın.

Yöntemler işaretlenebilir. `inline` Hakkında bilgi `inline`için Bkz. [Satır İçi Fonksiyonlar.](../functions/inline-functions.md)

Satır içi olmayan yöntemler, tür içinde özyinelemeli olarak kullanılabilir; anahtar kelimeyi `rec` açıkça kullanmaya gerek yoktur.

## <a name="instance-methods"></a>Örnek Yöntemleri

Örnek yöntemleri `member` anahtar kelime ve *kendi kendini tanımlayıcı*ile bildirilir, ardından bir dönem (.) ve yöntem adı ve parametreleri. Bağlamalar için `let` olduğu gibi, *parametre listesi* bir desen olabilir. Genellikle, yöntem parametrelerini parantez içinde bir tuple formuna alarsınız, bu da yöntemlerdiğer .NET Framework dillerinde oluşturulduklarında F#'da nasıl görünür? Ancak, körili form (boşluklara göre ayrılmış parametreler) de yaygındır ve diğer desenler de desteklenir.

Aşağıdaki örnek, soyut olmayan bir örnek yönteminin tanımını ve kullanımını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Örnek yöntemleri içinde, let bağlamaları kullanılarak tanımlanan alanlara erişmek için öz tanımlayıcıyı kullanmayın. Diğer üyelere ve özelliklere erişirken kendi kendini tanımlayıcıyı kullanın.

## <a name="static-methods"></a>Statik Yöntemler

Anahtar kelime, `static` bir yöntemin bir örnek olmadan çağrılabileceğini ve bir nesne örneğiyle ilişkilendirilmediğini belirtmek için kullanılır. Aksi takdirde, yöntemler örnek yöntemleridir.

Sonraki bölümde ki `let` örnekte, anahtar kelimeyle bildirilen alanlar, `member` anahtar kelimeyle bildirilen özellik `static` üyeleri ve anahtar kelimeyle birlikte bildirilen statik bir yöntem gösterilmektedir.

Aşağıdaki örnekte statik yöntemlerin tanımı ve kullanımı gösterilmektedir. Bu yöntem tanımlarının önceki `SomeType` bölümde sınıfta olduğunu varsayalım.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve Sanal Yöntemler

Anahtar kelime, `abstract` bir yöntemin sanal bir gönderme yuvasına sahip olduğunu ve sınıfta bir tanımı nın olmayabilir olduğunu belirtir. *Sanal gönderme yuvası,* nesne yönelimli bir türde sanal işlev çağrılarını aramak için çalışma zamanında kullanılan dahili olarak korunan işlevler tablosundaki bir giriştir. Sanal gönderme mekanizması, nesne yönelimli programlamanın önemli bir özelliği olan *çok biçimliliği*uygulayan mekanizmadır. Tanımı olmayan en az bir soyut metod olan bir sınıf soyut bir *sınıftır,* bu da o sınıftan hiçbir örnek oluşturulamayacağı anlamına gelir. Soyut sınıflar hakkında daha fazla bilgi için [bkz.](../abstract-classes.md)

Soyut yöntem bildirimleri bir yöntem gövdesi içermez. Bunun yerine, yöntemin adı bir iki nokta üst üste (:) ve yöntem için bir tür imza. Bir yöntemin tür imzası, parametre adları dışında, Görsel Stüdyo Kodu Düzenleyicisi'ndeki bir yöntem adı üzerinde fare işaretçisini duraklattığınızda IntelliSense tarafından gösterilenle aynıdır. Tür imzaları da etkileşimli çalışırken, tercüman, fsi.exe tarafından görüntülenir. Bir yöntemin tür imzası, parametrelerin türlerinin listelenmesiyle oluşur ve ardından dönüş türü, uygun ayırıcı sembollerle oluşturulur. Curried parametreleri `->` ile ayrılır ve tuple parametreleri ile `*`ayrılır . İade değeri her zaman bir `->` sembol le bağımsız değişkenlerden ayrılır. Parantez, işlev türünün bir parametre olması gibi karmaşık parametreleri gruplandırmak veya bir tuple'ın iki parametre yerine tek bir parametre olarak ne zaman ele alındığını belirtmek için kullanılabilir.

Ayrıca, bu konuda sözdizimi bloğunda gösterildiği gibi, `default` tanımı sınıfa ekleyerek ve anahtar sözcüğü kullanarak soyut yöntemler varsayılan tanımlar da verebilirsiniz. Aynı sınıfta tanımı olan soyut bir yöntem, diğer .NET Framework dillerinde sanal yönteme eşdeğerdir. Bir tanım var olsun `abstract` veya olmasın, anahtar kelime sınıf için sanal işlev tablosunda yeni bir gönderme yuvası oluşturur.

Bir taban sınıfın soyut yöntemlerini uygulayıp uygulamadığına bakılmaksızın, türemiş sınıflar soyut yöntemlerin uygulamalarını sağlayabilir. Türemiş bir sınıfta soyut bir yöntem uygulamak için, türemiş sınıfta, anahtar `override` sözcüğü kullanmak dışında aynı ada ve imzaya sahip bir yöntem tanımlayın `default` ve yöntem gövdesini sağlayın. Anahtar `override` kelimeler `default` ve tam olarak aynı şey anlamına gelir. Yeni `override` yöntem taban sınıf uygulamasını geçersiz kılıyorsa kullanın; özgün `default` özet bildirimle aynı sınıfta bir uygulama oluşturduğunuzda kullanın. Taban sınıfta `abstract` soyut olarak bildirilen yöntemi uygulayan yöntemde anahtar sözcüğü kullanmayın.

Aşağıdaki örnekte, bir `Rotate` .NET Framework sanal yöntemieşdeğeri olan varsayılan bir uygulama olan soyut bir yöntem gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Aşağıdaki örnekte, taban sınıf yöntemini geçersiz kılan türetilmiş bir sınıf gösterilmiştir. Bu durumda, geçersiz kılma, yöntemin hiçbir şey yapamaması için davranışı değiştirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Aşırı Yüklenmiş Yöntemler

Aşırı yüklenen yöntemler, belirli bir türde aynı adlara sahip ancak farklı bağımsız değişkenleri olan yöntemlerdir. F#'da, genellikle aşırı yüklü yöntemler yerine isteğe bağlı bağımsız değişkenler kullanılır. Ancak, aşırı yüklenen yöntemler, bağımsız değişkenler tuple şeklinde değil, curried şeklinde olması koşuluyla, dilde izin verilir.

## <a name="optional-arguments"></a>İsteğe Bağlı Bağımsız Değişkenler

F# 4.1 ile başlayarak, yöntemlerde varsayılan parametre değerine sahip isteğe bağlı bağımsız değişkenler de olabilir.  Bu, C# kodu ile birlikte çalışma işlemini kolaylaştırmak içindir.  Aşağıdaki örnek sözdizimini gösterir:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Için `DefaultParameterValue` geçirilen değerin giriş türüyle eşleşmesi gerektiğini unutmayın.  Yukarıdaki örnekte, bir `int`.  Tamsayı olmayan bir değeri derleme `DefaultParameterValue` hatasına neden olur.

## <a name="example-properties-and-methods"></a>Örnek: Özellikler ve Yöntemler

Aşağıdaki örnek, alanlar, özel işlevler, özellikler ve statik bir yöntem örnekleri içeren bir tür içerir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
