---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d75c9b9123b52b3e241bea1bbd1d302c406715e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190387"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="52c1c-102">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="52c1c-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="52c1c-103">Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="52c1c-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c1c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c1c-104">Example</span></span>  
 <span data-ttu-id="52c1c-105">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanılarak `Query`) SQL sorgu dönüştürün ve sunucu üzerinde yürütülen isteriz.</span><span class="sxs-lookup"><span data-stu-id="52c1c-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="52c1c-106">Ancak `where` yan tümcesi kullanıcı tanımlı bir istemci-tarafı yöntemi başvurur (`isValidProduct`), dönüştürülemeyen SQL.</span><span class="sxs-lookup"><span data-stu-id="52c1c-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="52c1c-107">İstemci tarafı genel belirtmek için çözümüdür <xref:System.Collections.Generic.IEnumerable%601> uygulaması `where` genel değiştirilecek <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="52c1c-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="52c1c-108">Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="52c1c-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="52c1c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c1c-109">See also</span></span>

- [<span data-ttu-id="52c1c-110">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="52c1c-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
