---
title: 'Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163156"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="7990f-102">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="7990f-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="7990f-103">Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir parçasıdır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] teknoloji ailesi ve Hizmetleri tarafından sağlanan dayanır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], arasında bir bağlantı kullanabilirsiniz bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="7990f-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7990f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7990f-104">Example</span></span>  
 <span data-ttu-id="7990f-105">Aşağıdaki örnek nasıl arasında aynı bağlantıyı yeniden gösterir bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] komut ve <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="7990f-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7990f-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7990f-106">See also</span></span>

- [<span data-ttu-id="7990f-107">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="7990f-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="7990f-108">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7990f-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="7990f-109">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="7990f-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
