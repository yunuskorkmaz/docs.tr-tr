---
title: Daraltma
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
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351470"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="04a06-102">Daraltma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04a06-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="04a06-103">Bir dönüştürme işlecinin (`CType`) bir sınıfı ya da yapıyı özgün sınıf veya yapının olası bazı değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="04a06-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="04a06-104">Daraltma anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="04a06-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="04a06-105">Dönüştürme yordamının `Narrowing`ek olarak `Public Shared` belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a06-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="04a06-106">Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="04a06-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="04a06-107">Örnekler, türetilmiş bir türe `Integer`, `Date``String` ve temel bir tür `Long`.</span><span class="sxs-lookup"><span data-stu-id="04a06-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="04a06-108">Temel tür türetilmiş türün tüm üyelerini içermediğinden ve bu nedenle türetilmiş türün bir örneği olmadığından, bu son dönüştürme daraltma yapılır.</span><span class="sxs-lookup"><span data-stu-id="04a06-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="04a06-109">`Option Strict` `On`, tüketen kodun tüm daraltma dönüştürmeleri için `CType` kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a06-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="04a06-110">`Narrowing` anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="04a06-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="04a06-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="04a06-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="04a06-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a06-112">See also</span></span>

- [<span data-ttu-id="04a06-113">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="04a06-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="04a06-114">Widening</span><span class="sxs-lookup"><span data-stu-id="04a06-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="04a06-115">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="04a06-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="04a06-116">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="04a06-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="04a06-117">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="04a06-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="04a06-118">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="04a06-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
