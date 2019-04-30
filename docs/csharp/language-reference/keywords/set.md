---
title: anahtar sözcüğü - Ayarla C# başvurusu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0322f1bb94174dd3a0cdd2089c8626d25a80cc1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660755"
---
# <a name="set-c-reference"></a><span data-ttu-id="0ad80-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0ad80-102">set (C# Reference)</span></span>

<span data-ttu-id="0ad80-103">`set` Tanımlayan anahtar sözcüğü bir *erişimci* yönteminde bir özellik veya dizin özelliği veya dizin oluşturucu öğenin bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="0ad80-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="0ad80-104">Daha fazla bilgi ve örnekler için bkz. [özellikleri](../../programming-guide/classes-and-structs/properties.md), [Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), ve [dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ad80-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="0ad80-105">Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik erişimcisi `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="0ad80-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="0ad80-106">Adlı bir özel alan kullanan `_seconds` özellik değeri yedeklenir.</span><span class="sxs-lookup"><span data-stu-id="0ad80-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="0ad80-107">Genellikle, `set` erişimci, önceki örnekte olduğu gibi bir değer atar tek bir deyimde oluşur.</span><span class="sxs-lookup"><span data-stu-id="0ad80-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="0ad80-108">C# 7.0 ile başlayarak, uygulayabileceğiniz `set` bir ifade gövdeli üyesi erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="0ad80-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="0ad80-109">Aşağıdaki örnek her ikisini birden uygular `get` ve `set` ifade gövdeli üyeler olarak erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="0ad80-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="0ad80-110">Basit durumlarda için bir özelliğin `get` ve `set` erişimcileri ayarlama veya özel destek alanı bir değer alınırken daha başka bir işlem gerçekleştirme, otomatik uygulanan özellikler için C# Derleyici desteği yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad80-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="0ad80-111">Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak.</span><span class="sxs-lookup"><span data-stu-id="0ad80-111">The following example implements `Hours` as an auto-implemented property.</span></span> 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="0ad80-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0ad80-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0ad80-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad80-113">See also</span></span>

- [<span data-ttu-id="0ad80-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0ad80-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="0ad80-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ad80-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ad80-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0ad80-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0ad80-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0ad80-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
