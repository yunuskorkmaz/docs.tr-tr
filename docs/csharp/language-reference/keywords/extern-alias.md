---
title: extern diğer adı-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 891e56b064f8a327abe28293223a85b9d95e8fd3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301820"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="45d2f-102">extern alias (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="45d2f-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="45d2f-103">Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="45d2f-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="45d2f-104">Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="45d2f-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="45d2f-105">Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="45d2f-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45d2f-106">[Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45d2f-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="45d2f-107">Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="45d2f-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="45d2f-108">Bu, dış diğer adları oluşturur `GridV1` ve `GridV2` .</span><span class="sxs-lookup"><span data-stu-id="45d2f-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="45d2f-109">Bu diğer adları bir program içinden kullanmak için anahtar sözcüğünü kullanarak bunlara başvurun `extern` .</span><span class="sxs-lookup"><span data-stu-id="45d2f-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="45d2f-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="45d2f-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="45d2f-111">Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="45d2f-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="45d2f-112">Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="45d2f-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="45d2f-113">Önceki örnekte, `GridV1::Grid` kılavuz denetimi olur `grid.dll` ve `GridV2::Grid` kılavuz denetimi olacaktır `grid20.dll` .</span><span class="sxs-lookup"><span data-stu-id="45d2f-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="45d2f-114">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="45d2f-114">Using Visual Studio</span></span>

<span data-ttu-id="45d2f-115">Visual Studio kullanıyorsanız, diğer adlar benzer şekilde sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="45d2f-115">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="45d2f-116">Visual Studio 'da projenize *grid.dll* ve *grid20.dll* başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45d2f-116">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="45d2f-117">Bir özellik sekmesi açın ve Global olan diğer adları sırasıyla GridV1 ve GridV2 olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="45d2f-117">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="45d2f-118">Bu diğer adları yukarıdaki şekilde kullanın</span><span class="sxs-lookup"><span data-stu-id="45d2f-118">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="45d2f-119">Artık *diğer ad yönergesini kullanarak*bir ad alanı veya tür için takma ad oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d2f-119">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="45d2f-120">Daha fazla bilgi için bkz. [using yönergesi](using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="45d2f-120">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="45d2f-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="45d2f-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45d2f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45d2f-122">See also</span></span>

- [<span data-ttu-id="45d2f-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="45d2f-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45d2f-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="45d2f-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45d2f-125">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="45d2f-125">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="45d2f-126">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="45d2f-126">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="45d2f-127">-Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="45d2f-127">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
