---
title: -= İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 7cade0811536d836480f80a56cf8c4d09e089a0b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254400"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="7dc6a-102">-= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7dc6a-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="7dc6a-103">Çıkarma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="7dc6a-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dc6a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dc6a-104">Remarks</span></span>  
 <span data-ttu-id="7dc6a-105">Bir ifade kullanarak `-=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="7dc6a-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="7dc6a-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="7dc6a-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="7dc6a-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7dc6a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="7dc6a-108">Anlamını [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler için çıkarma temsilci temsilcinin işlenenleri için temizleme vb.).</span><span class="sxs-lookup"><span data-stu-id="7dc6a-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="7dc6a-109">`-=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7dc6a-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="7dc6a-110">-= İşleci ayrıca C# dilinde bir olayın aboneliğini kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7dc6a-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="7dc6a-111">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="7dc6a-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dc6a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dc6a-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7dc6a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dc6a-113">See Also</span></span>

- [<span data-ttu-id="7dc6a-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7dc6a-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7dc6a-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7dc6a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7dc6a-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7dc6a-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
