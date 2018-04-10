---
title: -&gt;İşleci (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="a8f4d-102">-&gt;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a8f4d-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="a8f4d-103">`->` İşleci, birleştirir işaretçi başvurusunun kaldırılmasının ve üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="a8f4d-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8f4d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8f4d-104">Remarks</span></span>  
 <span data-ttu-id="a8f4d-105">Bir ifade formun</span><span class="sxs-lookup"><span data-stu-id="a8f4d-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="a8f4d-106">(burada `x` işaretçi türü `T*` ve `y` üyesi `T`), eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="a8f4d-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="a8f4d-107">`->` İşleci olarak işaretlenen kod kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a8f4d-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="a8f4d-108">`->` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a8f4d-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f4d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8f4d-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f4d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f4d-110">See Also</span></span>  
 [<span data-ttu-id="a8f4d-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a8f4d-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a8f4d-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8f4d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8f4d-113">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="a8f4d-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
