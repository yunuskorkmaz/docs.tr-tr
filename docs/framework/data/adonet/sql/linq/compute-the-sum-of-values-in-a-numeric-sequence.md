---
title: Sayısal Dizideki Değerlerin Toplamını Hesaplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247922"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="268d9-102">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="268d9-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="268d9-103">Bir dizideki sayısal değerlerin toplamını hesaplamak için işlecinikullanın.<xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="268d9-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="268d9-104">`Sum` İçindeki[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]işlecinin aşağıdaki özelliklerine göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="268d9-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="268d9-105">Standart sorgu işleci toplama işleci `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="268d9-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="268d9-106">' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, SQL 'in semantiği değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="268d9-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="268d9-107">Bu nedenle, `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır yerine null olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="268d9-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="268d9-108">Ara sonuçlarda SQL sınırlamaları, içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]toplamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="268d9-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="268d9-109">32 bitlik tamsayı miktarları toplamı 64 bit sonuçlar kullanılarak hesaplanmaz ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum`çevirisi için taşma oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="268d9-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="268d9-110">Bu olasılık, standart sorgu Işleci uygulamasının karşılık gelen bellek içi sıra için taşmaya neden olmaması durumunda bile vardır.</span><span class="sxs-lookup"><span data-stu-id="268d9-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268d9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="268d9-111">Example</span></span>  
 <span data-ttu-id="268d9-112">Aşağıdaki örnek, `Order` tablosundaki tüm siparişlerin toplam Navlun düzeyini bulur.</span><span class="sxs-lookup"><span data-stu-id="268d9-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="268d9-113">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="268d9-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="268d9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="268d9-114">Example</span></span>  
 <span data-ttu-id="268d9-115">Aşağıdaki örnek, tüm ürünlerin sırasıyla toplam birim sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="268d9-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="268d9-116">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `780`.</span><span class="sxs-lookup"><span data-stu-id="268d9-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="268d9-117">Türleri (örneğin,) `short` `Sum` , `UnitsOnOrder`kısa türler için aşırı yüklemesi olmadığından, tür atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="268d9-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="268d9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="268d9-118">See also</span></span>

- [<span data-ttu-id="268d9-119">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="268d9-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="268d9-120">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="268d9-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
