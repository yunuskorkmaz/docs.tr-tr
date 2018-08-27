---
title: -&gt; İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930310"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="f6cfc-102">-&gt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f6cfc-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="f6cfc-103">`->` İşleci, bir araya getirir işaretçi başvurusunun kaldırılması ve üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="f6cfc-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6cfc-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6cfc-104">Remarks</span></span>  
 <span data-ttu-id="f6cfc-105">Bir ifade form</span><span class="sxs-lookup"><span data-stu-id="f6cfc-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="f6cfc-106">(burada `x` bir işaretçi türü `T*` ve `y` üyesi `T`) için eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="f6cfc-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="f6cfc-107">`->` İşleci olarak işaretlenmiş kod kullanılabilir [güvenli](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="f6cfc-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="f6cfc-108">`->` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="f6cfc-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6cfc-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6cfc-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f6cfc-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6cfc-110">See Also</span></span>

- [<span data-ttu-id="f6cfc-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f6cfc-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f6cfc-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f6cfc-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f6cfc-113">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f6cfc-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
