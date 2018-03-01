---
title: "Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="9d143-102">Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz</span><span class="sxs-lookup"><span data-stu-id="9d143-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="9d143-103">Bir sınıf, yapı veya dizi türü veya içeren bir genel türü tarafından tanımlanan bir tür parametresi olarak bir sabit bildirme denediniz.</span><span class="sxs-lookup"><span data-stu-id="9d143-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="9d143-104">Sabitler iç bir türde olması gerekir (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, veya `UShort`), veya bir `Enum` tam sayı türlerinden birini temel türü.</span><span class="sxs-lookup"><span data-stu-id="9d143-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="9d143-105">**Hata Kimliği:** BC30424</span><span class="sxs-lookup"><span data-stu-id="9d143-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d143-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9d143-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9d143-107">Bir iç olarak sabit bildirme veya `Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="9d143-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="9d143-108">Bir sabit da özel bir değer gibi olabilir `True`, `False`, veya `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d143-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="9d143-109">Derleyici iç uygun türde olması için bu önceden tanımlanmış değerler göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="9d143-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d143-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d143-110">See Also</span></span>  
 [<span data-ttu-id="9d143-111">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="9d143-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="9d143-112">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="9d143-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="9d143-113">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="9d143-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
