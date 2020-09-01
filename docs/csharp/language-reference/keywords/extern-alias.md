---
description: extern diğer adı-C# başvurusu
title: extern diğer adı-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 301ae06ec02fa6f09257dc87383bc2ec7f589b6d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139014"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="2b63d-103">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b63d-103">extern alias (C# Reference)</span></span>
<span data-ttu-id="2b63d-104">Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-104">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="2b63d-105">Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-105">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="2b63d-106">Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-106">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b63d-107">[Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b63d-107">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="2b63d-108">Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="2b63d-108">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="2b63d-109">Bu, dış diğer adları oluşturur `GridV1` ve `GridV2` .</span><span class="sxs-lookup"><span data-stu-id="2b63d-109">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="2b63d-110">Bu diğer adları bir program içinden kullanmak için anahtar sözcüğünü kullanarak bunlara başvurun `extern` .</span><span class="sxs-lookup"><span data-stu-id="2b63d-110">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="2b63d-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b63d-111">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="2b63d-112">Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="2b63d-112">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="2b63d-113">Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-113">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="2b63d-114">Önceki örnekte, `GridV1::Grid` kılavuz denetimi olur `grid.dll` ve `GridV2::Grid` kılavuz denetimi olacaktır `grid20.dll` .</span><span class="sxs-lookup"><span data-stu-id="2b63d-114">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="2b63d-115">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="2b63d-115">Using Visual Studio</span></span>

<span data-ttu-id="2b63d-116">Visual Studio kullanıyorsanız, diğer adlar benzer şekilde sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-116">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="2b63d-117">Visual Studio 'da projenize *grid.dll* ve *grid20.dll* başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b63d-117">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="2b63d-118">Bir özellik sekmesi açın ve Global olan diğer adları sırasıyla GridV1 ve GridV2 olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2b63d-118">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="2b63d-119">Bu diğer adları yukarıdaki şekilde kullanın</span><span class="sxs-lookup"><span data-stu-id="2b63d-119">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="2b63d-120">Artık *diğer ad yönergesini kullanarak*bir ad alanı veya tür için takma ad oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b63d-120">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="2b63d-121">Daha fazla bilgi için bkz. [using yönergesi](using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="2b63d-121">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="2b63d-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2b63d-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b63d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b63d-123">See also</span></span>

- [<span data-ttu-id="2b63d-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b63d-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2b63d-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b63d-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2b63d-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2b63d-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2b63d-127">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="2b63d-127">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="2b63d-128">-Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2b63d-128">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
