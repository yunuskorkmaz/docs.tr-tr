---
title: "Nasıl yapılır: değişiklik çakışmalarını yönetin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: caacb4c3b877ce6bf7ba11001f602a76ad7f9734
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="7f15d-102">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="7f15d-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7f15d-103">bir koleksiyon bulabilir, değerlendirmek ve eşzamanlılık çakışmaları yardımcı olmak için API sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f15d-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7f15d-104">In This Section</span></span>  
 [<span data-ttu-id="7f15d-105">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="7f15d-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="7f15d-106">Algılamak ve eşzamanlılık çakışmalarını çözmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="7f15d-107">Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme</span><span class="sxs-lookup"><span data-stu-id="7f15d-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="7f15d-108">Eşzamanlılık çakışmalarına da haberdar zamanı belirtmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="7f15d-109">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="7f15d-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="7f15d-110">Eşzamanlılık çakışmalar için denetlenip denetlenmeyeceğini belirtmek için üyeleri özniteliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="7f15d-111">Nasıl yapılır: Varlık Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="7f15d-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="7f15d-112">Varlık çakışmaları hakkında bilgi toplamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="7f15d-113">Nasıl yapılır: Üye Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="7f15d-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="7f15d-114">Üye çakışmaları hakkında bilgi toplamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="7f15d-115">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="7f15d-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="7f15d-116">Geçerli değerler veritabanı değerlerle üzerine açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="7f15d-117">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="7f15d-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="7f15d-118">Veritabanı değerlerini yazarak geçerli değerleri korumak açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="7f15d-119">Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="7f15d-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="7f15d-120">Veritabanı ve geçerli değerleri birleştirerek bir çakışmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f15d-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7f15d-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7f15d-121">Related Sections</span></span>  
 [<span data-ttu-id="7f15d-122">İyimser Eşzamanlılık: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7f15d-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="7f15d-123">İyimser eşzamanlılık uygulamak terimler açıklanmıştır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f15d-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
