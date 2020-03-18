---
title: C# ön işlemci yönergeleri
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: f63ba3e0bd89a88ad04b14c2f359a8cde65e8f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "69608603"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="c261b-102">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c261b-102">C# preprocessor directives</span></span>
<span data-ttu-id="c261b-103">Bu bölümde aşağıdaki C# önişlemci yönergeleri hakkında bilgi içerir:</span><span class="sxs-lookup"><span data-stu-id="c261b-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="c261b-104">#if</span><span class="sxs-lookup"><span data-stu-id="c261b-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="c261b-105">#else</span><span class="sxs-lookup"><span data-stu-id="c261b-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="c261b-106">#elif</span><span class="sxs-lookup"><span data-stu-id="c261b-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="c261b-107">#endif</span><span class="sxs-lookup"><span data-stu-id="c261b-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="c261b-108"># define</span><span class="sxs-lookup"><span data-stu-id="c261b-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="c261b-109">#undef</span><span class="sxs-lookup"><span data-stu-id="c261b-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="c261b-110">#warning</span><span class="sxs-lookup"><span data-stu-id="c261b-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="c261b-111">#error</span><span class="sxs-lookup"><span data-stu-id="c261b-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="c261b-112">#line</span><span class="sxs-lookup"><span data-stu-id="c261b-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="c261b-113">#region</span><span class="sxs-lookup"><span data-stu-id="c261b-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="c261b-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="c261b-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="c261b-115"># pragma</span><span class="sxs-lookup"><span data-stu-id="c261b-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="c261b-116">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="c261b-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="c261b-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c261b-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="c261b-118">Daha fazla bilgi ve örnekler için tek tek konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="c261b-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="c261b-119">Derleyicinin ayrı bir önişlemcisi olmamasına rağmen, bu bölümde açıklanan yönergeler varsa işlenir.</span><span class="sxs-lookup"><span data-stu-id="c261b-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="c261b-120">Koşullu derlemede yardımcı olmak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="c261b-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="c261b-121">C ve C++ yönergelerinin aksine, makro oluşturmak için bu yönergeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c261b-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="c261b-122">Bir satırdaki tek yönerge önişlemci yönergesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c261b-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="c261b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c261b-123">See also</span></span>

- [<span data-ttu-id="c261b-124">C# Referans</span><span class="sxs-lookup"><span data-stu-id="c261b-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c261b-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c261b-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
