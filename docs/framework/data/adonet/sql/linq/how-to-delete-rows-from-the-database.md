---
title: 'Nasıl yapılır: veritabanından satırları silme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f84531be8bc8ae57db895959513fdc7dd4a8d154
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="fe872-102">Nasıl yapılır: veritabanından satırları silme</span><span class="sxs-lookup"><span data-stu-id="fe872-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="fe872-103">Karşılık gelen kaldırarak bir veritabanında satır silebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendi tablo ilişkili koleksiyon nesneleri.</span><span class="sxs-lookup"><span data-stu-id="fe872-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="fe872-104"> Değişikliklerinizi uygun SQL çevirir `DELETE` komutları.</span><span class="sxs-lookup"><span data-stu-id="fe872-104"> translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="fe872-105"> desteklemez veya art arda silme işlemleri algılar.</span><span class="sxs-lookup"><span data-stu-id="fe872-105"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="fe872-106">Bu karşı kısıtlamalarına sahip bir tablosunda bir satırı silmek istiyorsanız, aşağıdaki görevlerin birini tamamlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fe872-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
-   <span data-ttu-id="fe872-107">Ayarlama `ON DELETE CASCADE` veritabanındaki yabancı anahtar kısıtlaması kuralında.</span><span class="sxs-lookup"><span data-stu-id="fe872-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
-   <span data-ttu-id="fe872-108">İlk olarak üst nesneyi silinmesini engellemek bağımlı nesneleri Sil için kendi kodunuzu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe872-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="fe872-109">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe872-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="fe872-110">Bu konunun ilerleyen bölümlerinde ikinci kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="fe872-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe872-111">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="fe872-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="fe872-112">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fe872-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="fe872-113">Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="fe872-113">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="fe872-114">Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="fe872-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="fe872-115">Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="fe872-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="fe872-116">Veritabanındaki bir satır silmek için</span><span class="sxs-lookup"><span data-stu-id="fe872-116">To delete a row in the database</span></span>  
  
1.  <span data-ttu-id="fe872-117">Satırın silinmesi için veritabanını sorgula.</span><span class="sxs-lookup"><span data-stu-id="fe872-117">Query the database for the row to be deleted.</span></span>  
  
2.  <span data-ttu-id="fe872-118">Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe872-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3.  <span data-ttu-id="fe872-119">Veritabanı için değişiklik gönderin.</span><span class="sxs-lookup"><span data-stu-id="fe872-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe872-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe872-120">Example</span></span>  
 <span data-ttu-id="fe872-121">Bu ilk kod örneği veritabanı sipariş #11000 ait, bu sipariş ayrıntılarını silme işlemi için işaretler ve bu değişiklikler veritabanına gönderdiğinde sipariş ayrıntıları için sorgular.</span><span class="sxs-lookup"><span data-stu-id="fe872-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="fe872-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe872-122">Example</span></span>  
 <span data-ttu-id="fe872-123">Bu ikinci örnekte hedefi (#10250) sipariş kaldırmaktır.</span><span class="sxs-lookup"><span data-stu-id="fe872-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="fe872-124">Kod ilk inceler `OrderDetails` kaldırılacak sırasını alt var olup olmadığını görmek için tablo.</span><span class="sxs-lookup"><span data-stu-id="fe872-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="fe872-125">Sipariş alt öğe, alt ve sırası kaldırılmak üzere işaretlenmiş ilk varsa.</span><span class="sxs-lookup"><span data-stu-id="fe872-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="fe872-126"><xref:System.Data.Linq.DataContext> Veritabanına gönderilen silme komutları veritabanı kısıtlamalar tarafından uymanız doğru sırayla gerçek siler geçirir.</span><span class="sxs-lookup"><span data-stu-id="fe872-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fe872-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe872-127">See Also</span></span>  
 [<span data-ttu-id="fe872-128">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="fe872-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="fe872-129">Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın</span><span class="sxs-lookup"><span data-stu-id="fe872-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="fe872-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="fe872-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
