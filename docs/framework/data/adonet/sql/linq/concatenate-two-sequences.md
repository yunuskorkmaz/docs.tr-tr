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
ms.workload: dotnet
ms.openlocfilehash: 8bcb20f5d057c3b54e49e2fac81e9799ac42b1f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="16149-102">İki dizileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="16149-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="16149-103">Kullanım <xref:System.Linq.Queryable.Concat%2A> iki sıraları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="16149-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="16149-104"><xref:System.Linq.Queryable.Concat%2A> İşleci alıcı ve bağımsız değişkeni siparişleri bulunduğu aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="16149-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="16149-105">Sonuçları üretilen önce SQL'de sıralama son adımdır.</span><span class="sxs-lookup"><span data-stu-id="16149-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="16149-106">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerini sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="16149-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="16149-107">Sıralama emin olmak için sonuçları doğru olduğundan, açıkça sonuçları sıralamak emin olun.</span><span class="sxs-lookup"><span data-stu-id="16149-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16149-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="16149-108">Example</span></span>  
 <span data-ttu-id="16149-109">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` telefon ve Faks numaraları.</span><span class="sxs-lookup"><span data-stu-id="16149-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="16149-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="16149-110">Example</span></span>  
 <span data-ttu-id="16149-111">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` adı ve telefon numarası eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="16149-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="16149-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16149-112">See Also</span></span>  
 [<span data-ttu-id="16149-113">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="16149-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="16149-114">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="16149-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
