---
title: += İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bcd56acad8e2b08585e5ae60f1c3cf8183b5664a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f95fb-102">+= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f95fb-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="f95fb-103">Toplama atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f95fb-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f95fb-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f95fb-104">Remarks</span></span>  
 <span data-ttu-id="f95fb-105">Bir ifade kullanılarak `+=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="f95fb-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```csharp  
x += y  
```  
  
 <span data-ttu-id="f95fb-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="f95fb-106">is equivalent to</span></span>  
  
```csharp  
x = x + y  
```  
  
 <span data-ttu-id="f95fb-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f95fb-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f95fb-108">Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (toplama sayısal işlenenler, dize işlenenleri ve benzeri için birleştirme).</span><span class="sxs-lookup"><span data-stu-id="f95fb-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="f95fb-109">`+=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f95fb-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="f95fb-110">`+=` İşleci bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için de kullanılır; bu tür yöntemleri olay işleyicileri çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f95fb-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="f95fb-111">Kullanımını `+=` bu bağlamda işleci olarak adlandırılır *bir olaya abone*.</span><span class="sxs-lookup"><span data-stu-id="f95fb-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="f95fb-112">Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f95fb-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f95fb-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f95fb-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f95fb-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f95fb-114">See Also</span></span>  
 [<span data-ttu-id="f95fb-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f95fb-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f95fb-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f95fb-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f95fb-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f95fb-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
