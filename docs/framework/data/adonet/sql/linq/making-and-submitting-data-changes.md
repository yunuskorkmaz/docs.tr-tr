---
description: 'Hakkında daha fazla bilgi edinin: veri değişiklikleri oluşturma ve gönderme'
title: Veri Değişiklikleri Yapma ve Gönderme
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 260dab911057b45250d44ded7c254dd903e2aed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695581"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="c78b1-103">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="c78b1-103">Making and Submitting Data Changes</span></span>

<span data-ttu-id="c78b1-104">Bu bölümdeki konular, veritabanında yapılan değişikliklerin nasıl yapılacağını ve iletileceğinizi ve iyimser eşzamanlılık çakışmalarını nasıl ele alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c78b1-104">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="c78b1-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` .</span><span class="sxs-lookup"><span data-stu-id="c78b1-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="c78b1-106">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c78b1-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="c78b1-107">Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c78b1-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c78b1-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c78b1-108">In This Section</span></span>

<span data-ttu-id="c78b1-109">[Nasıl yapılır: veritabanına satır ekleme](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-109">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="c78b1-110">Nesne modeline nesneler ekleyerek veritabanına nasıl satır ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-110">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="c78b1-111">[Nasıl yapılır: veritabanındaki satırları güncelleştirme](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-111">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="c78b1-112">Nesne modelindeki nesneleri güncelleştirerek veritabanındaki satırların nasıl güncelleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-112">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="c78b1-113">[Nasıl yapılır: veritabanından satırları silme](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-113">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="c78b1-114">Nesne modelindeki nesneleri silerek veritabanındaki satırların nasıl silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-114">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="c78b1-115">[Nasıl yapılır: değişiklikleri veritabanına gönderme](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-115">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="c78b1-116">Veritabanına nesne modeli değişikliklerinin nasıl gönderileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-116">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="c78b1-117">[Nasıl yapılır: Işlemleri kullanarak veri gönderilerini ayraç içine alma](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-117">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="c78b1-118">İşlemlere işlem eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-118">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="c78b1-119">[Nasıl yapılır: dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-119">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="c78b1-120">Bu yaklaşım için dinamik olarak veritabanlarının ve tipik senaryoların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-120">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="c78b1-121">[Nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="c78b1-121">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="c78b1-122">İyimser eşzamanlılık sorunlarını gidermeye yönelik teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c78b1-122">Describes techniques for addressing optimistic concurrency issues.</span></span>
