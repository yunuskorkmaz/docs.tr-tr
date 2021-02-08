---
description: "Hakkında daha fazla bilgi edinin: BC30020: ' IS ' başvuru türleri olan işlenenler gerektirir, ancak bu işlenen değer türüne sahiptir '<typename>"
title: "'Is' için başvuru türünde işlenenler gerekir, ancak bu işlenen '<typename>' değer türünde"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: f12d4bb4787c3d003c9afc6a0367f7f9e9248f15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796008"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="e336f-103">BC30020: ' IS ' için başvuru türleri olan işlenenler gerekiyor, ancak bu işlenen ' ' değer türünde \<typename></span><span class="sxs-lookup"><span data-stu-id="e336f-103">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="e336f-104">`Is`Karşılaştırma işleci iki nesne değişkeninin aynı örneğe başvurmasının gerekip gerekmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e336f-104">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="e336f-105">Bu karşılaştırma değer türleri için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="e336f-105">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="e336f-106">**Hata kimliği:** BC30020</span><span class="sxs-lookup"><span data-stu-id="e336f-106">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e336f-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e336f-107">To correct this error</span></span>

- <span data-ttu-id="e336f-108">`Like`İki değer türünü karşılaştırmak için uygun aritmetik karşılaştırma işlecini veya işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e336f-108">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="e336f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e336f-109">See also</span></span>

- [<span data-ttu-id="e336f-110">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="e336f-110">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="e336f-111">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="e336f-111">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="e336f-112">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="e336f-112">Comparison Operators</span></span>](../operators/comparison-operators.md)
