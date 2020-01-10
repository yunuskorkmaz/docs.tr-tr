---
title: Parametreleri geçirme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705476"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="badd1-102">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="badd1-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="badd1-103">' C#De, bağımsız değişkenler değere veya başvuruya göre parametrelere geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="badd1-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="badd1-104">Başvuruya göre geçirme işlevi üyeleri, Yöntemler, özellikler, Dizin oluşturucular, işleçler ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında kalıcı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="badd1-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="badd1-105">Değeri değiştirme amacına sahip bir parametreyi başvuruya göre geçirmek için `ref`veya `out` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="badd1-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="badd1-106">Kopyalamayı önleme amacını vererek ve değeri değiştirmezseniz başvuruya göre geçiş yapmak için `in` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="badd1-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="badd1-107">Basitlik için, bu konudaki örneklerde yalnızca `ref` anahtar sözcüğü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="badd1-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="badd1-108">`in`, `ref`ve `out`arasındaki fark hakkında daha fazla bilgi için bkz. [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)ve [Out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="badd1-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="badd1-109">Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="badd1-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="badd1-110">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="badd1-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="badd1-111">Değer Türü Parametrelerini Geçirme</span><span class="sxs-lookup"><span data-stu-id="badd1-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="badd1-112">Başvuru Türü Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="badd1-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="badd1-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="badd1-113">C# Language Specification</span></span>  

<span data-ttu-id="badd1-114">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) .</span><span class="sxs-lookup"><span data-stu-id="badd1-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="badd1-115">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="badd1-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="badd1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="badd1-116">See also</span></span>

- [<span data-ttu-id="badd1-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="badd1-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="badd1-118">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="badd1-118">Methods</span></span>](./methods.md)
