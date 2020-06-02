---
title: 'Nasıl yapılır: Veritabanından Satır Silme'
description: Tablo ile ilgili bir koleksiyondan LINQ to SQL nesneleri kaldırarak veritabanındaki satırları silmeyi öğrenin. LINQ to SQL, silme işlemlerini SQL DELETE komutlarına çevirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286397"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="13001-104">Nasıl yapılır: Veritabanından Satır Silme</span><span class="sxs-lookup"><span data-stu-id="13001-104">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="13001-105">İlgili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri tablo ile ilgili koleksiyonlarından kaldırarak veritabanındaki satırları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13001-105">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="13001-106">Değişikliklerinizi uygun SQL `DELETE` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="13001-106">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="13001-107">, Cascade silme işlemlerini desteklemez veya tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="13001-107">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="13001-108">Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek isterseniz, aşağıdaki görevlerden birini gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="13001-108">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="13001-109">`ON DELETE CASCADE`Kuralı veritabanındaki yabancı anahtar kısıtlamasından ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="13001-109">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="13001-110">Üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanın.</span><span class="sxs-lookup"><span data-stu-id="13001-110">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="13001-111">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="13001-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="13001-112">Bu konunun ilerleyen kısımlarında ikinci kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="13001-112">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="13001-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` .</span><span class="sxs-lookup"><span data-stu-id="13001-113">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="13001-114">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="13001-114">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="13001-115">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="13001-115">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="13001-116">Aşağıdaki adımlarda, geçerli bir <xref:System.Data.Linq.DataContext> veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="13001-116">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="13001-117">Daha fazla bilgi için bkz. [nasıl yapılır: bir veritabanına bağlanma](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="13001-117">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="13001-118">Veritabanındaki bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="13001-118">To delete a row in the database</span></span>

1. <span data-ttu-id="13001-119">Silinecek satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="13001-119">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="13001-120">Yöntemini çağırın <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> .</span><span class="sxs-lookup"><span data-stu-id="13001-120">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="13001-121">Değişikliği veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13001-121">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="13001-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="13001-122">Example</span></span>

<span data-ttu-id="13001-123">Bu ilk kod örneği, sırasıyla Order #11000 ait sipariş ayrıntıları için veritabanını sorgular, bu sıra ayrıntılarını silinmek üzere işaretler ve bu değişiklikleri veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="13001-123">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="13001-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="13001-124">Example</span></span>

<span data-ttu-id="13001-125">Bu ikinci örnekte, amaç bir siparişi kaldırmak (#10250).</span><span class="sxs-lookup"><span data-stu-id="13001-125">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="13001-126">Kod önce, `OrderDetails` kaldırılacak siparişin alt öğeye sahip olup olmadığını görmek için tabloyu inceler.</span><span class="sxs-lookup"><span data-stu-id="13001-126">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="13001-127">Sıralamada alt öğe varsa, önce alt öğeler ve sonra sıra kaldırma için işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="13001-127">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="13001-128">, <xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları tarafından veritabanı kısıtlamalarını veritabanına gönderilen silme komutlarının olması için gerçek silmeleri doğru sırada koyar.</span><span class="sxs-lookup"><span data-stu-id="13001-128">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="13001-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13001-129">See also</span></span>

- [<span data-ttu-id="13001-130">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="13001-130">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="13001-131">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="13001-131">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="13001-132">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="13001-132">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
