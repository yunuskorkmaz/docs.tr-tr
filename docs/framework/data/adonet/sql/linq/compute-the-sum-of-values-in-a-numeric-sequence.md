---
title: Sayısal Dizideki Değerlerin Toplamını Hesaplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3d160e2cce5f3e0a7eea305657260b6fa4ded7fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164447"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="74395-102">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="74395-102">Compute the Sum of Values in a Numeric Sequence</span></span>

<span data-ttu-id="74395-103"><xref:System.Linq.Enumerable.Sum%2A>Bir dizideki sayısal değerlerin toplamını hesaplamak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="74395-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="74395-104">İçindeki işlecinin aşağıdaki özelliklerine göz önünde edin `Sum` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="74395-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="74395-105">Standart sorgu Işleci toplama işleci `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="74395-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="74395-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, SQL 'in semantiği değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="74395-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="74395-107">Bu nedenle, `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır yerine null olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="74395-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="74395-108">Ara sonuçlarda SQL sınırlamaları, içindeki toplamalar için geçerlidir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="74395-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="74395-109">32 bitlik tamsayı miktarları toplamı 64 bit sonuçlar kullanılarak hesaplanmaz ve çevirisi için taşma oluşabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum` .</span><span class="sxs-lookup"><span data-stu-id="74395-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="74395-110">Bu olasılık, standart sorgu Işleci uygulamasının karşılık gelen bellek içi sıra için taşmaya neden olmaması durumunda bile vardır.</span><span class="sxs-lookup"><span data-stu-id="74395-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74395-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="74395-111">Example</span></span>  

 <span data-ttu-id="74395-112">Aşağıdaki örnek, tablosundaki tüm siparişlerin toplam Navlun düzeyini bulur `Order` .</span><span class="sxs-lookup"><span data-stu-id="74395-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="74395-113">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `64942.6900` .</span><span class="sxs-lookup"><span data-stu-id="74395-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="74395-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="74395-114">Example</span></span>  

 <span data-ttu-id="74395-115">Aşağıdaki örnek, tüm ürünlerin sırasıyla toplam birim sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="74395-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="74395-116">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `780` .</span><span class="sxs-lookup"><span data-stu-id="74395-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="74395-117">`short`Türleri (örneğin, `UnitsOnOrder` ), `Sum` kısa türler için aşırı yüklemesi olmadığından, tür atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="74395-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="74395-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74395-118">See also</span></span>

- [<span data-ttu-id="74395-119">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="74395-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="74395-120">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="74395-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
