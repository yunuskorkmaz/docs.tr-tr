---
title: get (C# Başvurusu)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 671cadce0bd120ec0728562ec448b2ce6edf2dd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216115"
---
# <a name="get-c-reference"></a><span data-ttu-id="d361f-102">get (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d361f-102">get (C# Reference)</span></span>

<span data-ttu-id="d361f-103">`get` Anahtar sözcüğü tanımlayan bir *erişimci* yöntemi bir özellik ya da özellik değeri veya dizin oluşturucu öğesi döndürür. dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d361f-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="d361f-104">Daha fazla bilgi için bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d361f-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="d361f-105">Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik için erişimci `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="d361f-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="d361f-106">Adlı özel bir alan kullanan `_seconds` özellik değeri yedeklenir.</span><span class="sxs-lookup"><span data-stu-id="d361f-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="d361f-107">Genellikle, `get` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d361f-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="d361f-108">C# 7. 0'dan başlayarak, uygulayabileceğiniz `get` bir ifade bodied üye olarak erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="d361f-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="d361f-109">Aşağıdaki örnek hem de uygulayan `get` ve `set` ifade bodied üye olarak erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="d361f-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="d361f-110">Basit durumlarda için bir özelliğin `get` ve `set` erişimciler ayarlama veya özel yedekleme alanını değerinde alma daha diğer işlemi gerçekleştirmek, otomatik uygulanan özellikler için C# Derleyici 's desteğinin avantajından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d361f-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="d361f-111">Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak.</span><span class="sxs-lookup"><span data-stu-id="d361f-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d361f-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d361f-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d361f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d361f-113">See Also</span></span>  
 [<span data-ttu-id="d361f-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d361f-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d361f-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d361f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="d361f-116">[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="d361f-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>
