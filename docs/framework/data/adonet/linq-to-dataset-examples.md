---
title: "LINQ-DataSet örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 61e2e107c3e62569a47b4bd84e451ff55adab208
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="d5b90-102">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="d5b90-103">Bu bölümde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] standart sorgu işleçleri kullanma örnekleri programlama.</span><span class="sxs-lookup"><span data-stu-id="d5b90-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="d5b90-104"><xref:System.Data.DataSet> Bu örneklerde kullanılan kullanılarak doldurulur `FillDataSet` belirtilen yöntemi [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d5b90-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="d5b90-105">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="d5b90-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5b90-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d5b90-106">In This Section</span></span>  
 [<span data-ttu-id="d5b90-107">Sorgu İfadesi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="d5b90-108">Aşağıdaki örnekler içerir:</span><span class="sxs-lookup"><span data-stu-id="d5b90-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="d5b90-109">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="d5b90-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="d5b90-110">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d5b90-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="d5b90-111">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="d5b90-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="d5b90-112">Sıralama</span><span class="sxs-lookup"><span data-stu-id="d5b90-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="d5b90-113">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="d5b90-114">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="d5b90-115">Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="d5b90-116">Metot Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="d5b90-117">Aşağıdaki örnekler içerir:</span><span class="sxs-lookup"><span data-stu-id="d5b90-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="d5b90-118">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="d5b90-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="d5b90-119">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="d5b90-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="d5b90-120">Sıralama</span><span class="sxs-lookup"><span data-stu-id="d5b90-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="d5b90-121">Ayarlama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="d5b90-122">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="d5b90-123">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="d5b90-124">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="d5b90-125">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="d5b90-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="d5b90-126">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5b90-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="d5b90-127">Nasıl kullanılacağını gösteren örnekleri içeren <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi ve <xref:System.Data.DataRowComparer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5b90-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b90-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5b90-128">See Also</span></span>  
 [<span data-ttu-id="d5b90-129">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5b90-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="d5b90-130">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="d5b90-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
