---
title: LINQ to DataSet Örnekleri
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: 68d4ed74713858a643c6db40b6982ba2775dbfa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783762"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="73670-102">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="73670-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="73670-103">Bu bölümde, standart sorgu işleçlerini kullanan LINQ to DataSet programlama örnekleri sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73670-103">This section provides LINQ to DataSet programming examples that use the standard query operators.</span></span> <span data-ttu-id="73670-104">Bu örneklerde `FillDataSet`kullanılanyöntemi kullanılarak doldurulur ve [veri kümesine veri yükleme](loading-data-into-a-dataset.md)sırasında belirtilir. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="73670-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="73670-105">Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="73670-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73670-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="73670-106">In This Section</span></span>  
 [<span data-ttu-id="73670-107">Sorgu İfadesi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="73670-107">Query Expression Examples</span></span>](query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="73670-108">Aşağıdaki örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="73670-108">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="73670-109">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="73670-109">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
- [<span data-ttu-id="73670-110">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="73670-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
- [<span data-ttu-id="73670-111">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="73670-111">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
  
- [<span data-ttu-id="73670-112">Sıralama</span><span class="sxs-lookup"><span data-stu-id="73670-112">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="73670-113">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-113">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="73670-114">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-114">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="73670-115">Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-115">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="73670-116">Metot Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="73670-116">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="73670-117">Aşağıdaki örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="73670-117">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="73670-118">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="73670-118">Projection</span></span>](method-based-query-syntax-examples-projection.md)  
  
- [<span data-ttu-id="73670-119">Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="73670-119">Partitioning</span></span>](method-based-query-syntax-examples-partitioning-linq.md)  
  
- [<span data-ttu-id="73670-120">Sıralama</span><span class="sxs-lookup"><span data-stu-id="73670-120">Ordering</span></span>](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="73670-121">Ayarlama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-121">Set Operators</span></span>](method-based-query-syntax-examples-set-operators.md)  
  
- [<span data-ttu-id="73670-122">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-122">Conversion Operators</span></span>](method-based-query-syntax-examples-conversion-operators.md)  
  
- [<span data-ttu-id="73670-123">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-123">Element Operators</span></span>](method-based-query-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="73670-124">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="73670-124">Aggregate Operators</span></span>](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="73670-125">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="73670-125">Join</span></span>](method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="73670-126">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="73670-126">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="73670-127"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yönteminin<xref:System.Data.DataRowComparer> ve sınıfının nasıl kullanılacağını gösteren örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="73670-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73670-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73670-128">See also</span></span>

- [<span data-ttu-id="73670-129">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="73670-129">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="73670-130">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="73670-130">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
