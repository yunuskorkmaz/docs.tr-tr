---
title: 'Döngüler: for...in İfadesi'
description: F# İçin bkz.... ifade döngüsü yapısı, sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216450"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="7a159-103">Döngüler: for...in İfadesi</span><span class="sxs-lookup"><span data-stu-id="7a159-103">Loops: for...in Expression</span></span>

<span data-ttu-id="7a159-104">Bu döngü yapısı, bir Aralık ifadesi, sırası, liste, dizi ya da numaralandırmayı destekleyen diğer yapı gibi sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a159-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a159-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a159-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="7a159-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a159-106">Remarks</span></span>

<span data-ttu-id="7a159-107">İfade, sıralanabilir bir koleksiyondaki değerleri döngüye `for each` almak için kullanıldığından, diğer .net dillerdeki deyimle karşılaştırılabilir. `for...in`</span><span class="sxs-lookup"><span data-stu-id="7a159-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="7a159-108">Bununla birlikte `for...in` , yalnızca tüm koleksiyon üzerinde yineleme yerine koleksiyon üzerinde model eşleştirmeyi de destekler.</span><span class="sxs-lookup"><span data-stu-id="7a159-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="7a159-109">Sıralanabilir ifade, sıralanabilir bir koleksiyon olarak veya `..` işleç kullanılarak integral türünde bir Aralık olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a159-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="7a159-110">Sıralanabilir koleksiyonlar listeler, sıralar, diziler, kümeler, haritalar vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="7a159-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="7a159-111">Uygulayan `System.Collections.IEnumerable` herhangi bir tür kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a159-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="7a159-112">`..` İşlecini kullanarak bir Aralık ifade ettiğinizde, aşağıdaki sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a159-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="7a159-113">*Başlat* ..</span><span class="sxs-lookup"><span data-stu-id="7a159-113">*start* ..</span></span> <span data-ttu-id="7a159-114">*sona*</span><span class="sxs-lookup"><span data-stu-id="7a159-114">*finish*</span></span>

<span data-ttu-id="7a159-115">Aşağıdaki kodda olduğu gibi, *Atla*adlı bir artış içeren bir sürüm de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a159-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="7a159-116">*Başlat* ..</span><span class="sxs-lookup"><span data-stu-id="7a159-116">*start* ..</span></span> <span data-ttu-id="7a159-117">*Atla* ..</span><span class="sxs-lookup"><span data-stu-id="7a159-117">*skip* ..</span></span> <span data-ttu-id="7a159-118">*sona*</span><span class="sxs-lookup"><span data-stu-id="7a159-118">*finish*</span></span>

<span data-ttu-id="7a159-119">Model olarak integral aralıklar ve basit bir sayaç değişkeni kullandığınızda, tipik davranış her yinelemede Sayaç değişkenini 1 artırır, ancak Aralık bir atlama değeri içeriyorsa, sayaç atlama değeri ile artırılır.</span><span class="sxs-lookup"><span data-stu-id="7a159-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="7a159-120">Düzende eşleşen değerler de gövde ifadesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a159-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="7a159-121">Aşağıdaki kod örnekleri, `for...in` ifadesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a159-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="7a159-122">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7a159-122">The output is as follows.</span></span>

```console
1
5
100
450
788
```

<span data-ttu-id="7a159-123">Aşağıdaki örnek, bir sıranın üzerinde nasıl döngü yapılacağını ve basit bir değişken yerine demet deseninin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a159-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="7a159-124">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7a159-124">The output is as follows.</span></span>

```console
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="7a159-125">Aşağıdaki örnek, bir basit tamsayı aralığının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a159-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="7a159-126">İşlev1 çıkışı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a159-126">The output of function1 is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="7a159-127">Aşağıdaki örnek, aralığın her bir öğesini de içeren, bir Aralık üzerinde döngünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a159-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="7a159-128">Çıkışı `function2` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a159-128">The output of `function2` is as follows.</span></span>

```console
1 3 5 7 9
```

<span data-ttu-id="7a159-129">Aşağıdaki örnek, bir karakter aralığının nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a159-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="7a159-130">Çıkışı `function3` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a159-130">The output of `function3` is as follows.</span></span>

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="7a159-131">Aşağıdaki örnek, bir ters yineleme için negatif atlama değeri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a159-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="7a159-132">Çıkışı `function4` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a159-132">The output of `function4` is as follows.</span></span>

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="7a159-133">Aralığın başlangıcı ve bitişi, aşağıdaki kodda olduğu gibi işlevler gibi ifadeler de olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a159-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="7a159-134">Bu girişle çıkış `function5` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a159-134">The output of `function5` with this input is as follows.</span></span>

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="7a159-135">Sonraki örnekte, öğe döngüde gerekli olmadığında bir joker karakteri (\_) kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a159-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="7a159-136">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7a159-136">The output is as follows.</span></span>

```console
Number of elements in list1: 5
```

<span data-ttu-id="7a159-137">`Note`Dizi ifadelerinde ve `for...in` diğer hesaplama ifadelerinde kullanabilirsiniz, bu durumda `for...in` ifadenin özelleştirilmiş bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a159-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="7a159-138">Daha fazla bilgi için bkz. [diziler](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [Hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7a159-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a159-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a159-139">See also</span></span>

- [<span data-ttu-id="7a159-140">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7a159-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7a159-141">Lerin `for...to`İfadesini</span><span class="sxs-lookup"><span data-stu-id="7a159-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="7a159-142">Lerin `while...do`İfadesini</span><span class="sxs-lookup"><span data-stu-id="7a159-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
