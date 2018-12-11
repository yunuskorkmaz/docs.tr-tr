---
title: -= İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239592"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="52246-102">-= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52246-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="52246-103">Çıkarma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="52246-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52246-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52246-104">Remarks</span></span>  
 <span data-ttu-id="52246-105">Bir ifade kullanarak `-=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="52246-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="52246-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="52246-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="52246-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52246-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="52246-108">Anlamını [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler için çıkarma temsilci temsilcinin işlenenleri için temizleme vb.).</span><span class="sxs-lookup"><span data-stu-id="52246-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="52246-109">`-=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="52246-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="52246-110">-= İşleci ayrıca C# dilinde bir olayın aboneliğini kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52246-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="52246-111">Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="52246-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52246-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="52246-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="52246-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52246-113">See Also</span></span>

- [<span data-ttu-id="52246-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52246-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="52246-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52246-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="52246-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="52246-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
