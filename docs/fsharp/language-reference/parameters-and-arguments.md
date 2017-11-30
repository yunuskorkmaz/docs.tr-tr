---
title: "Parametreler ve Bağımsız Değişkenler (F#)"
description: "Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için F # dil desteği hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler

Bu konuda parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteği açıklanmaktadır. Nasıl başvuruya göre geçirme ve tanımlayın ve değişken sayıda bağımsız değişken sürebilir yöntemleri kullanma hakkında bilgi içerir.


## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler
Terim *parametresi* sağlanacak beklenen değerler adlarını tanımlamak için kullanılır. Terim *bağımsız değişkeni* her parametre için sağlanan değerler için kullanılır.

Parametre tanımlama grubu ya da curried form veya bazı ikisinin birleşimini belirtilebilir. Bir açık parametre adını kullanarak bağımsız değişkenler geçirebilirsiniz. Yöntem parametreleri isteğe bağlı olarak belirtilen ve varsayılan bir değer verilir.


## <a name="parameter-patterns"></a>Parametre desenleri
İşlevler ve yöntemleri için sağlanan parametreler genel olarak, boşluklarla ayırarak desenleri alır. Temelde desenleri hiçbirini açıklanan, yani [eşleşme ifadeleri](match-expressions.md) parametre listesinde bir işlevi veya üye için kullanılabilir.

Yöntemleri genellikle argümanları tanımlama grubu formu kullanın. Tuple formun bağımsız değişkenler .NET yöntemlerinde geçirilir şekilde eşleştiğinden bunu diğer .NET dilleri perspektifinden daha anlaşılır bir sonuç uygular.

Curried form çoğunlukla kullanılarak oluşturulan işlevleri ile kullanılır `let` bağlar.

Aşağıdaki yarı kodu tanımlama grubu ve curried bağımsız örnekleri gösterilir.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Birleşik forms bazı bağımsız değişkenler tanımlama grupları ve bazı değil mümkündür.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Diğer desenleri parametre listelerinde de kullanılabilir, ancak parametre düzeni tüm olası girişleri eşleşmiyorsa olabilir tamamlanmamış bir eşleşme çalışma zamanında. Özel durum `MatchFailureException` bağımsız değişken değeri parametre listesinde belirtilen desenleri eşleşmediğinde oluşturulur. Bir parametre düzeni için tam eşleşme izin veriyorsa derleyici bir uyarı verir. En az bir desen parametre listeleri için yaygın olarak yararlıdır ve joker karakter deseni olmasıdır. Yalnızca sağlanan herhangi bir bağımsız değişken yok saymak istediğinizde bir parametre listesinde joker karakter deseni kullanın. Aşağıdaki kodu bir bağımsız değişken listesinde joker karakter deseni kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Aşağıdaki kod olduğu gibi bir dize dizisi olarak normal olarak sağlanan komut satırı bağımsız değişkenleri ilginizi olmadığında Joker karakter deseni geçirilen bağımsız değişken gerekmez olduğunca yararlı, örn. bir program için ana giriş noktası olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Bazen değişkenlerinde kullanılan diğer desenleri olan `as` düzeni ve ayrılmış birleşimler ve Etkin desenler ilişkili tanımlayıcı desenleri. Tek durumda ayrılmış birleşim deseni gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Çıktı aşağıdaki gibidir:

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Etkin desenler aşağıdaki örnekteki gibi istenen bir biçime dönüştürme bağımsız değişken olarak parametreler, örneğin, kullanışlı olabilir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Kullanabileceğiniz `as` aşağıdaki kod satırını gösterildiği gibi bir yerel değer olarak eşleşen bir değeri depolamak için desen.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Bazen kullanılan başka bir düzen, işlev gövdesi olarak sağlayarak adlandırılmamış son bağımsız değişken ayrıldığında bir işlev, hemen örtük bağımsız bir desen eşleştirme gerçekleştiren bir lambda ifadesi yöneliktir. Bu aşağıdaki satırlık bir kod örneğidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Bu kod, genel bir liste alır ve döndüren bir işlev tanımlar `true` liste boşsa ve `false` Aksi takdirde. Bu tür teknikler kullanımını kod okumak daha zor hale getirebilir.

Bazen, tamamlanmamış eşleşmeleri içeren desenleri faydalıdır, programınızı listelerinde yalnızca üç öğe olduğunu biliyorsanız, örneğin, aşağıdaki gibi bir desen parametre listesini kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Tamamlanmamış eşleşmeleri sahip desenleri kullanımını en iyi hızlı prototipi oluşturulurken ve diğer geçici kullanım için ayrılmıştır. Derleyici, bu tür kodu için bir uyarı verecek. Desenler tüm olası girdi genel durum kapak olamaz ve API bileşeni için uygun değildir.

## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler
Yöntemleri için bağımsız bir virgülle ayrılmış bağımsız değişken listesinde konuma göre belirtilebilir veya bunların bir yönteme açıkça eşittir işareti ve geçirilmesi değeri adından, sağlayarak geçirilebilir. Adı sağlayarak belirtilmişse bildiriminde kullanılan ile farklı bir sırada yer alabilir.

