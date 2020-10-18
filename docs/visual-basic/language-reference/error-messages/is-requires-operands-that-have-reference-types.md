---
title: "'Is' için başvuru türünde işlenenler gerekir, ancak bu işlenen '<typename>' değer türünde"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163356"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="7ac53-102">BC30020: ' IS ' için başvuru türleri olan işlenenler gerekiyor, ancak bu işlenen ' ' değer türünde \<typename></span><span class="sxs-lookup"><span data-stu-id="7ac53-102">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="7ac53-103">`Is`Karşılaştırma işleci iki nesne değişkeninin aynı örneğe başvurmasının gerekip gerekmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="7ac53-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="7ac53-104">Bu karşılaştırma değer türleri için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="7ac53-104">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="7ac53-105">**Hata kimliği:** BC30020</span><span class="sxs-lookup"><span data-stu-id="7ac53-105">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7ac53-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7ac53-106">To correct this error</span></span>

- <span data-ttu-id="7ac53-107">`Like`İki değer türünü karşılaştırmak için uygun aritmetik karşılaştırma işlecini veya işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ac53-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ac53-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ac53-108">See also</span></span>

- [<span data-ttu-id="7ac53-109">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="7ac53-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="7ac53-110">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="7ac53-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="7ac53-111">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="7ac53-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
