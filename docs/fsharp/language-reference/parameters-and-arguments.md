---
title: Parametreler ve Bağımsız Değişkenler
description: Parametreleri tanımlama F# ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği hakkında bilgi edinin.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837135"
---
# <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Bu konuda, parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği açıklanmaktadır. Başvuruya göre geçme ve değişken sayıda bağımsız değişken alan yöntemler tanımlama ve kullanma hakkında bilgi içerir.

## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Terimi *parametresi* , sağlanması beklenen değerlerin adlarını anlatmak için kullanılır. *Bağımsız değişkeni* , her bir parametre için belirtilen değerler için kullanılır.

Parametreler demet veya curried formunda ya da ikisinin bir birleşimi içinde belirtilebilir. Açık bir parametre adı kullanarak bağımsız değişkenler geçirebilirsiniz. Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan bir değer verilir.

## <a name="parameter-patterns"></a>Parametre desenleri

İşlevlere ve yöntemlere sağlanan parametreler, genel olarak boşluklarla ayrılmış desenlerdir. Bu, ilke içinde, [eşleşme ifadelerinde](match-expressions.md) açıklanan desenlerin herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceği anlamına gelir.

Yöntemler genellikle bağımsız değişkenlerin geçirilerek demet biçimini kullanır. Bu, diğer .NET dillerinin perspektifinden daha net bir sonuca ulaşır çünkü demet formu, bağımsız değişkenlerin .NET yöntemlerine geçirilmesi ile eşleşir.

Curried form çoğunlukla `let` bağlamaları kullanılarak oluşturulan işlevlerle kullanılır.

Aşağıdaki sözde kod, kayıt düzeni ve curried bağımsız değişkenlerinin örneklerini gösterir.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Bazı bağımsız değişkenler diziler halinde olduğunda ve bazıları olmadığında birleştirilmiş formlar mümkündür.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişlerle eşleşmezse, çalışma zamanında tamamlanmamış bir eşleşme olabilir. Bir bağımsız değişkenin değeri parametre listesinde belirtilen desenlerle eşleşmediği zaman özel durum `MatchFailureException` oluşturulur. Bir parametre deseninin tamamlanmamış eşleştirmelere izin verdiği durumlarda derleyici bir uyarı verir. En az bir diğer model genellikle parametre listeleri için yararlıdır ve bu, joker karakter örüntü. Yalnızca sağlanan bağımsız değişkenleri yoksaymak istediğinizde joker karakter modelini bir parametre listesinde kullanırsınız. Aşağıdaki kod, bir bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Joker karakter düzeni, aşağıdaki kodda olduğu gibi, normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleri ile ilgilenmediğiniz zaman, bir programa yönelik ana giriş noktasında, örneğin, bir program için ana giriş noktasında, bir programın ana giriş noktasındaki bağımsız değişkenlere ihtiyaç duymadığınızda yararlı olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Bazen bağımsız değişkenlerde kullanılan diğer desenler, `as` desendir ve ayırt edici birleşimler ve etkin desenlerle ilişkili tanımlayıcı desenlerdir. Tek durum ayrılmış birleşim modelini aşağıdaki gibi kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Çıktı aşağıdaki gibidir:

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Etkin desenler, aşağıdaki örnekte olduğu gibi, bir bağımsız değişken istenen biçime dönüştürülürken parametre olarak yararlı olabilir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Aşağıdaki kod satırında gösterildiği gibi, eşleşen bir değeri yerel bir değer olarak depolamak için `as` modelini kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Bazen kullanılan başka bir model, işlevin gövdesi olarak, örtük bağımsız değişkende bir model eşleşmesi yapan bir lambda ifadesi sağlayarak adlandırılmamış en son bağımsız değişkeni bir işlev olarak bırakır. Aşağıdaki kod satırı buna bir örnektir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Bu kod, genel liste alan ve liste boşsa `true` döndüren ve aksi durumda `false` döndüren bir işlevi tanımlar. Bu tür tekniklerin kullanımı, kodun okunmasını zorlaştırabilir.

Bazen, tamamlanmamış eşleşmeleri içeren desenler yararlı olur, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, aşağıdaki gibi bir deseni parametre listesinde kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Tamamlanmamış eşleşmelerin kullanıldığı desenlerin kullanımı, Hızlı Prototipleme ve diğer geçici kullanımlar için en iyi ayırmıştır. Derleyici bu tür kodlar için bir uyarı verebilir. Bu tür desenler tüm olası girdilerin genel durumunu kapsamaz ve bu nedenle bileşen API 'Leri için uygun değildir.

## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler

Yöntemler için bağımsız değişkenler, virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad ve ardından bir eşittir işareti ve geçirilecek değer tarafından açıkça bir yönteme geçirilebilir. Ad sağlanarak belirtilmişse bildirimde kullanılan farklı bir sırada görünebilirler.

Adlandırılmış bağımsız değişkenler, API 'de yöntem parametrelerinin yeniden sıralanması gibi belirli değişiklik türlerine kod daha okunabilir ve daha uyumlu hale getirebilirsiniz.

