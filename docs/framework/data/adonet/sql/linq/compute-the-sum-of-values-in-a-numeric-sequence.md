---
title: "Bir sayısal sırada değerlerinin toplamı işlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 547d9f245d41fac2e2d65877ddbb2a8660d73c42
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="a33cd-102">Bir sayısal sırada değerlerinin toplamı işlem</span><span class="sxs-lookup"><span data-stu-id="a33cd-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="a33cd-103">Kullanım <xref:System.Linq.Enumerable.Sum%2A> bir sırada sayısal değerlerinin toplamı işlem işleci.</span><span class="sxs-lookup"><span data-stu-id="a33cd-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="a33cd-104">Aşağıdaki özellikleri Not `Sum` işlecinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a33cd-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="a33cd-105">Standart sorgu işleci Toplama işleci `Sum` için boş bir dizi veya yalnızca null içeren bir dizi sıfır değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a33cd-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="a33cd-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değişmez.</span><span class="sxs-lookup"><span data-stu-id="a33cd-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="a33cd-107">Bu nedenle, `Sum` null yerine sıfır yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a33cd-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
-   <span data-ttu-id="a33cd-108">Ara sonuçların SQL sınırlamalar uygulanır Toplamaların [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a33cd-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a33cd-109">32 bit tamsayı miktarların toplamı hesaplanan 64-bit sonuçları kullanarak ve taşma için oluşabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi `Sum`.</span><span class="sxs-lookup"><span data-stu-id="a33cd-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="a33cd-110">Standart sorgu işleci uygulama karşılık gelen bellek içi dizisi taşma neden olmaz olsa bile bu olasılığı bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a33cd-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a33cd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a33cd-111">Example</span></span>  
 <span data-ttu-id="a33cd-112">Aşağıdaki örnekte tüm siparişler, toplam nakliye bulur `Order` tablo.</span><span class="sxs-lookup"><span data-stu-id="a33cd-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="a33cd-113">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="a33cd-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="a33cd-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a33cd-114">Example</span></span>  
 <span data-ttu-id="a33cd-115">Aşağıdaki örnek, tüm ürünleri için sipariş birimlerin toplam sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="a33cd-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="a33cd-116">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `780`.</span><span class="sxs-lookup"><span data-stu-id="a33cd-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="a33cd-117">Cast gerekir Not `short` türleri (örneğin, `UnitsOnOrder`) çünkü `Sum` kısa türleri için hiçbir aşırı yüklemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="a33cd-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="a33cd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a33cd-118">See Also</span></span>  
 [<span data-ttu-id="a33cd-119">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="a33cd-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="a33cd-120">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="a33cd-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
