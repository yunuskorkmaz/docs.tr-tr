---
title: "&lt;&lt;= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5c2a177182561075442afc3f1b76603c6646bd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="f6f25-102">&lt;&lt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f6f25-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="f6f25-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f6f25-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6f25-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6f25-104">Remarks</span></span>  
 <span data-ttu-id="f6f25-105">Formun bir ifade</span><span class="sxs-lookup"><span data-stu-id="f6f25-105">An expression of the form</span></span>  
  
```  
x <<= y  
```  
  
 <span data-ttu-id="f6f25-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="f6f25-106">is evaluated as</span></span>  
  
```  
x = x << y  
```  
  
 <span data-ttu-id="f6f25-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f6f25-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f6f25-108">[<< İşleci](../../../csharp/language-reference/operators/left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı tarafından sol `y`.</span><span class="sxs-lookup"><span data-stu-id="f6f25-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="f6f25-109">`<<=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](../../../csharp/language-reference/operators/left-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f6f25-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f25-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6f25-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f25-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f25-111">See Also</span></span>  
 [<span data-ttu-id="f6f25-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f6f25-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f6f25-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f6f25-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6f25-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="f6f25-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
