---
title: 'Nasıl yapılır: Veritabanına Satır Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cb62522a951afd3a7159114d3b6575f1d83278bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743324"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="9af2c-102">Nasıl yapılır: Veritabanına Satır Ekleme</span><span class="sxs-lookup"><span data-stu-id="9af2c-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="9af2c-103">İlişkili nesneleri ekleyerek bir veritabanına satır ekleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> koleksiyonu ve ardından veritabanına değişiklikleri gönderme.</span><span class="sxs-lookup"><span data-stu-id="9af2c-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9af2c-104">uygun SQL değişikliklerinizi çevirir `INSERT` komutları.</span><span class="sxs-lookup"><span data-stu-id="9af2c-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9af2c-105">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı.</span><span class="sxs-lookup"><span data-stu-id="9af2c-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9af2c-106">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9af2c-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="9af2c-107">Visual Studio kullanan geliştiricilerin, Nesne İlişkisel Tasarımcısı, aynı amaçla saklı yordamlar geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9af2c-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="9af2c-108">Aşağıdaki adımlardan istediğinizi düşünelim. geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="9af2c-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="9af2c-109">Daha fazla bilgi için [nasıl yapılır: Bir veritabanına bağlanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="9af2c-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="9af2c-110">Veritabanına bir satır eklemek için</span><span class="sxs-lookup"><span data-stu-id="9af2c-110">To insert a row into the database</span></span>  
  
1. <span data-ttu-id="9af2c-111">Gönderilecek sütun verileri içeren yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9af2c-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2. <span data-ttu-id="9af2c-112">Eklemek istediğiniz yeni nesneye [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanında hedef tabloyla ilişkili koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3. <span data-ttu-id="9af2c-113">Veritabanı için değişiklik gönderin.</span><span class="sxs-lookup"><span data-stu-id="9af2c-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9af2c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9af2c-114">Example</span></span>  
 <span data-ttu-id="9af2c-115">Aşağıdaki kod örneği, türü yeni bir nesne oluşturur `Order` ve uygun değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="9af2c-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="9af2c-116">Ardından yeni nesneye ekler `Order` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="9af2c-117">Son olarak, yeni bir satır olarak değişiklik veritabanına gönderdiğinde `Orders` tablo.</span><span class="sxs-lookup"><span data-stu-id="9af2c-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9af2c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9af2c-118">See also</span></span>

- [<span data-ttu-id="9af2c-119">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="9af2c-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="9af2c-120">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="9af2c-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="9af2c-121">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="9af2c-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="9af2c-122">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="9af2c-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
