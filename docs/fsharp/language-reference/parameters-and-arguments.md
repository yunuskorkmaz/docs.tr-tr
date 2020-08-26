---
title: Parametreler ve Bağımsız Değişkenler
description: 'Parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için F # dil desteği hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811528"
---
# <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Bu konuda, parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği açıklanmaktadır. Başvuruya göre geçme ve değişken sayıda bağımsız değişken alan yöntemler tanımlama ve kullanma hakkında bilgi içerir.

## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Terimi *parametresi* , sağlanması beklenen değerlerin adlarını anlatmak için kullanılır. *Bağımsız değişkeni* , her bir parametre için belirtilen değerler için kullanılır.

Parametreler demet veya curried formunda ya da ikisinin bir birleşimi içinde belirtilebilir. Açık bir parametre adı kullanarak bağımsız değişkenler geçirebilirsiniz. Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan bir değer verilir.

## <a name="parameter-patterns"></a>Parametre desenleri

İşlevlere ve yöntemlere sağlanan parametreler, genel olarak boşluklarla ayrılmış desenlerdir. Bu, ilke içinde, [eşleşme ifadelerinde](match-expressions.md) açıklanan desenlerin herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceği anlamına gelir.

Yöntemler genellikle bağımsız değişkenlerin geçirilerek demet biçimini kullanır. Bu, diğer .NET dillerinin perspektifinden daha net bir sonuca ulaşır çünkü demet formu, bağımsız değişkenlerin .NET yöntemlerine geçirilmesi ile eşleşir.

Curried form, genellikle bağlamalar kullanılarak oluşturulan işlevlerle kullanılır `let` .

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

Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişlerle eşleşmezse, çalışma zamanında tamamlanmamış bir eşleşme olabilir. `MatchFailureException`Bir bağımsız değişkenin değeri, parametre listesinde belirtilen desenlerle eşleşmezse, bu özel durum oluşturulur. Bir parametre deseninin tamamlanmamış eşleştirmelere izin verdiği durumlarda derleyici bir uyarı verir. En az bir diğer model genellikle parametre listeleri için yararlıdır ve bu, joker karakter örüntü. Yalnızca sağlanan bağımsız değişkenleri yoksaymak istediğinizde joker karakter modelini bir parametre listesinde kullanırsınız. Aşağıdaki kod, bir bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Joker karakter düzeni, aşağıdaki kodda olduğu gibi, normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleri ile ilgilenmediğiniz zaman, bir programa yönelik ana giriş noktasında, örneğin, bir program için ana giriş noktasında, bir programın ana giriş noktasındaki bağımsız değişkenlere ihtiyaç duymadığınızda yararlı olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Bazen bağımsız değişkenlerde kullanılan diğer desenler `as` , düzen ve ayrılmış birleşimler ve etkin desenlerle ilişkili tanımlayıcı desenlerdir. Tek durum ayrılmış birleşim modelini aşağıdaki gibi kullanabilirsiniz.

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

`as`Aşağıdaki kod satırında gösterildiği gibi, eşleşen bir değeri yerel bir değer olarak depolamak için, bu kalıbı kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Bazen kullanılan başka bir model, işlevin gövdesi olarak, örtük bağımsız değişkende bir model eşleşmesi yapan bir lambda ifadesi sağlayarak adlandırılmamış en son bağımsız değişkeni bir işlev olarak bırakır. Aşağıdaki kod satırı buna bir örnektir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Bu kod, genel liste alan ve `true` Liste boşsa ve aksi takdirde döndüren bir işlevi tanımlar `false` . Bu tür tekniklerin kullanımı, kodun okunmasını zorlaştırabilir.

Bazen, tamamlanmamış eşleşmeleri içeren desenler yararlı olur, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, aşağıdaki gibi bir deseni parametre listesinde kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Tamamlanmamış eşleşmelerin kullanıldığı desenlerin kullanımı, Hızlı Prototipleme ve diğer geçici kullanımlar için en iyi ayırmıştır. Derleyici bu tür kodlar için bir uyarı verebilir. Bu tür desenler tüm olası girdilerin genel durumunu kapsamaz ve bu nedenle bileşen API 'Leri için uygun değildir.

## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler

Yöntemler için bağımsız değişkenler, virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad ve ardından bir eşittir işareti ve geçirilecek değer tarafından açıkça bir yönteme geçirilebilir. Ad sağlanarak belirtilmişse bildirimde kullanılan farklı bir sırada görünebilirler.

Adlandırılmış bağımsız değişkenler, API 'de yöntem parametrelerinin yeniden sıralanması gibi belirli değişiklik türlerine kod daha okunabilir ve daha uyumlu hale getirebilirsiniz.

Adlandırılmış bağımsız değişkenlere yalnızca, for `let` -bağlanmadı işlevleri, işlev değerleri veya lambda ifadeleri için izin verilir.

