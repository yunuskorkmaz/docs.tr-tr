---
title: '&#39;Olan&#39; işlenenler gerektirir başvuru türleri vardır, ancak bu işlenen değer türünde &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722926"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="34725-102">&#39;Olan&#39; işlenenler gerektirir başvuru türleri vardır, ancak bu işlenen değer türünde &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="34725-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="34725-103">`Is` Karşılaştırma işleci iki nesne değişkenini aynı örneğe atıfta olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="34725-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="34725-104">Bu karşılaştırma, değer türleri için tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="34725-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="34725-105">**Hata Kimliği:** BC30020</span><span class="sxs-lookup"><span data-stu-id="34725-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34725-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="34725-106">To correct this error</span></span>  
  
-   <span data-ttu-id="34725-107">Uygun aritmetik karşılaştırma işlecini kullanın veya `Like` iki veri türünü karşılaştırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="34725-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34725-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34725-108">See also</span></span>
- [<span data-ttu-id="34725-109">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="34725-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="34725-110">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="34725-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="34725-111">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="34725-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
