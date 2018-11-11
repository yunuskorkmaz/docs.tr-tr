---
title: F# İşlevsel Programlamaya Giriş
description: İşlevsel programlamaya temellerini öğrenin F#.
ms.date: 10/29/2018
ms.openlocfilehash: d4a9bb0cd826b41aca96e12e2bcb5aab80c18eb4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25863842"
---
# <a name="introduction-to-functional-programming-in-f"></a>F# İşlevsel Programlamaya Giriş #

İşlevsel programlama, İşlevler ve sabit veri kullanımını vurgulamaktadır programlama stilidir. Türü belirlenmiş işlevsel programlama, işlevsel programlama statik türler ile gibi ile birleştirildiğinde F#. Genel olarak, aşağıdaki kavramları işlevsel programlamaya vurgulanır:

* Kullandığınız yönelik birincil yapılar işlevleri
* İfadeler yerine deyimleri
* Değişkenler üzerinde değişmez değerleri
* Bildirim temelli üzerinden zorunlu programlama

Bu seri boyunca kavramları ve desenler işlevsel programlama kullanarak keşfedeceksiniz F#. Bu doğrultuda, bazı öğreneceksiniz F# çok.

## <a name="terminology"></a>Terminoloji

Diğer programlama paradigmalarını gibi fonksiyonel programlama sonunda öğrenmek için ihtiyacınız olacak bir sözlük ile birlikte gelir. Her zaman göreceğiniz bazı ortak şartları şunlardır:

* **İşlev** -bir işlev bir giriş verildiğinde bir çıktı oluşturacak bir yapıdır. Daha fazla izlerse, _eşler_ birinden bir öğe için başka bir grubu ayarlayın. Bu formalism özellikle çalışan işlevler koleksiyon veri kullanılırken, pek çok yolla somut içine kaldırılır. Bu, en temel (ve önemli) kavram olarak fonksiyonel programlama olur. 
* **İfade** -bir ifade bir değer üreten kodda bir yapıdır. İçinde F#, bu değer bağlı veya açıkça yoksayıldı. Bir ifade, basit bir şekilde işlev çağrısına göre değiştirilebilir.
* **Saflığa** -Saflığa olduğu bir özelliği bir işlevin dönüş değeri her zaman aynı bağımsız değişkenleri aynı olduğundan emin ve kendi değerlendirme yan etkileri vardır. Saf işlev tamamen bağımsız değişkenlerini bağlıdır.
* **Başvuru saydamlık** -başvuru saydamlık çıktılarını ile bunlar değiştirilebilir bir programın davranışını etkilemeden, ifadelerin bir özelliği olan.
* **Değiştirilemezlik** -değiştirilen yerinde bir değer olamaz Değiştirilemezlik anlamına gelir. Yerinde değiştirebileceğiniz değişkenler kullanılmasının budur.

## <a name="examples"></a>Örnekler

Aşağıdaki örnekler, bu kavramları göstermektedir.

### <a name="functions"></a>İşlevler

En yaygın ve temel işlevsel programlama yapısında işlevdir. Tamsayıya 1 ekler, basit bir işlevi şu şekildedir:

```fsharp
let addOne x = x + 1
```

Tür imzası aşağıdaki gibidir:

```fsharp
val addOne: x:int -> int
```

İmza, okunabilir "`addOne` kabul eden bir `int` adlı `x` ve oluşturacak bir `int`". Daha eski adıyla `addOne` olduğu _eşleme_ tamsayılar kümesi ile tamsayılar kümesi arasında bir değer. `->` Belirteci bu eşlemeyi gösterir. İçinde F#, ne yaptığını fikir işlev imzası genellikle bakabilirsiniz.

Bu nedenle, neden imza önemlidir? Türü belirlenmiş işlevsel programlama, bir işlev uygulaması genellikle küçük gerçek tür imzası daha önemlidir! Olgu, `addOne` çalışma zamanında, ilgi çekici bir tamsayı değerine 1 ekler ancak zaman, oluşturmak bir program kabul edip döndürür olgu bir `int` olduğundan bu işlev gerçekte nasıl kullanacağını ne bildirir. Bu işlev doğru (göre türü imzası) kullandığınızda, ayrıca, herhangi bir sorunu tanılamada gövdesi içinde yalnızca yapılabilir `addOne` işlevi. Arkasında yazılı işlevsel programlama impetus budur.

### <a name="expressions"></a>İfadeler

İfade bir değer olarak değerlendirilmesi yapılarıdır. Bir eylem gerçekleştirmek, deyimleri aksine, geri bir değer veren bir eylem gerçekleştirmek ifadeleri düşünülebilir. İfadeler, neredeyse her zaman işlevsel programlama deyimlerinde yerine kullanılır.

