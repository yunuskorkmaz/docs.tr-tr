---
title: "Esnek Türler (F#)"
description: "Bir parametre, değişken veya değer belirtilen tür ile uyumlu bir türe sahip olduğunu gösterir F # esnek türü açıklama kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="9bce4-104">Esnek Türler</span><span class="sxs-lookup"><span data-stu-id="9bce4-104">Flexible Types</span></span>

<span data-ttu-id="9bce4-105">A *esnek türü ek açıklama* bir parametre, değişken veya değer uyumluluk sınıfların veya arabirimleri nesne yönelimli bir hiyerarşinin konuma göre belirlendiği belirtilen bir tür ile uyumlu bir türü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bce4-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="9bce4-106">Esnek türler, özellikle türleri tür hiyerarşisinde daha yüksek otomatik dönüştürme oluşmaz ancak hala hiyerarşideki herhangi bir tür veya bir arabirimini uygulayan herhangi bir türü ile çalışmak, işlevselliğini etkinleştirmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="9bce4-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bce4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bce4-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="9bce4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bce4-108">Remarks</span></span>

<span data-ttu-id="9bce4-109">Önceki sözdiziminde *türü* bir taban türü veya bir arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9bce4-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="9bce4-110">Esnek bir türü, temel veya arabirim türü ile uyumlu türleri için izin verilen türleri sınırlayan bir kısıtlamaya sahip genel bir tür eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9bce4-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="9bce4-111">Diğer bir deyişle, aşağıdaki iki kod satırı eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9bce4-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="9bce4-112">Esnek türler çeşitli türlerde durumlarda, yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9bce4-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="9bce4-113">Daha yüksek bir sipariş işlevi (işlev bağımsız değişken olarak alan işlevi) varsa, örneğin, genellikle bir esnek türü dönüş işlevi yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9bce4-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="9bce4-114">Aşağıdaki örnekte, bir sıra bağımsız değişkeni bir esnek türüyle kullanımını `iterate2` sıraları, diziler, listeler ve herhangi bir numaralandırma türü oluşturan işlevler ile çalışmak daha yüksek sipariş işlevini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9bce4-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="9bce4-115">Aşağıdaki iki işlevleri, bir sıralı bir hangi verir, biri diğer esnek bir tür döndüren göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9bce4-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="9bce4-116">Başka bir örnek olarak, göz önünde bulundurun [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) kitaplığı işlevi:</span><span class="sxs-lookup"><span data-stu-id="9bce4-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="9bce4-117">Bu işleve aşağıdaki numaralandırılabilir sıralarının geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9bce4-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="9bce4-118">Liste listesini</span><span class="sxs-lookup"><span data-stu-id="9bce4-118">A list of lists</span></span>
- <span data-ttu-id="9bce4-119">Diziler listesi</span><span class="sxs-lookup"><span data-stu-id="9bce4-119">A list of arrays</span></span>
- <span data-ttu-id="9bce4-120">Bir dizi listeler</span><span class="sxs-lookup"><span data-stu-id="9bce4-120">An array of lists</span></span>
- <span data-ttu-id="9bce4-121">Bir dizi sıraları</span><span class="sxs-lookup"><span data-stu-id="9bce4-121">An array of sequences</span></span>
- <span data-ttu-id="9bce4-122">Herhangi bir birleşimini numaralandırılabilir sıralarının</span><span class="sxs-lookup"><span data-stu-id="9bce4-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="9bce4-123">Aşağıdaki kod `Seq.concat` esnek türler kullanarak destekleyebilir senaryolarını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="9bce4-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="9bce4-124">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9bce4-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="9bce4-125">F #'ta nesne yönelimli diğer diller olduğu gibi yok bağlamları içinde türetilmiş türler veya arabirimlerini türleri otomatik olarak bir taban türü veya arabirim türü dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9bce4-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="9bce4-126">Bu otomatik dönüşümler doğrudan bağımsız değişkenleri, ancak türü bir işlev türü dönüş türü gibi daha karmaşık türde bir parçası olarak ya da bir tür bağımsız değişkeni olarak bir alt konumda olmadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="9bce4-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="9bce4-127">Bu nedenle, bu uygulamaya uygulama türü daha karmaşık bir tür parçası olduğunda esnek türü gösterimi özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9bce4-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bce4-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bce4-128">See Also</span></span>

[<span data-ttu-id="9bce4-129">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="9bce4-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9bce4-130">Genel türler</span><span class="sxs-lookup"><span data-stu-id="9bce4-130">Generics</span></span>](generics/index.md)