Aşağıdaki kod örneği adlandırılmış bağımsız değişkenlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Bir sınıf oluşturucusuna yapılan çağrıda, adlandırılmış bağımsız değişkenlerden benzer bir sözdizimi kullanarak sınıfının özelliklerinin değerlerini ayarlayabilirsiniz. Aşağıdaki örnek bu söz dizimini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Daha fazla bilgi için bkz. [oluşturucular (F #)](members/constructors.md).

## <a name="optional-parameters"></a>İsteğe Bağlı Parametreler

Parametre adının önünde bir soru işareti kullanarak, bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz. İsteğe bağlı parametreler F # seçenek türü olarak yorumlanır. bu nedenle, ve ile bir ifade kullanarak bunları seçenek türlerinin sorgulandığı normal şekilde sorgulayabilirsiniz `match` `Some` `None` . İsteğe bağlı parametrelere, bağlamalar kullanılarak oluşturulan işlevlerde değil, yalnızca üyelerde izin verilir `let` .

İsteğe bağlı değerleri, veya gibi parametre adına göre yönteme geçirebilirsiniz `?arg=None` `?arg=Some(3)` `?arg=arg` . Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçiren bir yöntem oluştururken yararlı olabilir.

`defaultArg`İsteğe bağlı bir bağımsız değişkenin varsayılan değerini ayarlayan bir işlevi de kullanabilirsiniz. `defaultArg`İşlevi, isteğe bağlı parametreyi ilk bağımsız değişken olarak ve varsayılan değeri ikinci olarak alır.

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

C# ve Visual Basic birlikte çalışabilirliğine yönelik `[<Optional; DefaultParameterValue<(...)>]` olarak, F # içindeki öznitelikleri kullanarak çağıranların isteğe bağlı olarak bir bağımsız değişken görmesini sağlayabilirsiniz. Bu, bağımsız değişkeni C# ' de olduğu gibi isteğe bağlı olarak tanımlamaya eşdeğerdir `MyMethod(int i = 3)` .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Ayrıca, varsayılan parametre değeri olarak yeni bir nesne belirtebilirsiniz. Örneğin, `Foo` üyenin `CancellationToken` bunun yerine giriş olarak isteğe bağlı olması olabilir:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

Bağımsız değişkeni olarak verilen değerin `DefaultParameterValue` parametrenin türüyle eşleşmesi gerekir. Örneğin, aşağıdakilere izin verilmez:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Bu durumda, derleyici bir uyarı oluşturur ve iki özniteliği de tamamen yoksayar. Diğer bir deyişle, `null` derleyici yanlış türü (ör.), aksi takdirde, varsayılan değerin tür-açıklama olması gerektiğini unutmayın `[<Optional; DefaultParameterValue(null:obj)>] o:obj` .

## <a name="passing-by-reference"></a>Başvuruya göre geçirme

Bir F # değerinin başvuruya geçirilmesi, yönetilen işaretçi türleri olan [ByRef](byrefs.md)'ler ile ilgilidir. Kullanılacak tür ile ilgili kılavuz aşağıdaki gibidir:

- `inref<'T>`Yalnızca işaretçiyi okumanız gerekiyorsa kullanın.
- `outref<'T>`Yalnızca işaretçiye yazmanız gerekiyorsa kullanın.
- `byref<'T>`Hem okuma hem de işaretçiye yazma gerekiyorsa kullanın.

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

.NET kitaplığı yöntemlerinde herhangi bir parametreyi depolamak için bir kayıt düzeni değerini dönüş değeri olarak kullanabilirsiniz `out` . Alternatif olarak, `out` parametresini bir parametre olarak kabul edebilirsiniz `byref` . Aşağıdaki kod örneğinde her iki yol da gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parametre Dizileri

Bazen heterojen türden rastgele sayıda parametre alan bir işlev tanımlanması gerekir. Tüm olası aşırı yüklenmiş yöntemlerin, kullanılabilecek tüm türlere yönelik olarak oluşturulması pratik değildir. .NET uygulamaları, parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar. İmzasında parametre dizisi alan bir yöntem, rastgele sayıda parametre ile birlikte etkinleştirilebilir. Parametreler bir diziye konur. Dizi öğelerinin türü, işleve geçirilebilecek parametre türlerini belirler. Parametre dizisini `System.Object` öğesi türü olarak tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.

F # içinde parametre dizileri yalnızca yöntemlerde tanımlanabilir. Bunlar tek başına işlevlerde veya modüllerde tanımlanmış işlevlerde kullanılamaz.

Özniteliğini kullanarak bir parametre dizisi tanımlarsınız `ParamArray` . `ParamArray`Özniteliği yalnızca son parametreye uygulanabilir.

Aşağıdaki kod, bir parametre dizisi alan bir .NET yöntemi ve bir parametre dizisi alan bir yöntemi olan F # içindeki bir tür tanımını gösterir.

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
