---
description: Select yan tümcesi-C# başvurusu
title: Select yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136908"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="68ccc-103">select tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="68ccc-103">select clause (C# Reference)</span></span>

<span data-ttu-id="68ccc-104">Bir sorgu ifadesinde `select` yan tümce, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-104">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="68ccc-105">Sonuç, tüm önceki yan tümcelerin ve yan tümcedeki herhangi bir ifadenin değerlendirmesine dayanır `select` .</span><span class="sxs-lookup"><span data-stu-id="68ccc-105">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="68ccc-106">Sorgu ifadesinin bir `select` yan tümce veya bir [Grup](group-clause.md) yan tümcesiyle sonlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-106">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="68ccc-107">Aşağıdaki örnekte bir `select` sorgu ifadesinde basit bir yan tümce gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-107">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="68ccc-108">Yan tümce tarafından üretilen sıranın türü, `select` sorgu değişkeninin türünü belirler `queryHighScores` .</span><span class="sxs-lookup"><span data-stu-id="68ccc-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="68ccc-109">En basit durumda, `select` yan tümce yalnızca Aralık değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="68ccc-110">Bu, döndürülen sıranın veri kaynağıyla aynı türdeki öğeleri içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="68ccc-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="68ccc-111">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="68ccc-111">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="68ccc-112">Ancak `select` yan tümce, kaynak verilerini yeni türlere dönüştürmek (veya *yansıtma*) için güçlü bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="68ccc-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="68ccc-113">Daha fazla bilgi için bkz. [LINQ Ile veri dönüştürmeleri (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="68ccc-113">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="68ccc-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="68ccc-114">Example</span></span>

<span data-ttu-id="68ccc-115">Aşağıdaki örnek, bir `select` yan tümcesinin götüreolabileceği tüm farklı formları gösterir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="68ccc-116">Her sorguda, `select` yan tümcesi ve *sorgu değişkeninin* türü ( `studentQuery1` ,, vb.) arasındaki ilişkiyi aklınızda yazın `studentQuery2` .</span><span class="sxs-lookup"><span data-stu-id="68ccc-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="68ccc-117">`studentQuery8`Önceki örnekte gösterildiği gibi, bazen döndürülen dizideki öğelerin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68ccc-117">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="68ccc-118">Döndürülen sırayı mümkün olduğunca küçük tutarak, bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68ccc-118">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="68ccc-119">Bunu, yan tümcesinde anonim bir tür oluşturarak `select` ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcısı kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68ccc-119">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="68ccc-120">Bunun nasıl yapılacağı hakkında bir örnek için bkz. [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="68ccc-120">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="68ccc-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68ccc-121">Remarks</span></span>

<span data-ttu-id="68ccc-122">Derleme zamanında `select` yan tümce <xref:System.Linq.Enumerable.Select%2A> Standart sorgu işlecine bir yöntem çağrısına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="68ccc-122">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="68ccc-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68ccc-123">See also</span></span>

- [<span data-ttu-id="68ccc-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="68ccc-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="68ccc-125">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="68ccc-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="68ccc-126">from tümcesi</span><span class="sxs-lookup"><span data-stu-id="68ccc-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="68ccc-127">partial (Yöntem) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="68ccc-127">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="68ccc-128">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="68ccc-128">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="68ccc-129">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="68ccc-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="68ccc-130">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="68ccc-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
