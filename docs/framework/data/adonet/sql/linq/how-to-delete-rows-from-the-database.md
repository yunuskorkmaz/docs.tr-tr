---
title: 'Nasıl yapılır: Veritabanından Satır Silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: bae67646d39ad716ed0974987ccbc76e5dd0e58a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940234"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="8547b-102">Nasıl yapılır: Veritabanından Satır Silme</span><span class="sxs-lookup"><span data-stu-id="8547b-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="8547b-103">İlgili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri tablo ile ilgili koleksiyonlarından kaldırarak veritabanındaki satırları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8547b-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8547b-104">Değişikliklerinizi uygun SQL `DELETE` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="8547b-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8547b-105">, Cascade silme işlemlerini desteklemez veya tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="8547b-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="8547b-106">Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek isterseniz, aşağıdaki görevlerden birini gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8547b-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
- <span data-ttu-id="8547b-107">`ON DELETE CASCADE` Kuralı veritabanındaki yabancı anahtar kısıtlamasından ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8547b-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
- <span data-ttu-id="8547b-108">Üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8547b-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="8547b-109">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8547b-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="8547b-110">Bu konunun ilerleyen kısımlarında ikinci kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="8547b-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8547b-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update`</span><span class="sxs-lookup"><span data-stu-id="8547b-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="8547b-112">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8547b-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="8547b-113">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8547b-113">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="8547b-114">Aşağıdaki adımlarda, geçerli <xref:System.Data.Linq.DataContext> bir veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8547b-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="8547b-115">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bağlanın.</span><span class="sxs-lookup"><span data-stu-id="8547b-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="8547b-116">Veritabanındaki bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="8547b-116">To delete a row in the database</span></span>  
  
1. <span data-ttu-id="8547b-117">Silinecek satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="8547b-117">Query the database for the row to be deleted.</span></span>  
  
2. <span data-ttu-id="8547b-118">Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8547b-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3. <span data-ttu-id="8547b-119">Değişikliği veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8547b-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8547b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="8547b-120">Example</span></span>  
 <span data-ttu-id="8547b-121">Bu ilk kod örneği, sırasıyla Order #11000 ait sipariş ayrıntıları için veritabanını sorgular, bu sıra ayrıntılarını silinmek üzere işaretler ve bu değişiklikleri veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="8547b-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="8547b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8547b-122">Example</span></span>  
 <span data-ttu-id="8547b-123">Bu ikinci örnekte, amaç bir siparişi kaldırmak (#10250).</span><span class="sxs-lookup"><span data-stu-id="8547b-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="8547b-124">Kod önce, kaldırılacak siparişin `OrderDetails` alt öğeye sahip olup olmadığını görmek için tabloyu inceler.</span><span class="sxs-lookup"><span data-stu-id="8547b-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="8547b-125">Sıralamada alt öğe varsa, önce alt öğeler ve sonra sıra kaldırma için işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="8547b-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="8547b-126">, <xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları tarafından veritabanı kısıtlamalarını veritabanına gönderilen silme komutlarının olması için gerçek silmeleri doğru sırada koyar.</span><span class="sxs-lookup"><span data-stu-id="8547b-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8547b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8547b-127">See also</span></span>

- [<span data-ttu-id="8547b-128">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="8547b-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="8547b-129">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="8547b-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="8547b-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="8547b-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
