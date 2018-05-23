---
title: -&gt; İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="c5d5c-102">-&gt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c5d5c-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="c5d5c-103">`->` İşleci, birleştirir işaretçi başvurusunun kaldırılmasının ve üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="c5d5c-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5d5c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5d5c-104">Remarks</span></span>  
 <span data-ttu-id="c5d5c-105">Bir ifade formun</span><span class="sxs-lookup"><span data-stu-id="c5d5c-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="c5d5c-106">(burada `x` işaretçi türü `T*` ve `y` üyesi `T`), eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="c5d5c-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="c5d5c-107">`->` İşleci olarak işaretlenen kod kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="c5d5c-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="c5d5c-108">`->` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c5d5c-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5d5c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5d5c-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c5d5c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d5c-110">See Also</span></span>  
 [<span data-ttu-id="c5d5c-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5d5c-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5d5c-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c5d5c-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5d5c-113">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c5d5c-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
