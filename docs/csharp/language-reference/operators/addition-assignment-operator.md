---
title: "+= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91286b3c6b9a7239bcd5d5bac0ef08bfd7fa8345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f29a8-102">+= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f29a8-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="f29a8-103">Toplama atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f29a8-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f29a8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f29a8-104">Remarks</span></span>  
 <span data-ttu-id="f29a8-105">Bir ifade kullanılarak `+=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="f29a8-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="f29a8-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="f29a8-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="f29a8-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f29a8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f29a8-108">Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (toplama sayısal işlenenler, dize işlenenleri ve benzeri için birleştirme).</span><span class="sxs-lookup"><span data-stu-id="f29a8-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="f29a8-109">`+=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f29a8-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="f29a8-110">`+=` İşleci bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için de kullanılır; bu tür yöntemleri olay işleyicileri çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f29a8-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="f29a8-111">Kullanımını `+=` bu bağlamda işleci olarak adlandırılır *bir olaya abone*.</span><span class="sxs-lookup"><span data-stu-id="f29a8-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="f29a8-112">Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f29a8-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="f29a8-113">ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f29a8-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f29a8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f29a8-114">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f29a8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f29a8-115">See Also</span></span>  
 [<span data-ttu-id="f29a8-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f29a8-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f29a8-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f29a8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f29a8-118">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="f29a8-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
