---
title: C# başvuru al
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602138"
---
# <a name="get-c-reference"></a><span data-ttu-id="8a6c2-102">get (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8a6c2-102">get (C# Reference)</span></span>

<span data-ttu-id="8a6c2-103">Anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir erişimci yöntemi tanımlar. `get`</span><span class="sxs-lookup"><span data-stu-id="8a6c2-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="8a6c2-104">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a6c2-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="8a6c2-105">Aşağıdaki örnek adlı `get` `set` birözellik`Seconds`için hem hem de erişimcisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="8a6c2-106">Özellik değerini geri yüklemek için adlı `_seconds` bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="8a6c2-107">Genellikle, `get` erişimci, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="8a6c2-108">7,0 ' C# den başlayarak, `get` erişimciyi bir ifade olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="8a6c2-109">Aşağıdaki örnek, `get` `set` hem hem de erişimcisini ifade-Bodied Üyeler olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="8a6c2-110">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicinin otomatik olarak uygulanmış olan desteğiyle faydalanabilirsiniz özelliklerinin.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="8a6c2-111">Aşağıdaki örnek `Hours` otomatik uygulanan bir özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a6c2-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8a6c2-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a6c2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-113">See also</span></span>

- [<span data-ttu-id="8a6c2-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="8a6c2-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8a6c2-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8a6c2-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8a6c2-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8a6c2-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8a6c2-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8a6c2-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
