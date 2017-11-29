---
title: "INSERT, Update ve silme işlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adbe7faa50b06c330b942b451d5a4a0bd832cde3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="f3814-102">INSERT, Update ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="f3814-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="f3814-103">Gerçekleştirdiğiniz `Insert`, `Update`, ve `Delete` işlemlerinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleyerek, değiştirerek ve nesne modelinde nesneleri kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="f3814-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="f3814-104">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eylemlerinizi SQL dönüşür ve değişiklikler veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="f3814-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f3814-105">düzenleme ve, nesnelere yapılan değişiklikleri devam ettirmeden en büyük esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3814-105"> offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="f3814-106">Varlık nesnesi (veya bunları bir sorgu aracılığıyla alarak mı başlatacağı oluşturma tarafından) kullanılabilir duruma geldiğinde, bunları uygulamanızda gibi tipik nesneleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3814-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="f3814-107">Diğer bir deyişle, kendi değerlerini değiştirebilirsiniz, Koleksiyonlarınız için ekleyebilirsiniz ve, koleksiyonları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3814-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f3814-108">yaptığınız değişiklikleri izler ve çağırdığınızda bunları veritabanına aktarmak hazır <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3814-108"> tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f3814-109">desteklemez veya art arda silme işlemleri algılar.</span><span class="sxs-lookup"><span data-stu-id="f3814-109"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="f3814-110">Bu karşı kısıtlamalarına sahip bir tablosunda bir satırı silmek istiyorsanız, ayarlayın ya da gerekir `ON DELETE CASCADE` kural veritabanındaki yabancı anahtar kısıtlaması içinde ya da kendi kodunuzu ilk üst nesne silinmesini engellemek alt nesneleri silmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3814-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="f3814-111">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f3814-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="f3814-112">Daha fazla bilgi için bkz: [nasıl yapılır: Sil satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="f3814-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="f3814-113">Aşağıdaki parçalarını kullanım `Customer` ve `Order` Northwind örnek veritabanı sınıflardan.</span><span class="sxs-lookup"><span data-stu-id="f3814-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="f3814-114">Sınıf tanımları okumanızdır gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="f3814-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="f3814-115">Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] otomatik olarak oluşturur ve değişikliklerinizi veritabanına aktarmak için gereken SQL komutlarını yürütür.</span><span class="sxs-lookup"><span data-stu-id="f3814-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3814-116">Saklı yordam yapmamanız genellikle kendi özel mantık kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3814-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="f3814-117">Daha fazla bilgi için bkz: [Geliştirici içinde geçersiz kılma varsayılan davranışı sorumluluklarını](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="f3814-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="f3814-118">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="f3814-118">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3814-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3814-119">See Also</span></span>  
 [<span data-ttu-id="f3814-120">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="f3814-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="f3814-121">Özelleştirme ekleme, güncelleştirme ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="f3814-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
