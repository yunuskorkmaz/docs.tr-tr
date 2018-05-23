---
title: '*= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="65442-102">\*= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="65442-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="65442-103">İkili çarpma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="65442-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65442-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65442-104">Remarks</span></span>  
 <span data-ttu-id="65442-105">Bir ifade kullanılarak `*=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="65442-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="65442-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="65442-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="65442-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="65442-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="65442-108">[\* İşleci](../../../csharp/language-reference/operators/multiplication-operator.md) çarpma gerçekleştirmek sayısal türler için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="65442-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="65442-109">`*=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [* işleci](../../../csharp/language-reference/operators/multiplication-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="65442-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65442-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="65442-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="65442-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65442-111">See Also</span></span>  
 [<span data-ttu-id="65442-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="65442-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65442-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="65442-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65442-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="65442-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