Adlandırılmış bağımsız değişkenler kodunu daha okunabilir ve daha uyarlanabilir belirli türde bir yöntem parametreleri, sipariş API'sindeki değişiklikleri yapabilirsiniz.

Adlandırılmış bağımsız değişkenler için değil yalnızca yöntemleri için verilir `let`-bağlı İşlevler, işlevi değerleri veya lambda ifadeleri.

Aşağıdaki kod örneğinde adlandırılmış bağımsız değişkenler kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Bir sınıf oluşturucu için bir çağrı adlandırılmış bağımsız değişkenler için benzer bir söz dizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz. Aşağıdaki örnekte bu söz dizimini gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Daha fazla bilgi için bkz: [oluşturucular (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>İsteğe Bağlı Parametreler
İsteğe bağlı parametresi bir yöntem için parametre adı önünde soru işareti kullanarak belirtebilirsiniz. İsteğe bağlı parametreler, F # seçeneği türü olarak yorumlanır, seçenek türleri, kullanarak seçmeleri istenir, normal şekilde sorgulayabilirsiniz şekilde bir `match` ifadesiyle `Some` ve `None`. İsteğe bağlı parametreler kullanılarak oluşturulan işlevlerde üyeleri yalnızca üzerinde verilen `let` bağlar.

Bir işlev de kullanabilirsiniz `defaultArg`, isteğe bağlı bir bağımsız değişken varsayılan değerini ayarlar. `defaultArg` İşlev, ilk bağımsız değişken olarak isteğe bağlı bir parametre ve ikinci olarak varsayılan değerini alır.

Aşağıdaki örnek, isteğe bağlı parametreler kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Çıktı aşağıdaki gibidir:

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Başvuruya göre geçirme
F # destekler `byref` anahtar sözcüğü bir parametre başvuruya göre geçirilir belirtir. Bu değer herhangi bir değişiklik işlevi yürütme sonrasında korunur anlamına gelir. İçin sağlanan değerlerden bir `byref` parametresi değişebilir olmalıdır. Alternatif olarak, uygun bir tür başvuru hücreleri geçirebilirsiniz.

Bir işlevden birden fazla değer döndürmek için bir yol olarak gelişen .NET dillerinde başvuruya göre geçirme. F #'ta yapabilir bu amaç için bir tanımlama grubu döndürür veya kesilebilir başvuru hücresi parametre olarak kullanın. `byref` Parametresi .NET kitaplıkları ile birlikte çalışabilirlik için temel olarak sağlanır.

Aşağıdaki örnekler kullanımını göstermek `byref` anahtar sözcüğü. Parametre olarak bir başvuru hücresi kullandığınızda, gerekir adlandırılmış değeri olarak başvuru hücresi oluşturur ve parametre olarak kullanan, yalnızca eklemek dikkat edin `ref` yapılan ilk çağrıda gösterildiği gibi işleci `Increment` aşağıdaki kodda. Bir başvuru hücre oluşturma temel alan değeri bir kopyasını oluşturduğundan ilk çağrı yalnızca geçici bir değeri artırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

Herhangi bir depolamak için dönüş değeri olarak bir tanımlama grubu kullanabilirsiniz `out` .NET kitaplığı yöntem parametreleri. Alternatif olarak, davranabilirsiniz `out` parametre olarak bir `byref` parametresi. Aşağıdaki kod örneği, her iki yolu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parametre Dizileri
Bazen rastgele sayıda heterojen türü parametre isteyen bir işlev tanımlamak gereklidir. Kullanılabilir tüm türleri için hesap için tüm olası aşırı yüklenmiş yöntemler oluşturmak mümkün olmayacaktır. .NET uygulamaları için parametre dizisi özelliği aracılığıyla böyle yöntemleri için destek sağlar. Bir parametre dizisi kendi İmzada gereken bir yöntem rastgele sayıda parametre ile sağlanabilir. Parametreleri bir diziye yerleştirilir. Dizi öğelerin türü işlevine geçirilen parametre türleri belirler. Parametre dizisi ile tanımlarsanız `System.Object` öğe türü olarak istemci kodu herhangi bir tür değerleri geçirebilirsiniz.

F #'ta parametre dizileri, yalnızca yöntemleri tanımlanabilir. Tek başına işlevlerde veya modüllerde tanımlı işlevler kullanılamaz.

Bir parametre dizisi kullanarak tanımladığınız `ParamArray` özniteliği. `ParamArray` Özniteliği yalnızca son parametre uygulanabilir.

Aşağıdaki kod, her iki çağırma F bir parametre dizisi alan yöntemi olan #'de bir parametre dizisi ve bir tür tanımını alır .NET yöntemi gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Bir proje ile çalıştırdığınızda, önceki kod çıkışı aşağıdaki gibidir:

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeleri](members/index.md)
