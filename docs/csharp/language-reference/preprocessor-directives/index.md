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
ms.openlocfilehash: 210a024a8062f5070b2a500384f51b37c9d802c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157960"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="dc70f-103">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dc70f-103">C# preprocessor directives</span></span>

<span data-ttu-id="dc70f-104">Bu bölüm aşağıdaki C# Önişlemci yönergeleri hakkında bilgiler içerir:</span><span class="sxs-lookup"><span data-stu-id="dc70f-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="dc70f-105">#if</span><span class="sxs-lookup"><span data-stu-id="dc70f-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="dc70f-106">#else</span><span class="sxs-lookup"><span data-stu-id="dc70f-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="dc70f-107">#elif</span><span class="sxs-lookup"><span data-stu-id="dc70f-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="dc70f-108">#endif</span><span class="sxs-lookup"><span data-stu-id="dc70f-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="dc70f-109">#define</span><span class="sxs-lookup"><span data-stu-id="dc70f-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="dc70f-110">#undef</span><span class="sxs-lookup"><span data-stu-id="dc70f-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="dc70f-111">#warning</span><span class="sxs-lookup"><span data-stu-id="dc70f-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="dc70f-112">#error</span><span class="sxs-lookup"><span data-stu-id="dc70f-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="dc70f-113">#line</span><span class="sxs-lookup"><span data-stu-id="dc70f-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="dc70f-114">#region</span><span class="sxs-lookup"><span data-stu-id="dc70f-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="dc70f-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="dc70f-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="dc70f-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="dc70f-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="dc70f-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="dc70f-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="dc70f-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="dc70f-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="dc70f-119">Daha fazla bilgi ve örnek için bireysel konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="dc70f-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="dc70f-120">Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="dc70f-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="dc70f-121">Koşullu derlemede yardımcı olmak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="dc70f-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="dc70f-122">C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dc70f-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="dc70f-123">Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc70f-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc70f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc70f-124">See also</span></span>

- [<span data-ttu-id="dc70f-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dc70f-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dc70f-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dc70f-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
