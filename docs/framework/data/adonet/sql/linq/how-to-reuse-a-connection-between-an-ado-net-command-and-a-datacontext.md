---
title: "Nasıl yapılır: ADO.NET komutu ile bir DataContext arasında bir bağlantı yeniden"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 483a97817162140af61df6a58c3e9ab003235c74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Nasıl yapılır: ADO.NET komutu ile bir DataContext arasında bir bağlantı yeniden
Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir parçası olan [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] teknoloji ailesi ve Hizmetleri tarafından sağlanan dayalı [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], arasında bir bağlantı yeniden bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komutu ve bir <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek arasında aynı bağlantı yeniden gösterilmektedir bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka plan bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [ADO.NET ve LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [Veritabanı ile iletişim](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
