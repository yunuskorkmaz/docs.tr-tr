---
title: += İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933793"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6a458-102">+= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6a458-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="6a458-103">Toplama atama işleci.</span><span class="sxs-lookup"><span data-stu-id="6a458-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a458-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a458-104">Remarks</span></span>  
 <span data-ttu-id="6a458-105">Bir ifade kullanarak `+=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="6a458-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```csharp  
x += y  
```  
  
 <span data-ttu-id="6a458-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="6a458-106">is equivalent to</span></span>  
  
```csharp  
x = x + y  
```  
  
 <span data-ttu-id="6a458-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6a458-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6a458-108">Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler, dize işlenenler ve benzeri için birleştirme için ek olarak).</span><span class="sxs-lookup"><span data-stu-id="6a458-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="6a458-109">`+=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6a458-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="6a458-110">`+=` İşleci ayrıca bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için kullanılır; bu tür yöntemler olay işleyicileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6a458-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="6a458-111">Kullanımını `+=` bu bağlam içinde işleç olarak adlandırılır *bir olaya abone olma*.</span><span class="sxs-lookup"><span data-stu-id="6a458-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="6a458-112">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a458-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a458-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a458-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6a458-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a458-114">See Also</span></span>

- [<span data-ttu-id="6a458-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6a458-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6a458-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6a458-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6a458-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6a458-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
