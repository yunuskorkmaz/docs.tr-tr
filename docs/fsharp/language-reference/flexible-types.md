---
title: Esnek Türler (F#)
description: 'Bir parametre, değişken veya değer belirtilen bir tür ile uyumlu bir türe sahip olduğunu gösterir F # esnek türü açıklama kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615566"
---
# <a name="flexible-types"></a><span data-ttu-id="d01eb-103">Esnek Türler</span><span class="sxs-lookup"><span data-stu-id="d01eb-103">Flexible Types</span></span>

<span data-ttu-id="d01eb-104">A *esnek tür ek açıklamasına* bir parametre, değişken veya değer uyumluluk sınıfları arabirimler ve nesne yönelimli bir hiyerarşideki konuma göre belirlendiği belirtilen bir tür ile uyumlu bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d01eb-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="d01eb-105">Esnek türler, özellikle otomatik dönüştürme türü hiyerarşinin üst düzeylerindeki türlerine oluşmaz ancak yine de hiyerarşideki herhangi bir türü veya bir arabirimi uygulayan herhangi bir türü ile çalışmak, işlevselliğini etkinleştirmek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d01eb-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="d01eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d01eb-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="d01eb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d01eb-107">Remarks</span></span>

<span data-ttu-id="d01eb-108">Önceki sözdiziminde, *türü* bir taban türü veya bir arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d01eb-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="d01eb-109">Esnek bir tür, taban veya arabirim türü ile uyumlu türlere izin verilen türlerden sınırlayan bir kısıtlamaya sahip genel bir tür eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d01eb-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="d01eb-110">Diğer bir deyişle, aşağıdaki iki kod satırlarını eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d01eb-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="d01eb-111">Esnek türler, çeşitli türlerde durumlarda, kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d01eb-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="d01eb-112">Daha yüksek sıralı işlev (işlev bağımsız değişken olarak alan bir işlev) sahip olduğunuzda, örneğin, genellikle işlev dönüş esnek bir türü sahip olmak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d01eb-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="d01eb-113">Aşağıdaki örnekte, bir sıra bağımsız değişkeni ile esnek bir türü kullanımını `iterate2` dizileri, diziler, listeler ve numaralandırılabilir herhangi bir türü oluşturan işlevler ile çalışmak daha yüksek sıralı işlev sağlar.</span><span class="sxs-lookup"><span data-stu-id="d01eb-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="d01eb-114">Aşağıdaki iki işlevi, bir dizisini döndüren biri diğerinin esnek bir tür döndüren bir göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d01eb-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="d01eb-115">Başka bir örnek olarak göz önünde bulundurun [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) kitaplığı işlevi:</span><span class="sxs-lookup"><span data-stu-id="d01eb-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="d01eb-116">Bu işleve aşağıdaki numaralandırılabilir sıralarının geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d01eb-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="d01eb-117">Bir liste</span><span class="sxs-lookup"><span data-stu-id="d01eb-117">A list of lists</span></span>
- <span data-ttu-id="d01eb-118">Bir diziler listesi</span><span class="sxs-lookup"><span data-stu-id="d01eb-118">A list of arrays</span></span>
- <span data-ttu-id="d01eb-119">Bir dizi listeler</span><span class="sxs-lookup"><span data-stu-id="d01eb-119">An array of lists</span></span>
- <span data-ttu-id="d01eb-120">Bir dizi sırası</span><span class="sxs-lookup"><span data-stu-id="d01eb-120">An array of sequences</span></span>
- <span data-ttu-id="d01eb-121">Herhangi bir birleşimini numaralandırılabilir sırası</span><span class="sxs-lookup"><span data-stu-id="d01eb-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="d01eb-122">Aşağıdaki kod `Seq.concat` esnek türlerini kullanarak destekleyebilir senaryoları göstermek için.</span><span class="sxs-lookup"><span data-stu-id="d01eb-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="d01eb-123">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d01eb-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="d01eb-124">F # nesne yönelimli diğer dillerde olduğu gibi var. türetilmiş türler veya arabirimlerini uygulayan türler otomatik olarak bir taban türü veya arabirim türü dönüştürüldüğü bağlamları</span><span class="sxs-lookup"><span data-stu-id="d01eb-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="d01eb-125">Otomatik dönüştürmeler doğrudan bağımsız, ancak türü bir işlev türünün bir dönüş türü gibi daha karmaşık bir türün bir parçası olarak ya da bir tür bağımsız değişkeni olarak bir alt konumda olmadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="d01eb-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="d01eb-126">Bu nedenle, kendisine uyguladığınızı türü daha karmaşık bir türün bir parçası olduğunda esnek türü gösterimi özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d01eb-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="d01eb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d01eb-127">See also</span></span>

- [<span data-ttu-id="d01eb-128">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d01eb-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d01eb-129">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d01eb-129">Generics</span></span>](generics/index.md)
