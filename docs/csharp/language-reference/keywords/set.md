---
title: Set anahtar sözcüğü-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795072"
---
# <a name="set-c-reference"></a><span data-ttu-id="f3086-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f3086-102">set (C# Reference)</span></span>

<span data-ttu-id="f3086-103">`set` Anahtar sözcüğü, özelliği veya dizinleyici öğesine bir değer atayan bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3086-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="f3086-104">Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3086-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="f3086-105">Aşağıdaki örnek adlı `get` `Seconds`bir özellik için hem hem `set` de erişimcisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3086-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="f3086-106">Özellik değerini geri yüklemek için adlı `_seconds` bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3086-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="f3086-107">Genellikle, `set` erişimci, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3086-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="f3086-108">C# 7,0 ' den başlayarak, `set` erişimciyi bir ifade olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3086-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="f3086-109">Aşağıdaki örnek, `get` hem hem de `set` erişimcilerinin ifade-Bodied Üyeler olarak uyguladığı.</span><span class="sxs-lookup"><span data-stu-id="f3086-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="f3086-110">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3086-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="f3086-111">Aşağıdaki örnek otomatik uygulanan `Hours` bir özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f3086-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="f3086-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f3086-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f3086-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3086-113">See also</span></span>

- [<span data-ttu-id="f3086-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f3086-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f3086-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f3086-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f3086-116">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f3086-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f3086-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3086-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
