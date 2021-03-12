---
description: init anahtar sözcüğü-C# başvurusu
title: init anahtar sözcüğü-C# başvurusu
ms.date: 03/03/2021
f1_keywords:
- init
- init_CSharpKeyword
helpviewer_keywords:
- init keyword [C#]
ms.openlocfilehash: 2271b5332c8bfd3223d0c034a44eca4e2ca0ca54
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190471"
---
# <a name="init-c-reference"></a><span data-ttu-id="e204a-103">init (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e204a-103">init (C# Reference)</span></span>

<span data-ttu-id="e204a-104">C# 9 ve sonraki sürümlerde `init` anahtar sözcüğü bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e204a-104">In C# 9 and later, the `init` keyword defines an *accessor* method in a property or indexer.</span></span> <span data-ttu-id="e204a-105">Yalnızca bir başlatma ayarlayıcısı, özellik veya Dizin Oluşturucu öğesi yalnızca nesne oluşturma sırasında bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="e204a-105">An init-only setter assigns a value to the property or the indexer element only during object construction.</span></span> <span data-ttu-id="e204a-106">Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e204a-106">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="e204a-107">Aşağıdaki örnek `get` `init` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="e204a-107">The following example defines both a `get` and an `init` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="e204a-108">`_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="e204a-108">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[init#1](snippets/InitExample1.cs)]

<span data-ttu-id="e204a-109">Genellikle, `init` erişimci, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e204a-109">Often, the `init` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="e204a-110">`init`Erişimciyi bir ifade olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e204a-110">You can implement the `init` accessor as an expression-bodied member.</span></span> <span data-ttu-id="e204a-111">Aşağıdaki örnek, hem hem de `get` `init` erişimcilerinin ifade-Bodied Üyeler olarak uyguladığı.</span><span class="sxs-lookup"><span data-stu-id="e204a-111">The following example implements both the `get` and the `init` accessors as expression-bodied members.</span></span>

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
<span data-ttu-id="e204a-112">Bir özelliğin `get` ve `init` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e204a-112">For simple cases in which a property's `get` and `init` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="e204a-113">Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e204a-113">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="e204a-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e204a-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e204a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e204a-115">See also</span></span>

- [<span data-ttu-id="e204a-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e204a-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e204a-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e204a-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e204a-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e204a-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e204a-119">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e204a-119">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
