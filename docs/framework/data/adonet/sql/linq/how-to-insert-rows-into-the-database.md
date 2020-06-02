---
title: 'Nasıl yapılır: Veritabanına Satır Ekleme'
description: Tablo ile ilgili bir koleksiyona LINQ to SQL nesneleri ekleyerek veritabanına satır eklemeyi öğrenin. LINQ to SQL, eklemeleri SQL INSERT komutlarına çevirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286358"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="5e580-104">Nasıl yapılır: Veritabanına Satır Ekleme</span><span class="sxs-lookup"><span data-stu-id="5e580-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="5e580-105">İlişkili koleksiyona nesneler ekleyerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ve sonra değişiklikleri veritabanına göndererek bir veritabanına satır eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="5e580-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5e580-106">Değişikliklerinizi uygun SQL `INSERT` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="5e580-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="5e580-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` .</span><span class="sxs-lookup"><span data-stu-id="5e580-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="5e580-108">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5e580-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="5e580-109">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e580-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="5e580-110">Aşağıdaki adımlarda, geçerli bir <xref:System.Data.Linq.DataContext> veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5e580-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="5e580-111">Daha fazla bilgi için bkz. [nasıl yapılır: bir veritabanına bağlanma](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="5e580-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="5e580-112">Veritabanına bir satır eklemek için</span><span class="sxs-lookup"><span data-stu-id="5e580-112">To insert a row into the database</span></span>

1. <span data-ttu-id="5e580-113">Gönderilecek sütun verilerini içeren yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e580-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="5e580-114">Yeni nesneyi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanındaki hedef tabloyla ilişkili koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e580-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="5e580-115">Değişikliği veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e580-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="5e580-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e580-116">Example</span></span>

<span data-ttu-id="5e580-117">Aşağıdaki kod örneği, türünde yeni bir nesne oluşturur `Order` ve uygun değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="5e580-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="5e580-118">Daha sonra yeni nesneyi `Order` koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="5e580-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="5e580-119">Son olarak, değişikliği veritabanına tabloya yeni bir satır olarak gönderir `Orders` .</span><span class="sxs-lookup"><span data-stu-id="5e580-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="5e580-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e580-120">See also</span></span>

- [<span data-ttu-id="5e580-121">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="5e580-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="5e580-122">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="5e580-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="5e580-123">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="5e580-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="5e580-124">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="5e580-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
