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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608603"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="0b1b9-102">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0b1b9-102">C# preprocessor directives</span></span>
<span data-ttu-id="0b1b9-103">Bu bölüm aşağıdaki C# Önişlemci yönergeleri hakkında bilgiler içerir:</span><span class="sxs-lookup"><span data-stu-id="0b1b9-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="0b1b9-104">#if</span><span class="sxs-lookup"><span data-stu-id="0b1b9-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="0b1b9-105">#else</span><span class="sxs-lookup"><span data-stu-id="0b1b9-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="0b1b9-106">#elif</span><span class="sxs-lookup"><span data-stu-id="0b1b9-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="0b1b9-107">#endif</span><span class="sxs-lookup"><span data-stu-id="0b1b9-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="0b1b9-108">#define</span><span class="sxs-lookup"><span data-stu-id="0b1b9-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="0b1b9-109">#undef</span><span class="sxs-lookup"><span data-stu-id="0b1b9-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="0b1b9-110">#warning</span><span class="sxs-lookup"><span data-stu-id="0b1b9-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="0b1b9-111">#error</span><span class="sxs-lookup"><span data-stu-id="0b1b9-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="0b1b9-112">#line</span><span class="sxs-lookup"><span data-stu-id="0b1b9-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="0b1b9-113">#region</span><span class="sxs-lookup"><span data-stu-id="0b1b9-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="0b1b9-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="0b1b9-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="0b1b9-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="0b1b9-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="0b1b9-116">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="0b1b9-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="0b1b9-117">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="0b1b9-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="0b1b9-118">Daha fazla bilgi ve örnek için bireysel konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="0b1b9-119">Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="0b1b9-120">Koşullu derlemede yardımcı olmak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="0b1b9-121">C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="0b1b9-122">Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b1b9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b1b9-123">See also</span></span>

- [<span data-ttu-id="0b1b9-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0b1b9-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0b1b9-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b1b9-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
