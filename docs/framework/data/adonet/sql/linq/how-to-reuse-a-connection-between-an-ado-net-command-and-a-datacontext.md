---
title: 'Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 079b4b28a613ce6a9ae525514b89ea9e316a7c66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613681"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma
Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir parçasıdır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] teknoloji ailesi ve Hizmetleri tarafından sağlanan dayanır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], arasında bir bağlantı kullanabilirsiniz bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl arasında aynı bağlantıyı yeniden gösterir bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [ADO.NET ve LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [Veritabanı ile İletişim Kurma](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
