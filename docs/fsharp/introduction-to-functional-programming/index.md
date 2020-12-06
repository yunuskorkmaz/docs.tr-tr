---
title: 'F # İşlevsel Programlamaya Giriş'
description: "F # ' da işlevsel programlama temellerini öğrenin."
ms.date: 10/29/2018
ms.openlocfilehash: fc2aebe80de16b92942c3557c0e03c198883dde1
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740334"
---
# <a name="introduction-to-functional-programming-in-f"></a>F 'de Işlevsel programlamaya giriş\#

Fonksiyonel programlama, işlevlerin ve değişmez verilerin kullanımını vurgulayarak programlama stilidir. Yazılan fonksiyonel programlama, fonksiyonel programlamanın, F # gibi statik türlerle birleştirilme biçimdedir. Genel olarak, aşağıdaki kavramlar işlevsel programlamada vurgulandı:

* Kullandığınız birincil yapılar olarak işlevler
* Deyimler yerine ifadeler
* Değişkenlerin üzerinde sabit değerler
* Kesinlik temelli programlama üzerinden bildirim temelli programlama

Bu serinin tamamında, F # kullanarak işlevsel programlamada kavramları ve desenleri keşfedebilirsiniz. Bu şekilde, bazı F # hakkında bilgi edineceksiniz.

## <a name="terminology"></a>Terminoloji

Diğer programlama paradigmalarına gibi işlevsel programlama, sonunda öğreneceği bir sözlük ile birlikte gelir. Aşağıda, her zaman bir süre sonra göreceğiniz bazı yaygın terimler verilmiştir:

* **Function** -bir işlev, bir giriş verildiğinde çıkış oluşturacak bir yapıdır. Daha resmi bir öğeyi bir kümeden başka bir küme ile _eşleştirir_ . Bu formalroni, özellikle veri koleksiyonlarında çalışan işlevler kullanılırken birçok şekilde somut yükseltilmemiş. Fonksiyonel programlamada en temel (ve önemli) kavramdır.
* **İfade** -bir ifade, bir değer üreten bir kod yapısıdır. F # ' da, bu değerin bağlanması veya açıkça yoksayılması gerekir. Bir ifade, bir işlev çağrısıyla daha fazla değiştirilebilir.
* **Purity** Bu, bir işlevin özelliği olan dönüş değeri aynı bağımsız değişkenler için her zaman aynı ve değerlendirmesinin bir yan etkisi yoktur. Saf işlev tamamen bağımsız değişkenlerine bağlıdır.
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

İmza, " `addOne` adlandırılmış bir adı kabul eder `int` `x` ve bir" oluşturur "olarak okunabilir `int` . Daha resmi olarak, `addOne` tamsayıların kümesinden bir değeri tamsayılar kümesine _eşliyorlar_ . `->`Belirteç bu eşlemeyi belirtir. F # ' da genellikle işlev imzasına bakarak ne yapacaklarınız hakkında bir fikir edinebilirsiniz.

Bu nedenle imza neden önemlidir? Yazılan işlevsel programlamada, bir işlevin uygulanması genellikle gerçek tür imzasına göre daha az önemlidir! `addOne`1 değerini bir tamsayıya ekleyen olgu, çalışma zamanında ilgi çekici, ancak bir program oluştururken, kabul ettiği ve döndüren olgu, `int` Bu işlevi gerçekten nasıl kullanacağınızı bildirir. Ayrıca, bu işlevi doğru bir şekilde (tür imzasına göre) kullandığınızda, herhangi bir sorunu tanılamak yalnızca işlevin gövdesinde yapılabilir `addOne` . Bu, yazılı işlevsel programlamanın arkasındaki aksaklýmdır.

### <a name="expressions"></a>İfadeler

İfadeler bir değeri değerlendiren yapılardır. Bir eylem gerçekleştiren deyimlerin aksine, ifadeler bir değeri geri veren bir eylem gerçekleştirmeye düşünülebilir. İfadeler, işlevsel programlamada deyimler için neredeyse her zaman kullanılır.

