---
title: 'Nasıl yapılır: Veritabanına Satır Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 3e365f0c12b2c1c6ddfa91c96ad5769b63c9e25e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043598"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="a2008-102">Nasıl yapılır: Veritabanına Satır Ekleme</span><span class="sxs-lookup"><span data-stu-id="a2008-102">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="a2008-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İlişkili<xref:System.Data.Linq.Table%601> koleksiyona nesneler ekleyerek ve sonra değişiklikleri veritabanına göndererek bir veritabanına satır eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="a2008-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a2008-104">Değişikliklerinizi uygun SQL `INSERT` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="a2008-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="a2008-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update`</span><span class="sxs-lookup"><span data-stu-id="a2008-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="a2008-106">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a2008-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="a2008-107">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a2008-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="a2008-108">Aşağıdaki adımlarda, geçerli <xref:System.Data.Linq.DataContext> bir veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a2008-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="a2008-109">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bağlanın.</span><span class="sxs-lookup"><span data-stu-id="a2008-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="a2008-110">Veritabanına bir satır eklemek için</span><span class="sxs-lookup"><span data-stu-id="a2008-110">To insert a row into the database</span></span>

1. <span data-ttu-id="a2008-111">Gönderilecek sütun verilerini içeren yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2008-111">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="a2008-112">Yeni nesneyi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanındaki hedef tabloyla ilişkili koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2008-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="a2008-113">Değişikliği veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2008-113">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="a2008-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2008-114">Example</span></span>

<span data-ttu-id="a2008-115">Aşağıdaki kod örneği, türünde `Order` yeni bir nesne oluşturur ve uygun değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="a2008-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="a2008-116">Daha sonra yeni nesneyi `Order` koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="a2008-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="a2008-117">Son olarak, değişikliği veritabanına `Orders` tabloya yeni bir satır olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="a2008-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="a2008-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2008-118">See also</span></span>

- [<span data-ttu-id="a2008-119">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="a2008-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="a2008-120">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="a2008-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="a2008-121">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="a2008-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="a2008-122">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="a2008-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
