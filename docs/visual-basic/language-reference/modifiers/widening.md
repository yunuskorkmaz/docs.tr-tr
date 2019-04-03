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
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825319"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="a472c-102">Genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a472c-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="a472c-103">Bildiren bir dönüştürme operatörünün (`CType`) bir sınıf ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a472c-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="a472c-104">Genişletme anahtar sözcüğü ile dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a472c-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="a472c-105">Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Widening`.</span><span class="sxs-lookup"><span data-stu-id="a472c-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="a472c-106">Genişletme dönüştürmeleri, çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden.</span><span class="sxs-lookup"><span data-stu-id="a472c-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="a472c-107">Örnekler `Single` için `Double`, `Char` için `String`ve türetilmiş bir tür yerine bunun temel türü.</span><span class="sxs-lookup"><span data-stu-id="a472c-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="a472c-108">Türetilmiş tür temel türünün tüm üyelerini içerir ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme genişletme.</span><span class="sxs-lookup"><span data-stu-id="a472c-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="a472c-109">Tüketici kod kullanmak zorunda kalmazsınız `CType` genişletme dönüştürmeleri, için bile `Option Strict` olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="a472c-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="a472c-110">`Widening` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a472c-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="a472c-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a472c-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="a472c-112">Örneğin genişletme ve daraltma dönüştürme operatörlerini tanımları bkz [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a472c-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a472c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a472c-113">See also</span></span>

- [<span data-ttu-id="a472c-114">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a472c-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a472c-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="a472c-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="a472c-116">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="a472c-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="a472c-117">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="a472c-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="a472c-118">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="a472c-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="a472c-119">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="a472c-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a472c-120">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="a472c-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
