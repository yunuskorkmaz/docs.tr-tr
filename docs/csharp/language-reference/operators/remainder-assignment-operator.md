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
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998662"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5ffec-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5ffec-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="5ffec-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="5ffec-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ffec-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ffec-104">Remarks</span></span>  
 <span data-ttu-id="5ffec-105">Bir ifade kullanarak `%=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="5ffec-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="5ffec-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="5ffec-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="5ffec-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5ffec-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="5ffec-108">[% İşleci](../../../csharp/language-reference/operators/remainder-operator.md) bölme işleminden kalanı hesaplamak sayısal türleri için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="5ffec-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="5ffec-109">`%=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [% işleci](../../../csharp/language-reference/operators/remainder-operator.md) (bkz [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5ffec-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ffec-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ffec-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5ffec-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ffec-111">See Also</span></span>

- [<span data-ttu-id="5ffec-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5ffec-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5ffec-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5ffec-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5ffec-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5ffec-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
