---
title: Parametreler ve Bağımsız Değişkenler (F#)
description: 'Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için F # dil desteği hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131986"
---
# <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Bu konuda tanımlayan parametreler ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteği açıklanmaktadır. Başvuruya göre nasıl ve tanımlayın ve değişken sayıda bağımsız değişken alabilir yöntemleri kullanma hakkında bilgiler içerir.

## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Terim *parametre* sağlanacak beklenen değerleri adlarını tanımlamak için kullanılır. Terim *bağımsız değişken* her parametre için sağlanan değerler için kullanılır.

Parametreleri, tanımlama grubu ya da curried form veya ikisinin birleşimi belirtilebilir. Bir açık parametre adını kullanarak, bağımsız değişkenler geçirebilirsiniz. Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve bir varsayılan değer verilir.

## <a name="parameter-patterns"></a>Parametre desenleri

İşlevlere ve metotlara için sağlanan parametreler, genel olarak, boşluklarla ayırarak desenleri alır. İlkesi, herhangi bir kalıpla açıklanan, yani [eşleşme ifadeleri](match-expressions.md) bir işlevi veya üye için parametre listesinde kullanılabilir.

Yöntemler, genellikle bağımsız değişkenleri geçirme demet biçimini kullanın. Kayıt formu .NET yöntemleri bağımsız değişkenler geçirilir şekilde eşleştiği için bu diğer .NET dilleri perspektifinden NET bir sonuç elde edilir.

Formun curried işlevleri kullanılarak oluşturulan ile en sık kullanılan `let` bağlar.

Aşağıdaki sözde kod tanımlama grubu ve curried bağımsız örneklerini gösterir.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Birleşik forms bazı bağımsız değişkenler de tanımlama gruplarına ve bazı değil mümkündür.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Diğer desenler içinde parametre listeleri de kullanılabilir, ancak parametre düzeni tüm olası girişleri eşleşmiyorsa olabilir bir tam eşleşme çalışma zamanında. Özel durum `MatchFailureException` bir bağımsız değişkenin değeri parametre listesinde belirtilen desenleri eşleşmediğinde oluşturulur. Parametre düzeni için eksik eşleşmeler izin veriyorsa, derleyici bir uyarı verir. Diğer düzen en az bir parametre listeleri için yaygın olarak kullanışlıdır ve joker karakter deseni. Yalnızca sağlanan herhangi bir bağımsız değişken yok saymak istediğinizde bir parametre listesinde joker karakter deseni kullanın. Aşağıdaki kodu bir bağımsız değişken listesinde joker karakter deseni kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Aşağıdaki kodda gösterildiği gibi bir dize dizisi olarak normal olarak sağlanan komut satırı bağımsız değişkenleri ilginizi olmadığında yararlı geçirilen bağımsız değişkenlerdeki ihtiyacınız olduğunda, bir programa ana girdi noktası olduğu gibi joker karakter deseni olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Bağımsız değişkenler bazen kullanılan diğer desenler `as` deseni ve ayrılmış birleşimler ve Etkin desenler ilişkili tanımlayıcı desenler. Tek örneği ayrılmış birleşim deseni şu şekilde kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Çıktı aşağıdaki gibidir:

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Etkin desenler, bağımsız değişken aşağıdaki örnekte olduğu gibi istediğiniz bir biçime dönüştürme, parametre olarak, örneğin, yararlı olabilir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Kullanabileceğiniz `as` kod aşağıdaki satırda gösterildiği gibi yerel bir değer olarak, eşleşen bir değeri depolamak için desen.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Nadiren kullanılan başka bir desendir son bağımsız değişken, işlev gövdesi olarak sağlayarak adlandırılmamış ayrıldığında bir işlev, bir lambda ifadesi hemen örtük bağımsız değişken bir desen eşleştirmesi gerçekleştirir. Buna örnek olarak aşağıdaki kod satırını ' dir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Bu kod, genel bir liste alan ve döndüren bir işlev tanımlar `true` liste boşsa ve `false` Aksi takdirde. Bu tür teknikler kullanımını kod okumak daha zor hale getirebilir.

Bazen, eksik eşleşmeler içeren desenleri kullanışlıdır, programınızdaki listeleri yalnızca üç öğe olduğunu biliyorsanız, örneğin, bir desen aşağıdaki gibi bir parametre listesinde kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Tam eşleşme sahip desenleri kullanımını en iyi hızlı prototip oluşturma ve geçici diğer kullanımlar için ayrılmıştır. Derleyici bu tür kod için bir uyarı verir. Desenler, tüm olası girişleri genel durumunun kapsamamaktadır ve bileşen API'leri için uygun değildir.

## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler

Bağımsız değişkenler yöntemleri için bir virgülle ayrılmış bağımsız değişken listesindeki konumu ile belirtilebilir veya bunlar bir yönteme açıkça ardından bir eşittir işareti ve geçirilmesi değer adı sağlayarak geçirilebilir. Belirtilen ad sağlayarak, bildirimde kullanılan ile farklı bir sırada görünebilir.

Adlandırılmış bağımsız değişkenler kod daha okunabilir ve uyarlanabilir daha belirli türde bir yöntem parametreleri, yeniden sıralama API'sindeki değişiklikler yapabilirsiniz.

Adlandırılmış bağımsız değişkenler için değil yalnızca yöntemleri için verilir `let`-bağlı İşlevler, işlev değerleri veya lambda ifadeleri.

Aşağıdaki kod örneği, adlandırılmış bağımsız değişkenler kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Bir sınıf oluşturucusuna bir çağrı adlandırılmış bağımsız değişkenler için benzer bir sözdizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz. Aşağıdaki örnek bu söz dizimini gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Daha fazla bilgi için [oluşturucular (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>İsteğe Bağlı Parametreler

İsteğe bağlı parametresi bir yöntem için parametre adının önüne bir soru işareti kullanarak belirtebilirsiniz. İsteğe bağlı parametreler, F # seçeneği türü olarak yorumlanır, seçenek türleri, kullanarak sorgulanır, normal şekilde sorgulayabilmesi bir `match` ifadesiyle `Some` ve `None`. İsteğe bağlı parametreler kullanılarak oluşturulan işlevleri, üye üzerinde yalnızca verilen `let` bağlar.

Bir işlev de kullanabilirsiniz `defaultArg`, isteğe bağlı varsayılan değerini ayarlar. `defaultArg` İşlevi isteğe bağlı parametre olarak ilk bağımsız değişken ve varsayılan değer olarak saniye alır.

Aşağıdaki örnek, isteğe bağlı parametreler kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Çıktı aşağıdaki gibidir:

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Başvuruya göre geçirme

Bir F # değere Başvuruya göre geçirme içerir [zkratka](byrefs.md), Yönetilen işaretçi türleri olduğu. Kılavuz, hangi tür kullanmak aşağıdaki gibidir:

* Kullanım `inref<'T>` yalnızca işaretçi okumak gerekiyorsa.
* Kullanım `outref<'T>` yalnızca işaretçi yazmak gerekiyorsa.
* Kullanım `byref<'T>` hem okuma hem de yazma işaretçisi gerekiyorsa.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

Parametre bir işaretçi ve değer değişebilir olduğundan, işlevi yürütme sonrasında değeri herhangi bir değişiklik korunur.

Tüm depolamak için bir dönüş değeri olarak bir tanımlama grubu kullanabilirsiniz `out` .NET kitaplığı yöntem parametreleri. Alternatif olarak davranabileceğiniz `out` parametre olarak bir `byref` parametresi. Aşağıdaki kod örneği iki yolunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parametre Dizileri

Bazen tercihe bağlı sayıda heterojen türünde parametre alan bir işlev tanımlamak gereklidir. Kullanılabilen tüm türleri için hesap için tüm olası aşırı yüklenmiş yöntemler oluşturmak pratik olmaz. .NET uygulamaları için parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar. Bir parametre dizisi içinde imzasını alan bir yöntem rastgele sayıda parametre ile sağlanabilir. Parametreler, bir dizi içine yerleştirilir. Dizi öğelerinin türü, işleve geçirilen parametre türleri belirler. Parametre dizisi ile tanımlarsanız `System.Object` öğe türü istemci kodu her türden değer geçirebilirsiniz.

F #'ta parametre dizileri, yalnızca yöntemlerdeki tanımlanabilir. Tek başına işlevleri veya modül içinde tanımlanan işlevleri kullanılamaz.

Bir parametre dizisi kullanarak tanımladığınız `ParamArray` özniteliği. `ParamArray` Özniteliği yalnızca en son parametreye uygulanabilir.

Aşağıdaki kod, her iki arama alan bir parametre dizisi ve bir tür tanımını içeren bir parametre dizisi alan bir yöntem içinde F # .NET yöntemi gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Bir projeyi çalıştırdığınızda, önceki kodun çıktısı aşağıdaki gibidir:

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

- [Üyeler](members/index.md)
