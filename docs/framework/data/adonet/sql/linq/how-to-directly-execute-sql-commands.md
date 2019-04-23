---
title: 'Nasıl yapılır: Doğrudan SQL Komutları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078908"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="00419-102">Nasıl yapılır: Doğrudan SQL Komutları Yürütme</span><span class="sxs-lookup"><span data-stu-id="00419-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="00419-103">Varsayılarak bir <xref:System.Data.Linq.DataContext> kullanabileceğiniz bağlantısı <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> nesneleri döndürmeyen SQL komutları yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="00419-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00419-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="00419-104">Example</span></span>  
 <span data-ttu-id="00419-105">Aşağıdaki örnek, SQL Server'ı tarafından 1,00 UnitPrice artırmak neden olur.</span><span class="sxs-lookup"><span data-stu-id="00419-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="00419-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00419-106">See also</span></span>

- [<span data-ttu-id="00419-107">Nasıl yapılır: Doğrudan SQL sorguları yürütme</span><span class="sxs-lookup"><span data-stu-id="00419-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="00419-108">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="00419-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
