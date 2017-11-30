---
title: "*= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="484c8-102">*= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="484c8-102">*= Operator (C# Reference)</span></span>
<span data-ttu-id="484c8-103">İkili çarpma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="484c8-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="484c8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="484c8-104">Remarks</span></span>  
 <span data-ttu-id="484c8-105">Bir ifade kullanılarak `*=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="484c8-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="484c8-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="484c8-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="484c8-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="484c8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="484c8-108">[* İşleci](../../../csharp/language-reference/operators/multiplication-operator.md) çarpma gerçekleştirmek sayısal türler için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="484c8-108">The [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="484c8-109">`*=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [* işleci](../../../csharp/language-reference/operators/multiplication-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="484c8-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="484c8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="484c8-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="484c8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="484c8-111">See Also</span></span>  
 [<span data-ttu-id="484c8-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="484c8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="484c8-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="484c8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="484c8-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="484c8-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
