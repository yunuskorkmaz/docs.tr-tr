---
title: C# ön işlemci yönergeleri
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 54067777ed2e92eea263b17cce0d4cdf13ed731d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689326"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="b53a0-102">C# ön işlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b53a0-102">C# preprocessor directives</span></span>
<span data-ttu-id="b53a0-103">Bu bölüm, aşağıdaki C# önişlemci yönergeleri hakkında bilgi içerir:</span><span class="sxs-lookup"><span data-stu-id="b53a0-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="b53a0-104">#if</span><span class="sxs-lookup"><span data-stu-id="b53a0-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="b53a0-105">#else</span><span class="sxs-lookup"><span data-stu-id="b53a0-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="b53a0-106">#elif</span><span class="sxs-lookup"><span data-stu-id="b53a0-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="b53a0-107">#endif</span><span class="sxs-lookup"><span data-stu-id="b53a0-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="b53a0-108">#define</span><span class="sxs-lookup"><span data-stu-id="b53a0-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="b53a0-109">#undef</span><span class="sxs-lookup"><span data-stu-id="b53a0-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="b53a0-110">#warning</span><span class="sxs-lookup"><span data-stu-id="b53a0-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="b53a0-111">#error</span><span class="sxs-lookup"><span data-stu-id="b53a0-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="b53a0-112">#line</span><span class="sxs-lookup"><span data-stu-id="b53a0-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="b53a0-113">#region</span><span class="sxs-lookup"><span data-stu-id="b53a0-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="b53a0-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="b53a0-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="b53a0-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="b53a0-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="b53a0-116">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="b53a0-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="b53a0-117">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="b53a0-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="b53a0-118">Daha fazla bilgi ve örnekler tek tek ilgili konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="b53a0-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="b53a0-119">Derleyicinin ayrı bir önişlemci olması gerekmese de, bu bölümde açıklanan yönergeleri yokmuş gibi bir işlenir.</span><span class="sxs-lookup"><span data-stu-id="b53a0-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="b53a0-120">Koşullu derlemede kullanılan yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b53a0-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="b53a0-121">C ve C++ yönergeleri, makrolara oluşturmak için bu yönergeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b53a0-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="b53a0-122">Önişlemci yönergesi yalnızca yönerge bir satırda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b53a0-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="b53a0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b53a0-123">See also</span></span>

- [<span data-ttu-id="b53a0-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b53a0-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b53a0-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b53a0-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
