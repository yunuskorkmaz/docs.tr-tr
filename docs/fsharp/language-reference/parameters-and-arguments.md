---
title: Parametreler ve Bağımsız Değişkenler
description: Parametreleri tanımlamak ve bağımsız değişkenleri işlevlere, yöntemlere ve özelliklere geçirmek için F# dil desteği hakkında bilgi edinin.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400199"
---
# <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Bu konu, parametreleri tanımlamak ve bağımsız değişkenleri işlevlere, yöntemlere ve özelliklere geçirmek için dil desteğini açıklar. Başvuruya göre nasıl geçirilebileceği ve değişken sayıda bağımsız değişken alabilecek yöntemlerin nasıl tanımlanabileceği ve kullanılacağı hakkında bilgiler içerir.

## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Terim *parametresi,* sağlanmalıdır beklenen değerlerin adlarını açıklamak için kullanılır. Terim *bağımsız değişkeni,* her parametre için sağlanan değerler için kullanılır.

Parametreler tuple veya curried şeklinde veya ikisinin bir kombinasyonunda belirtilebilir. Açık bir parametre adı kullanarak bağımsız değişkenleri geçirebilirsiniz. Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan değer verilebilir.

## <a name="parameter-patterns"></a>Parametre Desenleri

Fonksiyonlara ve yöntemlere verilen parametreler, genel olarak boşluklara göre ayrılmış desenlerdir. Bu, ilke olarak, [Eşler İfadeleri'nde](match-expressions.md) açıklanan desenlerden herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceğini zedebilirsiniz.

Yöntemler genellikle geçen bağımsız değişkenlerin tuple biçimini kullanır. Bu, diğer .NET dillerinin perspektifinden daha net bir sonuç elde eder, çünkü tuple formu .NET yöntemlerinde bağımsız değişkenlerin geçirildiği şekilde eşleşir.

Körili form en sık bağlamalar kullanılarak `let` oluşturulan işlevlerle kullanılır.

Aşağıdaki pseudocode tuple ve curried bağımsız değişkenörnekleri gösterir.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Bazı bağımsız değişkenler tuples ve bazı değildir kombine formlar mümkündür.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişler le eşleşmiyorsa, çalışma zamanında eksik bir eşleşme olabilir. Bir `MatchFailureException` bağımsız değişkenin değeri parametre listesinde belirtilen desenlerle eşleşmediğinde özel durum oluşturulur. Derleyici, parametre deseni eksik eşleşmeler için izin verdiğinde bir uyarı verir. Parametre listeleri için en az bir desen daha yararlıdır ve bu joker karakter desenidir. Sağlanan bağımsız değişkenleri yok saymak istediğinizde, bir parametre listesinde joker karakter deseni kullanırsınız. Aşağıdaki kod, bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Joker karakter deseni, aşağıdaki kodda olduğu gibi normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleriyle ilgilenmediğiniz bir programa ana giriş noktası gibi bağımsız değişkenlere gerek kalmadığında yararlı olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Bazen bağımsız değişkenlerde kullanılan diğer `as` desenler desen ve ayrımcı sendikalar ve etkin desenler ile ilişkili tanımlayıcı desenleri vardır. Tek harfli ayrımlı birleşim modelini aşağıdaki gibi kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Çıktı aşağıdaki gibidir:

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Etkin desenler, örneğin aşağıdaki örnekte olduğu gibi, bir bağımsız değişkeni istenilen biçime dönüştürürken parametreler olarak yararlı olabilir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

`as` Aşağıdaki kod satırında gösterildiği gibi, eşleşen bir değeri yerel bir değer olarak depolamak için deseni kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Bazen kullanılan başka bir desen, işlevin gövdesi olarak, örtük bağımsız değişken üzerinde hemen bir desen eşleşmesi gerçekleştiren bir lambda ifadesi sağlayarak, son bağımsız değişkeni isimsiz bırakan bir işlevdir. Bunun bir örneği aşağıdaki kod satırıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Bu kod, genel bir liste alan `true` ve liste boşsa `false` ve başka türlü döndüren bir işlev tanımlar. Bu tür tekniklerin kullanımı kodun okunmasını zorlaştırabilir.

Bazen, tamamlanmamış eşleşmeler içeren desenler yararlıdır, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, parametre listesinde aşağıdaki gibi bir desen kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Eksik eşleşmeleri olan desenlerin kullanımı en iyi hızlı prototipleme ve diğer geçici kullanımlar için ayrılmıştır. Derleyici bu tür kod için bir uyarı yayımlar. Bu tür desenler tüm olası girdilerin genel durumunu kapsayamaz ve bu nedenle bileşen API'leri için uygun değildir.

## <a name="named-arguments"></a>Adlandırılmış Bağımsız Değişkenler

Yöntemler için bağımsız değişkenler virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad sağlanarak, ardından eşit bir işaret ve geçirilecek değer sağlanarak bir yönteme geçirilebilir. Ad belirtilerek belirtilirse, bildirimde kullanılandan farklı bir sırada görünebilirler.

Adlandırılmış bağımsız değişkenler, kodu yöntem parametrelerinin yeniden sıralanması gibi API'deki belirli değişiklik türlerine daha kolay ve daha uyarlanabilir hale getirebilir.

Adlandırılmış bağımsız değişkenlere yalnızca `let`bağlı işlevler, işlev değerleri veya lambda ifadeleri için değil, yöntemler için izin verilir.

Aşağıdaki kod örneği, adlandırılmış bağımsız değişkenlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Bir sınıf oluşturucuya yapılan bir çağrıda, adlandırılmış bağımsız değişkenlere benzer bir sözdizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz. Aşağıdaki örnekte bu sözdizimi gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Daha fazla bilgi için [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)bakın.

## <a name="optional-parameters"></a>İsteğe Bağlı Parametreler

Parametre adının önünde bir soru işareti kullanarak bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz. İsteğe bağlı parametreler F# seçeneği türü olarak yorumlanır, böylece seçenek türlerinin sorgulanacağı normal `match` şekilde `Some` `None`sorgulayabilirsiniz. İsteğe bağlı parametrelere yalnızca üyelere izin `let` verilir, bağlamalar kullanılarak oluşturulan işlevlerde değil.

Varolan isteğe bağlı değerleri parametre adı `?arg=None` ile `?arg=Some(3)` `?arg=arg`yönteme geçirebilirsiniz, örneğin veya . Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçen bir yöntem yaparken yararlı olabilir.

İsteğe bağlı bir `defaultArg`bağımsız değişkenin varsayılan değerini belirleyen bir işlev de kullanabilirsiniz. İşlev, `defaultArg` isteğe bağlı parametreyi ilk bağımsız değişken olarak, varsayılan değeri ise ikinci olarak alır.

Aşağıdaki örnekte isteğe bağlı parametrelerin kullanımı gösteriş verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Çıktı aşağıdaki gibidir:

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

C# ve Visual Basic interop amaçları için `[<Optional; DefaultParameterValue<(...)>]` F# özniteliklerini kullanabilirsiniz, böylece arayanlar isteğe bağlı olarak bir argüman göreceksiniz. Bu, bağımsız değişkeni C#'da isteğe `MyMethod(int i = 3)`bağlı olarak tanımlamaya eşdeğerdir.

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Varsayılan parametre değeri olarak yeni bir nesne de belirtebilirsiniz. Örneğin, `Foo` üye nin giriş `CancellationToken` olarak isteğe bağlı bir girişi olabilir:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

Bağımsız değişken olarak `DefaultParameterValue` verilen değer, parametrenin türüyle eşleşmelidir. Örneğin, aşağıdakiler izin verilmez:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Bu durumda, derleyici bir uyarı oluşturur ve her iki öznitelikleri tamamen yoksayacaktır. Varsayılan değerin `null` tür açıklamalı olması gerektiğini unutmayın, aksi takdirde derleyici yanlış türü çıkar, `[<Optional; DefaultParameterValue(null:obj)>] o:obj`yani.

## <a name="passing-by-reference"></a>Başvuruya Göre Geçiş

F# değerini referansla geçmek, yönetilen işaretçi türlerini içeren [byrefs](byrefs.md)içerir. Hangi türde kullanılacağı nayönelik yönerge aşağıdaki gibidir:

- Yalnızca `inref<'T>` işaretçiyi okumanız gerekiyorsa kullanın.
- Yalnızca `outref<'T>` işaretçiye yazmanız gerekiyorsa kullanın.
- Hem `byref<'T>` okumanız hem de işaretçiye yazmanız gerekiyorsa kullanın.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

Parametre bir işaretçi ve değer değişken olduğundan, işlev in yürütülmesinden sonra değerdeki tüm değişiklikler korunur.

Herhangi `out` bir parametreyi .NET kitaplık yöntemlerinde depolamak için bir tuple'ı iade değeri olarak kullanabilirsiniz. Alternatif olarak, parametreyi `out` bir `byref` parametre olarak değerlendirebilirsiniz. Aşağıdaki kod örneği her iki yolu da göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parametre Dizileri

Bazen heterojen tip parametrelerin rasgele bir sayı alan bir işlev tanımlamak için gereklidir. Kullanılabilecek tüm türleri hesaba katmak için tüm olası aşırı yükleme yöntemlerini oluşturmak pratik olmaz. .NET uygulamaları, parametre diziözelliği aracılığıyla bu tür yöntemler için destek sağlar. İmzasında parametre dizisini alan bir yöntem, rasgele bir parametre sayısıyla sağlanabilir. Parametreler bir diziye konur. Dizi öğelerinin türü, işleve geçirilebilen parametre türlerini belirler. Öğe türü `System.Object` ile parametre dizisini tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.

F#'da parametre dizileri yalnızca yöntemlerle tanımlanabilir. Bağımsız işlevlerde veya modüllerde tanımlanan işlevlerde kullanılamaz.

Özniteliği kullanarak bir parametre `ParamArray` dizisini tanımlarsınız. Öznitelik `ParamArray` yalnızca son parametreye uygulanabilir.

Aşağıdaki kod, hem parametre dizisini alan bir .NET yöntemini hem de parametre dizisini alan bir metodu olan F# türü tanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Bir projede çalıştırıldığında, önceki kodun çıktısı aşağıdaki gibidir:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](./members/index.md)
