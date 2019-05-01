---
title: 'Nasıl yapılır: Değişiklik Çakışmalarını Yönetme'
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 7858dc304d281dfb99755d83eec19b421f63d2ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903389"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="13019-102">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="13019-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="13019-103">keşfedin, değerlendirin ve eşzamanlılık çakışmaları çözümlemek amacıyla API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="13019-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13019-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="13019-104">In This Section</span></span>  
 [<span data-ttu-id="13019-105">Nasıl yapılır: Algılamak ve çözmek çakışan gönderimleri</span><span class="sxs-lookup"><span data-stu-id="13019-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="13019-106">Algılama ve eşzamanlılık çakışmaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="13019-107">Nasıl yapılır: Özel zaman eşzamanlılık durumlar belirtin</span><span class="sxs-lookup"><span data-stu-id="13019-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="13019-108">Eşzamanlılık çakışmalarını bilgilendirilmesi zamanı belirtmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="13019-109">Nasıl yapılır: Üyeleri eşzamanlılık çakışmaları için test edildiğini belirtme</span><span class="sxs-lookup"><span data-stu-id="13019-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="13019-110">Üyeleri eşzamanlılık çakışmaları için denetlenip denetlenmeyeceğini belirtmek için özniteliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="13019-111">Nasıl yapılır: Varlık çakışma bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="13019-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="13019-112">Varlık çakışmalar hakkında bilgi toplamak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="13019-113">Nasıl yapılır: Üye çakışma bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="13019-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="13019-114">Üye çakışıyor hakkında bilgi toplamak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="13019-115">Nasıl yapılır: Veritabanı değerlerini tutarak çakışmaları</span><span class="sxs-lookup"><span data-stu-id="13019-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="13019-116">Veritabanı değerleri ile geçerli değerlerin üzerine açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="13019-117">Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları</span><span class="sxs-lookup"><span data-stu-id="13019-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="13019-118">Veritabanı değerlerinin üzerine yazarak geçerli değerleri tutmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="13019-119">Nasıl yapılır: Veritabanı değerleri ile birleştirerek çakışmaları</span><span class="sxs-lookup"><span data-stu-id="13019-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="13019-120">Veritabanı ve geçerli değerlerini birleştirerek bir çakışmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="13019-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13019-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="13019-121">Related Sections</span></span>  
 [<span data-ttu-id="13019-122">İyimser eşzamanlılık: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13019-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="13019-123">İyimser eşzamanlılık uygulamak terimler açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13019-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
