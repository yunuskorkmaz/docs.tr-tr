---
title: Otomatik Genelleştirme (F#)
description: 'Böylece birden çok tür mümkün olduğunda çalıştıkları nasıl F # otomatik olarak işlevleri türünü ve bağımsız değişkenler genelleştirir öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9b599fd9fe1220b41987bc14a420ed5740aa05f5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="automatic-generalization"></a><span data-ttu-id="51d35-103">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="51d35-103">Automatic Generalization</span></span>

<span data-ttu-id="51d35-104">F # tür çıkarımı türlerini işlevleri ve ifadeler değerlendirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51d35-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="51d35-105">Bu konu, mümkün olduğunda bunlar birden çok tür çalışmak üzere nasıl F # otomatik olarak işlevleri türünü ve bağımsız değişkenler genelleştirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="51d35-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="51d35-106">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="51d35-106">Automatic Generalization</span></span>
<span data-ttu-id="51d35-107">Tür çıkarımı işlevi üzerinde gerçekleştirdiğinde, F # derleyici, verilen bir parametrenin genel olup olamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="51d35-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="51d35-108">Derleyici her bir parametreyi inceler ve işlevi bu parametrenin belirli türüne bir bağımlılığa sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="51d35-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="51d35-109">Yoksa, türü genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="51d35-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="51d35-110">Aşağıdaki kod örneğinde genel olarak derleyici oluşturur bir işlev gösterir.</span><span class="sxs-lookup"><span data-stu-id="51d35-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="51d35-111">Tür çıkarımı yapılan olmasını `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="51d35-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="51d35-112">Türü bu aynı bilinmeyen türde iki bağımsız değişken alan ve aynı türde bir değer döndüren bir işlev gösterir.</span><span class="sxs-lookup"><span data-stu-id="51d35-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="51d35-113">Önceki işlevi olabilir nedenlerden biri dolayısıyla genel daha büyük olan-işleci'den (`>`) kendisi geneldir.</span><span class="sxs-lookup"><span data-stu-id="51d35-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="51d35-114">Büyük-işleci imza varolandan `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="51d35-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="51d35-115">Tüm işleçleri geneldir ve kod işlevinin parametre türü bir genel olmayan işlev veya işleci birlikte kullanıyorsa, bu parametre türü genelleştirilmiş olamaz.</span><span class="sxs-lookup"><span data-stu-id="51d35-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="51d35-116">Çünkü `max` olan genel, bu tür gibi kullanılabilir `int`, `float`ve benzeri, aşağıdaki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="51d35-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="51d35-117">Ancak, iki bağımsız değişkenleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51d35-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="51d35-118">İmza `'a -> 'a -> 'a`değil `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="51d35-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="51d35-119">Bu nedenle, türleri eşleşmediği için aşağıdaki kodu bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51d35-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="51d35-120">`max` İşlevi de büyük destekleyen herhangi bir türü ile çalışır-işleci daha.</span><span class="sxs-lookup"><span data-stu-id="51d35-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="51d35-121">Bu nedenle, ayrıca, bir dizesine, aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51d35-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="51d35-122">Değer kısıtlama</span><span class="sxs-lookup"><span data-stu-id="51d35-122">Value Restriction</span></span>
<span data-ttu-id="51d35-123">Derleyici otomatik Genelleştirme yalnızca açık bağımsız değişkenlerinin tam işlev tanımları ve basit değişmez değerleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="51d35-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="51d35-124">Başka bir deyişle, yeterince belirli bir tür olması zorunlu değildir, ancak aynı zamanda genelleştirilebilir Kodu derlemek çalışırsanız derleyici bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="51d35-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="51d35-125">Bu kısıtlama değerleri için otomatik Genelleştirme üzerinde bu sorun için hata iletisini başvurduğu *değer kısıtlaması*.</span><span class="sxs-lookup"><span data-stu-id="51d35-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="51d35-126">Genellikle, genel olarak bir yapı istiyor ancak derleyici onu genelleştirmek için yeterli bilgiye sahip olduğunda veya yeterli türü bilgileri nongeneric yapısında istemeden atladığınızda değer kısıtlama hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="51d35-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="51d35-127">Değer kısıtlama hatası çözüme daha eksiksiz türü çıkarımı sorunu aşağıdaki yollardan biriyle sınırlamak için daha açık bilgilerini sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="51d35-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="51d35-128">Bir tür değeri veya parametre için bir açık tür ek açıklama ekleyerek nongeneric olacak şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="51d35-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="51d35-129">Sorun kullanıyorsa, genel işlevi, bir işlev oluşturma gibi ya da eksik olarak tanımlamak için bir nongeneralizable yapısı curried işlev bağımsız değişkenleri uygulanır, bir sıradan işlev tanımı işlevi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="51d35-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="51d35-130">Sorun genelleştirilmiş için çok karmaşık bir ifade ise, bir ek, kullanılmayan parametresini ekleyerek bir işlevdeki olun.</span><span class="sxs-lookup"><span data-stu-id="51d35-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="51d35-131">Açık genel tür parametreleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="51d35-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="51d35-132">Bu seçenek nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51d35-132">This option is rarely used.</span></span>

- <span data-ttu-id="51d35-133">Aşağıdaki kod örnekleri bu senaryoların her biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51d35-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="51d35-134">Durum 1: Çok karmaşık bir ifade.</span><span class="sxs-lookup"><span data-stu-id="51d35-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="51d35-135">Bu örnekte, listenin `counter` olması amaçlanmıştır `int option ref`, ancak basit bir sabit değer tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="51d35-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="51d35-136">Durum 2: nongeneralizable yapı genel işlevi tanımlamak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="51d35-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="51d35-137">İşlev bağımsız değişkenleri kısmi uygulaması içerdiğinden bu örnekte, nongeneralizable yapıdır.</span><span class="sxs-lookup"><span data-stu-id="51d35-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="51d35-138">Durum 3: bir ek, kullanılmayan parametresi ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="51d35-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="51d35-139">Bu ifade için genelleştirme kadar basit olmadığından derleyici değer kısıtlama hatası verir.</span><span class="sxs-lookup"><span data-stu-id="51d35-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="51d35-140">Durum 4: Tür parametreleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="51d35-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="51d35-141">Son durumda, aşağıdaki gibi birçok farklı türlerde değerler örneğin oluşturmak için kullanılabilir bir tür işlevi değeri olur:</span><span class="sxs-lookup"><span data-stu-id="51d35-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="51d35-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51d35-142">See Also</span></span>
[<span data-ttu-id="51d35-143">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="51d35-143">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="51d35-144">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="51d35-144">Generics</span></span>](index.md)

[<span data-ttu-id="51d35-145">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="51d35-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="51d35-146">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="51d35-146">Constraints</span></span>](constraints.md)

