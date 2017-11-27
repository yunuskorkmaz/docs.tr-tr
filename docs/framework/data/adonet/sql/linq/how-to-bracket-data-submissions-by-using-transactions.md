---
title: "Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 071c0c8bc7e0bb8dca01e9fc51c66fb930ed102b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="a0917-102">Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç</span><span class="sxs-lookup"><span data-stu-id="a0917-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="a0917-103">Kullanabileceğiniz <xref:System.Transactions.TransactionScope> veritabanına, gönderimlerini köşeli ayraç için.</span><span class="sxs-lookup"><span data-stu-id="a0917-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="a0917-104">Daha fazla bilgi için bkz: [işlem desteği](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="a0917-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0917-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0917-105">Example</span></span>  
 <span data-ttu-id="a0917-106">Aşağıdaki kod veritabanı gönderisine kapsayan bir <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="a0917-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a0917-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0917-107">See Also</span></span>  
 [<span data-ttu-id="a0917-108">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="a0917-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="a0917-109">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="a0917-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="a0917-110">İşlem desteği</span><span class="sxs-lookup"><span data-stu-id="a0917-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
