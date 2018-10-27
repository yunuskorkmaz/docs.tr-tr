---
title: select tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 3fa60d4e7546fc88ac2a2ffea45ae69b0da7a6a6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183548"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="8646c-102">select tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8646c-102">select clause (C# Reference)</span></span>

<span data-ttu-id="8646c-103">Bir sorgu ifadesinde `select` yan tümcesi sorgu yürütüldüğünde, üretilecek değerler türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8646c-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="8646c-104">Önceki tümceleri tüm değerlendirmesi ve tüm ifadelerin sonucu dayalı `select` yan tümcesi kendisi.</span><span class="sxs-lookup"><span data-stu-id="8646c-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="8646c-105">Sorgu ifadesi ile bitmesi bir `select` yan tümcesi veya [grubu](group-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8646c-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="8646c-106">Aşağıdaki örnek, basit bir gösterir `select` yan tümcesi bir sorgu ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="8646c-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="8646c-107">Sıra türü tarafından üretilen `select` yan tümcesi bir sorgu değişkeni türünü belirler `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="8646c-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="8646c-108">En basit durumda, `select` yan tümcesi yalnızca aralık değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8646c-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="8646c-109">Bu veri kaynağı olarak aynı türdeki öğeleri içeren döndürülen dizinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="8646c-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="8646c-110">Daha fazla bilgi için [LINQ Sorgu işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8646c-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="8646c-111">Ancak, `select` yan tümcesi, ayrıca dönüştürme için güçlü bir mekanizma sağlar (veya *planlanması*) yeni tür olarak veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="8646c-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="8646c-112">Daha fazla bilgi için [LINQ (C#) ile veri dönüştürmeler](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8646c-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="8646c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8646c-113">Example</span></span>

<span data-ttu-id="8646c-114">Aşağıdaki örnekte tüm farklı formları gösteren bir `select` yan tümcesi alabilir.</span><span class="sxs-lookup"><span data-stu-id="8646c-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="8646c-115">Her sorgu, arasındaki ilişkiyi unutmayın `select` yan tümcesi ve türünü *sorgu değişkeni* (`studentQuery1`, `studentQuery2`, vb.).</span><span class="sxs-lookup"><span data-stu-id="8646c-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="8646c-116">Gösterildiği `studentQuery8` önceki örnekte, bazı durumlarda, yalnızca bir alt kümesini kaynak öğeleri özelliklerini içeren döndürülen dizinin öğelerini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8646c-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="8646c-117">Döndürülen dizi olabildiğince küçük tutmak tarafından bellek gereksinimlerini azaltın ve sorgu yürütme hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="8646c-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="8646c-118">İçindeki anonim bir tür oluşturarak bunu gerçekleştirebilirsiniz `select` yan tümcesi ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcı kullanma.</span><span class="sxs-lookup"><span data-stu-id="8646c-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="8646c-119">Bunu yapmak nasıl bir örnek için bkz [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="8646c-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="8646c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8646c-120">Remarks</span></span>

<span data-ttu-id="8646c-121">Derleme zamanında `select` yan tümcesi için bir yöntem çağrısına çevrilir <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="8646c-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="8646c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8646c-122">See also</span></span>

- [<span data-ttu-id="8646c-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8646c-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8646c-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8646c-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="8646c-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8646c-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="8646c-126">partial (yöntem) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8646c-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="8646c-127">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="8646c-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="8646c-128">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8646c-128">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="8646c-129">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="8646c-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)