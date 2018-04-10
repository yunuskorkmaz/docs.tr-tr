---
title: '%= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ec4c7-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ec4c7-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="ec4c7-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="ec4c7-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4c7-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec4c7-104">Remarks</span></span>  
 <span data-ttu-id="ec4c7-105">Bir ifade kullanılarak `%=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="ec4c7-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="ec4c7-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="ec4c7-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="ec4c7-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ec4c7-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ec4c7-108">[% İşleci](../../../csharp/language-reference/operators/modulus-operator.md) ayırmadan sonra geri kalan işlem sayısal türler için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="ec4c7-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="ec4c7-109">`%=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [% işleci](../../../csharp/language-reference/operators/modulus-operator.md) (bkz [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ec4c7-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec4c7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec4c7-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ec4c7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec4c7-111">See Also</span></span>  
 [<span data-ttu-id="ec4c7-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ec4c7-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ec4c7-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ec4c7-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec4c7-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="ec4c7-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
