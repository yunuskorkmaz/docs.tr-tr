---
title: 'Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793296"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma
, ADO.net 'in teknoloji ailesinin bir parçası olduğundan ve ADO.NET tarafından sunulan hizmetleri temel aldığı için, bir ADO.NET komutu <xref:System.Data.Linq.DataContext>ve arasında bir bağlantıyı yeniden kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ADO.NET komutu ve ile <xref:System.Data.Linq.DataContext>aynı bağlantının nasıl yeniden kullanılacağını göstermektedir.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [ADO.NET ve LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
