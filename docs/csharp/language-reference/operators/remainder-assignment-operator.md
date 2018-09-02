---
title: '%= İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399497"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d6ac2-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d6ac2-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="d6ac2-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="d6ac2-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ac2-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6ac2-104">Remarks</span></span>  
 <span data-ttu-id="d6ac2-105">Bir ifade kullanarak `%=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="d6ac2-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="d6ac2-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="d6ac2-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="d6ac2-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d6ac2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d6ac2-108">[% İşleci](../../../csharp/language-reference/operators/remainder-operator.md) bölme işleminden kalanı hesaplamak sayısal türleri için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="d6ac2-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="d6ac2-109">`%=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [% işleci](../../../csharp/language-reference/operators/remainder-operator.md) (bkz [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d6ac2-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ac2-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6ac2-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ac2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ac2-111">See Also</span></span>

- [<span data-ttu-id="d6ac2-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d6ac2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d6ac2-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6ac2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d6ac2-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d6ac2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
