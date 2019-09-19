---
title: Esnek Türler
description: Bir parametre, değişken F# veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu gösteren esnek tür ek açıklamasını nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: bf05f78f163d1f9c73c667df60925b66a5315627
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083072"
---
# <a name="flexible-types"></a><span data-ttu-id="36aa9-103">Esnek Türler</span><span class="sxs-lookup"><span data-stu-id="36aa9-103">Flexible Types</span></span>

<span data-ttu-id="36aa9-104">*Esnek tür ek açıklaması* , bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu belirtir; burada uyumluluk, nesne odaklı sınıfların veya arabirimlerin bulunduğu konuma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="36aa9-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="36aa9-105">Esnek türler özellikle tür hiyerarşisinde daha üst türlere otomatik dönüştürme gerçekleşmezse yararlı olur ancak yine de işlevselliği hiyerarşide herhangi bir türle veya bir arabirim uygulayan herhangi bir tür ile çalışacak şekilde etkinleştirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="36aa9-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="36aa9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36aa9-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="36aa9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36aa9-107">Remarks</span></span>

<span data-ttu-id="36aa9-108">Önceki sözdiziminde, *tür* bir temel türü veya arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36aa9-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="36aa9-109">Esnek tür, izin verilen türleri temel veya arabirim türüyle uyumlu türlere sınırlayan bir kısıtlamaya sahip genel bir tür ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="36aa9-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="36aa9-110">Diğer bir deyişle, aşağıdaki iki kod satırı eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="36aa9-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="36aa9-111">Esnek türler birkaç tür durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="36aa9-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="36aa9-112">Örneğin, daha yüksek bir order işleviniz (bağımsız değişken olarak işlev alan bir işlev) olduğunda, işlevin esnek bir tür döndürmesi genellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="36aa9-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="36aa9-113">Aşağıdaki örnekte, içinde `iterate2` bir dizi bağımsız değişkeni olan esnek bir tür kullanılması, daha yüksek sıralı işlevin diziler, diziler, listeler ve diğer herhangi bir sıralanabilir tür oluşturan işlevlerle çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="36aa9-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="36aa9-114">Aşağıdaki iki işlevi göz önünde bulundurun, bunlardan biri bir dizi döndürür, diğeri ise esnek bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="36aa9-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="36aa9-115">Başka bir örnek olarak, [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) Kitaplık işlevini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="36aa9-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="36aa9-116">Aşağıdaki sıralanabilir dizileri bu işleve geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36aa9-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="36aa9-117">Listelerin listesi</span><span class="sxs-lookup"><span data-stu-id="36aa9-117">A list of lists</span></span>
- <span data-ttu-id="36aa9-118">Dizilerin listesi</span><span class="sxs-lookup"><span data-stu-id="36aa9-118">A list of arrays</span></span>
- <span data-ttu-id="36aa9-119">Listelerden oluşan bir dizi</span><span class="sxs-lookup"><span data-stu-id="36aa9-119">An array of lists</span></span>
- <span data-ttu-id="36aa9-120">Dizi dizileri</span><span class="sxs-lookup"><span data-stu-id="36aa9-120">An array of sequences</span></span>
- <span data-ttu-id="36aa9-121">Sıralanabilir sıraların diğer birleşimleri</span><span class="sxs-lookup"><span data-stu-id="36aa9-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="36aa9-122">Aşağıdaki kod, esnek `Seq.concat` türler kullanarak destekleyerek kullanabileceğiniz senaryoları göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="36aa9-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="36aa9-123">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="36aa9-123">The output is as follows.</span></span>

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="36aa9-124">' F#De, diğer nesne yönelimli dillerde olduğu gibi, arabirimleri uygulayan türetilmiş türlerin veya türlerin otomatik olarak temel türe veya arabirim türüne dönüştürüldüğü bağlamlar vardır.</span><span class="sxs-lookup"><span data-stu-id="36aa9-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="36aa9-125">Bu otomatik dönüştürmeler doğrudan bağımsız değişkenlerde oluşur, ancak tür bir alt konumda olduğunda değil, bir işlev türünün dönüş türü veya tür bağımsız değişkeni gibi daha karmaşık bir türün parçası olarak değildir.</span><span class="sxs-lookup"><span data-stu-id="36aa9-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="36aa9-126">Bu nedenle, esnek tür gösterimi öncelikle, uyguladığınız tür daha karmaşık bir türün parçası olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="36aa9-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="36aa9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36aa9-127">See also</span></span>

- [<span data-ttu-id="36aa9-128">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="36aa9-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="36aa9-129">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="36aa9-129">Generics</span></span>](./generics/index.md)
