---
title: 'Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793810"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma
Gönderimlerinizi veritabanına <xref:System.Transactions.TransactionScope> eklemek için ' i kullanabilirsiniz. Daha fazla bilgi için bkz. [Işlem desteği](transaction-support.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, içindeki <xref:System.Transactions.TransactionScope>veritabanı gönderimini barındırır.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
- [İşlem Desteği](transaction-support.md)
