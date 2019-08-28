---
title: Veri Değişiklikleri Yapma ve Gönderme
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 699a8730f21ff290ad15d1932f565ab7a2478fb5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043984"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="8c811-102">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="8c811-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="8c811-103">Bu bölümdeki konular, veritabanında yapılan değişikliklerin nasıl yapılacağını ve iletileceğinizi ve iyimser eşzamanlılık çakışmalarını nasıl ele alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c811-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="8c811-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update`</span><span class="sxs-lookup"><span data-stu-id="8c811-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="8c811-105">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8c811-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="8c811-106">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8c811-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8c811-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8c811-107">In This Section</span></span>

<span data-ttu-id="8c811-108">[Nasıl yapılır: Veritabanına satır ekleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-108">[How to: Insert Rows Into the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="8c811-109">Nesne modeline nesneler ekleyerek veritabanına nasıl satır ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="8c811-110">[Nasıl yapılır: Veritabanındaki satırları güncelleştir](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-110">[How to: Update Rows in the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="8c811-111">Nesne modelindeki nesneleri güncelleştirerek veritabanındaki satırların nasıl güncelleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="8c811-112">[Nasıl yapılır: Veritabanından satırları sil](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-112">[How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="8c811-113">Nesne modelindeki nesneleri silerek veritabanındaki satırların nasıl silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="8c811-114">[Nasıl yapılır: Değişiklikleri veritabanına gönder](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-114">[How to: Submit Changes to the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="8c811-115">Veritabanına nesne modeli değişikliklerinin nasıl gönderileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="8c811-116">[Nasıl yapılır: Işlemleri kullanarak köşeli ayraç veri gönderimleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-116">[How to: Bracket Data Submissions by Using Transactions](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="8c811-117">İşlemlere işlem eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="8c811-118">[Nasıl yapılır: Dinamik olarak veritabanı oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-118">[How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="8c811-119">Bu yaklaşım için dinamik olarak veritabanlarının ve tipik senaryoların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="8c811-120">[Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="8c811-120">[How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="8c811-121">İyimser eşzamanlılık sorunlarını gidermeye yönelik teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c811-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
