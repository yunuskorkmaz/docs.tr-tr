---
title: 'F # İşlevsel Programlamaya Giriş'
description: "' De F#fonksiyonel programlama temellerini öğrenin."
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424707"
---
# <a name="introduction-to-functional-programming-in-f"></a>F\# Işlevsel programlamaya giriş

Fonksiyonel programlama, işlevlerin ve değişmez verilerin kullanımını vurgulayarak programlama stilidir. Türü belirlenmiş fonksiyonel programlama, fonksiyonel programlamanın ile F#gibi statik türlerle birleştirilme biçimdedir. Genel olarak, aşağıdaki kavramlar işlevsel programlamada vurgulandı:

* Kullandığınız birincil yapılar olarak işlevler
* Deyimler yerine ifadeler
* Değişkenlerin üzerinde sabit değerler
* Kesinlik temelli programlama üzerinden bildirim temelli programlama

Bu serinin tamamında, kullanarak F#işlevsel programlama içindeki kavramları ve desenleri keşfedebilirsiniz. Bu şekilde, biraz F# daha öğrenirsiniz.

## <a name="terminology"></a>Terminoloji

Diğer programlama paradigmalarına gibi işlevsel programlama, sonunda öğreneceği bir sözlük ile birlikte gelir. Aşağıda, her zaman bir süre sonra göreceğiniz bazı yaygın terimler verilmiştir:

* **Function** -bir işlev, bir giriş verildiğinde çıkış oluşturacak bir yapıdır. Daha resmi bir öğeyi bir kümeden başka bir küme ile _eşleştirir_ . Bu formalroni, özellikle veri koleksiyonlarında çalışan işlevler kullanılırken birçok şekilde somut yükseltilmemiş. Fonksiyonel programlamada en temel (ve önemli) kavramdır.
* **İfade** -bir ifade, bir değer üreten bir kod yapısıdır. ' F#De, bu değerin bağlanması veya açıkça yoksayılması gerekir. Bir ifade, bir işlev çağrısıyla daha fazla değiştirilebilir.
* Bu, bir işlevin özelliği olan dönüş değeri aynı bağımsız değişkenler için her zaman aynı ve değerlendirmesinin bir yan etkisi yoktur. Saf işlev tamamen bağımsız değişkenlerine bağlıdır.
* **Bilgi saydamlığı** -başvurusal saydamlık, bir programın davranışını etkilemeden kendi çıktılarıyla değiştirilmeleri için ifadelerin bir özelliğidir.
* **Imlebilirlik kullanılabilirliği** -değişiklik, bir değerin yerinde değiştirilememe anlamına gelir. Bu, yerinde değişiklik olabilen değişkenlerle aynıdır.

## <a name="examples"></a>Örnekler

Aşağıdaki örneklerde bu temel kavramlar gösterilmektedir.

### <a name="functions"></a>İşlevler

Fonksiyonel programlamada en yaygın ve temel yapı işlevdir. İşte 1 tamsayı ekleyen basit bir işlev:

```fsharp
let addOne x = x + 1
```

Tür imzası aşağıdaki gibidir:

```fsharp
val addOne: x:int -> int
```

İmza, "`addOne` `x` adlı bir `int` kabul ettiğinde ve bir `int`oluşturacak şekilde okunabilir. Daha resmi olmayan `addOne`, tamsayıların kümesinden bir değeri tamsayılar kümesine _eşliyorlar_ . `->` belirteç bu eşlemeyi belirtir. İçinde F#, genellikle işlevinin ne yaptığını anladığını görmek için işlev imzasına bakabilirsiniz.

Bu nedenle imza neden önemlidir? Yazılan işlevsel programlamada, bir işlevin uygulanması genellikle gerçek tür imzasına göre daha az önemlidir! `addOne`, çalışma zamanında 1 değerini bir tamsayıya ekler. ancak bir program oluştururken, kabul ettiği ve bir `int` döndüren olgu, bu işlevi gerçekten nasıl kullanacağınızı bildirir. Ayrıca, bu işlevi doğru bir şekilde (tür imzasına göre) kullandığınızda, herhangi bir sorunu tanılamak yalnızca `addOne` işlevinin gövdesinde yapılabilir. Bu, yazılı işlevsel programlamanın arkasındaki aksaklýmdır.

