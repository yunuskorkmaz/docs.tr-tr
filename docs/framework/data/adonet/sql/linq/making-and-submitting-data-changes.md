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
ms.workload: dotnet
ms.openlocfilehash: d2b121bdadcc231d2ea3a2c1d2ebdab40306c5ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="6098d-102">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="6098d-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="6098d-103">Bu bölümdeki konular, yapmak ve değişiklikleri veritabanına aktarmak nasıl ve iyimser eşzamanlılık çakışmaları nasıl ele alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6098d-104">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="6098d-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="6098d-105">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6098d-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="6098d-106">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="6098d-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6098d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6098d-107">In This Section</span></span>  
 [<span data-ttu-id="6098d-108">Nasıl yapılır: Veritabanına Satır Ekleme</span><span class="sxs-lookup"><span data-stu-id="6098d-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="6098d-109">Nesne modeli nesneleri ekleyerek veritabanında satır eklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="6098d-110">Nasıl yapılır: Veritabanında Satırları Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6098d-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="6098d-111">Nesne modelinde güncelleştirerek veritabanındaki satırları güncelleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="6098d-112">Nasıl yapılır: Veritabanından Satır Silme</span><span class="sxs-lookup"><span data-stu-id="6098d-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="6098d-113">Nesne modelinde silerek veritabanında satır silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="6098d-114">Nasıl yapılır: Veritabanına Değişiklikleri Gönderme</span><span class="sxs-lookup"><span data-stu-id="6098d-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="6098d-115">Veritabanı için nesne modeli değişikliklerini göndermeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="6098d-116">Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma</span><span class="sxs-lookup"><span data-stu-id="6098d-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="6098d-117">Bir işlem içinde işlemleri içeren açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="6098d-118">Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6098d-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="6098d-119">Veritabanlarını dinamik olarak oluşturmak nasıl ve bu yaklaşım için tipik senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6098d-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="6098d-120">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="6098d-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="6098d-121">İyimser eşzamanlılık sorunlarını çözdükten teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="6098d-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
