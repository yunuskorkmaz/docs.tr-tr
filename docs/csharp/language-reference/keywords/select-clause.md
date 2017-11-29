---
title: "select tümcesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f40bc26d1812e76ac618c5a0ddf23c4cef2700d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="4d182-102">select tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4d182-102">select clause (C# Reference)</span></span>
<span data-ttu-id="4d182-103">Bir sorgu ifadesinde `select` yan tümcesi sorgu yürütüldüğünde, üretilecek değerleri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d182-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="4d182-104">Sonuç önceki tüm yan tümceleri değerlendirmesi ve tüm ifadelerinde dayalı `select` yan tümcesi kendisi.</span><span class="sxs-lookup"><span data-stu-id="4d182-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="4d182-105">Bir sorgu ifadesi ile bitmesi bir `select` yan tümcesinin veya bir [grup](../../../csharp/language-reference/keywords/group-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d182-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="4d182-106">Aşağıdaki örnekte basit bir `select` yan tümcesinde bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4d182-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 <span data-ttu-id="4d182-107">Sıra türü üretilen tarafından `select` yan tümcesi belirler sorgu değişkeninin türü `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="4d182-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="4d182-108">En basit durumda, `select` yan tümcesi yalnızca aralık değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d182-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="4d182-109">Bu veri kaynağı olarak aynı türdeki öğeleri içerecek şekilde döndürülen dizi neden olur.</span><span class="sxs-lookup"><span data-stu-id="4d182-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="4d182-110">Daha fazla bilgi için bkz: [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4d182-110">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="4d182-111">Ancak, `select` yan tümcesi de dönüştürme için güçlü bir mekanizma sağlar (veya *planlanması*) yeni türlerine veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="4d182-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="4d182-112">Daha fazla bilgi için bkz: [LINQ (C#) ile veri dönüştürmeler](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4d182-112">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d182-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d182-113">Example</span></span>  
 <span data-ttu-id="4d182-114">Tüm farklı formları aşağıdaki örnekte gösterilir bir `select` yan tümcesi alabilir.</span><span class="sxs-lookup"><span data-stu-id="4d182-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="4d182-115">Her sorguda arasındaki ilişkiyi Not `select` yan tümcesi ve türünü *sorgu değişkeni* (`studentQuery1`, `studentQuery2`, vb.).</span><span class="sxs-lookup"><span data-stu-id="4d182-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 <span data-ttu-id="4d182-116">Gösterildiği gibi `studentQuery8` önceki örnekte, bazı durumlarda, yalnızca bir alt kümesini kaynak öğelerin özellikleri içerecek şekilde döndürülen sıradaki isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d182-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="4d182-117">Döndürülen dizi olabildiğince küçük tutarak bellek gereksinimlerini azaltın ve sorgu yürütme hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="4d182-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="4d182-118">Anonim bir tür oluşturarak bunu gerçekleştirebilirsiniz `select` yan tümcesi ve source öğesi uygun özelliklerinden başlatılamadı nesne Başlatıcı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4d182-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="4d182-119">Bunun nasıl yapılacağı örneği için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="4d182-119">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d182-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d182-120">Remarks</span></span>  
 <span data-ttu-id="4d182-121">Derleme zamanında `select` yan tümcesi bir yöntem çağrısı için çevrilir <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="4d182-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d182-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d182-122">See Also</span></span>  
 [<span data-ttu-id="4d182-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4d182-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4d182-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4d182-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="4d182-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d182-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="4d182-126">partial (yöntem) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4d182-126">partial (Method) (C# Reference)</span></span>](../../../csharp/language-reference/keywords/partial-method.md)  
 [<span data-ttu-id="4d182-127">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="4d182-127">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="4d182-128">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="4d182-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="4d182-129">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="4d182-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
