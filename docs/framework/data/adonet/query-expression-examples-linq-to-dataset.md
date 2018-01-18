---
title: "Sorgu ifade örnekleri (LINQ-DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 01b31debeb71180f4b1c86e6c9e0dfb1251bf807
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="de07b-102">Sorgu ifade örnekleri (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="de07b-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="de07b-103">Bu bölümde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] standart sorgu işleçleri kullanmak sorgu ifade sözdizimi örneklerde programlama.</span><span class="sxs-lookup"><span data-stu-id="de07b-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="de07b-104"><xref:System.Data.DataSet> Bu örneklerde kullanılan kullanılarak doldurulur `FillDataSet` belirtilen yöntemi [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="de07b-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="de07b-105">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="de07b-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de07b-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="de07b-106">In This Section</span></span>  
 [<span data-ttu-id="de07b-107">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="de07b-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="de07b-108">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="de07b-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="de07b-109">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="de07b-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="de07b-110">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Where%2A> sorgu yönteme bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="de07b-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="de07b-111">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="de07b-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="de07b-112">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sonuçları bölüm.</span><span class="sxs-lookup"><span data-stu-id="de07b-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="de07b-113">Sıralama</span><span class="sxs-lookup"><span data-stu-id="de07b-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="de07b-114">Bu konudaki örnekler nasıl kullanılacağını göstermektedir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenByDescending%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sonuçları sıralayın.</span><span class="sxs-lookup"><span data-stu-id="de07b-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="de07b-115">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="de07b-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="de07b-116">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> ve <xref:System.Linq.Enumerable.ElementAt%2A> almak için yöntemleri <xref:System.Data.DataRow> öğelerinden bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="de07b-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="de07b-117">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="de07b-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="de07b-118">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve veri toplama.</span><span class="sxs-lookup"><span data-stu-id="de07b-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="de07b-119">Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="de07b-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="de07b-120">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="de07b-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de07b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de07b-121">See Also</span></span>  
 [<span data-ttu-id="de07b-122">Metot Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="de07b-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [<span data-ttu-id="de07b-123">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="de07b-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="de07b-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="de07b-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
