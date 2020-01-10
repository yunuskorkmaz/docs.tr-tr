---
title: '#Else- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712565"
---
# <a name="else-c-reference"></a><span data-ttu-id="b02ff-102">#else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b02ff-102">#else (C# Reference)</span></span>
<span data-ttu-id="b02ff-103">`#else`, yukarıdaki [#if](./preprocessor-if.md) veya (isteğe bağlı) [#elif](./preprocessor-elif.md) yönergelerinden hiçbiri `true`değerlendiriyorsa derleyici, `#else` ve sonraki `#endif`arasındaki tüm kodları değerlendirmek için bileşik bir koşullu yönerge oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02ff-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b02ff-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b02ff-104">Remarks</span></span>  
 <span data-ttu-id="b02ff-105">`#else`sonrasında [#endif](./preprocessor-endif.md) sonraki Önişlemci yönergesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b02ff-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="b02ff-106">`#else`nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="b02ff-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02ff-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b02ff-107">See also</span></span>

- [<span data-ttu-id="b02ff-108">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b02ff-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b02ff-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b02ff-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b02ff-110">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b02ff-110">C# Preprocessor Directives</span></span>](./index.md)
