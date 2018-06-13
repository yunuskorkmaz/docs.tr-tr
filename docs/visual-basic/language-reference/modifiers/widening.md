---
title: Genişletme (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595319"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="6e001-102">Genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e001-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="6e001-103">Belirten bir dönüşüm işleci (`CType`) bir sınıf veya yapı özgün sınıf veya yapı tüm olası değerlerini tutan bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6e001-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="6e001-104">Genişletme anahtar sözcüğü ile dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6e001-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="6e001-105">Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Widening`.</span><span class="sxs-lookup"><span data-stu-id="6e001-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="6e001-106">Genişletme dönüşümleri çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden.</span><span class="sxs-lookup"><span data-stu-id="6e001-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="6e001-107">Örnekler `Single` için `Double`, `Char` için `String`ve türetilmiş bir tür için temel türü.</span><span class="sxs-lookup"><span data-stu-id="6e001-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="6e001-108">Türetilmiş bir tür temel türdeki tüm üyelerin içerir ve bu nedenle temel türü örneği olduğundan bu son dönüştürme genişletme.</span><span class="sxs-lookup"><span data-stu-id="6e001-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="6e001-109">Kullanıcı kodu kullanmak zorunda kalmazsınız `CType` dönüşümleri, için bile `Option Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="6e001-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="6e001-110">`Widening` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6e001-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="6e001-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e001-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="6e001-112">Örneğin genişletme ve daraltma dönüşüm işleçleri tanımları bkz [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6e001-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e001-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e001-113">See Also</span></span>  
 [<span data-ttu-id="6e001-114">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e001-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="6e001-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="6e001-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="6e001-116">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="6e001-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="6e001-117">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6e001-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="6e001-118">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="6e001-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="6e001-119">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e001-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="6e001-120">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6e001-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