Adlandırılmış bağımsız değişkenlere yalnızca metotlar için izin verilir, `let`bağlantılı işlevler, işlev değerleri veya lambda ifadeleri için kullanılamaz.

Aşağıdaki kod örneği adlandırılmış bağımsız değişkenlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Bir sınıf oluşturucusuna yapılan çağrıda, adlandırılmış bağımsız değişkenlerden benzer bir sözdizimi kullanarak sınıfının özelliklerinin değerlerini ayarlayabilirsiniz. Aşağıdaki örnek bu söz dizimini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Daha fazla bilgi için bkz. [oluşturucularF#()](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>İsteğe Bağlı Parametreler

Parametre adının önünde bir soru işareti kullanarak, bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz. İsteğe bağlı parametreler F# seçenek türü olarak yorumlanır. bu nedenle, `Some` ve `None`ile bir `match` ifadesi kullanarak bunları seçenek türlerinin sorgulandığı düzenli şekilde sorgulayabilirsiniz. İsteğe bağlı parametrelere, `let` bağlamaları kullanılarak oluşturulan işlevlerde değil, yalnızca üyelerde izin verilir.

`?arg=None` veya `?arg=Some(3)` veya `?arg=arg`gibi parametre adına göre isteğe bağlı değerleri yönteme geçirebilirsiniz. Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçiren bir yöntem oluştururken yararlı olabilir.

İsteğe bağlı bir bağımsız değişkenin varsayılan değerini ayarlayan bir `defaultArg`işlevi de kullanabilirsiniz. `defaultArg` işlevi, isteğe bağlı parametreyi ilk bağımsız değişken olarak ve varsayılan değeri ikinci olarak alır.

Aşağıdaki örnek, isteğe bağlı parametrelerin kullanımını gösterir.

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

Ve Visual Basic birlikte çalışabilirliğine sahip olmak için, içindeki C# F#`[<Optional; DefaultParameterValue<(...)>]` özniteliklerini kullanarak, çağıranların bir bağımsız değişkeni isteğe bağlı olarak görmesini sağlayabilirsiniz. Bu, bağımsız değişkeni `MyMethod(int i = 3)`C# gibi isteğe bağlı olarak tanımlamaya eşdeğerdir.

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Ayrıca, varsayılan parametre değeri olarak yeni bir nesne belirtebilirsiniz. Örneğin, `Foo` üyesi giriş olarak isteğe bağlı `CancellationToken` olabilir:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

`DefaultParameterValue` bağımsız değişkeni olarak verilen değer parametrenin türüyle eşleşmelidir. Örneğin, aşağıdakilere izin verilmez:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Bu durumda, derleyici bir uyarı oluşturur ve iki özniteliği de tamamen yoksayar. Varsayılan değer `null` tür açıklanmalıdır; Aksi durumda, derleyici yanlış türde (örneğin, `[<Optional; DefaultParameterValue(null:obj)>] o:obj`).

## <a name="passing-by-reference"></a>Başvuruya göre geçirme

Bir F# değerin başvuruya göre geçirilmesi, yönetilen işaretçi türleri olan [ByRef 'ler](byrefs.md)içerir. Kullanılacak tür ile ilgili kılavuz aşağıdaki gibidir:

- Yalnızca işaretçiyi okumanız gerekiyorsa `inref<'T>` kullanın.
- Yalnızca işaretçiye yazmanız gerekiyorsa `outref<'T>` kullanın.
- Hem okuma hem de işaretçiye yazma gerekiyorsa `byref<'T>` kullanın.

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

Parametresi bir işaretçi olduğundan ve değer değişebilir olduğundan, değer üzerinde yapılan tüm değişiklikler işlevin yürütülmesinden sonra tutulur.

.NET kitaplığı yöntemlerinde `out` parametrelerini depolamak için bir kayıt düzeni dönüş değeri olarak kullanabilirsiniz. Alternatif olarak, `out` parametresini bir `byref` parametresi olarak kabul edebilirsiniz. Aşağıdaki kod örneğinde her iki yol da gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parametre Dizileri

Bazen heterojen türden rastgele sayıda parametre alan bir işlev tanımlanması gerekir. Tüm olası aşırı yüklenmiş yöntemlerin, kullanılabilecek tüm türlere yönelik olarak oluşturulması pratik değildir. .NET uygulamaları, parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar. İmzasında parametre dizisi alan bir yöntem, rastgele sayıda parametre ile birlikte etkinleştirilebilir. Parametreler bir diziye konur. Dizi öğelerinin türü, işleve geçirilebilecek parametre türlerini belirler. Parametre dizisini öğe türü olarak `System.Object` tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.

İçinde F#, parametre dizileri yalnızca yöntemlerde tanımlanabilir. Bunlar tek başına işlevlerde veya modüllerde tanımlanmış işlevlerde kullanılamaz.

Bir parametre dizisini `ParamArray` özniteliği kullanarak tanımlarsınız. `ParamArray` özniteliği yalnızca son parametreye uygulanabilir.

Aşağıdaki kod, her ikisi de bir parametre dizisi alan ve içindeki F# bir tür tanımı bir parametre dizisi alan bir .net yönteminin çağrılmasını göstermektedir.

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
