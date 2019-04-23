---
title: 'Nasıl yapılır: LINQ to SQL Komutlarını Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: d71eaf834ebf36d462f8581f0074b2f6a90bae17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211614"
---
# <a name="how-to-display-linq-to-sql-commands"></a>Nasıl yapılır: LINQ to SQL Komutlarını Görüntüleme
Kullanım <xref:System.Data.Linq.DataContext.GetCommand%2A> SQL komutları ve diğer bilgileri görüntülemek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, sorgudan oluşturulan SQL komutları, komut türü koyun ve bağlantı türü tarafından çıkış konsol penceresinde görüntüler.  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 Çıktı aşağıdaki gibi görünür:  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