Önceki işlevi göz önünde bulundurun `addOne` . Gövdesi `addOne` bir ifadedir:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

İşlevin sonuç türünü tanımlayan bu ifadenin sonucudur `addOne` . Örneğin, bu işlevi oluşturan ifade, gibi farklı bir tür olacak şekilde değiştirilebilir `string` :

```fsharp
let addOne x = x.ToString() + "1"
```

İşlevin imzası artık şu şekilde olur:

```fsharp
val addOne: x:'a -> string
```

F # ' deki herhangi bir tür `ToString()` üzerinde çağrılabilecek olduğundan, türü `x` genel yapıldı ( [Otomatik Genelleştirme](../language-reference/generics/automatic-generalization.md)adı verilir) ve sonuç türü bir olur `string` .

İfadeler yalnızca işlevlerin gövdeleridir. Başka bir yerde kullandığınız bir değer üreten deyimleriniz olabilir. Yaygın bir tane şunlardır `if` :

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

`if`İfade adlı bir değer oluşturur `result` . Tamamen yok saymayacağınızı ve `result` `if` ifadeyi işlevin gövdesinde yapmayı unutmayın `addOneIfOdd` . İfadeler hakkında hatırlamanız gereken önemli şey bir değer üretmeleridir.

Döndürülecek bir şey olmadığında kullanılan özel bir tür vardır `unit` . Örneğin, şu basit işlevi göz önünde bulundurun:

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

İmza şöyle görünür:

```fsharp
val printString: str:string -> unit
```

`unit`Türü, döndürülmekte olan gerçek değer olmadığını gösterir. Bu, işin sonucu olarak döndürülecek bir değer olmamasına rağmen "iş yap" gerektiren bir yordamınız olduğunda faydalıdır.

Bu, eşdeğer `if` yapının bir ifade olduğu ve değer oluşturmanın genellikle değişkenlerle birlikte yapılması gereken, kesin programlamaya yönelik keskin karşıtlığa sahiptir. Örneğin, C# ' de kod şöyle yazılmış olabilir:

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

C# ve diğer C stili dillerin, ifade tabanlı koşullu programlamaya izin veren [Üçlü ifadeyi](../../csharp/language-reference/operators/conditional-operator.md)desteklediğini belirtmekte de dikkat edin.

Fonksiyonel programlamada, deyimleri olan değerleri bulunmamalıdır olarak ifade edilir. Bazı işlevsel diller deyimleri ve mutasyonlarını desteklese de, bu kavramların işlevsel programlamada kullanılması yaygın değildir.

### <a name="pure-functions"></a>Saf işlevler

Daha önce belirtildiği gibi, saf işlevler şu şekilde çalışır:

* Aynı giriş için her zaman aynı değere değerlendirin.
* Yan etkileri yoktur.

Matematik işlevlerini bu bağlamda düşünmek yararlıdır. Matematik olarak işlevler yalnızca bağımsız değişkenlerine bağımlıdır ve herhangi bir yan etkisi yoktur. Matematik işlevinde `f(x) = x + 1` , değeri `f(x)` yalnızca değerine göre değişir `x` . İşlevsel programlamada saf işlevler aynı şekilde yapılır.

Saf bir işlev yazarken, işlev yalnızca bağımsız değişkenlerine bağlı olmalıdır ve yan etkisi olan herhangi bir eylem gerçekleştirmez.

