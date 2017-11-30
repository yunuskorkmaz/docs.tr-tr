---
title: "set (C# Başvurusu)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords: set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a><span data-ttu-id="2207a-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2207a-102">set (C# Reference)</span></span>
<span data-ttu-id="2207a-103">`set` Anahtar sözcüğü tanımlayan bir *erişimci* yöntemi bir özellik ya da özellik veya dizin oluşturucu öğesi için bir değer atar dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="2207a-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="2207a-104">Daha fazla bilgi ve örnekler için bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="2207a-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="2207a-105">Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik için erişimci `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="2207a-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="2207a-106">Adlı özel bir alan kullanan `_seconds` özellik değeri yedeklenir.</span><span class="sxs-lookup"><span data-stu-id="2207a-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="2207a-107">Genellikle, `set` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimde oluşur.</span><span class="sxs-lookup"><span data-stu-id="2207a-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="2207a-108">C# 7 ile başlayan, uygulayabileceğiniz `set` bir ifade bodied üye olarak erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="2207a-108">Starting with C# 7, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="2207a-109">Aşağıdaki örnek hem de uygulayan `get` ve `set` erişimciler ifade bodied üye olarak.</span><span class="sxs-lookup"><span data-stu-id="2207a-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="2207a-110">Basit durumlarda için bir özelliğin `get` ve `set` erişimciler ayarlama veya özel yedekleme alanını değerinde alma daha diğer işlemi gerçekleştirmek, otomatik uygulanan özellikler için C# Derleyici 's desteğinin avantajından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2207a-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="2207a-111">Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak.</span><span class="sxs-lookup"><span data-stu-id="2207a-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="2207a-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2207a-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2207a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2207a-113">See Also</span></span>  
 [<span data-ttu-id="2207a-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2207a-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2207a-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2207a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2207a-116">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2207a-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2207a-117">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2207a-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
