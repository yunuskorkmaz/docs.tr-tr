---
description: 'Hakkında daha fazla bilgi: sayısal bir dizide en küçük değeri bulma'
title: Sayısal Dizideki En Küçük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 6f265c6db3e143bdd5371aa9d30b4dd248e8fe3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803847"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="e09e7-103">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="e09e7-103">Find the Minimum Value in a Numeric Sequence</span></span>

<span data-ttu-id="e09e7-104"><xref:System.Linq.Enumerable.Min%2A>Bir sayısal değer dizisinden en küçük değeri döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e09e7-104">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09e7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e09e7-105">Example</span></span>  

 <span data-ttu-id="e09e7-106">Aşağıdaki örnek, herhangi bir ürünün en düşük birim fiyatını bulur.</span><span class="sxs-lookup"><span data-stu-id="e09e7-106">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="e09e7-107">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `2.5000` .</span><span class="sxs-lookup"><span data-stu-id="e09e7-107">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="e09e7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e09e7-108">Example</span></span>  

 <span data-ttu-id="e09e7-109">Aşağıdaki örnek herhangi bir sipariş için en düşük navlun miktarını bulur.</span><span class="sxs-lookup"><span data-stu-id="e09e7-109">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="e09e7-110">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `0.0200` .</span><span class="sxs-lookup"><span data-stu-id="e09e7-110">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e09e7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e09e7-111">Example</span></span>  

 <span data-ttu-id="e09e7-112">Aşağıdaki örnek, `Products` her kategoride en düşük birim fiyatına sahip olan öğesini bulmak Için min kullanır.</span><span class="sxs-lookup"><span data-stu-id="e09e7-112">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="e09e7-113">Çıktı kategoriye göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="e09e7-113">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="e09e7-114">Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlarınız aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="e09e7-114">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="e09e7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e09e7-115">See also</span></span>

- [<span data-ttu-id="e09e7-116">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="e09e7-116">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="e09e7-117">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="e09e7-117">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
