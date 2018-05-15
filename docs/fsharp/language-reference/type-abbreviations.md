---
title: Tür Kısaltmaları (F#)
description: 'Bir tür kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için F # tür kısaltmaları hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="f858b-103">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="f858b-103">Type Abbreviations</span></span>

<span data-ttu-id="f858b-104">A *türü kısaltması* bir diğer ad veya bir tür için diğer ad.</span><span class="sxs-lookup"><span data-stu-id="f858b-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="f858b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f858b-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="f858b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f858b-106">Remarks</span></span>
<span data-ttu-id="f858b-107">Tür kısaltmaları türü kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f858b-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="f858b-108">Ayrıca bunları aksi yazamadı sıkıcı bir tür için kullanımı kolay bir ad oluşturmak için kullanabilirsiniz. Ayrıca, temel alınan tür türü kullanan tüm kodu değiştirmeden değiştirmek kolaylaştırmak için tür kısaltmaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f858b-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="f858b-109">Bir basit tür kısaltması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f858b-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="f858b-110">Tür kısaltmaları erişilebilirliğini varsayılanları `public`.</span><span class="sxs-lookup"><span data-stu-id="f858b-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="f858b-111">Tür kısaltmaları aşağıdaki kodu olduğu gibi genel parametreler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f858b-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="f858b-112">Önceki kod `Transform` herhangi bir türde tek bir bağımsız değişken bir işlevi temsil eden bir tür kısaltması olduğu ve aynı türde tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f858b-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="f858b-113">Tür kısaltmaları .NET Framework MSIL kodda korunmaz.</span><span class="sxs-lookup"><span data-stu-id="f858b-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="f858b-114">Bu nedenle, F # bütünleştirilmiş başka bir .NET Framework dilden kullandığınızda, bir tür kısaltması için temel alınan tür adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f858b-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="f858b-115">Tür kısaltmaları ölçü üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f858b-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="f858b-116">Daha fazla bilgi için bkz: [ölçü](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="f858b-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="f858b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f858b-117">See Also</span></span>
[<span data-ttu-id="f858b-118">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f858b-118">F# Language Reference</span></span>](index.md)

