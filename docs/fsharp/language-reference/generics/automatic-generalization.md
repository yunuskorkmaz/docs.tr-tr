---
title: Otomatik Genelleştirme
description: Mümkün olduğunda F# birden çok tür ile çalışacak şekilde işlevlerin bağımsız değişkenlerini ve türlerini otomatik olarak genelleştirir.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630632"
---
# <a name="automatic-generalization"></a><span data-ttu-id="9c096-103">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="9c096-103">Automatic Generalization</span></span>

<span data-ttu-id="9c096-104">F#işlev ve ifade türlerini değerlendirmek için tür çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c096-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="9c096-105">Bu konu, bağımsız F# değişkenleri ve işlev türlerini otomatik olarak genelleştirerek, bu mümkün olduğunda birden çok tür ile çalışabilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9c096-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="9c096-106">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="9c096-106">Automatic Generalization</span></span>

<span data-ttu-id="9c096-107">F# Derleyici, bir işlevde tür çıkarımı gerçekleştirdiğinde, belirli bir parametrenin genel olup olmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="9c096-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="9c096-108">Derleyici her parametreyi inceler ve işlevin belirli bir parametre türüne bağımlılığı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9c096-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="9c096-109">Değilse, tür genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="9c096-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="9c096-110">Aşağıdaki kod örneği, derleyicinin genel olmasını sağlayan bir işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c096-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="9c096-111">Türü olarak algılanır `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="9c096-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="9c096-112">Türü, aynı bilinmeyen türden iki bağımsız değişken alan ve aynı türde bir değer döndüren bir işlev olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c096-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="9c096-113">Önceki işlevin genel olma nedenlerinden biri, büyüktür işlecinin (`>`) kendine genel olmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9c096-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="9c096-114">Büyüktür işleci imzaya `'a -> 'a -> bool`sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9c096-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="9c096-115">Tüm işleçler geneldir ve bir işlevdeki kod bir parametre türünü genel olmayan bir işlev veya işleçle birlikte kullanıyorsa, bu parametre türü genelleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9c096-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="9c096-116">Genel olduğundan, aşağıdaki örneklerde gösterildiği gibi,, vb. gibi `int`türlerle `float`kullanılabilir. `max`</span><span class="sxs-lookup"><span data-stu-id="9c096-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="9c096-117">Ancak, iki bağımsız değişken aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c096-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="9c096-118">İmza `'a -> 'a -> 'a`, değildir `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="9c096-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="9c096-119">Bu nedenle, türler eşleşmediğinden aşağıdaki kod bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c096-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="9c096-120">İşlevi `max` , büyüktür işlecini destekleyen her türlü tür ile de çalışır.</span><span class="sxs-lookup"><span data-stu-id="9c096-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="9c096-121">Bu nedenle, aşağıdaki kodda gösterildiği gibi bir dize üzerinde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c096-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="9c096-122">Değer kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="9c096-122">Value Restriction</span></span>

<span data-ttu-id="9c096-123">Derleyici, yalnızca açık bağımsız değişkenlere ve basit sabit değerlere sahip olan tüm işlev tanımlarında otomatik Genelleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9c096-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="9c096-124">Bu, belirli bir tür olarak sınırlı olmayan, ancak genelleştirilebilir bir kod derlemeye çalıştığınızda derleyicinin bir hata verdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9c096-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="9c096-125">Bu sorun için hata iletisi *değer kısıtlaması*olarak değerler için otomatik Genelleştirme üzerinde bu kısıtlamayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="9c096-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="9c096-126">Genellikle, değer kısıtlaması hatası, bir yapının genel olmasını istediğinizde, derleyicinin Bunu genelleştirmek için yeterli bilgiye sahip olması veya genel olmayan bir yapı içinde yeterli tür bilgilerini yanlışlıkla atlarsanız meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="9c096-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="9c096-127">Değer kısıtlama hatasına çözüm, tür çıkarımı sorununu daha kesin bir şekilde kısıtlamak için aşağıdaki yollarla daha açık bilgi sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="9c096-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="9c096-128">Bir değere veya parametreye açık bir tür ek açıklaması ekleyerek bir türü genel olmayan olacak şekilde kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="9c096-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="9c096-129">Sorun, işlev bileşimi veya eksik curried işlev bağımsız değişkenleri gibi genel bir işlev tanımlamak için genelleştirilsel olmayan bir yapı kullanıyorsa, işlevi sıradan bir işlev tanımı olarak yeniden yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="9c096-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="9c096-130">Sorun genelleştirilemeyecek kadar karmaşık bir ifadesiyse, fazladan, kullanılmamış bir parametre ekleyerek onu bir işlev haline getirin.</span><span class="sxs-lookup"><span data-stu-id="9c096-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="9c096-131">Açık genel tür parametreleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c096-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="9c096-132">Bu seçenek nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c096-132">This option is rarely used.</span></span>

- <span data-ttu-id="9c096-133">Aşağıdaki kod örnekleri, bu senaryoların her birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c096-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="9c096-134">Durum 1: İfade çok karmaşık.</span><span class="sxs-lookup"><span data-stu-id="9c096-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="9c096-135">Bu örnekte, listenin `counter` olması `int option ref`amaçlanmıştır, ancak basit bir sabit değer olarak tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="9c096-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="9c096-136">Durum 2: Genel bir işlev tanımlamak için genelleştirtirilebilir olmayan bir yapı kullanma.</span><span class="sxs-lookup"><span data-stu-id="9c096-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="9c096-137">Bu örnekte, işlev bağımsız değişkenlerinin kısmi bir uygulaması içerdiğinden, yapı genelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9c096-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="9c096-138">Durum 3: Fazladan, kullanılmamış bir parametre ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="9c096-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="9c096-139">Bu ifade Genelleştirme için yeterince basit olmadığından, derleyici değer kısıtlaması hatası verir.</span><span class="sxs-lookup"><span data-stu-id="9c096-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="9c096-140">Durum 4: Tür parametreleri ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="9c096-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="9c096-141">Son durumda, değer bir tür işlevi olur ve örneğin aşağıdaki gibi birçok farklı türde değer oluşturmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9c096-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="9c096-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c096-142">See also</span></span>

- [<span data-ttu-id="9c096-143">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="9c096-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="9c096-144">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="9c096-144">Generics</span></span>](index.md)
- [<span data-ttu-id="9c096-145">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="9c096-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="9c096-146">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="9c096-146">Constraints</span></span>](constraints.md)
