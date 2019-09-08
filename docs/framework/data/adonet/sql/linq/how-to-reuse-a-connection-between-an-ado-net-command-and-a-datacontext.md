---
title: 'Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793296"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="5804c-102">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="5804c-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="5804c-103">, ADO.net 'in teknoloji ailesinin bir parçası olduğundan ve ADO.NET tarafından sunulan hizmetleri temel aldığı için, bir ADO.NET komutu <xref:System.Data.Linq.DataContext>ve arasında bir bağlantıyı yeniden kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5804c-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5804c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5804c-104">Example</span></span>  
 <span data-ttu-id="5804c-105">Aşağıdaki örnek, bir ADO.NET komutu ve ile <xref:System.Data.Linq.DataContext>aynı bağlantının nasıl yeniden kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5804c-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5804c-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5804c-106">See also</span></span>

- [<span data-ttu-id="5804c-107">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="5804c-107">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="5804c-108">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5804c-108">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="5804c-109">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="5804c-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
