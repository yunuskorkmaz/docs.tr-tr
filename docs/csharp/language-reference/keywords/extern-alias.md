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
ms.openlocfilehash: 09d1247c51f0e600973840cfef2d3b396d9bf0d0
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520282"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="d9312-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d9312-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="d9312-103">Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d9312-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="d9312-104">Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d9312-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="d9312-105">Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="d9312-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9312-106">[Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9312-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="d9312-107">Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="d9312-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="d9312-108">Bu, `GridV1` ve `GridV2` dış diğer adlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9312-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="d9312-109">Bu diğer adları bir program içinden kullanmak için, `extern` anahtar sözcüğünü kullanarak bunlara başvurun.</span><span class="sxs-lookup"><span data-stu-id="d9312-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="d9312-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d9312-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="d9312-111">Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="d9312-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="d9312-112">Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="d9312-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="d9312-113">Önceki örnekte, `GridV1::Grid` kılavuz denetimi `grid.dll` ve `grid20.dll` `GridV2::Grid` kılavuz denetimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d9312-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d9312-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d9312-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9312-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9312-115">See also</span></span>

- [<span data-ttu-id="d9312-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="d9312-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9312-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d9312-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9312-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d9312-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d9312-119">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="d9312-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="d9312-120">-Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d9312-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