Genel, kesilebilir duruma bağlı olduğundan, saf olmayan bir işleve bir örnek aşağıda verilmiştir:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue`İşlev, `value` herhangi bir zamanda 1 ' den farklı bir değere sahip olacak şekilde değiştirilebildiğinden, açıkça kesin bir şekilde belirlenir. Genel değere bağlı olarak bu düzenin işlevsel programlamada kaçınılmaz.

Bir yan etkisi gerçekleştirdiğinden, saf olmayan bir işlevin başka bir örneği aşağıda verilmiştir:

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

Bu işlev genel bir değere bağımlı olmasa da, değerini `x` programın çıktısına yazar. Bunu yaparken doğal olarak yanlış bir şey olmasa da, işlevin saf olmadığı anlamına gelir. Programınızın başka bir bölümü, çıkış arabelleği gibi programa ait bir şeye bağımlıysa, bu işlevi çağırmak programınızın diğer bölümünü etkileyebilir.

Deyimin kaldırılması `printfn` işlevi saf hale getirir:

```fsharp
let addOneToValue x = x + 1
```

Bu işlev doğal olarak önceki sürümden _daha iyi_ olmasa da `printfn` , tüm bu işlevin bir değer döndürdiğinin garantisi vardır. Bu işlevi çağırmak, herhangi bir sayıda kez aynı sonucu üretir: yalnızca bir değer oluşturur. Öngörüler tarafından verilen öngörülebilirlik, birçok işlevsel programcı için çaba göstermesidir.

### <a name="immutability"></a>Değiştirilemezlik

Son olarak, yazılan fonksiyonel programlama için en temel kavramlardan biri imlebilirlik olarak belirlenir. F # ' da, tüm değerler varsayılan olarak sabittir. Diğer bir deyişle, bunları açıkça değişebilir olarak işaretlemediğiniz sürece bu, yerinde değiştirilemez.

Uygulamada, değişmez değerlerle çalışmak, programlama yaklaşımınızı "bir şeyi değiştirmem", "yeni bir değer üretmem gerekiyor" olarak değiştirdiğiniz anlamına gelir.

Örneğin, bir değere 1 eklemek, var olan bir değer üretilmeden yeni bir değer üretilmesinin anlamına gelir:

```fsharp
let value = 1
let secondValue = value + 1
```

F # ' da, aşağıdaki kod işlevi **göstermez** `value` ; bunun yerine bir eşitlik denetimi gerçekleştirir:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Bazı işlevsel programlama dilleri hiç birini desteklemez. F # içinde desteklenir, ancak değerler için varsayılan davranış değildir.

Bu kavram, veri yapılarını daha da artırır. İşlevsel programlamada, kümeler (ve çok daha fazlası) gibi değişmez veri yapıları, başlangıçta bekleneceğiniz farklı bir uygulamaya sahiptir. Kavramsal olarak, bir küme için bir öğe eklemeye benzer şekilde küme değişmez; eklenen değere sahip _Yeni_ bir küme oluşturur. Bu, genellikle bir değeri etkin bir şekilde izlemeye izin veren farklı bir veri yapısı tarafından gerçekleştirilir. böylece, verilerin uygun gösterimi sonuç olarak verilebilir.

Değerler ve veri yapıları ile çalışmanın bu stili, bu işlemin yeni bir sürümünü oluşturuyor gibi bir şeyi değiştiren herhangi bir işlemi bildirmeye zorlarsa kritik öneme sahiptir. Bu, eşitlik ve karşılaştırıcı gibi öğelerin programlarınızda tutarlı olmasını sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Sonraki bölümde işlevleri kapsamlı olarak ele alınmaktadır ve bunları işlevsel programlamada kullanabileceğiniz farklı şekillerde bulabilirsiniz.

[Birinci sınıf işlevler](first-class-functions.md) , işlevleri çeşitli bağlamlarda nasıl kullanabileceğinizi gösteren daha derin bir şekilde araştırır.

## <a name="further-reading"></a>Daha fazla bilgi

[Düşünce](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) işlevi serisi, F # ile işlevsel programlama hakkında bilgi edinmek için harika bir kaynaktır. Kavramları göstermek için F # özelliklerini kullanarak, işlevsel programlama temellerini kolay ve kolay okunabilir bir şekilde ele alır.
