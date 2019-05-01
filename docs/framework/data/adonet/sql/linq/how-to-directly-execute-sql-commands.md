---
title: 'Nasıl yapılır: Doğrudan SQL Komutları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903233"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="d9d3c-102">Nasıl yapılır: Doğrudan SQL Komutları Yürütme</span><span class="sxs-lookup"><span data-stu-id="d9d3c-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="d9d3c-103">Varsayılarak bir <xref:System.Data.Linq.DataContext> kullanabileceğiniz bağlantısı <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> nesneleri döndürmeyen SQL komutları yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d3c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9d3c-104">Example</span></span>  
 <span data-ttu-id="d9d3c-105">Aşağıdaki örnek, SQL Server'ı tarafından 1,00 UnitPrice artırmak neden olur.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d9d3c-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-106">See also</span></span>

- [<span data-ttu-id="d9d3c-107">Nasıl yapılır: Doğrudan SQL sorguları yürütme</span><span class="sxs-lookup"><span data-stu-id="d9d3c-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="d9d3c-108">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="d9d3c-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
