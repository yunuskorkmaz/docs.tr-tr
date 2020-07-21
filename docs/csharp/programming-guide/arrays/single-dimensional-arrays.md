---
title: Tek boyutlu diziler-C# Programlama Kılavuzu
description: Dizi öğesi türü ve öğe sayısını belirten New işlecini kullanarak C# ' de tek boyutlu bir dizi oluşturun.
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474598"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="9931c-103">Tek Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9931c-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="9931c-104">Dizi öğesi türünü ve öğe sayısını belirten [New](../../language-reference/operators/new-operator.md) işlecini kullanarak tek boyutlu bir dizi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="9931c-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="9931c-105">Aşağıdaki örnek, beş tamsayının dizisini bildirir:</span><span class="sxs-lookup"><span data-stu-id="9931c-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="9931c-106">Bu dizi öğesine öğesinden öğelerini içerir `array[0]` `array[4]` .</span><span class="sxs-lookup"><span data-stu-id="9931c-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="9931c-107">Dizi öğeleri, tamsayılar için, öğe türünün varsayılan değerine başlatılır `0` .</span><span class="sxs-lookup"><span data-stu-id="9931c-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="9931c-108">Diziler, bir dizi dizeyi bildiren aşağıdaki örnek gibi, belirttiğiniz herhangi bir öğe türünü depolayabilirler:</span><span class="sxs-lookup"><span data-stu-id="9931c-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="9931c-109">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="9931c-109">Array Initialization</span></span>

<span data-ttu-id="9931c-110">Diziyi bildirdiğinizde dizideki öğeleri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9931c-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="9931c-111">Başlangıç listesindeki öğe sayısı tarafından çıkarsandığı için uzunluk belirleyicisi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9931c-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="9931c-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9931c-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="9931c-113">Aşağıdaki kod, her dizi öğesinin bir günün adı ile başlatıldığı dize dizisinin bir bildirimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="9931c-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="9931c-114">`new`Aşağıdaki kodda gösterildiği gibi, bildirim üzerine bir diziyi başlattığınızda ifadeden ve dizi türünden kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9931c-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="9931c-115">Buna [örtük olarak yazılmış dizi](implicitly-typed-arrays.md)denir:</span><span class="sxs-lookup"><span data-stu-id="9931c-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="9931c-116">Bir dizi değişkenini oluşturmadan bildirebilirsiniz, ancak `new` Bu değişkene yeni bir dizi atadığınızda işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9931c-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="9931c-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9931c-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="9931c-118">Değer türü ve başvuru türü dizileri</span><span class="sxs-lookup"><span data-stu-id="9931c-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="9931c-119">Aşağıdaki dizi bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9931c-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="9931c-120">Bu deyimin sonucu, `SomeType` bir değer türü veya başvuru türü olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9931c-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="9931c-121">Değer bir tür ise, ifade, her birinin türü olan 10 öğeden oluşan bir dizi oluşturur `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="9931c-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="9931c-122">`SomeType`Bir başvuru türü ise, ifade her biri null başvuruya başlatılan 10 öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9931c-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="9931c-123">Her iki örnekte de öğeler, öğe türü için varsayılan değer olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9931c-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="9931c-124">Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/builtin-types/value-types.md) ve [başvuru türleri](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9931c-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9931c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9931c-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="9931c-126">Diziler</span><span class="sxs-lookup"><span data-stu-id="9931c-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="9931c-127">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="9931c-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="9931c-128">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="9931c-128">Jagged Arrays</span></span>](./jagged-arrays.md)
