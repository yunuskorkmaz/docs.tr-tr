---
title: '#endif - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712552"
---
# <a name="endif-c-reference"></a><span data-ttu-id="9db30-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9db30-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9db30-103">`#endif`[#if](./preprocessor-if.md) yönergesi ile başlayan koşullu bir direktifin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9db30-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="9db30-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9db30-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9db30-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9db30-105">Remarks</span></span>  
 <span data-ttu-id="9db30-106">Bir `#if` yönergeyle başlayan koşullu bir yönerge, `#endif` bir yönergeyle açıkça sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9db30-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9db30-107">Nasıl [#if](./preprocessor-if.md) kullanılacağına bir örnek `#endif`için #if bakın.</span><span class="sxs-lookup"><span data-stu-id="9db30-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db30-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9db30-108">See also</span></span>

- [<span data-ttu-id="9db30-109">C# Referans</span><span class="sxs-lookup"><span data-stu-id="9db30-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9db30-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9db30-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9db30-111">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="9db30-111">C# Preprocessor Directives</span></span>](./index.md)
