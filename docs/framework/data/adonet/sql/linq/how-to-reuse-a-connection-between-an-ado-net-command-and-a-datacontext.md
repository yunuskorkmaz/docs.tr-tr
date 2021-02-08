---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir bağlantıyı bir ADO.NET komutu ile DataContext arasında yeniden kullanma'
title: 'Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: d5bf45dfd705ed6e9b9d4ed9659e01bfcb539df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785958"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma

, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ADO.net 'in teknoloji ailesinin bir parçası olduğundan ve ADO.NET tarafından sunulan hizmetleri temel aldığı için, bir ADO.NET komutu ve arasında bir bağlantıyı yeniden kullanabilirsiniz <xref:System.Data.Linq.DataContext> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir ADO.NET komutu ve ile aynı bağlantının nasıl yeniden kullanılacağını göstermektedir <xref:System.Data.Linq.DataContext> .  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [ADO.NET ve LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
