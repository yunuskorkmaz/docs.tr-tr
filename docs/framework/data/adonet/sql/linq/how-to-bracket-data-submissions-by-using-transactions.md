---
title: 'Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: aa77d364d1ee4efc09386dd7e889914aeb2f3f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361533"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç
Kullanabileceğiniz <xref:System.Transactions.TransactionScope> veritabanına, gönderimlerini köşeli ayraç için. Daha fazla bilgi için bkz: [işlem desteği](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod veritabanı gönderisine kapsayan bir <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [İşlem Desteği](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