Önceki işlevi `addOne`. Gövdesi `addOne` ifade:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Bu ifadenin sonuç türü tanımlayan sonucudur `addOne` işlevi. Örneğin, bu işlevi oluşturan ifade gibi farklı bir tür olarak değiştirilemedi bir `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

İşlev imzası sunulmuştur:

```fsharp
val addOne: x:'a -> string
```

Herhangi bir türü beri F# olabilir `ToString()` bunun üzerinde türü adlı `x` genel yapılan (adlı [otomatik Genelleştirme](../language-reference/generics/automatic-generalization.md)), ve sonuç türü bir `string`.

İfadeleri yalnızca işlev gövdeleri değildir. Başka bir yerde kullanmak için bir değer üreten ifadeleri olabilir. Bir ortak biridir `if`:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

`if` İfade olarak adlandırılan bir değer oluşturuyor `result`. Atlarsanız Not `result` tamamen yapmadan `if` ifade gövdesi, `addOneIfOdd` işlevi. Deyimler hakkında hatırlamak anahtar değer üretme şeydir.

Özel bir tür `unit`, olduğunda döndürülecek bir şey kullanılır. Örneğin, bu basit işlev göz önünde bulundurun:

```fsharp
let printString (str: string) =
    printfn "String is: %s" s
```

İmza şöyle görünür:

```fsharp
val printString: str:string -> unit
```

`unit` Türü, döndürülen gerçek değer olduğunu gösterir. Gereken bir yordamı olması gerektiğinde bu faydalıdır "İş" Bu çalışma sonucunda döndürülecek değer sahip olmasına rağmen.

Kesin programlama sharp Karşıtlık budur burada eşdeğer `if` yapıdır bir deyim ve değerleri üreten genellikle yapılır değişkenleri diziyi ile. Örneğin, C#, kod şu şekilde yazılmış olabilir:

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

Hatalarının ayıklanabileceğini belirtmekte yarar C# ve diğer C stili dillerin desteği [Üçlü ifade](../../csharp/language-reference/operators/conditional-operator.md), ifade tabanlı koşullu programlama için izin verir.

İşlevsel programlama, bu deyimleri değerlerle kesilecek nadir olarak rastlanıyor. Bazı işlevsel dillerin deyimleri ve Mutasyon desteklese de, bu kavramları işlevsel programlamaya kullanmak yaygın değildir.

### <a name="pure-functions"></a>Saf İşlevler

Daha önce belirtildiği gibi saf İşlevler, işlev:

* Aynı değere aynı giriş için her zaman değerlendirin.
* Hiçbir yan etkisi yoktur.

Matematik işlevleri bu bağlamda düşünmek faydalıdır. Matematik, işlevleri yalnızca kendi bağımsız değişkenlerine göre değişir ve tüm yan etkileri izniniz yok. Matematik işlevindeki `f(x) = x + 1`, değerini `f(x)` yalnızca değerine bağlıdır `x`. Saf işlevsel programlama, aynı şekilde işlevlerdir.

Saf işlev yazarken işlevi bağımsız değişkenlerinden yalnızca üzerinde bağlıdır ve sonuçları bir yan etkisi herhangi bir eylem gerçekleştirmenize gerekir.

Aşağıda, genel, kesilebilir durumuna bağlıdır çünkü saf olmayan işlev örneği verilmiştir:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue` İşlevi açıkça Hanuka çünkü `value` 1'den farklı bir değere sahip için herhangi bir zamanda değiştirilebilir. Bu, genel bir değerde bağlı olarak, işlevsel programlama kaçınılması modelidir.

Bir yan etkisi gerçekleştirdiğinden, saf olmayan bir işlevin başka bir örnek aşağıdadır:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

Bu işlev üzerinde genel bir değerde benzemez olsa da, bu değeri Yazar `x` programın çıkışı için. Olmasa da Bunun yapılması doğal olarak yanlış bir şey, işlevin saf değil anlamına gelmez.

Kaldırma `printfn` deyimi finally yapar işlevin saf:

```fsharp
let addOneToValue x = x + 1
```

Bu işlev bir kendiliğinden olmasa da _daha iyi_ daha önceki sürümüyle `printfn` deyimi, bunu garanti bu işlev yaptığı olduğundan, bir değer döndürür. Bunu çağıran bir kez işlev ya da 1 milyardan fazla kez aynı şeyi hala neden olur: yalnızca bir değer üretir. Bu tahmin edilebilirliğini işlevsel programlama, değerli aynıdır tüm saf işlev referentially saydam olduğu anlamına gelir.

### <a name="referential-transparency"></a>Başvuru saydamlık

