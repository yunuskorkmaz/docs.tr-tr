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
# <a name="nullable-value-types"></a><span data-ttu-id="e2437-103">Boş değer atanabilen değer türleri</span><span class="sxs-lookup"><span data-stu-id="e2437-103">Nullable value types</span></span>

<span data-ttu-id="e2437-104">_Null yapılabilir bir değer türü_ `Nullable<'T>` , aynı zamanda olabilecek herhangi bir [Yapı](structures.md) türünü temsil eder `null` .</span><span class="sxs-lookup"><span data-stu-id="e2437-104">A _nullable value type_ `Nullable<'T>` represents any [struct](structures.md) type that could also be `null`.</span></span> <span data-ttu-id="e2437-105">Bu tür türleri, bir verimlilik açısından bir değere sahip tamsayılar gibi, bu tür türleri temsil eden kitaplıklar ve bileşenlerle etkileşim kurarken yararlı olur `null` .</span><span class="sxs-lookup"><span data-stu-id="e2437-105">This is helpful when interacting with libraries and components that may choose to represent these kinds of types, like integers, with a `null` value for efficiency reasons.</span></span> <span data-ttu-id="e2437-106">Bu yapıyı yedekleyen temel tür <xref:System.Nullable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e2437-106">The underlying type that backs this construct is <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2437-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2437-107">Syntax</span></span>

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a><span data-ttu-id="e2437-108">Değer ile bildirme ve atama</span><span class="sxs-lookup"><span data-stu-id="e2437-108">Declare and assign with values</span></span>

<span data-ttu-id="e2437-109">Null yapılabilir bir değer türü bildirmek tıpkı F # içinde sarmalayıcı benzeri tür bildirmek gibidir:</span><span class="sxs-lookup"><span data-stu-id="e2437-109">Declaring a nullable value type is just like declaring any wrapper-like type in F#:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

<span data-ttu-id="e2437-110">Ayrıca genel tür parametresini de ve tür çıkarımı çözümlemek için izin verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2437-110">You can also elide the generic type parameter and allow type inference to resolve it:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

<span data-ttu-id="e2437-111">Null olabilen bir değer türüne atamak için ayrıca açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2437-111">To assign to a nullable value type, you'll need to also be explicit.</span></span> <span data-ttu-id="e2437-112">F # tanımlı Nullable değer türleri için örtük dönüştürme yok:</span><span class="sxs-lookup"><span data-stu-id="e2437-112">There is no implicit conversion for F#-defined nullable value types:</span></span>

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a><span data-ttu-id="e2437-113">Null ata</span><span class="sxs-lookup"><span data-stu-id="e2437-113">Assign null</span></span>

<span data-ttu-id="e2437-114">`null`Null yapılabilen bir değer türüne doğrudan atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e2437-114">You cannot directly assign `null` to a nullable value type.</span></span> <span data-ttu-id="e2437-115">`Nullable()`Bunun yerine şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e2437-115">Use `Nullable()` instead:</span></span>

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

<span data-ttu-id="e2437-116">Bunun nedeni, `Nullable<'T>` `null` uygun bir değer değil.</span><span class="sxs-lookup"><span data-stu-id="e2437-116">This is because `Nullable<'T>` does not have `null` as a proper value.</span></span>

## <a name="pass-and-assign-to-members"></a><span data-ttu-id="e2437-117">Üyelere geçir ve ata</span><span class="sxs-lookup"><span data-stu-id="e2437-117">Pass and assign to members</span></span>

<span data-ttu-id="e2437-118">Üyeler ve F # değerleriyle çalışma arasındaki önemli bir fark, üye ile çalışırken, null olabilen değer türlerinin örtük olarak çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="e2437-118">A key difference between working with members and F# values is that nullable value types can be implicitly inferred when you're working with members.</span></span> <span data-ttu-id="e2437-119">Giriş olarak null olabilen bir değer türü alan aşağıdaki yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e2437-119">Consider the following method that takes a nullable value type as input:</span></span>

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

