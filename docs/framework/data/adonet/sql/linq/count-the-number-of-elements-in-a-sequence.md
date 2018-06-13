---
title: Bir dizi öğelerin sayısı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 928cfd33a187637c6d18da3cccefb22bb2950acf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353843"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="a01f5-102">Bir dizi öğelerin sayısı</span><span class="sxs-lookup"><span data-stu-id="a01f5-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="a01f5-103">Kullanım <xref:System.Linq.Enumerable.Count%2A> işleci dizisindeki öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a01f5-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="a01f5-104">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak üretir çıktısı `91`.</span><span class="sxs-lookup"><span data-stu-id="a01f5-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01f5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a01f5-105">Example</span></span>  
 <span data-ttu-id="a01f5-106">Aşağıdaki örnek sayısını sayar `Customers` veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="a01f5-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a01f5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a01f5-107">Example</span></span>  
 <span data-ttu-id="a01f5-108">Aşağıdaki örnek veritabanındaki değil sonlandırdıktan ürün sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="a01f5-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="a01f5-109">Bu örnek Northwind örnek veritabanı karşı çalıştırmak üretir çıktısı `69`.</span><span class="sxs-lookup"><span data-stu-id="a01f5-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a01f5-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a01f5-110">See Also</span></span>  
 [<span data-ttu-id="a01f5-111">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="a01f5-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="a01f5-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="a01f5-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
