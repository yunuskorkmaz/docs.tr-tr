---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Işlemleri kullanarak veri gönderimlerinin ayracı'
title: 'Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: a1bbebfcdb4b65e83c4ac6dc9b87b06f33f2cb41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739033"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="9badc-103">Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma</span><span class="sxs-lookup"><span data-stu-id="9badc-103">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="9badc-104"><xref:System.Transactions.TransactionScope>Gönderimlerinizi veritabanına eklemek için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9badc-104">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="9badc-105">Daha fazla bilgi için bkz. [Işlem desteği](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="9badc-105">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9badc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9badc-106">Example</span></span>  

 <span data-ttu-id="9badc-107">Aşağıdaki kod, içindeki veritabanı gönderimini barındırır <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="9badc-107">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9badc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9badc-108">See also</span></span>

- [<span data-ttu-id="9badc-109">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="9badc-109">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="9badc-110">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="9badc-110">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="9badc-111">İşlem Desteği</span><span class="sxs-lookup"><span data-stu-id="9badc-111">Transaction Support</span></span>](transaction-support.md)
