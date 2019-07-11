---
title: 'Nasıl yapılır: Veritabanından Satır Silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 89b552d919898f78c0733c2af4507728f59a3c8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743337"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="b84d7-102">Nasıl yapılır: Veritabanından Satır Silme</span><span class="sxs-lookup"><span data-stu-id="b84d7-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="b84d7-103">Buna karşılık gelen kaldırarak bir veritabanındaki satırları silebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilgili tablo koleksiyonu nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b84d7-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b84d7-104">uygun SQL yaptığınız değişiklikleri çevirir `DELETE` komutları.</span><span class="sxs-lookup"><span data-stu-id="b84d7-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b84d7-105">desteklemez veya art arda silme işlemleri tanıyın.</span><span class="sxs-lookup"><span data-stu-id="b84d7-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="b84d7-106">Bunu yönelik kısıtlamalar içeren bir tabloda bir satır silmek istiyorsanız, aşağıdaki görevlerden birini tamamlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b84d7-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
- <span data-ttu-id="b84d7-107">Ayarlama `ON DELETE CASCADE` veritabanında yabancı anahtar kısıtlaması kuralı.</span><span class="sxs-lookup"><span data-stu-id="b84d7-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
- <span data-ttu-id="b84d7-108">Kendi kodunuzu ilk üst nesnenin silinmesini engelleyen alt nesneleri silmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b84d7-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="b84d7-109">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b84d7-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="b84d7-110">İkinci kod örneğinde bu konunun ilerleyen bölümlerinde bkz.</span><span class="sxs-lookup"><span data-stu-id="b84d7-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b84d7-111">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı.</span><span class="sxs-lookup"><span data-stu-id="b84d7-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="b84d7-112">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b84d7-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="b84d7-113">Visual Studio kullanan geliştiricilerin, Nesne İlişkisel Tasarımcısı, aynı amaçla saklı yordamlar geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84d7-113">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="b84d7-114">Aşağıdaki adımlardan istediğinizi düşünelim. geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="b84d7-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="b84d7-115">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına bağlanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="b84d7-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="b84d7-116">Veritabanı bir satırı silin</span><span class="sxs-lookup"><span data-stu-id="b84d7-116">To delete a row in the database</span></span>  
  
1. <span data-ttu-id="b84d7-117">Silinecek satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="b84d7-117">Query the database for the row to be deleted.</span></span>  
  
2. <span data-ttu-id="b84d7-118">Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b84d7-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3. <span data-ttu-id="b84d7-119">Veritabanı için değişiklik gönderin.</span><span class="sxs-lookup"><span data-stu-id="b84d7-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b84d7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b84d7-120">Example</span></span>  
 <span data-ttu-id="b84d7-121">Bu ilk kod örneği veritabanı için sipariş #11000 ait, bu Sipariş Ayrıntıları silme işlemi için işaretler ve bu değişiklikleri veritabanına gönderdiğinde sipariş ayrıntıları için sorgular.</span><span class="sxs-lookup"><span data-stu-id="b84d7-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b84d7-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b84d7-122">Example</span></span>  
 <span data-ttu-id="b84d7-123">Bu ikinci örnekte hedefi bir sipariş (#10250) kaldırılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b84d7-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="b84d7-124">İlk olarak kodu inceler `OrderDetails` sırasını kaldırılacak şekilde alt öğeleri var olup olmadığını görmek için tabloyu.</span><span class="sxs-lookup"><span data-stu-id="b84d7-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="b84d7-125">Sipariş alt öğeleri, ilk alt ve sırasını kaldırılmak üzere işaretlenir varsa.</span><span class="sxs-lookup"><span data-stu-id="b84d7-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="b84d7-126"><xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları silme komutlarını veritabanına gönderilen uymayı doğru sırada gerçek siler geçirir.</span><span class="sxs-lookup"><span data-stu-id="b84d7-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b84d7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b84d7-127">See also</span></span>

- [<span data-ttu-id="b84d7-128">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="b84d7-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="b84d7-129">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="b84d7-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="b84d7-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="b84d7-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
