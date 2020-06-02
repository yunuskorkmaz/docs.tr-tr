---
title: 'Nasıl yapılır: Veritabanında Satırları Güncelleştirme'
description: Tablo ile ilgili bir koleksiyondaki LINQ to SQL nesneleri değiştirerek veritabanındaki satırları güncelleştirmeyi öğrenin. LINQ to SQL, eklemeleri SQL UPDATE komutlarına çevirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286345"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="2f51a-104">Nasıl yapılır: Veritabanında Satırları Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="2f51a-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="2f51a-105">Bir veritabanındaki satırları, koleksiyonla ilişkili nesnelerin üye değerlerini değiştirerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ve sonra değişiklikleri veritabanına göndererek güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f51a-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2f51a-106">Değişikliklerinizi uygun SQL `UPDATE` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="2f51a-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="2f51a-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` .</span><span class="sxs-lookup"><span data-stu-id="2f51a-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="2f51a-108">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2f51a-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="2f51a-109">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f51a-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="2f51a-110">Aşağıdaki adımlarda, geçerli bir <xref:System.Data.Linq.DataContext> veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2f51a-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="2f51a-111">Daha fazla bilgi için bkz. [nasıl yapılır: bir veritabanına bağlanma](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="2f51a-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="2f51a-112">Veritabanındaki bir satırı güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2f51a-112">To update a row in the database</span></span>

1. <span data-ttu-id="2f51a-113">Güncelleştirileceği satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="2f51a-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="2f51a-114">Sonuç nesnesindeki üye değerlerinde istenen değişiklikleri yapın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2f51a-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="2f51a-115">Değişiklikleri veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f51a-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="2f51a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f51a-116">Example</span></span>

<span data-ttu-id="2f51a-117">Aşağıdaki örnek, #11000 sıra için veritabanını sorgular ve `ShipName` sonuç nesnesinde ve değerlerini değiştirir `ShipVia` `Order` .</span><span class="sxs-lookup"><span data-stu-id="2f51a-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="2f51a-118">Son olarak, bu üye değerlerindeki değişiklikler veritabanına ve sütunlarında değişiklik olarak veritabanına gönderilir `ShipName` `ShipVia` .</span><span class="sxs-lookup"><span data-stu-id="2f51a-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2f51a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f51a-119">See also</span></span>

- [<span data-ttu-id="2f51a-120">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="2f51a-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="2f51a-121">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="2f51a-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="2f51a-122">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="2f51a-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
