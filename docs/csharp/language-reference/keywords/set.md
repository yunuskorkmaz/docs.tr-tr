---
title: set (C# Başvurusu)
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 5baab41a0f9fc81bbf9f606ef569f0653b873e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265794"
---
# <a name="set-c-reference"></a><span data-ttu-id="d0b52-102">set (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d0b52-102">set (C# Reference)</span></span>
<span data-ttu-id="d0b52-103">`set` Anahtar sözcüğü tanımlayan bir *erişimci* yöntemi bir özellik ya da özellik veya dizin oluşturucu öğesi için bir değer atar dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d0b52-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="d0b52-104">Daha fazla bilgi ve örnekler için bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0b52-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="d0b52-105">Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik için erişimci `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="d0b52-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="d0b52-106">Adlı özel bir alan kullanan `_seconds` özellik değeri yedeklenir.</span><span class="sxs-lookup"><span data-stu-id="d0b52-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="d0b52-107">Genellikle, `set` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d0b52-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="d0b52-108">C# 7. 0'dan başlayarak, uygulayabileceğiniz `set` bir ifade bodied üye olarak erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="d0b52-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="d0b52-109">Aşağıdaki örnek hem de uygulayan `get` ve `set` erişimciler ifade bodied üye olarak.</span><span class="sxs-lookup"><span data-stu-id="d0b52-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="d0b52-110">Basit durumlarda için bir özelliğin `get` ve `set` erişimciler ayarlama veya özel yedekleme alanını değerinde alma daha diğer işlemi gerçekleştirmek, otomatik uygulanan özellikler için C# Derleyici 's desteğinin avantajından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0b52-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="d0b52-111">Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak.</span><span class="sxs-lookup"><span data-stu-id="d0b52-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="d0b52-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d0b52-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b52-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b52-113">See Also</span></span>  
 [<span data-ttu-id="d0b52-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d0b52-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d0b52-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d0b52-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d0b52-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d0b52-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d0b52-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0b52-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
