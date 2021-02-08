---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir bağlantıyı bir ADO.NET komutu ile DataContext arasında yeniden kullanma'
title: 'Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: d5bf45dfd705ed6e9b9d4ed9659e01bfcb539df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785958"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="5d159-103">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="5d159-103">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>

<span data-ttu-id="5d159-104">, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ADO.net 'in teknoloji ailesinin bir parçası olduğundan ve ADO.NET tarafından sunulan hizmetleri temel aldığı için, bir ADO.NET komutu ve arasında bir bağlantıyı yeniden kullanabilirsiniz <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="5d159-104">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d159-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d159-105">Example</span></span>  

 <span data-ttu-id="5d159-106">Aşağıdaki örnek, bir ADO.NET komutu ve ile aynı bağlantının nasıl yeniden kullanılacağını göstermektedir <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="5d159-106">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5d159-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d159-107">See also</span></span>

- [<span data-ttu-id="5d159-108">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="5d159-108">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="5d159-109">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5d159-109">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="5d159-110">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="5d159-110">Communicating with the Database</span></span>](communicating-with-the-database.md)
