---
title: 'Nasıl yapılır: Doğrudan SQL Komutları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 6c72e683c37968ce18717b70ef6d647ca287bd20
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147651"
---
# <a name="how-to-directly-execute-sql-commands"></a>Nasıl yapılır: Doğrudan SQL Komutları Yürütme

Bir bağlantı kabul edildiğinde <xref:System.Data.Linq.DataContext> , <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> NESNELERI döndürmeyen SQL komutlarını yürütmek için kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, SQL Server BirimFiyat 'ın 1,00 ' i artırmasına neden olur.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Doğrudan SQL Sorguları Yürütme](how-to-directly-execute-sql-queries.md)
- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
