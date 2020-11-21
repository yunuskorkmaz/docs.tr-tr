---
description: C# ön işlemci yönergeleri
title: C# ön işlemci yönergeleri
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1269522b2687b76292f7b796a4ffc8095f23442e
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099067"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="e0540-103">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e0540-103">C# preprocessor directives</span></span>

<span data-ttu-id="e0540-104">Bu bölüm aşağıdaki C# Önişlemci yönergeleri hakkında bilgiler içerir:</span><span class="sxs-lookup"><span data-stu-id="e0540-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="e0540-105">#if</span><span class="sxs-lookup"><span data-stu-id="e0540-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="e0540-106">#else</span><span class="sxs-lookup"><span data-stu-id="e0540-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="e0540-107">#elif</span><span class="sxs-lookup"><span data-stu-id="e0540-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="e0540-108">#endif</span><span class="sxs-lookup"><span data-stu-id="e0540-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="e0540-109">#define</span><span class="sxs-lookup"><span data-stu-id="e0540-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="e0540-110">#undef</span><span class="sxs-lookup"><span data-stu-id="e0540-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="e0540-111">#warning</span><span class="sxs-lookup"><span data-stu-id="e0540-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="e0540-112">#error</span><span class="sxs-lookup"><span data-stu-id="e0540-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="e0540-113">#line</span><span class="sxs-lookup"><span data-stu-id="e0540-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="e0540-114">#nullable</span><span class="sxs-lookup"><span data-stu-id="e0540-114">#nullable</span></span>](./preprocessor-nullable.md)
- [<span data-ttu-id="e0540-115">#region</span><span class="sxs-lookup"><span data-stu-id="e0540-115">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="e0540-116">#endregion</span><span class="sxs-lookup"><span data-stu-id="e0540-116">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="e0540-117">#pragma</span><span class="sxs-lookup"><span data-stu-id="e0540-117">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="e0540-118">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="e0540-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="e0540-119">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="e0540-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="e0540-120">Daha fazla bilgi ve örnek için bireysel konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="e0540-120">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="e0540-121">Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="e0540-121">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="e0540-122">Koşullu derlemede yardımcı olmak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="e0540-122">They are used to help in conditional compilation.</span></span> <span data-ttu-id="e0540-123">C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e0540-123">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="e0540-124">Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0540-124">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0540-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0540-125">See also</span></span>

- [<span data-ttu-id="e0540-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0540-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0540-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0540-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