Başvuru saydamlık, ifadeler ve İşlevler için kullanılan bir özelliktir. Bir ifade referentially saydam olacak şekilde, programın davranışını değiştirmeden elde edilen değeriyle değiştirilmesi mümkün olmalıdır. Tüm saf işlevler referentially saydamdır.

Saf işlevler gibi ile başvuru saydamlık matematik açısından düşünmek yararlı olabilir. Matematik ifadesindeki `y = f(x)`, `f(x)` işlevin sonucu tarafından değiştirilebilir ve yine de eşit olacaktır `y`. Bu başvuru saydamlık fonksiyonel programlama için eşit oranda geçerlidir.

Önceden tanımlanmış çağırmayı düşünün `addOneIfOdd` iki kez çalışması:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 = addOneIffOdd 1 // Produces 2
let res2 = addOneIffOdd 2 // Produces 2
```

Biz bağımsız değişkenini değiştirerek işlev gövdesi ile her işlev çağrısının değiştirebilirsiniz `input` her değeri:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 =
    let result =
        if isOdd 1 then
            1 + 1
        else
            1

    result
let res2 =
    let result =
        if isOdd 2 then
            2 + 1
        else
            2

    result
```

Her ikisi de `res1` ve `res2` gösteren işlev çağrıldı sanki aynı değere sahip `addOneIfOdd` referentially saydamdır!

Ayrıca, bir işlev de referentially saydam olarak saf olmak zorunda değildir. Bir önceki tanımını dikkate `addOneTovalue`:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

Bu işlev için herhangi bir çağrı, gövdesinde tarafından değiştirilebilir ve her şeyi gerçekleşir:

* Çıktı, eklenmeden önce değeri yazdırılır
* Eklenmiş 1 değerine sahip

Programlama yaparken F#, genellikle saflığa yerine hedefi olan başvuru saydamlık olur. Ancak, mümkün olduğunda, saf işlevler yazma yine de iyi bir uygulamadır.

### <a name="immutability"></a>Değiştirilemezlik

Son olarak, en temel kavramlarını yazılmış işlevsel programlama değiştirilemezlik biridir. İçinde F#, varsayılan olarak tüm değerler sabittir. Bu, açıkça değişebilir olarak işaretlerken sürece yerinde olamaz anlamına gelir.

Uygulamada, değişmez değerleri ile çalışma "Bir şeyle değiştirmek istiyorum," programlamaya yaklaşımınızı değiştirmek, için "yeni bir değer oluşturmak istiyorum" gösterir.

Örneğin, bir değer eklemeyi 1 var olan bir diziyi değil, yeni bir değer üreten anlamına gelir:

```fsharp
let value = 1
let secondValue = value + 1
```

İçinde F#, aşağıdaki kod mu **değil** bulunmamalıdır `value` işlev; bunun yerine, bunu bir eşitlik denetimi gerçekleştirir:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Bazı işlevsel programlama dilleri Mutasyon hiç desteklemez. İçinde F#desteklenir, ancak bu değerler için varsayılan davranış değildir.

Bu kavram, hatta veri yapıları daha fazla sınırlandıramazsınız genişletir. Başlangıçta olabilir daha kümeleri (ve çok daha fazlası) farklı bir uygulama gibi işlevsel programlama, sabit veri yapılarını bekler. Kavramsal olarak, bir şey bir kümeye bir öğe eklemeye kümesi değişmez gibi ürettiği bir _yeni_ değer ile ayarlayın. Arka planda, bu genellikle sağlar ve böylece verilerin uygun gösterimi sonucunda verilebilir verimli bir şekilde bir değer izlemek için farklı veri yapısı tarafından gerçekleştirilir.

Bu şey yeni bir sürümü oluşturursa gibi bir şey değiştirir herhangi bir işlem davranmaya zorlar gibi bu stil, değerleri ve veri yapıları ile çalışma önemlidir. Bu eşitlik ve comparability gibi şeyleri programlarınızda tutarlı olmasını sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Sonraki bölümde işlevsel programlamaya kullanabileceğiniz farklı yolları keşfetmeye işlevleri, kapsamlı olarak ele alınacaktır.

[Birinci sınıf işlevler](first-class-functions.md) işlevleri çeşitli bağlamlarda bunları kullanabileceğinizi gösteren derin bir şekilde, keşfediyor.

## <a name="further-reading"></a>Daha fazla bilgi

[İşlevsel olarak düşünmek](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) serisi, işlevsel programlama ile ilgili bilgi edinmek için başka bir harika kaynak F#. Pragmatik ve kolay okunur bir biçimde işlevsel programlamanın temellerini kapsayan kullanarak F# kavramları göstermek için özellikleri.