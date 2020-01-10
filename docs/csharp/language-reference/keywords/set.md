---
title: anahtar sözcük C# başvurusunu ayarla
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 97b0dbf8716edc4cd465eb5ac693efa0ecaa498b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713085"
---
# <a name="set-c-reference"></a><span data-ttu-id="ba9a5-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ba9a5-102">set (C# Reference)</span></span>

<span data-ttu-id="ba9a5-103">`set` anahtar sözcüğü, özelliğe veya dizinleyici öğesine bir değer atayan bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="ba9a5-104">Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba9a5-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="ba9a5-105">Aşağıdaki örnek, `Seconds`adlı bir özellik için hem `get` hem de `set` erişimcisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="ba9a5-106">Özellik değerini geri yüklemek için `_seconds` adlı bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="ba9a5-107">Genellikle `set` erişimcisi, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="ba9a5-108">7,0 ' C# den başlayarak, `set` erişimcisini ifade-Bodied üyesi olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="ba9a5-109">Aşağıdaki örnek hem `get` hem de `set` erişimcileri ifadesini ifade eden Üyeler olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="ba9a5-110">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirmesinin gerçekleştirdiği basit durumlar için C# derleyicinin otomatik uygulanan özellikler desteğiyle yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="ba9a5-111">Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-111">The following example implements `Hours` as an auto-implemented property.</span></span> 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="ba9a5-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ba9a5-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ba9a5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba9a5-113">See also</span></span>

- [<span data-ttu-id="ba9a5-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="ba9a5-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ba9a5-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ba9a5-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ba9a5-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ba9a5-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ba9a5-117">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="ba9a5-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
