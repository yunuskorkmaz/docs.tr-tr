---
title: Sayısal Dizideki En Büyük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b7a2588b9e5082915dff4d371adff2ad3d232d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032545"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="f814f-102">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="f814f-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="f814f-103">Kullanım <xref:System.Linq.Enumerable.Max%2A> dizisini sayısal değerler en yüksek değeri bulmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="f814f-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f814f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f814f-104">Example</span></span>  
 <span data-ttu-id="f814f-105">Aşağıdaki örnek, tüm çalışanlar için işe en son tarihi bulur.</span><span class="sxs-lookup"><span data-stu-id="f814f-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="f814f-106">Northwind örnek veritabanına karşı bu sorguyu çalıştırmak, çıktı şu şekildedir: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="f814f-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="f814f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f814f-107">Example</span></span>  
 <span data-ttu-id="f814f-108">Aşağıdaki örnek, herhangi bir ürün için stokta çoğu birimleri bulur.</span><span class="sxs-lookup"><span data-stu-id="f814f-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="f814f-109">Bu örnek Northwind örnek veritabanına karşı çalıştırırsanız, çıktı şu şekildedir: `125`.</span><span class="sxs-lookup"><span data-stu-id="f814f-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="f814f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f814f-110">Example</span></span>  
 <span data-ttu-id="f814f-111">Aşağıdaki örnek bulmak için en çok kullandığı `Products` her kategoride en yüksek birim fiyatı vardır.</span><span class="sxs-lookup"><span data-stu-id="f814f-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="f814f-112">Çıkış, ardından sonuçları kategoriye göre listeler.</span><span class="sxs-lookup"><span data-stu-id="f814f-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="f814f-113">Northwind örnek veritabanıyla önceki sorguyu çalıştırırsanız, sonuçlar şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="f814f-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="f814f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f814f-114">See also</span></span>

- [<span data-ttu-id="f814f-115">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="f814f-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="f814f-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="f814f-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
