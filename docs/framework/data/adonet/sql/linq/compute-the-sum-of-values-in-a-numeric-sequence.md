---
title: Sayısal dizideki değerlerin toplamını işlem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 699211e8e573f03935b5406f1759e6c3834718f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713175"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="f1fe4-102">Sayısal dizideki değerlerin toplamını işlem</span><span class="sxs-lookup"><span data-stu-id="f1fe4-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="f1fe4-103">Kullanım <xref:System.Linq.Enumerable.Sum%2A> sıralı sayısal değerlerin toplamını hesaplamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="f1fe4-104">Aşağıdaki özellikleri Not `Sum` işlecinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f1fe4-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="f1fe4-105">Standart sorgu işleci Toplama işleci `Sum` sıfıra boş bir dizi veya yalnızca null içeren bir dizi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="f1fe4-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değişmez.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="f1fe4-107">Bu nedenle, `Sum` yerine null yalnızca null içeren bir dizi veya boş bir dizi için sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
-   <span data-ttu-id="f1fe4-108">Toplamalar Ara sonuçlar SQL sınırlamalar uygulanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1fe4-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="f1fe4-109">32 bit tamsayı miktarlar toplamı, 64-bit sonuçları kullanarak değil hesaplanır ve taşma için meydana gelebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi `Sum`.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="f1fe4-110">Standart sorgu işleci uygulaması karşılık gelen bir bellek içi dizisi taşmaya neden olmaz olsa bile bu olasılığı bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1fe4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1fe4-111">Example</span></span>  
 <span data-ttu-id="f1fe4-112">Aşağıdaki örnek tüm siparişleri toplam navlun bulur `Order` tablo.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="f1fe4-113">Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f1fe4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1fe4-114">Example</span></span>  
 <span data-ttu-id="f1fe4-115">Aşağıdaki örnek, tüm ürünler için sipariş toplam birim sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="f1fe4-116">Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `780`.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="f1fe4-117">Dönüştürmelisiniz Not `short` türleri (örneğin, `UnitsOnOrder`) çünkü `Sum` kısa türleri için hiçbir aşırı yüklemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f1fe4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1fe4-118">See also</span></span>
- [<span data-ttu-id="f1fe4-119">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="f1fe4-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="f1fe4-120">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="f1fe4-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
