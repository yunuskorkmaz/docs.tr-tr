---
description: '#Else-C# başvurusu'
title: '#Else-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: fb1a9f30a42c78b5c4c7323ec213ab8c20b9bb76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138182"
---
# <a name="else-c-reference"></a><span data-ttu-id="315f8-103">#else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="315f8-103">#else (C# Reference)</span></span>
<span data-ttu-id="315f8-104">`#else`, önceki [#if](./preprocessor-if.md) veya (isteğe bağlı) [#elif](./preprocessor-elif.md) yönergelerinden hiçbiri olarak değerlendiriyorsa `true` derleyici, ve arasındaki tüm kodları değerlendirmek için bileşik bir koşullu yönerge oluşturmanızı sağlar `#else` `#endif`</span><span class="sxs-lookup"><span data-stu-id="315f8-104">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315f8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="315f8-105">Remarks</span></span>  
 <span data-ttu-id="315f8-106">[#endif](./preprocessor-endif.md) sonraki ön işlemci yönergesi olmalıdır `#else` .</span><span class="sxs-lookup"><span data-stu-id="315f8-106">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="315f8-107">Öğesinin nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) `#else` .</span><span class="sxs-lookup"><span data-stu-id="315f8-107">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315f8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="315f8-108">See also</span></span>

- [<span data-ttu-id="315f8-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="315f8-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="315f8-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="315f8-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="315f8-111">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="315f8-111">C# Preprocessor Directives</span></span>](./index.md)
