---
title: Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 4d635d289ed99aed48c296c278bc546971af51da
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083928"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="45b12-102">Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz</span><span class="sxs-lookup"><span data-stu-id="45b12-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="45b12-103">Bir sınıf, yapı ya da dizi türü veya içeren bir genel türü tarafından tanımlanan bir tür parametresi olarak bir sabit bildirme girişiminde bulundunuz.</span><span class="sxs-lookup"><span data-stu-id="45b12-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="45b12-104">Sabitler iç bir türde olması gerekir (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, veya `UShort`), veya bir `Enum` türüne göre bir integral türleri.</span><span class="sxs-lookup"><span data-stu-id="45b12-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="45b12-105">**Hata Kimliği:** BC30424</span><span class="sxs-lookup"><span data-stu-id="45b12-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45b12-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="45b12-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="45b12-107">Bir iç öğe olarak bir sabit bildirme veya `Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="45b12-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="45b12-108">Bir sabit ayrıca özel bir değer gibi olabilir `True`, `False`, veya `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="45b12-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="45b12-109">Derleyici iç türü uygun olması için önceden tanımlanmış bu değerleri göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="45b12-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b12-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45b12-110">See Also</span></span>  
 [<span data-ttu-id="45b12-111">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="45b12-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="45b12-112">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="45b12-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="45b12-113">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="45b12-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
