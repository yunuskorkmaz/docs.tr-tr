---
title: get - C# Referans
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173633"
---
# <a name="get-c-reference"></a><span data-ttu-id="87829-102">get (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="87829-102">get (C# Reference)</span></span>

<span data-ttu-id="87829-103">Anahtar `get` kelime, özellik değerini veya dizinleyici öğesini döndüren bir özellik veya dizinleyicide bir *erişimci* yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87829-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="87829-104">Daha fazla bilgi için bkz: [Özellikler,](../../programming-guide/classes-and-structs/properties.md) [Otomatik Uygulanan Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizinleyiciler.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="87829-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="87829-105">Aşağıdaki örnek, adlandırılmış `get` `Seconds`bir `set` özellik için hem a hem de bir erişimci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87829-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="87829-106">Özellik değerini yedeklemek `_seconds` için özel bir alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="87829-106">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="87829-107">Genellikle, `get` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimoluşur.</span><span class="sxs-lookup"><span data-stu-id="87829-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="87829-108">C# 7.0 ile başlayarak, `get` erişime gireni ifade gövdeli bir üye olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87829-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="87829-109">Aşağıdaki örnek, hem `get` erişime `set` gireni hem de katılımcıyı ifade gövdeli üyeler olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="87829-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="87829-110">Bir özelliğin `get` ve `set` erişime sahip olanların özel bir destek alanında bir değer ayarlamaktan veya almaktan başka bir işlem gerçekleştirmediği basit durumlarda, Otomatik olarak uygulanan özellikler için C# derleyicisinin desteğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87829-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="87829-111">Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="87829-111">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="87829-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="87829-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87829-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87829-113">See also</span></span>

- [<span data-ttu-id="87829-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="87829-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="87829-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="87829-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="87829-116">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="87829-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="87829-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="87829-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
