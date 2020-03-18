---
title: Geçen Parametreler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705476"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="2a43d-102">Parametreleri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2a43d-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="2a43d-103">C#'da bağımsız değişkenler parametrelere değer veya başvuru ile geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a43d-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="2a43d-104">Başvuruyla geçmek, işlev üyelerinin, yöntemlerinin, özelliklerinin, dizin leyicilerin ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında devam etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a43d-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="2a43d-105">Değeri değiştirme amacıyla bir parametreyi referans olarak geçirmek `ref`için, `out` "veya anahtar kelimeyi" kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a43d-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="2a43d-106">Kopyalamaktan kaçınmak ancak değeri değiştirmemek amacıyla referans la geçmek `in` için değiştiricikullanın.</span><span class="sxs-lookup"><span data-stu-id="2a43d-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="2a43d-107">Basitlik için, bu `ref` konudaki örneklerde yalnızca anahtar kelime kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a43d-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="2a43d-108">Arasındaki `in`fark hakkında daha `ref`fazla `out`bilgi için , , ve , [,](../../language-reference/keywords/in-parameter-modifier.md)bakınız , [ref](../../language-reference/keywords/ref.md), ve [dışarı](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="2a43d-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="2a43d-109">Aşağıdaki örnekte değer ve başvuru parametreleri arasındaki fark gösterin.</span><span class="sxs-lookup"><span data-stu-id="2a43d-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="2a43d-110">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="2a43d-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="2a43d-111">Değer Türü Parametrelerini Geçirme</span><span class="sxs-lookup"><span data-stu-id="2a43d-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="2a43d-112">Başvuru Türü Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="2a43d-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2a43d-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2a43d-113">C# Language Specification</span></span>  

<span data-ttu-id="2a43d-114">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bağımsız Değişken listelerine](~/_csharplang/spec/expressions.md#argument-lists) bakın.</span><span class="sxs-lookup"><span data-stu-id="2a43d-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2a43d-115">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="2a43d-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2a43d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a43d-116">See also</span></span>

- [<span data-ttu-id="2a43d-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a43d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2a43d-118">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a43d-118">Methods</span></span>](./methods.md)
