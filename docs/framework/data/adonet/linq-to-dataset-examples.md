---
title: LINQ to DataSet örnekleri
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: ae43111a5b56e1edf3e1b4089902a8ca1d822d0d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903807"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="3f690-102">LINQ to DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f690-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="3f690-103">Bu bölümde, standart sorgu işleçlerini kullanan DataSet programlama örnekleri için LINQ sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f690-103">This section provides LINQ to DataSet programming examples that use the standard query operators.</span></span> <span data-ttu-id="3f690-104"><xref:System.Data.DataSet> Bu örneklerde kullanılan kullanarak doldurulur `FillDataSet` yöntemi içinde belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="3f690-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="3f690-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f690-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f690-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3f690-106">In This Section</span></span>  
 [<span data-ttu-id="3f690-107">Sorgu İfadesi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f690-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="3f690-108">Aşağıdaki örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3f690-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="3f690-109">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="3f690-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="3f690-110">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="3f690-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="3f690-111">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="3f690-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="3f690-112">Sıralama</span><span class="sxs-lookup"><span data-stu-id="3f690-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="3f690-113">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="3f690-114">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="3f690-115">Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="3f690-116">Metot Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f690-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="3f690-117">Aşağıdaki örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3f690-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="3f690-118">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="3f690-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="3f690-119">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="3f690-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="3f690-120">Sıralama</span><span class="sxs-lookup"><span data-stu-id="3f690-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="3f690-121">Ayarlama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="3f690-122">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="3f690-123">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="3f690-124">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3f690-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="3f690-125">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="3f690-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="3f690-126">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f690-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="3f690-127">Nasıl kullanılacağını gösteren örnekler içeren <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi ve <xref:System.Data.DataRowComparer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3f690-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f690-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f690-128">See also</span></span>
- [<span data-ttu-id="3f690-129">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3f690-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="3f690-130">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="3f690-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
