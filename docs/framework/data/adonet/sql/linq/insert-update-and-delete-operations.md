---
description: 'Daha fazla bilgi edinin: ekleme, güncelleştirme ve silme Işlemleri'
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 2d0470ed6abe654ca08f954c3de97de207adb75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803825"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="80b9d-103">Insert, Update ve Delete İşlemleri</span><span class="sxs-lookup"><span data-stu-id="80b9d-103">Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="80b9d-104">`Insert` `Update` `Delete` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nesne modelinize nesneleri ekleyerek, değiştirerek ve kaldırarak işlemleri gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b9d-104">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="80b9d-105">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] EYLEMLERINIZI SQL 'e çevirir ve değişiklikleri veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="80b9d-105">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80b9d-106">, nesneleriniz üzerinde yaptığınız işleme ve kalıcı değişiklikler için en yüksek esnekliği sunar.</span><span class="sxs-lookup"><span data-stu-id="80b9d-106">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="80b9d-107">Varlık nesneleri kullanılabilir duruma geldiğinde (bir sorgu aracılığıyla ya da onları bir sorgu aracılığıyla alarak), bunları uygulamanızda tipik nesneler olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b9d-107">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="80b9d-108">Diğer bir deyişle, değerlerini değiştirebilir, koleksiyonlarınıza ekleyebilirsiniz ve bunları Koleksiyonlarınızdan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b9d-108">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80b9d-109">değişikliklerinizi izler ve çağırdığınızda veritabanına geri aktarılmaya hazırlanın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="80b9d-109">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80b9d-110">, Cascade silme işlemlerini desteklemez veya tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="80b9d-110">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="80b9d-111">Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek istiyorsanız, `ON DELETE CASCADE` kuralı veritabanındaki yabancı anahtar kısıtlamasında ayarlamanız veya üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b9d-111">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="80b9d-112">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80b9d-112">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="80b9d-113">Daha fazla bilgi için bkz. [nasıl yapılır: veritabanından satırları silme](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="80b9d-113">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>

<span data-ttu-id="80b9d-114">Aşağıdaki alıntıları, `Customer` `Order` Northwind örnek veritabanındaki ve sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="80b9d-114">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="80b9d-115">Sınıf tanımları breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="80b9d-115">Class definitions are not shown for brevity.</span></span>

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

<span data-ttu-id="80b9d-116"><xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliklerinizi veritabanına geri aktarmak için sahip olması gereken SQL komutlarını otomatik olarak oluşturur ve yürütür.</span><span class="sxs-lookup"><span data-stu-id="80b9d-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>

> [!NOTE]
> <span data-ttu-id="80b9d-117">Bu davranışı, genellikle saklı bir yordamın yoluyla kendi özel mantığınızı kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b9d-117">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="80b9d-118">Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](responsibilities-of-the-developer-in-overriding-default-behavior.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="80b9d-118">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>
>
> <span data-ttu-id="80b9d-119">Visual Studio kullanan geliştiriciler, bu amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="80b9d-119">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for this purpose.</span></span>

## <a name="see-also"></a><span data-ttu-id="80b9d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80b9d-120">See also</span></span>

- [<span data-ttu-id="80b9d-121">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="80b9d-121">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="80b9d-122">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="80b9d-122">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
