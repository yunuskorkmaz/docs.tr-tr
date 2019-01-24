---
title: Türü genel IEnumerable öğesine dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d1f4c1c4a561c893b5846e6ae0b08b2d78c3589d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509603"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="26ada-102">Türü genel IEnumerable öğesine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="26ada-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="26ada-103">Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="26ada-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ada-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="26ada-104">Example</span></span>  
 <span data-ttu-id="26ada-105">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanılarak `Query`) SQL sorgu dönüştürün ve sunucu üzerinde yürütülen isteriz.</span><span class="sxs-lookup"><span data-stu-id="26ada-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="26ada-106">Ancak `where` yan tümcesi kullanıcı tanımlı bir istemci-tarafı yöntemi başvurur (`isValidProduct`), dönüştürülemeyen SQL.</span><span class="sxs-lookup"><span data-stu-id="26ada-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="26ada-107">İstemci tarafı genel belirtmek için çözümüdür <xref:System.Collections.Generic.IEnumerable%601> uygulaması `where` genel değiştirilecek <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="26ada-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="26ada-108">Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="26ada-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="26ada-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ada-109">See also</span></span>
- [<span data-ttu-id="26ada-110">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="26ada-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
