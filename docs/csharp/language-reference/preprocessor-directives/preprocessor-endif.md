---
title: '#endif- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712552"
---
# <a name="endif-c-reference"></a><span data-ttu-id="9739f-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9739f-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9739f-103">`#endif`, [#if](./preprocessor-if.md) yönergesiyle başlayan bir koşul yönergesinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9739f-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="9739f-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9739f-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9739f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9739f-105">Remarks</span></span>  
 <span data-ttu-id="9739f-106">`#if` yönergesiyle başlayan koşullu yönerge, açıkça bir `#endif` yönergesi ile sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9739f-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9739f-107">`#endif`nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="9739f-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9739f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9739f-108">See also</span></span>

- [<span data-ttu-id="9739f-109">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9739f-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9739f-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9739f-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9739f-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9739f-111">C# Preprocessor Directives</span></span>](./index.md)
