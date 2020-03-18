---
title: Örtülü Daktino Dizileri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705723"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="28d98-102">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="28d98-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="28d98-103">Dizi örneği türünün dizi initializer'inde belirtilen öğelerden çıkarıldığı örtülü olarak yazılmış bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28d98-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="28d98-104">Herhangi bir örtülü olarak yazılan değişkeniçin kurallar, örtülü olarak yazılan diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="28d98-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="28d98-105">Daha fazla bilgi için [bkz.](../classes-and-structs/implicitly-typed-local-variables.md)</span><span class="sxs-lookup"><span data-stu-id="28d98-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="28d98-106">Dolaylı olarak yazılan diziler genellikle sorgu ifadelerinde anonim türler ve nesne ve koleksiyon başlatmalayıcılarıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28d98-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="28d98-107">Aşağıdaki örnekler, örtülü olarak yazılan bir dizinin nasıl oluşturulabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="28d98-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="28d98-108">Önceki örnekte, örtülü olarak yazılan dizilerde, başlatma deyiminin sol tarafında kare ayraç kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28d98-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="28d98-109">Pürüzlü dizilerin tek boyutlu diziler gibi kullanılarak `new []` baş harflere batmış olduğunu da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28d98-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="28d98-110">Nesne Başharflerinde Örtülü Olarak Yazılan Diziler</span><span class="sxs-lookup"><span data-stu-id="28d98-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="28d98-111">Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi örtülü olarak tür nesnesi baş harflerine yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28d98-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="28d98-112">Aşağıdaki örnekte, `contacts` her biri .. `PhoneNumbers`</span><span class="sxs-lookup"><span data-stu-id="28d98-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="28d98-113">Anahtar kelimenin `var` nesne baş harflerini içinde kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28d98-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="28d98-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28d98-114">See also</span></span>

- [<span data-ttu-id="28d98-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28d98-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="28d98-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="28d98-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="28d98-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="28d98-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="28d98-118">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="28d98-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="28d98-119">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="28d98-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="28d98-120">var</span><span class="sxs-lookup"><span data-stu-id="28d98-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="28d98-121">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="28d98-121">LINQ in C#</span></span>](../../linq/index.md)
