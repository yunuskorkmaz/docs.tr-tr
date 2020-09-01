---
description: Get-C# başvurusu
title: Get-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139742"
---
# <a name="get-c-reference"></a><span data-ttu-id="c824e-103">get (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c824e-103">get (C# Reference)</span></span>

<span data-ttu-id="c824e-104">`get`Anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c824e-104">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="c824e-105">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c824e-105">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="c824e-106">Aşağıdaki örnek `get` `set` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="c824e-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="c824e-107">`_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="c824e-107">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="c824e-108">Genellikle, `get` erişimci, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c824e-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="c824e-109">C# 7,0 ' den başlayarak, `get` erişimciyi bir ifade olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c824e-109">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="c824e-110">Aşağıdaki örnek, hem hem de `get` `set` erişimcisini ifade-Bodied Üyeler olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="c824e-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="c824e-111">Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c824e-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="c824e-112">Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c824e-112">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c824e-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c824e-113">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c824e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c824e-114">See also</span></span>

- [<span data-ttu-id="c824e-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c824e-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c824e-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c824e-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c824e-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c824e-117">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c824e-118">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c824e-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
