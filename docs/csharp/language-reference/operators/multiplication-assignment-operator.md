---
title: '*= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: e47bc5c681c94ac3fc5c345c56b3814350ffa5ec
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517174"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="77531-102">\*= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="77531-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="77531-103">İkili çarpma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="77531-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77531-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77531-104">Remarks</span></span>  
 <span data-ttu-id="77531-105">Bir ifade kullanarak `*=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="77531-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="77531-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="77531-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="77531-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="77531-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="77531-108">[\* İşleci](../../../csharp/language-reference/operators/multiplication-operator.md) çarpma işlemi gerçekleştirmek sayısal türleri için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="77531-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="77531-109">`*=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [* işleci](../../../csharp/language-reference/operators/multiplication-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="77531-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77531-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="77531-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="77531-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77531-111">See Also</span></span>

- [<span data-ttu-id="77531-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="77531-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="77531-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="77531-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="77531-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="77531-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
