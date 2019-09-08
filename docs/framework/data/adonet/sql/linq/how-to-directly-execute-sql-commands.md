---
title: 'Nasıl yapılır: Doğrudan SQL Komutları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 3f28351a29915bebd698e00113bb05647d8412b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781988"
---
# <a name="how-to-directly-execute-sql-commands"></a>Nasıl yapılır: Doğrudan SQL Komutları Yürütme
Bir <xref:System.Data.Linq.DataContext> bağlantı kabul edildiğinde, nesneleri döndürmeyen <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> SQL komutlarını yürütmek için kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, SQL Server BirimFiyat 'ın 1,00 ' i artırmasına neden olur.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: SQL sorgularını doğrudan Yürüt](how-to-directly-execute-sql-queries.md)
- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
