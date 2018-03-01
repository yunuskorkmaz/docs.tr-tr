---
title: "-= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a><span data-ttu-id="5cbd5-102">-= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5cbd5-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="5cbd5-103">Çıkarma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="5cbd5-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cbd5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cbd5-104">Remarks</span></span>  
 <span data-ttu-id="5cbd5-105">Bir ifade kullanılarak `-=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="5cbd5-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="5cbd5-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="5cbd5-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="5cbd5-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5cbd5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="5cbd5-108">Anlamını [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) türleri üzerinde bağımlı `x` ve `y` (sayısal işlenenler için çıkarma kaldırma temsilci işlenenler için temsilci seçme ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="5cbd5-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="5cbd5-109">`-=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5cbd5-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="5cbd5-110">-= İşleci ayrıca C# dilinde bir olaydan aboneliğinizi iptal etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cbd5-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="5cbd5-111">Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="5cbd5-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cbd5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cbd5-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5cbd5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cbd5-113">See Also</span></span>  
 [<span data-ttu-id="5cbd5-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5cbd5-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5cbd5-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5cbd5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5cbd5-116">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5cbd5-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