### <a name="expressions"></a>İfadeler

İfadeler bir değeri değerlendiren yapılardır. Bir eylem gerçekleştiren deyimlerin aksine, ifadeler bir değeri geri veren bir eylem gerçekleştirmeye düşünülebilir. İfadeler, işlevsel programlamada deyimler için neredeyse her zaman kullanılır.

Önceki işlevi `addOne`düşünün. `addOne` gövdesi bir ifadedir:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Bu ifadenin `addOne` işlevinin sonuç türünü tanımlayan sonucudur. Örneğin, bu işlevi oluşturan ifade `string`gibi farklı bir tür olacak şekilde değiştirilebilir:

```fsharp
let addOne x = x.ToString() + "1"
```

İşlevin imzası artık şu şekilde olur:

```fsharp
val addOne: x:'a -> string
```

İçindeki F# herhangi bir tür üzerinde `ToString()` sahip olduğundan, `x` türü genel yapıldı ( [Otomatik Genelleştirme](../language-reference/generics/automatic-generalization.md)adı verilir) ve sonuç türü bir `string`.

İfadeler yalnızca işlevlerin gövdeleridir. Başka bir yerde kullandığınız bir değer üreten deyimleriniz olabilir. Yaygın bir tane `if`:

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

`if` ifadesi `result`adlı bir değer üretir. `result` tamamen yok saymayacağınızı ve `if` ifadesini `addOneIfOdd` işlevinin gövdesinde yapmayı unutmayın. İfadeler hakkında hatırlamanız gereken önemli şey bir değer üretmeleridir.

Döndürülecek bir şey olmadığında kullanılan `unit`özel bir tür vardır. Örneğin, şu basit işlevi göz önünde bulundurun:

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

İmza şöyle görünür:

```fsharp
val printString: str:string -> unit
```

`unit` türü, döndürülmekte olan gerçek değer olmadığını gösterir. Bu, işin sonucu olarak döndürülecek bir değer olmamasına rağmen "iş yap" gerektiren bir yordamınız olduğunda faydalıdır.

Bu, eşdeğer `if` yapısının bir ifade olduğu ve değer oluşturmanın genellikle değişkenlerle birlikte kullanıldığı, kesin programlamaya yönelik keskin karşıtlığa sahiptir. Örneğin, ' de C#, kod şöyle yazılmış olabilir:

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

Bu, ve diğer C C# stili dillerin, ifade tabanlı koşullu programlamaya izin veren [Üçlü ifadeyi](../../csharp/language-reference/operators/conditional-operator.md)desteklediğini belirtmekte de dikkat edin.

Fonksiyonel programlamada, deyimleri olan değerleri bulunmamalıdır olarak ifade edilir. Bazı işlevsel diller deyimleri ve mutasyonlarını desteklese de, bu kavramların işlevsel programlamada kullanılması yaygın değildir.

### <a name="pure-functions"></a>Saf işlevler

Daha önce belirtildiği gibi, saf işlevler şu şekilde çalışır:

* Aynı giriş için her zaman aynı değere değerlendirin.
* Yan etkileri yoktur.

Matematik işlevlerini bu bağlamda düşünmek yararlıdır. Matematik olarak işlevler yalnızca bağımsız değişkenlerine bağımlıdır ve herhangi bir yan etkisi yoktur. `f(x) = x + 1`matematik işlevinde, `f(x)` değeri yalnızca `x`değerine bağlıdır. İşlevsel programlamada saf işlevler aynı şekilde yapılır.

Saf bir işlev yazarken, işlev yalnızca bağımsız değişkenlerine bağlı olmalıdır ve yan etkisi olan herhangi bir eylem gerçekleştirmez.

