---
title: Parametreleri geçirme-C# Programlama Kılavuzu
description: Bir bağımsız değişkeni C# ' de değere veya başvuruya göre bir parametreye geçirebilirsiniz. Başvuru kalıcı olarak geçirilen bir bağımsız değişkende yapılan değişiklikler. Başvuruya göre geçmek için ref veya out kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 61ec6d31145df5a2aebe805fccdf7614a0ae74f6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186100"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="4c4f6-105">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4c4f6-105">Passing Parameters (C# Programming Guide)</span></span>

<span data-ttu-id="4c4f6-106">C# ' de, bağımsız değişkenler değere veya başvuruya göre parametrelere geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-106">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="4c4f6-107">Başvuruya göre geçirme işlevi üyeleri, Yöntemler, özellikler, Dizin oluşturucular, işleçler ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında kalıcı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-107">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="4c4f6-108">Değeri değiştirme amacına sahip bir parametreyi başvuruya göre geçirmek için, `ref` veya `out` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-108">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="4c4f6-109">Kopyalama ve değeri değiştirmemesini sağlama amacını kullanarak başvuruya göre geçiş yapmak için `in` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-109">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="4c4f6-110">Basitlik için, `ref` Bu konudaki örneklerde yalnızca anahtar sözcüğü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-110">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="4c4f6-111">, Ve arasındaki fark hakkında daha fazla bilgi için `in` `ref` `out` bkz. [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)ve [Out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="4c4f6-111">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="4c4f6-112">Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-112">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="4c4f6-113">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="4c4f6-113">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="4c4f6-114">Değer Türü Parametrelerini Geçirme</span><span class="sxs-lookup"><span data-stu-id="4c4f6-114">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="4c4f6-115">Başvuru Türü Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="4c4f6-115">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="4c4f6-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="4c4f6-116">C# Language Specification</span></span>  

<span data-ttu-id="4c4f6-117">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) .</span><span class="sxs-lookup"><span data-stu-id="4c4f6-117">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4c4f6-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4c4f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c4f6-119">See also</span></span>

- [<span data-ttu-id="4c4f6-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4c4f6-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4c4f6-121">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c4f6-121">Methods</span></span>](./methods.md)
