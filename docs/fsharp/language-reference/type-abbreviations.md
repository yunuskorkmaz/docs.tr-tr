---
title: Tür Kısaltmaları (F#)
description: 'Bir tür kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için F # tür kısaltmaları hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf17ee9795947fdc11fe958f09d52f5730b95bf8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="9358e-103">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="9358e-103">Type Abbreviations</span></span>

<span data-ttu-id="9358e-104">A *türü kısaltması* bir diğer ad veya bir tür için diğer ad.</span><span class="sxs-lookup"><span data-stu-id="9358e-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="9358e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9358e-105">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="9358e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9358e-106">Remarks</span></span>
<span data-ttu-id="9358e-107">Tür kısaltmaları türü kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9358e-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="9358e-108">Ayrıca bunları aksi yazamadı sıkıcı bir tür için kullanımı kolay bir ad oluşturmak için kullanabilirsiniz. Ayrıca, temel alınan tür türü kullanan tüm kodu değiştirmeden değiştirmek kolaylaştırmak için tür kısaltmaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9358e-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="9358e-109">Bir basit tür kısaltması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9358e-109">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="9358e-110">Tür kısaltmaları aşağıdaki kodu olduğu gibi genel parametreler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9358e-110">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="9358e-111">Önceki kod `Transform` herhangi bir türde tek bir bağımsız değişken bir işlevi temsil eden bir tür kısaltması olduğu ve aynı türde tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9358e-111">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="9358e-112">Tür kısaltmaları .NET Framework MSIL kodda korunmaz.</span><span class="sxs-lookup"><span data-stu-id="9358e-112">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="9358e-113">Bu nedenle, F # bütünleştirilmiş başka bir .NET Framework dilden kullandığınızda, bir tür kısaltması için temel alınan tür adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9358e-113">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="9358e-114">Tür kısaltmaları ölçü üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9358e-114">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="9358e-115">Daha fazla bilgi için bkz: [ölçü](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="9358e-115">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="9358e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9358e-116">See Also</span></span>
[<span data-ttu-id="9358e-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9358e-117">F# Language Reference</span></span>](index.md)

