---
title: İşlevler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: f31f829b53160da5a043617b9aa999b398859f17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080611"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="c4f91-102">İşlevler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="c4f91-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="c4f91-103">Entity SQL kullanıcı tanımlı işlevler, kurallı işlevler ve sağlayıcıya özgü işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c4f91-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="c4f91-104">Kullanıcı tanımlı işlevler kavramsal model veya satır içi sorgu belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="c4f91-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="c4f91-105">Daha fazla bilgi için [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c4f91-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c4f91-106">Kurallı İşlevler, varlık Çerçevesi'nde önceden tanımlanmıştır ve veri sağlayıcıları tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4f91-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="c4f91-107">Bir kullanıcı bir sağlayıcı tarafından desteklenmeyen bir işlevi çağırıyorsa varlık SQL komutlarını başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c4f91-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="c4f91-108">Bu nedenle, kurallı İşlevler, genellikle bir sağlayıcıya özel ad alanında deposu özel işlevleri, üzerinden önerilir.</span><span class="sxs-lookup"><span data-stu-id="c4f91-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="c4f91-109">Daha fazla bilgi için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c4f91-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="c4f91-110">Microsoft SQL istemci yönetilen sağlayıcı sağlayıcısı özel işlevler sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4f91-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="c4f91-111">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c4f91-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4f91-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c4f91-112">In This Section</span></span>  
 [<span data-ttu-id="c4f91-113">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="c4f91-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="c4f91-114">İşlev Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="c4f91-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="c4f91-115">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c4f91-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4f91-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f91-116">See also</span></span>

- [<span data-ttu-id="c4f91-117">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4f91-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
