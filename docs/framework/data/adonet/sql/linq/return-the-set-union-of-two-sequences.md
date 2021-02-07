---
description: 'Hakkında daha fazla bilgi edinin: Iki sıranın set birleşimini döndürün'
title: İki Dizinin Küme Birleşimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5541316560c05712e22c54f706b02d868fadb381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662968"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="dd310-103">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="dd310-103">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="dd310-104"><xref:System.Linq.Queryable.Union%2A>İki sıranın set birleşimini döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd310-104">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd310-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd310-105">Example</span></span>  

 <span data-ttu-id="dd310-106">Bu örnek <xref:System.Linq.Queryable.Union%2A> , ya da içinde olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .</span><span class="sxs-lookup"><span data-stu-id="dd310-106">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="dd310-107">' De, işleç multisets 'ler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Union%2A> için çoklu kümeler için TANıMLANıR ( [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL 'de yan tümcesinin sonucu etkin değildir).</span><span class="sxs-lookup"><span data-stu-id="dd310-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="dd310-108">Daha fazla bilgi ve örnek için bkz <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="dd310-108">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd310-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd310-109">See also</span></span>

- [<span data-ttu-id="dd310-110">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="dd310-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="dd310-111">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="dd310-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
