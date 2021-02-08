---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: doğrudan SQL komutları yürütme'
title: 'Nasıl yapılır: Doğrudan SQL Komutları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 9dd53b3582b6099bae51dc008debd8cb3142e386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786036"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="68fa2-103">Nasıl yapılır: Doğrudan SQL Komutları Yürütme</span><span class="sxs-lookup"><span data-stu-id="68fa2-103">How to: Directly Execute SQL Commands</span></span>

<span data-ttu-id="68fa2-104">Bir bağlantı kabul edildiğinde <xref:System.Data.Linq.DataContext> , <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> NESNELERI döndürmeyen SQL komutlarını yürütmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68fa2-104">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fa2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="68fa2-105">Example</span></span>  

 <span data-ttu-id="68fa2-106">Aşağıdaki örnek, SQL Server BirimFiyat 'ın 1,00 ' i artırmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="68fa2-106">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="68fa2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68fa2-107">See also</span></span>

- [<span data-ttu-id="68fa2-108">Nasıl yapılır: Doğrudan SQL Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="68fa2-108">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="68fa2-109">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="68fa2-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
