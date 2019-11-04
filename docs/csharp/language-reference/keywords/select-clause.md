---
title: Select yan tümcesi C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: f1bfbeccaf6c3916a591f6447760fa01c3f8a3b6
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422362"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="2e744-102">select tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2e744-102">select clause (C# Reference)</span></span>

<span data-ttu-id="2e744-103">Sorgu ifadesinde `select` yan tümcesi, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e744-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="2e744-104">Sonuç, tüm önceki yan tümcelerinin ve `select` yan tümcesinin içindeki herhangi bir ifadenin değerlendirmesine dayanır.</span><span class="sxs-lookup"><span data-stu-id="2e744-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="2e744-105">Sorgu ifadesinin bir `select` yan tümcesiyle veya bir [Grup](group-clause.md) yan tümcesiyle sonlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e744-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="2e744-106">Aşağıdaki örnekte, bir sorgu ifadesinde basit bir `select` yan tümcesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e744-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="2e744-107">`select` yan tümcesi tarafından üretilen sıranın türü, `queryHighScores`sorgu değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="2e744-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="2e744-108">En basit durumda, `select` yan tümcesi yalnızca Aralık değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e744-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="2e744-109">Bu, döndürülen sıranın veri kaynağıyla aynı türdeki öğeleri içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e744-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="2e744-110">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2e744-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="2e744-111">Ancak `select` yan tümcesi, kaynak verilerini yeni türlere dönüştürmek (veya *yansıtma*) için güçlü bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e744-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="2e744-112">Daha fazla bilgi için bkz. [LINQ (C#) ile veri dönüştürmeleri](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2e744-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e744-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e744-113">Example</span></span>

<span data-ttu-id="2e744-114">Aşağıdaki örnek, bir `select` yan tümcesinin götüreolabileceği tüm farklı formları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e744-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="2e744-115">Her sorguda `select` yan tümcesi ve *sorgu değişkeninin* türü (`studentQuery1`, `studentQuery2`, vb.) arasındaki ilişkiyi aklınızda yazın.</span><span class="sxs-lookup"><span data-stu-id="2e744-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="2e744-116">Önceki örnekte `studentQuery8` gösterildiği gibi, bazen döndürülen dizideki öğelerin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e744-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="2e744-117">Döndürülen sırayı mümkün olduğunca küçük tutarak, bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e744-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="2e744-118">Bunu, `select` yan tümcesinde anonim bir tür oluşturarak ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcısı kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e744-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="2e744-119">Bunun nasıl yapılacağı hakkında bir örnek için bkz. [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="2e744-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="2e744-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e744-120">Remarks</span></span>

<span data-ttu-id="2e744-121">Derleme zamanında, `select` yan tümcesi <xref:System.Linq.Enumerable.Select%2A> standart sorgu işlecine bir yöntem çağrısına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="2e744-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e744-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e744-122">See also</span></span>

- [<span data-ttu-id="2e744-123">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="2e744-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2e744-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2e744-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="2e744-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="2e744-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="2e744-126">partial (Yöntem) (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="2e744-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="2e744-127">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="2e744-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="2e744-128">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="2e744-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="2e744-129">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="2e744-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
