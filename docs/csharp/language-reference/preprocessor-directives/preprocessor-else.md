---
title: '#Else- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605724"
---
# <a name="else-c-reference"></a><span data-ttu-id="0e76e-102">#else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0e76e-102">#else (C# Reference)</span></span>
<span data-ttu-id="0e76e-103">`#else`, yukarıdaki [#if](./preprocessor-if.md) veya (isteğe bağlı) [#elif](./preprocessor-elif.md) yönergelerinden hiçbiri olarak `true`değerlendiriyorsa, derleyicinin tüm kodu ve arasındaki `#else` daha `#endif`sonra.</span><span class="sxs-lookup"><span data-stu-id="0e76e-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e76e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e76e-104">Remarks</span></span>  
 <span data-ttu-id="0e76e-105">[#endif](./preprocessor-endif.md) sonraki ön işlemci yönergesi `#else`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e76e-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="0e76e-106">Öğesinin [](./preprocessor-if.md) nasıl kullanılacağına `#else`ilişkin bir örnek için bkz. #if.</span><span class="sxs-lookup"><span data-stu-id="0e76e-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e76e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e76e-107">See also</span></span>

- [<span data-ttu-id="0e76e-108">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0e76e-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0e76e-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e76e-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0e76e-110">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0e76e-110">C# Preprocessor Directives</span></span>](./index.md)
