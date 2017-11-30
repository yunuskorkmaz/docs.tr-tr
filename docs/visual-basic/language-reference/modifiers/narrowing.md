---
title: Daraltma (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="4d336-102">Daraltma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d336-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="4d336-103">Belirten bir dönüşüm işleci (`CType`) bir sınıf veya yapı bazı özgün sınıf veya yapı olası değerlerini tutabilecek özellikte olmayabilecek türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4d336-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="4d336-104">Daraltma anahtar sözcüğü ile dönüştürme</span><span class="sxs-lookup"><span data-stu-id="4d336-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="4d336-105">Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="4d336-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="4d336-106">Daraltma dönüşümleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden.</span><span class="sxs-lookup"><span data-stu-id="4d336-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="4d336-107">Örnekler `Long` için `Integer`, `String` için `Date`ve türetilmiş bir tür için bir taban türü.</span><span class="sxs-lookup"><span data-stu-id="4d336-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="4d336-108">Temel türü türetilen türdeki tüm üyelerin içerebilir ve dolayısıyla türetilen tür örneği olmadığından bu son dönüştürme daraltma.</span><span class="sxs-lookup"><span data-stu-id="4d336-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="4d336-109">Varsa `Option Strict` olan `On`, kod tüketen kullanmalıdır `CType` tüm daraltma dönüşümleri için.</span><span class="sxs-lookup"><span data-stu-id="4d336-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="4d336-110">`Narrowing` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4d336-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="4d336-111">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="4d336-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d336-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d336-112">See Also</span></span>  
 [<span data-ttu-id="4d336-113">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="4d336-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="4d336-114">Genişletme</span><span class="sxs-lookup"><span data-stu-id="4d336-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="4d336-115">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4d336-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="4d336-116">Nasıl yapılır: bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="4d336-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="4d336-117">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="4d336-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="4d336-118">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="4d336-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
