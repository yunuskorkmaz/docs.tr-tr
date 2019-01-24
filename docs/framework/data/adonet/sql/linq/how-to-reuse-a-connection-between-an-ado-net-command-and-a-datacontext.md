---
title: 'Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 079b4b28a613ce6a9ae525514b89ea9e316a7c66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613681"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="14cc0-102">Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="14cc0-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="14cc0-103">Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir parçasıdır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] teknoloji ailesi ve Hizmetleri tarafından sağlanan dayanır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], arasında bir bağlantı kullanabilirsiniz bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="14cc0-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14cc0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="14cc0-104">Example</span></span>  
 <span data-ttu-id="14cc0-105">Aşağıdaki örnek nasıl arasında aynı bağlantıyı yeniden gösterir bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="14cc0-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="14cc0-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14cc0-106">See also</span></span>
- [<span data-ttu-id="14cc0-107">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="14cc0-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="14cc0-108">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="14cc0-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="14cc0-109">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="14cc0-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
