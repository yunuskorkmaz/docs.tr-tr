---
title: extern alias (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="4b460-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4b460-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="4b460-103">Aynı tam olarak nitelenmiş tür adları olan derlemeler iki sürümü başvuru gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4b460-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="4b460-104">Örneğin, bir derlemeyi iki veya daha fazla sürümünü ve aynı uygulamada kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4b460-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="4b460-105">Bir dış derleme diğer adı kullanarak, ad alanlarının her derlemesinden bunları aynı dosyada kullanılacak sağlayan diğer adı tarafından adlı kök düzeyinde ad içinde sarmalamak.</span><span class="sxs-lookup"><span data-stu-id="4b460-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b460-106">[Extern](../../../csharp/language-reference/keywords/extern.md) anahtar sözcüğü yönetilmeyen kod içinde yazılmış bir yöntem bildirme bir yöntemi değiştirici olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b460-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="4b460-107">İki derlemeleri aynı tam olarak nitelenmiş tür adları ile başvurmak için bir diğer ad bir komut isteminde şu şekilde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="4b460-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="4b460-108">Bu dış diğer adlar oluşturur `GridV1` ve `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="4b460-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="4b460-109">Bir programdan gelen bu diğer adları kullanmak için bunları kullanarak başvuru `extern` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4b460-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="4b460-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4b460-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="4b460-111">Parallels (ancak içinde bulunmayacak) bir ek kök düzeyinde ad alanı her extern alias bildirimi tanıtır genel ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4b460-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="4b460-112">Bu nedenle her derleme türlerinden için karışıklık uygun ad alanı-diğer kökü kullanıcıların tam adı, kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b460-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="4b460-113">Önceki örnekte, `GridV1::Grid` kılavuz denetiminden olacaktır `grid.dll`, ve `GridV2::Grid` kılavuz denetiminden olacaktır `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="4b460-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4b460-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="4b460-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b460-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b460-115">See Also</span></span>  
 [<span data-ttu-id="4b460-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b460-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4b460-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4b460-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4b460-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4b460-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4b460-119">Namespace anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4b460-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="4b460-120">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="4b460-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="4b460-121">/ Reference (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4b460-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
