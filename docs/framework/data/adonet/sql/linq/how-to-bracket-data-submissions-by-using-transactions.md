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
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma

<xref:System.Transactions.TransactionScope>Gönderimlerinizi veritabanına eklemek için ' i kullanabilirsiniz. Daha fazla bilgi için bkz. [Işlem desteği](transaction-support.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, içindeki veritabanı gönderimini barındırır <xref:System.Transactions.TransactionScope> .  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
- [İşlem Desteği](transaction-support.md)
