---
title: C# önişlemci yönergeleri
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1c0a97cabce347be0bc9367f3d090a1fc699db19
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036103"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="9ba5a-102">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9ba5a-102">C# preprocessor directives</span></span>
<span data-ttu-id="9ba5a-103">Bu bölüm, aşağıdaki C# önişlemci yönergeleri hakkında bilgi içerir:</span><span class="sxs-lookup"><span data-stu-id="9ba5a-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="9ba5a-104">#if</span><span class="sxs-lookup"><span data-stu-id="9ba5a-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="9ba5a-105">#else</span><span class="sxs-lookup"><span data-stu-id="9ba5a-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="9ba5a-106">#elif</span><span class="sxs-lookup"><span data-stu-id="9ba5a-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="9ba5a-107">#endif</span><span class="sxs-lookup"><span data-stu-id="9ba5a-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="9ba5a-108">#define</span><span class="sxs-lookup"><span data-stu-id="9ba5a-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="9ba5a-109">#undef</span><span class="sxs-lookup"><span data-stu-id="9ba5a-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="9ba5a-110">#warning</span><span class="sxs-lookup"><span data-stu-id="9ba5a-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="9ba5a-111">#error</span><span class="sxs-lookup"><span data-stu-id="9ba5a-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="9ba5a-112">#line</span><span class="sxs-lookup"><span data-stu-id="9ba5a-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="9ba5a-113">#region</span><span class="sxs-lookup"><span data-stu-id="9ba5a-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="9ba5a-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="9ba5a-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="9ba5a-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="9ba5a-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="9ba5a-116">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="9ba5a-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="9ba5a-117">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="9ba5a-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="9ba5a-118">Daha fazla bilgi ve örnekler tek tek ilgili konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="9ba5a-119">Derleyicinin ayrı bir önişlemci olması gerekmese de, bu bölümde açıklanan yönergeleri yokmuş gibi bir işlenir.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="9ba5a-120">Koşullu derlemede kullanılan yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="9ba5a-121">C ve C++ yönergeleri, makrolara oluşturmak için bu yönergeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="9ba5a-122">Önişlemci yönergesi yalnızca yönerge bir satırda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ba5a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ba5a-123">See also</span></span>

- [<span data-ttu-id="9ba5a-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9ba5a-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9ba5a-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ba5a-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
