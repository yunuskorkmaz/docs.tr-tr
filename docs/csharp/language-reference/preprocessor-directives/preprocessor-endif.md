---
title: '#endif- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608574"
---
# <a name="endif-c-reference"></a><span data-ttu-id="78ef1-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="78ef1-102">#endif (C# Reference)</span></span>
<span data-ttu-id="78ef1-103">`#endif`[#if](./preprocessor-if.md) yönergesiyle başlayan bir koşul yönergesinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="78ef1-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="78ef1-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="78ef1-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="78ef1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78ef1-105">Remarks</span></span>  
 <span data-ttu-id="78ef1-106">`#if` Yönergeyle başlayan koşullu yönerge, açıkça bir `#endif` yönergeyle sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78ef1-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="78ef1-107">Öğesinin [](./preprocessor-if.md) nasıl kullanılacağına `#endif`ilişkin bir örnek için bkz. #if.</span><span class="sxs-lookup"><span data-stu-id="78ef1-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ef1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78ef1-108">See also</span></span>

- [<span data-ttu-id="78ef1-109">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="78ef1-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78ef1-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="78ef1-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78ef1-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="78ef1-111">C# Preprocessor Directives</span></span>](./index.md)