Genel, kesilebilir duruma bağlı olduğundan, saf olmayan bir işleve bir örnek aşağıda verilmiştir:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue` işlevi, `value` herhangi bir zamanda 1 ' den farklı bir değere sahip olacak şekilde değiştirilebildiğinden, açıkça kesin bir şekilde belirlenir. Genel değere bağlı olarak bu düzenin işlevsel programlamada kaçınılmaz.

Bir yan etkisi gerçekleştirdiğinden, saf olmayan bir işlevin başka bir örneği aşağıda verilmiştir:

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

Bu işlev genel bir değere bağımlı olmasa da, `x` değerini programın çıktısına yazar. Bunu yaparken doğal olarak yanlış bir şey olmasa da, işlevin saf olmadığı anlamına gelir. Programınızın başka bir bölümü, çıkış arabelleği gibi programa ait bir şeye bağımlıysa, bu işlevi çağırmak programınızın diğer bölümünü etkileyebilir.

`printfn` deyimin kaldırılması işlevi saf hale getirir:

```fsharp
let addOneToValue x = x + 1
```

Bu işlev, `printfn` ifadesiyle önceki sürümden _daha iyi_ olmasa da, tüm bu işlevin bir değer döndürdiğinin garantisi vardır. Bu işlevi çağırmak, herhangi bir sayıda kez aynı sonucu üretir: yalnızca bir değer oluşturur. Öngörüler tarafından verilen öngörülebilirlik, birçok işlevsel programcı için çaba göstermesidir.

### <a name="immutability"></a>Değiştirilemezlik

Son olarak, yazılan fonksiyonel programlama için en temel kavramlardan biri imlebilirlik olarak belirlenir. ' F#De, tüm değerler varsayılan olarak sabittir. Diğer bir deyişle, bunları açıkça değişebilir olarak işaretlemediğiniz sürece bu, yerinde değiştirilemez.

Uygulamada, değişmez değerlerle çalışmak, programlama yaklaşımınızı "bir şeyi değiştirmem", "yeni bir değer üretmem gerekiyor" olarak değiştirdiğiniz anlamına gelir.

Örneğin, bir değere 1 eklemek, var olan bir değer üretilmeden yeni bir değer üretilmesinin anlamına gelir:

```fsharp
let value = 1
let secondValue = value + 1
```

' F#De, aşağıdaki kod `value` işlevini **mugöstermez** ; Bunun yerine, bir eşitlik denetimi gerçekleştirir:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Bazı işlevsel programlama dilleri hiç birini desteklemez. İçinde F#, desteklenir, ancak değerler için varsayılan davranış değildir.

Bu kavram, veri yapılarını daha da artırır. İşlevsel programlamada, kümeler (ve çok daha fazlası) gibi değişmez veri yapıları, başlangıçta bekleneceğiniz farklı bir uygulamaya sahiptir. Kavramsal olarak, bir küme için bir öğe eklemeye benzer şekilde küme değişmez; eklenen değere sahip _Yeni_ bir küme oluşturur. Bu, genellikle bir değeri etkin bir şekilde izlemeye izin veren farklı bir veri yapısı tarafından gerçekleştirilir. böylece, verilerin uygun gösterimi sonuç olarak verilebilir.

Değerler ve veri yapıları ile çalışmanın bu stili, bu işlemin yeni bir sürümünü oluşturuyor gibi bir şeyi değiştiren herhangi bir işlemi bildirmeye zorlarsa kritik öneme sahiptir. Bu, eşitlik ve karşılaştırıcı gibi öğelerin programlarınızda tutarlı olmasını sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Sonraki bölümde işlevleri kapsamlı olarak ele alınmaktadır ve bunları işlevsel programlamada kullanabileceğiniz farklı şekillerde bulabilirsiniz.

[Birinci sınıf işlevler](first-class-functions.md) , işlevleri çeşitli bağlamlarda nasıl kullanabileceğinizi gösteren daha derin bir şekilde araştırır.

## <a name="further-reading"></a>Daha fazla okuma

[Düşünce](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) işlevi serisi, ile F#işlevsel programlama hakkında bilgi edinmek için harika bir kaynaktır. Kavramları göstermek için özellikleri kullanarak F# , kolay ve kolay okunabilir bir şekilde işlevsel programlama temellerini ele alır.
