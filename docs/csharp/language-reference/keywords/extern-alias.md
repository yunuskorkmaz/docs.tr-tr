---
title: extern diğer ad C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: cfb662203216aa6ca208ceec20d55164c65163dc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626652"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="cdb86-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cdb86-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="cdb86-103">Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cdb86-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="cdb86-104">Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cdb86-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="cdb86-105">Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="cdb86-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdb86-106">[Extern](../../../csharp/language-reference/keywords/extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdb86-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="cdb86-107">Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="cdb86-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="cdb86-108">Bu, dış diğer adları `GridV1` oluşturur `GridV2`ve.</span><span class="sxs-lookup"><span data-stu-id="cdb86-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="cdb86-109">Bu diğer adları bir program içinden kullanmak için `extern` anahtar sözcüğünü kullanarak bunlara başvurun.</span><span class="sxs-lookup"><span data-stu-id="cdb86-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="cdb86-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cdb86-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="cdb86-111">Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="cdb86-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="cdb86-112">Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="cdb86-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="cdb86-113">Önceki örnekte, `GridV1::Grid` kılavuz `grid.dll`denetimi olur ve `GridV2::Grid` kılavuz denetimi `grid20.dll`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cdb86-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cdb86-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="cdb86-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cdb86-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdb86-115">See also</span></span>

- [<span data-ttu-id="cdb86-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="cdb86-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cdb86-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cdb86-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cdb86-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cdb86-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="cdb86-119">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="cdb86-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="cdb86-120">/Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="cdb86-120">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
