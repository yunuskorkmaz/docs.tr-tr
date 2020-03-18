---
title: select yan tümcesi - C# Reference
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173516"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="be44c-102">select tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="be44c-102">select clause (C# Reference)</span></span>

<span data-ttu-id="be44c-103">Sorgu ifadesinde, `select` tümce, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="be44c-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="be44c-104">Sonuç, önceki tüm yan tümmaddelerin değerlendirilmesini ve tümcenin `select` kendisindeki tüm ifadelere dayanır.</span><span class="sxs-lookup"><span data-stu-id="be44c-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="be44c-105">Sorgu ifadesi, bir `select` yan tümce veya [grup](group-clause.md) yan tümcesi ile sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be44c-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="be44c-106">Aşağıdaki örnekte, `select` sorgu ifadesinde basit bir yan tümce gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="be44c-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="be44c-107">`select` Yan tümcetarafından üretilen sıranın türü sorgu değişkeninin `queryHighScores`türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="be44c-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="be44c-108">En basit durumda, `select` yan tümce sadece aralık değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be44c-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="be44c-109">Bu, döndürülen dizinin veri kaynağıyla aynı türden öğeleri içermesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="be44c-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="be44c-110">Daha fazla bilgi için [LINQ Sorgu İşlemlerinde Tür İlişkileri'ne](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="be44c-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="be44c-111">Ancak, `select` yan tümce, kaynak verileri yeni türlere dönüştürmek (veya *yansıtmak)* için güçlü bir mekanizma da sağlar.</span><span class="sxs-lookup"><span data-stu-id="be44c-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="be44c-112">Daha fazla bilgi için [LINQ (C#) ile Veri Dönüşümleri'ne](../../programming-guide/concepts/linq/data-transformations-with-linq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="be44c-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="be44c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="be44c-113">Example</span></span>

<span data-ttu-id="be44c-114">Aşağıdaki örnek, bir `select` yan tümcenin alabilecekleri tüm farklı formları gösterir.</span><span class="sxs-lookup"><span data-stu-id="be44c-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="be44c-115">Her `select` sorguda, yan tümce ile sorgu *değişkeninin* türü (`studentQuery1`, , `studentQuery2`vb.) arasındaki ilişkiyi not edin.</span><span class="sxs-lookup"><span data-stu-id="be44c-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="be44c-116">Önceki örnekte `studentQuery8` gösterildiği gibi, bazen döndürülen dizinin öğelerinin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be44c-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="be44c-117">Döndürülen sırayı mümkün olduğunca küçük tutarak bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be44c-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="be44c-118">Bunu, `select` yan tümcede anonim bir tür oluşturarak ve kaynak öğeden uygun özelliklerle başlatılması için bir nesne baş harflerini kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be44c-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="be44c-119">Bunun nasıl yapılacağının bir örneği için [Object ve Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="be44c-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="be44c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be44c-120">Remarks</span></span>

<span data-ttu-id="be44c-121">Derleme zamanında, `select` yan tümce <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleciiçin bir yöntem çağrısına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="be44c-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="be44c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be44c-122">See also</span></span>

- [<span data-ttu-id="be44c-123">C# Referans</span><span class="sxs-lookup"><span data-stu-id="be44c-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be44c-124">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="be44c-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="be44c-125">fıkradan</span><span class="sxs-lookup"><span data-stu-id="be44c-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="be44c-126">kısmi (Yöntem) (C# Referans)</span><span class="sxs-lookup"><span data-stu-id="be44c-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="be44c-127">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="be44c-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="be44c-128">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="be44c-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="be44c-129">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="be44c-129">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
