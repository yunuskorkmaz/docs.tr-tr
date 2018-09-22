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
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584665"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="df7b7-102">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="df7b7-102">C# preprocessor directives</span></span>
<span data-ttu-id="df7b7-103">Bu bölüm, aşağıdaki C# önişlemci yönergeleri hakkında bilgi içerir:</span><span class="sxs-lookup"><span data-stu-id="df7b7-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="df7b7-104">#if</span><span class="sxs-lookup"><span data-stu-id="df7b7-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="df7b7-105">#else</span><span class="sxs-lookup"><span data-stu-id="df7b7-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="df7b7-106">#elif</span><span class="sxs-lookup"><span data-stu-id="df7b7-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="df7b7-107">#endif</span><span class="sxs-lookup"><span data-stu-id="df7b7-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="df7b7-108">#define</span><span class="sxs-lookup"><span data-stu-id="df7b7-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="df7b7-109">#undef</span><span class="sxs-lookup"><span data-stu-id="df7b7-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="df7b7-110">#warning</span><span class="sxs-lookup"><span data-stu-id="df7b7-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="df7b7-111">#error</span><span class="sxs-lookup"><span data-stu-id="df7b7-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="df7b7-112">#line</span><span class="sxs-lookup"><span data-stu-id="df7b7-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="df7b7-113">#region</span><span class="sxs-lookup"><span data-stu-id="df7b7-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="df7b7-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="df7b7-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="df7b7-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="df7b7-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="df7b7-116">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="df7b7-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="df7b7-117">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="df7b7-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="df7b7-118">Daha fazla bilgi ve örnekler tek tek ilgili konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="df7b7-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="df7b7-119">Derleyicinin ayrı bir önişlemci olması gerekmese de, bu bölümde açıklanan yönergeleri yokmuş gibi bir işlenir.</span><span class="sxs-lookup"><span data-stu-id="df7b7-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="df7b7-120">Koşullu derlemede kullanılan yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df7b7-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="df7b7-121">C ve C++ yönergeleri, makrolara oluşturmak için bu yönergeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="df7b7-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="df7b7-122">Önişlemci yönergesi yalnızca yönerge bir satırda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df7b7-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="df7b7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df7b7-123">See also</span></span>

- [<span data-ttu-id="df7b7-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="df7b7-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="df7b7-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="df7b7-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
