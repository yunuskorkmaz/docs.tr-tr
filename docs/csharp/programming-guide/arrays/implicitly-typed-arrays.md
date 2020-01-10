---
title: Örtük olarak yazılan diziler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705723"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="5c9f9-102">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5c9f9-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5c9f9-103">Dizi başlatıcısında belirtilen öğelerden dizi örneği türünün Çıkarsanan türü örtük olarak belirlenmiş bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="5c9f9-104">Örtük olarak yazılmış herhangi bir değişken için kurallar, örtülü olarak belirlenmiş diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="5c9f9-105">Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="5c9f9-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="5c9f9-106">Örtük olarak yazılmış diziler genellikle anonim türler ve nesne ve koleksiyon başlatıcıları ile birlikte sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="5c9f9-107">Aşağıdaki örneklerde, örtülü olarak yazılmış bir dizinin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5c9f9-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="5c9f9-108">Önceki örnekte, örtük olarak yazılmış diziler ile, başlatma ifadesinin sol tarafında bir köşeli ayraç kullanılmaması fark edilir.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="5c9f9-109">Ayrıca, tek boyutlu diziler gibi `new []` kullanılarak pürüzlü Diziler başlatılmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="5c9f9-110">Nesne başlatıcılarında örtük olarak yazılmış diziler</span><span class="sxs-lookup"><span data-stu-id="5c9f9-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="5c9f9-111">Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi türün nesne başlatıcısında örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="5c9f9-112">Aşağıdaki örnekte `contacts`, her biri `PhoneNumbers`adlı bir dizi içeren anonim türlerin örtük olarak yazılmış bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="5c9f9-113">`var` anahtar sözcüğünün nesne başlatıcıları içinde kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="5c9f9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9f9-114">See also</span></span>

- [<span data-ttu-id="5c9f9-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5c9f9-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5c9f9-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5c9f9-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="5c9f9-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="5c9f9-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5c9f9-118">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="5c9f9-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="5c9f9-119">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5c9f9-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="5c9f9-120">var</span><span class="sxs-lookup"><span data-stu-id="5c9f9-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="5c9f9-121">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="5c9f9-121">LINQ in C#</span></span>](../../linq/index.md)
