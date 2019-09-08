---
title: Veri Değişiklikleri Yapma ve Gönderme
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792968"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="0d17c-102">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="0d17c-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="0d17c-103">Bu bölümdeki konular, veritabanında yapılan değişikliklerin nasıl yapılacağını ve iletileceğinizi ve iyimser eşzamanlılık çakışmalarını nasıl ele alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d17c-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="0d17c-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update`</span><span class="sxs-lookup"><span data-stu-id="0d17c-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="0d17c-105">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0d17c-105">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="0d17c-106">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d17c-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0d17c-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0d17c-107">In This Section</span></span>

<span data-ttu-id="0d17c-108">[Nasıl yapılır: Veritabanına satır ekleme](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-108">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="0d17c-109">Nesne modeline nesneler ekleyerek veritabanına nasıl satır ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="0d17c-110">[Nasıl yapılır: Veritabanındaki satırları güncelleştir](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-110">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="0d17c-111">Nesne modelindeki nesneleri güncelleştirerek veritabanındaki satırların nasıl güncelleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="0d17c-112">[Nasıl yapılır: Veritabanından satırları sil](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-112">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="0d17c-113">Nesne modelindeki nesneleri silerek veritabanındaki satırların nasıl silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="0d17c-114">[Nasıl yapılır: Değişiklikleri veritabanına gönder](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-114">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="0d17c-115">Veritabanına nesne modeli değişikliklerinin nasıl gönderileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="0d17c-116">[Nasıl yapılır: Işlemleri kullanarak köşeli ayraç veri gönderimleri](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-116">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="0d17c-117">İşlemlere işlem eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="0d17c-118">[Nasıl yapılır: Dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-118">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="0d17c-119">Bu yaklaşım için dinamik olarak veritabanlarının ve tipik senaryoların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="0d17c-120">[Nasıl yapılır: Değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="0d17c-120">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="0d17c-121">İyimser eşzamanlılık sorunlarını gidermeye yönelik teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d17c-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
