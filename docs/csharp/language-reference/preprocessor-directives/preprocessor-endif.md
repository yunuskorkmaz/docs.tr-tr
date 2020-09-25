---
description: '#endif-C# başvurusu'
title: '#endif-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 0ccc00ceab2aa67c77140e3ef09907ba260d7e9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168640"
---
# <a name="endif-c-reference"></a><span data-ttu-id="2e2a4-103">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2e2a4-103">#endif (C# Reference)</span></span>

<span data-ttu-id="2e2a4-104">`#endif`[#if](./preprocessor-if.md) yönergesiyle başlayan bir koşul yönergesinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e2a4-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="2e2a4-105">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="2e2a4-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e2a4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e2a4-106">Remarks</span></span>  

 <span data-ttu-id="2e2a4-107">Yönergeyle başlayan koşullu yönerge `#if` , açıkça bir `#endif` yönergeyle sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e2a4-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="2e2a4-108">Öğesinin nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) `#endif` .</span><span class="sxs-lookup"><span data-stu-id="2e2a4-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2a4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e2a4-109">See also</span></span>

- [<span data-ttu-id="2e2a4-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2e2a4-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2e2a4-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2e2a4-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2e2a4-112">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2e2a4-112">C# Preprocessor Directives</span></span>](./index.md)
