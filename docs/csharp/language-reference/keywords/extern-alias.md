---
title: extern takma adı - C# Başvurusu
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713541"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="f011f-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f011f-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="f011f-103">Aynı tam nitelikli tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f011f-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="f011f-104">Örneğin, aynı uygulamada bir derlemenin iki veya daha fazla sürümü kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f011f-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="f011f-105">Dış derleme takma adı kullanılarak, her derlemedeki ad boşlukları, diğer adla adlandırılan kök düzeyindead boşluklarıiçinde paketlenebilir ve bu da aynı dosyada kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f011f-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f011f-106">[Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodla yazılmış bir yöntem bildiren bir yöntem değiştirici olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f011f-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="f011f-107">Aynı tam nitelikli tür adlarına sahip iki derlemeye başvurmak için, bir diğer adın komut isteminde aşağıdaki gibi belirtilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="f011f-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="f011f-108">Bu dış takma adlar `GridV1` `GridV2`oluşturur ve.</span><span class="sxs-lookup"><span data-stu-id="f011f-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="f011f-109">Bu diğer adları bir program içinden kullanmak için, anahtar sözcüğü kullanarak bunlara başvurun. `extern`</span><span class="sxs-lookup"><span data-stu-id="f011f-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="f011f-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f011f-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="f011f-111">Her extern diğer ad bildirimi, genel ad alanına paralel (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="f011f-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="f011f-112">Böylece, her derlemeden gelen türler, uygun ad alanı-diğer adlarına dayanan tam nitelikli adlarını kullanarak belirsizlik olmadan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="f011f-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="f011f-113">Önceki örnekte, `GridV1::Grid` 'den `grid.dll`ızgara denetimi `GridV2::Grid` olacaktır ve `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="f011f-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f011f-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f011f-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f011f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f011f-115">See also</span></span>

- [<span data-ttu-id="f011f-116">C# Referans</span><span class="sxs-lookup"><span data-stu-id="f011f-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f011f-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f011f-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f011f-118">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="f011f-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f011f-119">:: Operatör</span><span class="sxs-lookup"><span data-stu-id="f011f-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="f011f-120">-referans (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f011f-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
