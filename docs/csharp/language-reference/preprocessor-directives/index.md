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
ms.openlocfilehash: a7ffca8b39f1bd9f05193bccbb6d90e67fa262c9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132371"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="609cf-103">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="609cf-103">C# preprocessor directives</span></span>
<span data-ttu-id="609cf-104">Bu bölüm aşağıdaki C# Önişlemci yönergeleri hakkında bilgiler içerir:</span><span class="sxs-lookup"><span data-stu-id="609cf-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="609cf-105">#if</span><span class="sxs-lookup"><span data-stu-id="609cf-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="609cf-106">#else</span><span class="sxs-lookup"><span data-stu-id="609cf-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="609cf-107">#elif</span><span class="sxs-lookup"><span data-stu-id="609cf-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="609cf-108">#endif</span><span class="sxs-lookup"><span data-stu-id="609cf-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="609cf-109">#define</span><span class="sxs-lookup"><span data-stu-id="609cf-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="609cf-110">#undef</span><span class="sxs-lookup"><span data-stu-id="609cf-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="609cf-111">#warning</span><span class="sxs-lookup"><span data-stu-id="609cf-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="609cf-112">#error</span><span class="sxs-lookup"><span data-stu-id="609cf-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="609cf-113">#line</span><span class="sxs-lookup"><span data-stu-id="609cf-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="609cf-114">#region</span><span class="sxs-lookup"><span data-stu-id="609cf-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="609cf-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="609cf-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="609cf-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="609cf-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="609cf-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="609cf-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="609cf-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="609cf-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="609cf-119">Daha fazla bilgi ve örnek için bireysel konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="609cf-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="609cf-120">Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="609cf-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="609cf-121">Koşullu derlemede yardımcı olmak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="609cf-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="609cf-122">C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="609cf-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="609cf-123">Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="609cf-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="609cf-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609cf-124">See also</span></span>

- [<span data-ttu-id="609cf-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="609cf-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="609cf-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="609cf-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
