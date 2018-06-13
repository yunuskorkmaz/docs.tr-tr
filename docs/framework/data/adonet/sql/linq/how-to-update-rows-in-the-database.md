---
title: 'Nasıl yapılır: veritabanındaki satırları güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: b1e993aeb510d34e76d91cfd5222ef190d554846
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363760"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="49d6b-102">Nasıl yapılır: veritabanındaki satırları güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="49d6b-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="49d6b-103">Üye değerleri ile ilişkili nesnelerin değiştirerek bir veritabanında satır güncelleştirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> toplama ve değişiklikler veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="49d6b-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="49d6b-104"> Değişikliklerinizi uygun SQL içine çevirir `UPDATE` komutları.</span><span class="sxs-lookup"><span data-stu-id="49d6b-104"> translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49d6b-105">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="49d6b-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="49d6b-106">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="49d6b-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="49d6b-107">Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="49d6b-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="49d6b-108">Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="49d6b-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="49d6b-109">Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="49d6b-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="49d6b-110">Veritabanındaki bir satırı güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="49d6b-110">To update a row in the database</span></span>  
  
1.  <span data-ttu-id="49d6b-111">Veritabanı güncelleştirilmesi için satırı için sorgu.</span><span class="sxs-lookup"><span data-stu-id="49d6b-111">Query the database for the row to be updated.</span></span>  
  
2.  <span data-ttu-id="49d6b-112">Üye değerlerini elde edilen istenen değişiklik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnesi.</span><span class="sxs-lookup"><span data-stu-id="49d6b-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3.  <span data-ttu-id="49d6b-113">Değişiklikler veritabanına gönderin.</span><span class="sxs-lookup"><span data-stu-id="49d6b-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49d6b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="49d6b-114">Example</span></span>  
 <span data-ttu-id="49d6b-115">Aşağıdaki örnek, sipariş #11000 veritabanını sorgular ve değerlerini değiştirir `ShipName` ve `ShipVia` elde edilen içinde `Order` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="49d6b-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="49d6b-116">Son olarak, bu üye değerlerinin değişiklikleri veritabanına değişiklikler olarak gönderilen `ShipName` ve `ShipVia` sütun.</span><span class="sxs-lookup"><span data-stu-id="49d6b-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="49d6b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49d6b-117">See Also</span></span>  
 [<span data-ttu-id="49d6b-118">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="49d6b-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="49d6b-119">Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın</span><span class="sxs-lookup"><span data-stu-id="49d6b-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="49d6b-120">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="49d6b-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
