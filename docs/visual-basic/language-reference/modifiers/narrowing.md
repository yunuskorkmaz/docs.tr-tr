---
title: Daraltma (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838857"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="5e86d-102">Daraltma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e86d-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="5e86d-103">Bildiren bir dönüştürme operatörünün (`CType`) bir sınıf veya yapı, bazı özgün sınıf veya yapıda olası değerlerini tutabilecek özellikte olmayabilecek bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5e86d-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="5e86d-104">Daraltma anahtar sözcüğü ile dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5e86d-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="5e86d-105">Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="5e86d-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="5e86d-106">Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden.</span><span class="sxs-lookup"><span data-stu-id="5e86d-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="5e86d-107">Örnekler `Long` için `Integer`, `String` için `Date`ve türetilmiş bir tür için bir taban türü.</span><span class="sxs-lookup"><span data-stu-id="5e86d-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="5e86d-108">Temel tür türetilmiş bir türde tüm üyelerini içermeyebilir ve bu nedenle türetilmiş bir tür örneği olmadığından bu son dönüştürme belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="5e86d-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="5e86d-109">Varsa `Option Strict` olduğu `On`, kod tüketen kullanmalıdır `CType` tüm daraltma dönüştürmeleri için.</span><span class="sxs-lookup"><span data-stu-id="5e86d-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="5e86d-110">`Narrowing` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5e86d-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="5e86d-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e86d-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e86d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e86d-112">See also</span></span>

- [<span data-ttu-id="5e86d-113">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e86d-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="5e86d-114">Widening</span><span class="sxs-lookup"><span data-stu-id="5e86d-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="5e86d-115">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="5e86d-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5e86d-116">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="5e86d-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="5e86d-117">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="5e86d-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="5e86d-118">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e86d-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
