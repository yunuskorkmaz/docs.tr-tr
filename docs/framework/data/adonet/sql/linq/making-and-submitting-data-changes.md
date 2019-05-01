---
title: Veri Değişiklikleri Yapma ve Gönderme
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: c9d319727a750fbd3e2a186c28e79b20200c6bd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903350"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="e4a9a-102">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="e4a9a-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="e4a9a-103">Bu bölümdeki konular, sağlamak ve değişiklikleri veritabanına aktarmak ve iyimser eşzamanlılık çakışmalarını nasıl ele alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4a9a-104">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="e4a9a-105">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9a-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="e4a9a-106">Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar için aynı amaca geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-106">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4a9a-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e4a9a-107">In This Section</span></span>  
 [<span data-ttu-id="e4a9a-108">Nasıl yapılır: Satır veritabanına Ekle</span><span class="sxs-lookup"><span data-stu-id="e4a9a-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="e4a9a-109">Nesneleri için nesne modeli ekleyerek veritabanında satır eklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="e4a9a-110">Nasıl yapılır: Veritabanındaki satırları güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e4a9a-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="e4a9a-111">Nesne modelinde güncelleştirerek veritabanındaki satırları güncelleştirme işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="e4a9a-112">Nasıl yapılır: Veritabanından satır silme</span><span class="sxs-lookup"><span data-stu-id="e4a9a-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="e4a9a-113">Nesne modelinde silerek veritabanındaki satırları silmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="e4a9a-114">Nasıl yapılır: Veritabanına değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="e4a9a-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="e4a9a-115">Nesne modeli veritabanına değişiklikleri gönderme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="e4a9a-116">Nasıl yapılır: İşlemleri kullanarak veri gönderimlerini köşeli ayraç</span><span class="sxs-lookup"><span data-stu-id="e4a9a-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="e4a9a-117">Bir işlemde işlemleri eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="e4a9a-118">Nasıl yapılır: Dinamik olarak veritabanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4a9a-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="e4a9a-119">Veritabanlarını dinamik olarak oluşturma ve bu yaklaşım için tipik senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="e4a9a-120">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="e4a9a-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="e4a9a-121">İyimser eşzamanlılık sorunları çözmeye yönelik teknikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e4a9a-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
