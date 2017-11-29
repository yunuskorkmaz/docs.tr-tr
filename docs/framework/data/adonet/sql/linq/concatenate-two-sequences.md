---
title: "İki dizileri birleştirme"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e7230e1f53f58f37dacbb1f22fbad1593768e01e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="e1f7b-102">İki dizileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="e1f7b-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="e1f7b-103">Kullanım <xref:System.Linq.Queryable.Concat%2A> iki sıraları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="e1f7b-104"><xref:System.Linq.Queryable.Concat%2A> İşleci alıcı ve bağımsız değişkeni siparişleri bulunduğu aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="e1f7b-105">Sonuçları üretilen önce SQL'de sıralama son adımdır.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="e1f7b-106">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerini sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="e1f7b-107">Sıralama emin olmak için sonuçları doğru olduğundan, açıkça sonuçları sıralamak emin olun.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f7b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1f7b-108">Example</span></span>  
 <span data-ttu-id="e1f7b-109">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` telefon ve Faks numaraları.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="e1f7b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1f7b-110">Example</span></span>  
 <span data-ttu-id="e1f7b-111">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` adı ve telefon numarası eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="e1f7b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f7b-112">See Also</span></span>  
 [<span data-ttu-id="e1f7b-113">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="e1f7b-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="e1f7b-114">Standart sorgu işleci çevirisi</span><span class="sxs-lookup"><span data-stu-id="e1f7b-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
