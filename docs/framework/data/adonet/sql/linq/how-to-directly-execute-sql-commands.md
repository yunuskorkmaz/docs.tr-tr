---
title: 'Nasıl yapılır: doğrudan SQL komutları yürütün'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 90fb0d7027946ce4f38c2ba4930ac3510e2a42b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351878"
---
# <a name="how-to-directly-execute-sql-commands"></a>Nasıl yapılır: doğrudan SQL komutları yürütün
Varsayarak bir <xref:System.Data.Linq.DataContext> kullanabileceğiniz bağlantısı <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> nesneleri döndürmeyen SQL komutlarını çalıştırmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, SQL Server'ın 1.00 ile UnitPrice artırmak neden olur.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Doğrudan SQL Sorguları Yürütme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [Veritabanı ile İletişim Kurma](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
