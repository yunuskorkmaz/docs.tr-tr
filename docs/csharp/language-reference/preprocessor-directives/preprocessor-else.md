---
title: '#else - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712565"
---
# <a name="else-c-reference"></a><span data-ttu-id="e2d1f-102">#else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e2d1f-102">#else (C# Reference)</span></span>
<span data-ttu-id="e2d1f-103">`#else`bileşik koşullu yönerge oluşturmanıza olanak sağlar, böylece, yukarıdaki [#if](./preprocessor-if.md) veya (isteğe bağlı) `true` [#elif](./preprocessor-elif.md) yönergelerinde ifadelerhiçbiri değerlendirmek, derleyici ve sonraki arasındaki `#else` `#endif`tüm kodu değerlendirecektir .</span><span class="sxs-lookup"><span data-stu-id="e2d1f-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2d1f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2d1f-104">Remarks</span></span>  
 <span data-ttu-id="e2d1f-105">[#endif](./preprocessor-endif.md) sonra `#else`bir sonraki önişlemci yönergesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2d1f-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="e2d1f-106">Nasıl [#if](./preprocessor-if.md) kullanılacağına bir örnek `#else`için #if bakın.</span><span class="sxs-lookup"><span data-stu-id="e2d1f-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d1f-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2d1f-107">See also</span></span>

- [<span data-ttu-id="e2d1f-108">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e2d1f-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2d1f-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2d1f-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2d1f-110">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="e2d1f-110">C# Preprocessor Directives</span></span>](./index.md)
