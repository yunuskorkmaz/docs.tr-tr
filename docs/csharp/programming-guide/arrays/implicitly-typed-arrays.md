---
title: Örtük olarak yazılan diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 36ca18adc392643107b43a947656846f3b94a2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597350"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="a696b-102">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a696b-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="a696b-103">Dizi başlatıcısında belirtilen öğelerden dizi örneği türünün Çıkarsanan türü örtük olarak belirlenmiş bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a696b-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="a696b-104">Örtük olarak yazılmış herhangi bir değişken için kurallar, örtülü olarak belirlenmiş diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a696b-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="a696b-105">Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a696b-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="a696b-106">Örtük olarak yazılmış diziler genellikle anonim türler ve nesne ve koleksiyon başlatıcıları ile birlikte sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a696b-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="a696b-107">Aşağıdaki örneklerde, örtülü olarak yazılmış bir dizinin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a696b-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="a696b-108">Önceki örnekte, örtük olarak yazılmış diziler ile, başlatma ifadesinin sol tarafında bir köşeli ayraç kullanılmaması fark edilir.</span><span class="sxs-lookup"><span data-stu-id="a696b-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="a696b-109">Ayrıca, basit dizilerin tıpkı tek boyutlu diziler gibi `new []` kullanılarak başlatılmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a696b-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="a696b-110">Nesne başlatıcılarında örtük olarak yazılmış diziler</span><span class="sxs-lookup"><span data-stu-id="a696b-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="a696b-111">Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi türün nesne başlatıcısında örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a696b-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="a696b-112">Aşağıdaki örnekte, `contacts` her biri adlı `PhoneNumbers`bir dizi içeren, örtülü olarak yazılmış bir anonim türler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="a696b-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="a696b-113">`var` Anahtar sözcüğünün nesne başlatıcıları içinde kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a696b-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="a696b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a696b-114">See also</span></span>

- [<span data-ttu-id="a696b-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a696b-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a696b-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a696b-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="a696b-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="a696b-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="a696b-118">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="a696b-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="a696b-119">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="a696b-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="a696b-120">var</span><span class="sxs-lookup"><span data-stu-id="a696b-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="a696b-121">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a696b-121">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
