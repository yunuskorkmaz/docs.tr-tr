---
title: C# başvuru al
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713500"
---
# <a name="get-c-reference"></a><span data-ttu-id="1133d-102">get (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1133d-102">get (C# Reference)</span></span>

<span data-ttu-id="1133d-103">`get` anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1133d-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="1133d-104">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1133d-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="1133d-105">Aşağıdaki örnek, `Seconds`adlı bir özellik için hem `get` hem de `set` erişimcisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1133d-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="1133d-106">Özellik değerini geri yüklemek için `_seconds` adlı bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="1133d-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="1133d-107">Genellikle `get` erişimcisi, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1133d-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="1133d-108">7,0 ' C# den başlayarak, `get` erişimcisini ifade-Bodied üyesi olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1133d-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="1133d-109">Aşağıdaki örnek, ifadesi Bodied Üyeler olarak hem `get` hem de `set` erişimcisini uygular.</span><span class="sxs-lookup"><span data-stu-id="1133d-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="1133d-110">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirmesinin gerçekleştirdiği basit durumlar için C# derleyicinin otomatik uygulanan özellikler desteğiyle yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1133d-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="1133d-111">Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="1133d-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1133d-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1133d-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1133d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1133d-113">See also</span></span>

- [<span data-ttu-id="1133d-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="1133d-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1133d-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1133d-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1133d-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1133d-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1133d-117">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="1133d-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
