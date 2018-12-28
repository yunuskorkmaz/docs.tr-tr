---
title: Tür Kısaltmaları
description: Hakkında bilgi edinin F# bir tür, kodun okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kısaltmalar yazın.
ms.date: 05/16/2016
ms.openlocfilehash: 0deaef789367aad413e5a537bf7164034e1275c0
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613355"
---
# <a name="type-abbreviations"></a><span data-ttu-id="dd6d7-103">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="dd6d7-103">Type Abbreviations</span></span>

<span data-ttu-id="dd6d7-104">A *türü kısaltması* bir diğer ad ya da bir tür için diğer ad.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd6d7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd6d7-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="dd6d7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd6d7-106">Remarks</span></span>

<span data-ttu-id="dd6d7-107">Tür kısaltmaları bir tür, kodun okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="dd6d7-108">Ayrıca bunları aksi yazılmasına yarar yavaşlatan bir tür için kullanımı kolay bir ad oluşturmak için kullanabilirsiniz. Ayrıca, tür kısaltmaları türünü kullanan tüm kodunda değişiklik yapmadan bir temel türü değiştirme daha kolay hale getirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="dd6d7-109">Bir basit türü kısaltması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="dd6d7-110">Tür kısaltmaları erişilebilirliğini varsayılanları `public`.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="dd6d7-111">Tür kısaltmaları, aşağıdaki kodda gösterildiği gibi genel parametreler ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="dd6d7-112">Önceki kodda, `Transform` herhangi bir türde tek bir bağımsız değişken alan bir işlev temsil eden bir tür kısaltması olduğundan ve aynı türde tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="dd6d7-113">Tür kısaltmaları .NET Framework MSIL kodu korunmaz.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="dd6d7-114">Bu nedenle, kullandığınızda bir F# derleme başka bir .NET Framework dilinden türü kısaltması için temel alınan tür adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="dd6d7-115">Tür kısaltmaları ölçü birimi üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="dd6d7-116">Daha fazla bilgi için [ölçü](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="dd6d7-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd6d7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd6d7-117">See also</span></span>

- [<span data-ttu-id="dd6d7-118">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="dd6d7-118">F# Language Reference</span></span>](index.md)