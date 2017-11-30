---
title: "Sağlama ve veri değişiklikleri gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb52916e8e0948725a2eeb15cf78410077c7dca1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="b6e08-102">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="b6e08-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="b6e08-103">Bu bölümdeki konular, yapmak ve değişiklikleri veritabanına aktarmak nasıl ve iyimser eşzamanlılık çakışmaları nasıl ele alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6e08-104">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="b6e08-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="b6e08-105">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b6e08-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="b6e08-106">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="b6e08-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6e08-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b6e08-107">In This Section</span></span>  
 [<span data-ttu-id="b6e08-108">Nasıl yapılır: veritabanına Satır Ekle</span><span class="sxs-lookup"><span data-stu-id="b6e08-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="b6e08-109">Nesne modeli nesneleri ekleyerek veritabanında satır eklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="b6e08-110">Nasıl yapılır: veritabanındaki satırları güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="b6e08-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="b6e08-111">Nesne modelinde güncelleştirerek veritabanındaki satırları güncelleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="b6e08-112">Nasıl yapılır: veritabanından satırları silme</span><span class="sxs-lookup"><span data-stu-id="b6e08-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="b6e08-113">Nesne modelinde silerek veritabanında satır silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="b6e08-114">Nasıl yapılır: Veritabanı değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="b6e08-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="b6e08-115">Veritabanı için nesne modeli değişikliklerini göndermeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="b6e08-116">Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç</span><span class="sxs-lookup"><span data-stu-id="b6e08-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="b6e08-117">Bir işlem içinde işlemleri içeren açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="b6e08-118">Nasıl yapılır: dinamik olarak bir veritabanı oluşturun</span><span class="sxs-lookup"><span data-stu-id="b6e08-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="b6e08-119">Veritabanlarını dinamik olarak oluşturmak nasıl ve bu yaklaşım için tipik senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6e08-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="b6e08-120">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="b6e08-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="b6e08-121">İyimser eşzamanlılık sorunlarını çözdükten teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6e08-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
