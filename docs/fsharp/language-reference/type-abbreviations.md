---
title: Tür Kısaltmaları
description: Kodun daha F# kolay okunmasını sağlamak için türe daha anlamlı bir ad vermek üzere tür kısaltmaları hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630208"
---
# <a name="type-abbreviations"></a><span data-ttu-id="e0b1f-103">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="e0b1f-103">Type Abbreviations</span></span>

<span data-ttu-id="e0b1f-104">*Tür kısaltması* , bir tür için diğer ad veya alternatif addır.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0b1f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0b1f-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="e0b1f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0b1f-106">Remarks</span></span>

<span data-ttu-id="e0b1f-107">Kodun daha kolay okunmasını sağlamak için tür kısaltmalarını, bir türe daha anlamlı bir ad vermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="e0b1f-108">Ayrıca, yazmak üzere çok daha fazla olan bir tür için kullanımı kolay bir ad oluşturmak üzere bunları da kullanabilirsiniz. Ek olarak, türü kullanan tüm kodları değiştirmeden temel bir türün değiştirilmesini kolaylaştırmak için tür kısaltmalarının de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="e0b1f-109">Aşağıda basit bir tür kısaltması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="e0b1f-110">Tür kısaltmalarının erişilebilirliği varsayılan olarak `public`.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="e0b1f-111">Tür kısaltmaları, aşağıdaki kodda olduğu gibi genel parametreleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="e0b1f-112">Önceki kodda, `Transform` herhangi bir türde tek bir bağımsız değişken alan ve aynı türde tek bir değer döndüren bir işlevi temsil eden bir tür kısaltmadır.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="e0b1f-113">Tür kısaltmaları .NET Framework MSIL kodunda korunmaz.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="e0b1f-114">Bu nedenle, başka bir .NET Framework F# dilinden bir derlemeyi kullandığınızda, bir tür kısaltması için temel alınan tür adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="e0b1f-115">Tür kısaltmaları, ölçü birimleri üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="e0b1f-116">Daha fazla bilgi için bkz. [Ölçü birimleri](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="e0b1f-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0b1f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-117">See also</span></span>

- [<span data-ttu-id="e0b1f-118">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0b1f-118">F# Language Reference</span></span>](index.md)
