---
title: '% İşleci (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3f9b2-102">% İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f9b2-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="3f9b2-103">`%` İşleci, kendi ilk işlenen kendi ikinciye bölmenin sonra kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="3f9b2-104">Tüm sayısal türler kalan işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f9b2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f9b2-105">Remarks</span></span>  
 <span data-ttu-id="3f9b2-106">Kullanıcı tanımlı türler aşırı yükleme `%` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3f9b2-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3f9b2-107">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f9b2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f9b2-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="3f9b2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f9b2-109">Comments</span></span>  
 <span data-ttu-id="3f9b2-110">Çift türüyle ilişkili yuvarlama hataları not alın.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9b2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-111">See Also</span></span>  
 [<span data-ttu-id="3f9b2-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f9b2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3f9b2-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3f9b2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3f9b2-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="3f9b2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
