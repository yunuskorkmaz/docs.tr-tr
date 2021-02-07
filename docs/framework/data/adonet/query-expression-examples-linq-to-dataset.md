---
description: 'Daha fazla bilgi edinin: sorgu Ifadesi örnekleri (LINQ to DataSet)'
title: Sorgu Ifadesi örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1d1571a851fae685942cbdbd557b275e86e8b0d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663696"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="da4a2-103">Sorgu Ifadesi örnekleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="da4a2-103">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="da4a2-104">Bu bölümde, sorgu ifadesi sözdiziminde standart sorgu işleçlerini kullanan LINQ to DataSet programlama örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="da4a2-104">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="da4a2-105"><xref:System.Data.DataSet>Bu örneklerde kullanılan yöntemi kullanılarak doldurulur ve `FillDataSet` [veri kümesine veri yükleme](loading-data-into-a-dataset.md)sırasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="da4a2-105">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="da4a2-106">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da4a2-106">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da4a2-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="da4a2-107">In This Section</span></span>  

 [<span data-ttu-id="da4a2-108">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="da4a2-108">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="da4a2-109">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> <xref:System.Linq.Enumerable.SelectMany%2A> bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="da4a2-109">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="da4a2-110">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="da4a2-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="da4a2-111">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Where%2A> yöntemini sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="da4a2-111">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="da4a2-112">Bölümleme</span><span class="sxs-lookup"><span data-stu-id="da4a2-112">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="da4a2-113">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> <xref:System.Data.DataSet> sonuçlarını sorgulamak ve sonuçları bölümlemek için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da4a2-113">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="da4a2-114">Sıralama</span><span class="sxs-lookup"><span data-stu-id="da4a2-114">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="da4a2-115">Bu konudaki örneklerde,,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenByDescending%2A> yöntemlerinin bir sorgulamak <xref:System.Data.DataSet> ve sonuçları sıralamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da4a2-115">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="da4a2-116">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-116">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="da4a2-117">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.ElementAt%2A> öğelerinden öğeleri almak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataRow> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="da4a2-117">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="da4a2-118">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-118">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="da4a2-119">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Sum%2A> <xref:System.Data.DataSet> ve verileri sorgulamak için,,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da4a2-119">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="da4a2-120">JOIN Işleçleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-120">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="da4a2-121">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.GroupJoin%2A> <xref:System.Linq.Enumerable.Join%2A> bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="da4a2-121">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4a2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4a2-122">See also</span></span>

- [<span data-ttu-id="da4a2-123">Yöntem Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-123">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="da4a2-124">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-124">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="da4a2-125">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="da4a2-125">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