<span data-ttu-id="e2437-120">Önceki örnekte yöntemine geçiş yapabilirsiniz `12` `M` .</span><span class="sxs-lookup"><span data-stu-id="e2437-120">In the previous example, you can pass `12` to the method `M`.</span></span> <span data-ttu-id="e2437-121">Auto özelliğine de atayabilirsiniz `12` `NVT` .</span><span class="sxs-lookup"><span data-stu-id="e2437-121">You can also assign `12` to the auto property `NVT`.</span></span> <span data-ttu-id="e2437-122">Giriş, null yapılabilir bir değer türü olarak oluşturulabiliyorsanız ve hedef türle eşleşiyorsa, F # derleyicisi dolaylı olarak bu çağrıları veya atamaları dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e2437-122">If the input can be constructed as a nullable value type and it matches the target type, the F# compiler will implicitly convert such calls or assignments.</span></span>

## <a name="examine-a-nullable-value-type-instance"></a><span data-ttu-id="e2437-123">Null yapılabilir bir değer türü örneği inceleyin</span><span class="sxs-lookup"><span data-stu-id="e2437-123">Examine a nullable value type instance</span></span>

<span data-ttu-id="e2437-124">Olası bir değeri temsil etmek için genelleştirilmiş bir yapı olan [seçeneklerin](options.md)aksine, null olabilen değer türleri, model eşleştirme ile kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e2437-124">Unlike [Options](options.md), which are a generalized construct for representing a possible value, nullable value types are not used with pattern matching.</span></span> <span data-ttu-id="e2437-125">Bunun yerine, bir [`if`](conditional-expressions-if-then-else.md) ifade kullanıp özelliği kontrol etmeniz gerekir `HasValue` .</span><span class="sxs-lookup"><span data-stu-id="e2437-125">Instead, you need to use an [`if`](conditional-expressions-if-then-else.md) expression and check the `HasValue` property.</span></span>

<span data-ttu-id="e2437-126">Temel alınan değeri almak için, bu `Value` özelliği bir denetim sonrasında kullanın `HasValue` , örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2437-126">To get the underlying value, use the `Value` property after a `HasValue` check, like so:</span></span>

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a><span data-ttu-id="e2437-127">Null yapılabilir işleçler</span><span class="sxs-lookup"><span data-stu-id="e2437-127">Nullable operators</span></span>

<span data-ttu-id="e2437-128">Aritmetik veya karşılaştırma gibi Nullable değer türlerindeki işlemler, [null yapılabilir işleçlerin](symbol-and-operator-reference/nullable-operators.md)kullanımını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e2437-128">Operations on nullable value types, such as arithmetic or comparison, can require the use of [nullable operators](symbol-and-operator-reference/nullable-operators.md).</span></span>

<span data-ttu-id="e2437-129">Ad alanından, dönüştürme işleçlerini kullanarak bir null yapılabilir değer türünden diğerine dönüştürebilirsiniz `FSharp.Linq` :</span><span class="sxs-lookup"><span data-stu-id="e2437-129">You can convert from one nullable value type to another using conversion operators from the `FSharp.Linq` namespace:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

<span data-ttu-id="e2437-130">Temel bir türe dönüştürmek için uygun null atanamaz bir işleç de kullanabilirsiniz. değer yoksa özel bir duruma karşı riskmek için:</span><span class="sxs-lookup"><span data-stu-id="e2437-130">You can also use an appropriate non-nullable operator to convert to a primitive type, risking an exception if it has no value:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

<span data-ttu-id="e2437-131">Ayrıca, denetim için kısa bir süre olarak null yapılabilir işleçler kullanabilirsiniz `HasValue` `Value` :</span><span class="sxs-lookup"><span data-stu-id="e2437-131">You can also use nullable operators as a short-hand for checking `HasValue` and `Value`:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

<span data-ttu-id="e2437-132">`?>`Karşılaştırma, sol taraftaki boş değer atanabilir olup olmadığını denetler ve yalnızca bir değere sahipse başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e2437-132">The `?>` comparison checks if the left-hand side is nullable and only succeeds if it has a value.</span></span> <span data-ttu-id="e2437-133">Bu, izleyen satıra eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e2437-133">It is equivalent to the line that follows it.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2437-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2437-134">See also</span></span>

- [<span data-ttu-id="e2437-135">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e2437-135">Structures</span></span>](structures.md)
- [<span data-ttu-id="e2437-136">F # seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e2437-136">F# Options</span></span>](options.md)
