---
title: anahtar kelime yi ayarlama - C# Reference
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173503"
---
# <a name="set-c-reference"></a><span data-ttu-id="c058b-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c058b-102">set (C# Reference)</span></span>

<span data-ttu-id="c058b-103">Anahtar `set` kelime, bir özellik veya dizinleyici de bir özellik veya dizinleyici öğesi bir değer atayan bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c058b-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="c058b-104">Daha fazla bilgi ve örnekler için Bkz. [Özellikler,](../../programming-guide/classes-and-structs/properties.md) [Otomatik Uygulanan Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin leyiciler.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="c058b-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="c058b-105">Aşağıdaki örnek, adlandırılmış `get` `Seconds`bir `set` özellik için hem a hem de bir erişimci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c058b-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="c058b-106">Özellik değerini yedeklemek `_seconds` için özel bir alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="c058b-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="c058b-107">Genellikle, `set` erişimci önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c058b-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="c058b-108">C# 7.0 ile başlayarak, `set` erişime gireni ifade gövdeli bir üye olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c058b-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="c058b-109">Aşağıdaki örnek, hem `get` `set` erişime girenleri hem de erişime girenleri ifade gövdeli üyeler olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="c058b-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="c058b-110">Bir özelliğin `get` ve `set` erişime sahip olanların özel bir destek alanında bir değer ayarlamaktan veya almaktan başka bir işlem gerçekleştirmediği basit durumlarda, Otomatik olarak uygulanan özellikler için C# derleyicisinin desteğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c058b-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="c058b-111">Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="c058b-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="c058b-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c058b-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c058b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c058b-113">See also</span></span>

- [<span data-ttu-id="c058b-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="c058b-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="c058b-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c058b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c058b-116">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="c058b-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c058b-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c058b-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
