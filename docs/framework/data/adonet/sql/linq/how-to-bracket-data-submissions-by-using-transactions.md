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
