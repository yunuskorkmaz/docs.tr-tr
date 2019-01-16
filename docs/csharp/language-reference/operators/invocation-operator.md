---
title: () işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333284"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="432fd-102">() işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="432fd-102">() operator (C# Reference)</span></span>

<span data-ttu-id="432fd-103">Bir ifadede işlemlerin sırasını belirlemek için kullanılan ek olarak, parantezler, aşağıdaki görevleri gerçekleştirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="432fd-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>

1. <span data-ttu-id="432fd-104">Atamaları belirtin veya türü dönüşümleri.</span><span class="sxs-lookup"><span data-stu-id="432fd-104">Specify casts, or type conversions.</span></span>

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. <span data-ttu-id="432fd-105">Yöntem veya temsilci çağırır.</span><span class="sxs-lookup"><span data-stu-id="432fd-105">Invoke methods or delegates.</span></span>

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a><span data-ttu-id="432fd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="432fd-106">Remarks</span></span>

<span data-ttu-id="432fd-107">Bir yayın, bir türden diğerine dönüştürme işleci açıkça çağırır; Böyle bir dönüştürme işleci tanımlanırsa, dönüştürme başarısız.</span><span class="sxs-lookup"><span data-stu-id="432fd-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="432fd-108">Bir dönüşüm işleci tanımlama için bkz: [açık](../keywords/explicit.md) ve [örtük](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="432fd-108">To define a conversion operator, see [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md).</span></span>

 <span data-ttu-id="432fd-109">`()` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="432fd-109">The `()` operator cannot be overloaded.</span></span>

 <span data-ttu-id="432fd-110">Daha fazla bilgi için [atama ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="432fd-110">For more information, see [Casting and Type Conversions](../../programming-guide/types/casting-and-type-conversions.md).</span></span>

 <span data-ttu-id="432fd-111">Yöntem çağırma hakkında daha fazla bilgi için bkz: [yöntemleri](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="432fd-111">For more information about method invocation, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="432fd-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="432fd-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="432fd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="432fd-113">See also</span></span>

- [<span data-ttu-id="432fd-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="432fd-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="432fd-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="432fd-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="432fd-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="432fd-116">C# Operators</span></span>](index.md)