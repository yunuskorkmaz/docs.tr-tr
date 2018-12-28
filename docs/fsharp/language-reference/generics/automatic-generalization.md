---
title: Otomatik Genelleştirme
description: Bilgi nasıl F# bağımsız değişkenleri ve işlevleri bir türde birden çok tür mümkün olduğunda çalışmaları için otomatik olarak genelleştirir.
ms.date: 05/16/2016
ms.openlocfilehash: 15ecf8e6f07da19bb015fd028a7465ba8b837190
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611717"
---
# <a name="automatic-generalization"></a><span data-ttu-id="785ff-103">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="785ff-103">Automatic Generalization</span></span>

<span data-ttu-id="785ff-104">F#tür işlevleri ve ifadeleri türlerini değerlendirilecek çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="785ff-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="785ff-105">Bu konu açıklar nasıl F# işlevleri türünü ve bağımsız değişkenler mümkün olduğunda bunlar birden çok türleriyle çalışmak üzere otomatik olarak genelleştirir.</span><span class="sxs-lookup"><span data-stu-id="785ff-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="785ff-106">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="785ff-106">Automatic Generalization</span></span>

<span data-ttu-id="785ff-107">F# Derleyici bir işlevi üzerinde tür çıkarımı gerçekleştirdiğinde, verilen bir parametre genel olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="785ff-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="785ff-108">Derleyici, her parametreyi inceler ve işlev bu parametrenin türünü üzerinde bir bağımlılık olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="785ff-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="785ff-109">Kullanmıyorsa, türü genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="785ff-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="785ff-110">Aşağıdaki kod örneği, genel olarak derleyici çıkarsar bir işlev gösterir.</span><span class="sxs-lookup"><span data-stu-id="785ff-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="785ff-111">Tür çıkarımı yapılan olmasını `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="785ff-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="785ff-112">Türü, aynı bilinmeyen türde iki bağımsız değişkeni alır ve aynı türde bir değer döndüren bir işlev olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="785ff-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="785ff-113">Önceki işlevi olabilir nedenlerden biri dolayısıyla genel, büyük-işleci (`>`) kendisi geneldir.</span><span class="sxs-lookup"><span data-stu-id="785ff-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="785ff-114">Büyük-işleci imza olandan `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="785ff-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="785ff-115">Tüm işleçler geneldir ve bir işlevdeki kod ile birlikte bir genel olmayan işlev veya işleci bir parametre türü kullanıyorsa, bu parametre türü genelleştirilemediği.</span><span class="sxs-lookup"><span data-stu-id="785ff-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="785ff-116">Çünkü `max` olan genel, türleriyle gibi kullanılabilir `int`, `float`ve benzeri, aşağıdaki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="785ff-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="785ff-117">Ancak, iki bağımsız değişkenler aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="785ff-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="785ff-118">İmza `'a -> 'a -> 'a`değil `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="785ff-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="785ff-119">Bu nedenle, türleri eşleşmediğinden aşağıdaki kod bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="785ff-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="785ff-120">`max` İşlevi büyük destekleyen herhangi bir türü ile de çalışır-işleci.</span><span class="sxs-lookup"><span data-stu-id="785ff-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="785ff-121">Bu nedenle, ayrıca, bir dizesine, aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="785ff-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="785ff-122">Değer kısıtlama</span><span class="sxs-lookup"><span data-stu-id="785ff-122">Value Restriction</span></span>

<span data-ttu-id="785ff-123">Basit değişmez değerler ve açık bağımsız değişken içeren tam işlev tanımları, derleyici otomatik Genelleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="785ff-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="785ff-124">Başka bir deyişle, yeterince belirli bir tür olması zorunlu değildir, ancak aynı zamanda genelleştirilebilir değil, kodu derlemek denerseniz derleyici bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="785ff-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="785ff-125">Bu kısıtlama için değerler olarak otomatik Genelleştirme üzerinde bu sorun için hata iletisini başvurduğu *değer kısıtlaması*.</span><span class="sxs-lookup"><span data-stu-id="785ff-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="785ff-126">Genellikle, bir yapı genel olmasını istiyoruz, ancak derleyici bunu genelleştirmek için yeterli bilgiye sahip olduğunda veya bir jenerik olmayan yapısı yeterli tür bilgisi yanlışlıkla atladığınızda değer kısıtlama hatası gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="785ff-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="785ff-127">Değer kısıtlama hatası çözüme daha tam tür çıkarımı sorun aşağıdaki yollardan biriyle sınırlamak için daha net bilgi sağlamak için verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="785ff-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="785ff-128">Bir tür açık tür açıklamanın bir değer ya da parametre ekleyerek jenerik olmayan olacak şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="785ff-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="785ff-129">Sorun kullanıyorsa, genel bir işlev, işlev bileşimi veya önişlemcinin tanımlamak için bir nongeneralizable yapısı curried işlev bağımsız değişkenleri uygulanır, bir normal işlev tanımı işlevi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="785ff-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="785ff-130">Sorun genelleştirilmesini karmaşık bir ifade ise, ek, kullanılmayan bir parametre ekleyerek bir işleve olun.</span><span class="sxs-lookup"><span data-stu-id="785ff-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="785ff-131">Açık genel tür parametreleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="785ff-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="785ff-132">Bu seçeneği nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="785ff-132">This option is rarely used.</span></span>

- <span data-ttu-id="785ff-133">Aşağıdaki kod örnekleri, bu senaryoların her birini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="785ff-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="785ff-134">1. durum: Çok karmaşık bir ifade.</span><span class="sxs-lookup"><span data-stu-id="785ff-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="785ff-135">Bu örnekte, listenin `counter` olması amaçlanmıştır `int option ref`, ancak basit bir değişmez değer tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="785ff-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="785ff-136">2. durum: Genel bir işlev tanımlamak için bir nongeneralizable yapısı kullanma.</span><span class="sxs-lookup"><span data-stu-id="785ff-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="785ff-137">İşlev bağımsız değişkenlerinin kısmi uygulaması içerdiğinden bu örnekte, nongeneralizable yapıdır.</span><span class="sxs-lookup"><span data-stu-id="785ff-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="785ff-138">3. durum: Ek, kullanılmayan bir parametre ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="785ff-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="785ff-139">Bu ifade için genelleştirme kadar basit olmadığı için derleyici değeri kısıtlama hatası verir.</span><span class="sxs-lookup"><span data-stu-id="785ff-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="785ff-140">4. durum: Tür parametreleri ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="785ff-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="785ff-141">En son durumda değer gibi birçok farklı türlerde değerler örnek oluşturmak için kullanılabilir bir türü işlevi olur:</span><span class="sxs-lookup"><span data-stu-id="785ff-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="785ff-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="785ff-142">See also</span></span>

- [<span data-ttu-id="785ff-143">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="785ff-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="785ff-144">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="785ff-144">Generics</span></span>](index.md)
- [<span data-ttu-id="785ff-145">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="785ff-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="785ff-146">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="785ff-146">Constraints</span></span>](constraints.md)