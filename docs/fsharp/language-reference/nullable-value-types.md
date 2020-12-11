---
title: Boş değer atanabilen değer türleri
description: 'Null olabilen değer türlerini nasıl kullanacağınızı, F # içinde de null olabilen değer türlerini temsil etmenin nasıl yapılacağını öğrenin.'
ms.date: 11/19/2020
ms.openlocfilehash: e28cbfc57c5631573f46ac36462517cf011e96d2
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009644"
---
# <a name="nullable-value-types"></a>Boş değer atanabilen değer türleri

_Null yapılabilir bir değer türü_ `Nullable<'T>` , aynı zamanda olabilecek herhangi bir [Yapı](structures.md) türünü temsil eder `null` . Bu tür türleri, bir verimlilik açısından bir değere sahip tamsayılar gibi, bu tür türleri temsil eden kitaplıklar ve bileşenlerle etkileşim kurarken yararlı olur `null` . Bu yapıyı yedekleyen temel tür <xref:System.Nullable%601?displayProperty=nameWithType> .

## <a name="syntax"></a>Syntax

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a>Değer ile bildirme ve atama

Null yapılabilir bir değer türü bildirmek tıpkı F # içinde sarmalayıcı benzeri tür bildirmek gibidir:

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

Ayrıca genel tür parametresini de ve tür çıkarımı çözümlemek için izin verebilirsiniz:

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

Null olabilen bir değer türüne atamak için ayrıca açık olması gerekir. F # tanımlı Nullable değer türleri için örtük dönüştürme yok:

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a>Null ata

`null`Null yapılabilen bir değer türüne doğrudan atayamazsınız. `Nullable()`Bunun yerine şunu kullanın:

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

Bunun nedeni, `Nullable<'T>` `null` uygun bir değer değil.

## <a name="pass-and-assign-to-members"></a>Üyelere geçir ve ata

Üyeler ve F # değerleriyle çalışma arasındaki önemli bir fark, üye ile çalışırken, null olabilen değer türlerinin örtük olarak çıkarsanamıyor. Giriş olarak null olabilen bir değer türü alan aşağıdaki yöntemi göz önünde bulundurun:

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

Önceki örnekte yöntemine geçiş yapabilirsiniz `12` `M` . Auto özelliğine de atayabilirsiniz `12` `NVT` . Giriş, null yapılabilir bir değer türü olarak oluşturulabiliyorsanız ve hedef türle eşleşiyorsa, F # derleyicisi dolaylı olarak bu çağrıları veya atamaları dönüştürür.

## <a name="examine-a-nullable-value-type-instance"></a>Null yapılabilir bir değer türü örneği inceleyin

Olası bir değeri temsil etmek için genelleştirilmiş bir yapı olan [seçeneklerin](options.md)aksine, null olabilen değer türleri, model eşleştirme ile kullanılmaz. Bunun yerine, bir [`if`](conditional-expressions-if-then-else.md) ifade kullanıp özelliği kontrol etmeniz gerekir `HasValue` .

Temel alınan değeri almak için, bu `Value` özelliği bir denetim sonrasında kullanın `HasValue` , örneğin:

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a>Null yapılabilir işleçler

Aritmetik veya karşılaştırma gibi Nullable değer türlerindeki işlemler, [null yapılabilir işleçlerin](symbol-and-operator-reference/nullable-operators.md)kullanımını gerektirebilir.

Ad alanından, dönüştürme işleçlerini kullanarak bir null yapılabilir değer türünden diğerine dönüştürebilirsiniz `FSharp.Linq` :

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

Temel bir türe dönüştürmek için uygun null atanamaz bir işleç de kullanabilirsiniz. değer yoksa özel bir duruma karşı riskmek için:

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

Ayrıca, denetim için kısa bir süre olarak null yapılabilir işleçler kullanabilirsiniz `HasValue` `Value` :

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

`?>`Karşılaştırma, sol taraftaki boş değer atanabilir olup olmadığını denetler ve yalnızca bir değere sahipse başarılı olur. Bu, izleyen satıra eşdeğerdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](structures.md)
- [F # seçenekleri](options.md)
