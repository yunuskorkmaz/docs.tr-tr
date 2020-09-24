---
title: 'Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 4d3efedbf15be55fa7a9ab235f881f1c97758953
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161366"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="eb68a-102">Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma</span><span class="sxs-lookup"><span data-stu-id="eb68a-102">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="eb68a-103"><xref:System.Transactions.TransactionScope>Gönderimlerinizi veritabanına eklemek için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb68a-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="eb68a-104">Daha fazla bilgi için bkz. [Işlem desteği](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="eb68a-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb68a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb68a-105">Example</span></span>  

 <span data-ttu-id="eb68a-106">Aşağıdaki kod, içindeki veritabanı gönderimini barındırır <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="eb68a-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="eb68a-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb68a-107">See also</span></span>

- [<span data-ttu-id="eb68a-108">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="eb68a-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="eb68a-109">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="eb68a-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="eb68a-110">İşlem Desteği</span><span class="sxs-lookup"><span data-stu-id="eb68a-110">Transaction Support</span></span>](transaction-support.md)
