---
title: extern diğer adı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 0fd917d1af38ba558634dfcf5e3a1abf95420a9d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235378"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="2b870-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b870-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="2b870-103">İki sürümünü tam olarak nitelenmiş tür adları aynı bütünleştirilmiş kodları başvuru yapması gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b870-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="2b870-104">Örneğin, aynı uygulamada iki veya daha fazla derleme sürümünü kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2b870-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="2b870-105">Bir dış bütünleştirilmiş diğer adı kullanarak, aynı dosyada kullanılmak üzere etkinleştirir diğer ad tarafından adlandırılan kök düzeyinde ad alanları içinde her derlemenin ad alanlarını sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b870-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b870-106">[Extern](../../../csharp/language-reference/keywords/extern.md) anahtar sözcüğü yönetilmeyen kodda yazılmış bir yöntemi bildirmek, bir yöntemi değiştirici olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b870-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="2b870-107">İki derlemenin aynı tam olarak nitelenmiş tür adları ile başvurmak için bir diğer ad bir komut isteminde şu şekilde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="2b870-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="2b870-108">Bu dış diğer oluşturur `GridV1` ve `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="2b870-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="2b870-109">Bir programın gelen bu diğer adlar kullanmak için bunları kullanarak başvuru `extern` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2b870-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="2b870-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b870-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="2b870-111">Parallels (ancak içinde yer almıyor) bir ek kök düzeyinde ad alanı her extern diğer ad bildirimi tanıtır genel ad.</span><span class="sxs-lookup"><span data-stu-id="2b870-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="2b870-112">Bu nedenle her derlemesinden türleri için belirsizlik kökü uygun namespace-diğer kullanıcıların tam adı, kullanarak bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="2b870-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="2b870-113">Önceki örnekte, `GridV1::Grid` kılavuz denetiminden olacaktır `grid.dll`, ve `GridV2::Grid` kılavuz denetiminden olacaktır `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="2b870-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2b870-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2b870-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b870-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b870-115">See Also</span></span>

- [<span data-ttu-id="2b870-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b870-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2b870-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b870-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2b870-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2b870-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2b870-119">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2b870-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="2b870-120">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="2b870-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="2b870-121">/ Reference (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2b870-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
