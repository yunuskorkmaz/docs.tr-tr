---
title: 'Nasıl yapılır: Veritabanında Satırları Güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: bf4c50bba4b4bc2bf6b7b1c2b79426566c874dd4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043568"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="55fed-102">Nasıl yapılır: Veritabanında Satırları Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="55fed-102">How to: Update Rows in the Database</span></span>

<span data-ttu-id="55fed-103">Bir veritabanındaki satırları, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> koleksiyonla ilişkili nesnelerin üye değerlerini değiştirerek ve sonra değişiklikleri veritabanına göndererek güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55fed-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="55fed-104">Değişikliklerinizi uygun SQL `UPDATE` komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="55fed-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="55fed-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update`</span><span class="sxs-lookup"><span data-stu-id="55fed-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="55fed-106">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="55fed-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="55fed-107">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="55fed-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="55fed-108">Aşağıdaki adımlarda, geçerli <xref:System.Data.Linq.DataContext> bir veritabanının Northwind veritabanına bağladığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="55fed-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="55fed-109">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bağlanın.</span><span class="sxs-lookup"><span data-stu-id="55fed-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="55fed-110">Veritabanındaki bir satırı güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="55fed-110">To update a row in the database</span></span>

1. <span data-ttu-id="55fed-111">Güncelleştirileceği satırın veritabanını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="55fed-111">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="55fed-112">Sonuç [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnesindeki üye değerlerinde istenen değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="55fed-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="55fed-113">Değişiklikleri veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55fed-113">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="55fed-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="55fed-114">Example</span></span>

<span data-ttu-id="55fed-115">Aşağıdaki örnek, #11000 sıra için veritabanını sorgular ve sonuç `ShipName` `Order` nesnesinde ve `ShipVia` değerlerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="55fed-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="55fed-116">Son olarak, bu üye değerlerindeki değişiklikler veritabanına `ShipName` ve `ShipVia` sütunlarında değişiklik olarak veritabanına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="55fed-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="55fed-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55fed-117">See also</span></span>

- [<span data-ttu-id="55fed-118">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="55fed-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="55fed-119">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="55fed-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="55fed-120">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="55fed-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
