---
description: Set anahtar sözcüğü-C# başvurusu
title: Set anahtar sözcüğü-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136921"
---
# <a name="set-c-reference"></a><span data-ttu-id="e4a1a-103">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e4a1a-103">set (C# Reference)</span></span>

<span data-ttu-id="e4a1a-104">Anahtar sözcüğü, özelliği veya dizinleyici `set` öğesine bir değer atayan bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-104">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="e4a1a-105">Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4a1a-105">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="e4a1a-106">Aşağıdaki örnek `get` `set` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="e4a1a-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="e4a1a-107">`_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-107">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="e4a1a-108">Genellikle, `set` erişimci, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-108">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="e4a1a-109">C# 7,0 ' den başlayarak, `set` erişimciyi bir ifade olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-109">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="e4a1a-110">Aşağıdaki örnek, hem hem de `get` `set` erişimcilerinin ifade-Bodied Üyeler olarak uyguladığı.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-110">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="e4a1a-111">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="e4a1a-112">Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-112">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="e4a1a-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e4a1a-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e4a1a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4a1a-114">See also</span></span>

- [<span data-ttu-id="e4a1a-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e4a1a-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e4a1a-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4a1a-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e4a1a-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e4a1a-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e4a1a-118">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e4a1a-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
