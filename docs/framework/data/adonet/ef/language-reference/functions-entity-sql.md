---
title: "İşlevler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9008360a4af0a669a223a2e56ee5152b23c6ebe4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="functions-entity-sql"></a><span data-ttu-id="ce5d5-102">İşlevler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ce5d5-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="ce5d5-103">Varlık SQL kullanıcı tanımlı işlevler, kurallı işlevlerini ve sağlayıcıya özgü işlevlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="ce5d5-104">Kullanıcı tanımlı işlevler kavramsal model veya satır sorgu içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="ce5d5-105">Daha fazla bilgi için bkz: [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ce5d5-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ce5d5-106">Kurallı işlevleri Entity Framework önceden ve veri sağlayıcıları tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="ce5d5-107">Varlık SQL komutlarını bir kullanıcı bir sağlayıcı tarafından desteklenmeyen bir işlev çağrıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="ce5d5-108">Bu nedenle, kurallı işlevleri, bir sağlayıcıya özgü ad alanında deposu özgü işlevler üzerinden genellikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="ce5d5-109">Daha fazla bilgi için bkz: [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ce5d5-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="ce5d5-110">Microsoft SQL istemci yönetilen sağlayıcısı, bir sağlayıcıya özgü işlevler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="ce5d5-111">Daha fazla bilgi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ce5d5-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce5d5-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ce5d5-112">In This Section</span></span>  
 [<span data-ttu-id="ce5d5-113">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="ce5d5-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="ce5d5-114">İşlev Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="ce5d5-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="ce5d5-115">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ce5d5-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce5d5-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5d5-116">See Also</span></span>  
 [<span data-ttu-id="ce5d5-117">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce5d5-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
