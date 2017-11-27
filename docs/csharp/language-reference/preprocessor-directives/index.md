---
title: "C# önişlemci yönergeleri"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6378c8df794a4ee75e7b5ca283b18b228ba46383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="06efe-102">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="06efe-102">C# preprocessor directives</span></span>
<span data-ttu-id="06efe-103">Bu bölümde aşağıdaki C# önişlemci yönergeleri hakkında bilgi içerir:</span><span class="sxs-lookup"><span data-stu-id="06efe-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="06efe-104">#if</span><span class="sxs-lookup"><span data-stu-id="06efe-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="06efe-105">#else</span><span class="sxs-lookup"><span data-stu-id="06efe-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="06efe-106">#elif</span><span class="sxs-lookup"><span data-stu-id="06efe-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="06efe-107">#endif</span><span class="sxs-lookup"><span data-stu-id="06efe-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="06efe-108">#define</span><span class="sxs-lookup"><span data-stu-id="06efe-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="06efe-109">#undef</span><span class="sxs-lookup"><span data-stu-id="06efe-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="06efe-110">#warning</span><span class="sxs-lookup"><span data-stu-id="06efe-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="06efe-111">#error</span><span class="sxs-lookup"><span data-stu-id="06efe-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="06efe-112">#line</span><span class="sxs-lookup"><span data-stu-id="06efe-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="06efe-113">#region</span><span class="sxs-lookup"><span data-stu-id="06efe-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="06efe-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="06efe-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="06efe-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="06efe-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="06efe-116">#pragma Uyarısı</span><span class="sxs-lookup"><span data-stu-id="06efe-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="06efe-117">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="06efe-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="06efe-118">Daha fazla bilgi ve örnekler için tek tek konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="06efe-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="06efe-119">Derleyici ayrı önişlemci olması gerekmese de, bu bölümde açıklanan yönergeleri gibi varsa bir işlenir.</span><span class="sxs-lookup"><span data-stu-id="06efe-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="06efe-120">Koşullu derleme yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06efe-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="06efe-121">C ve C++ yönergeleri makroları oluşturmak için bu yönergeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="06efe-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="06efe-122">Önişlemci yönergesi yalnızca yönerge bir satırda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06efe-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="06efe-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06efe-123">See also</span></span>
 [<span data-ttu-id="06efe-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="06efe-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="06efe-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="06efe-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
