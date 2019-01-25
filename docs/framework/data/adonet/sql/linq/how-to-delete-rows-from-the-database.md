---
title: 'Nasıl yapılır: Veritabanından satır silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 598828f7750fe02082dfccacc64102f96588cb3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554315"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="75975-102">Nasıl yapılır: Veritabanından satır silme</span><span class="sxs-lookup"><span data-stu-id="75975-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="75975-103">Buna karşılık gelen kaldırarak bir veritabanındaki satırları silebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilgili tablo koleksiyonu nesneleri.</span><span class="sxs-lookup"><span data-stu-id="75975-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="75975-104">uygun SQL yaptığınız değişiklikleri çevirir `DELETE` komutları.</span><span class="sxs-lookup"><span data-stu-id="75975-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="75975-105">desteklemez veya art arda silme işlemleri tanıyın.</span><span class="sxs-lookup"><span data-stu-id="75975-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="75975-106">Bunu yönelik kısıtlamalar içeren bir tabloda bir satır silmek istiyorsanız, aşağıdaki görevlerden birini tamamlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="75975-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
-   <span data-ttu-id="75975-107">Ayarlama `ON DELETE CASCADE` veritabanında yabancı anahtar kısıtlaması kuralı.</span><span class="sxs-lookup"><span data-stu-id="75975-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
-   <span data-ttu-id="75975-108">Kendi kodunuzu ilk üst nesnenin silinmesini engelleyen alt nesneleri silmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="75975-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="75975-109">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="75975-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="75975-110">İkinci kod örneğinde bu konunun ilerleyen bölümlerinde bkz.</span><span class="sxs-lookup"><span data-stu-id="75975-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75975-111">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı.</span><span class="sxs-lookup"><span data-stu-id="75975-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="75975-112">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="75975-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="75975-113">Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar için aynı amaca geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="75975-113">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="75975-114">Aşağıdaki adımlardan istediğinizi düşünelim. geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="75975-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="75975-115">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına bağlanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="75975-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="75975-116">Veritabanı bir satırı silin</span><span class="sxs-lookup"><span data-stu-id="75975-116">To delete a row in the database</span></span>  
  
1.  <span data-ttu-id="75975-117">Silinecek satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="75975-117">Query the database for the row to be deleted.</span></span>  
  
2.  <span data-ttu-id="75975-118">Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75975-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3.  <span data-ttu-id="75975-119">Veritabanı için değişiklik gönderin.</span><span class="sxs-lookup"><span data-stu-id="75975-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75975-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="75975-120">Example</span></span>  
 <span data-ttu-id="75975-121">Bu ilk kod örneği veritabanı için sipariş #11000 ait, bu Sipariş Ayrıntıları silme işlemi için işaretler ve bu değişiklikleri veritabanına gönderdiğinde sipariş ayrıntıları için sorgular.</span><span class="sxs-lookup"><span data-stu-id="75975-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="75975-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="75975-122">Example</span></span>  
 <span data-ttu-id="75975-123">Bu ikinci örnekte hedefi bir sipariş (#10250) kaldırılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="75975-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="75975-124">İlk olarak kodu inceler `OrderDetails` sırasını kaldırılacak şekilde alt öğeleri var olup olmadığını görmek için tabloyu.</span><span class="sxs-lookup"><span data-stu-id="75975-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="75975-125">Sipariş alt öğeleri, ilk alt ve sırasını kaldırılmak üzere işaretlenir varsa.</span><span class="sxs-lookup"><span data-stu-id="75975-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="75975-126"><xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları silme komutlarını veritabanına gönderilen uymayı doğru sırada gerçek siler geçirir.</span><span class="sxs-lookup"><span data-stu-id="75975-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="75975-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75975-127">See also</span></span>
- [<span data-ttu-id="75975-128">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="75975-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="75975-129">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="75975-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="75975-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="75975-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
