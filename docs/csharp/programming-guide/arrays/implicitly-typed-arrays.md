---
title: Örtük olarak yazılan diziler-C# Programlama Kılavuzu
description: C# ' de örtük olarak yazılmış bir dizinin türü dizi başlatıcıdaki öğelerden çıkarsanamıyor. Sorgu ifadelerinde örtük olarak yazılmış diziler kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474715"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="4a793-104">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4a793-104">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="4a793-105">Dizi başlatıcısında belirtilen öğelerden dizi örneği türünün Çıkarsanan türü örtük olarak belirlenmiş bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a793-105">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="4a793-106">Örtük olarak yazılmış herhangi bir değişken için kurallar, örtülü olarak belirlenmiş diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a793-106">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="4a793-107">Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="4a793-107">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="4a793-108">Örtük olarak yazılmış diziler genellikle anonim türler ve nesne ve koleksiyon başlatıcıları ile birlikte sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a793-108">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="4a793-109">Aşağıdaki örneklerde, örtülü olarak yazılmış bir dizinin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4a793-109">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="4a793-110">Önceki örnekte, örtük olarak yazılmış diziler ile, başlatma ifadesinin sol tarafında bir köşeli ayraç kullanılmaması fark edilir.</span><span class="sxs-lookup"><span data-stu-id="4a793-110">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="4a793-111">Ayrıca, basit dizilerin `new []` tıpkı tek boyutlu diziler gibi kullanılarak başlatılmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a793-111">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="4a793-112">Nesne başlatıcılarında örtük olarak yazılmış diziler</span><span class="sxs-lookup"><span data-stu-id="4a793-112">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="4a793-113">Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi türün nesne başlatıcısında örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a793-113">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="4a793-114">Aşağıdaki örnekte, `contacts` her biri adlı bir dizi içeren, örtülü olarak yazılmış bir anonim türler dizisidir `PhoneNumbers` .</span><span class="sxs-lookup"><span data-stu-id="4a793-114">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="4a793-115">`var`Anahtar sözcüğünün nesne başlatıcıları içinde kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a793-115">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="4a793-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a793-116">See also</span></span>

- [<span data-ttu-id="4a793-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a793-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a793-118">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4a793-118">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="4a793-119">Diziler</span><span class="sxs-lookup"><span data-stu-id="4a793-119">Arrays</span></span>](./index.md)
- [<span data-ttu-id="4a793-120">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="4a793-120">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="4a793-121">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="4a793-121">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="4a793-122">var</span><span class="sxs-lookup"><span data-stu-id="4a793-122">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="4a793-123">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="4a793-123">LINQ in C#</span></span>](../../linq/index.md)
