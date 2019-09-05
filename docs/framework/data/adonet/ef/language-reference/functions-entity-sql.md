---
title: İşlevler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250917"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="e96e9-102">İşlevler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e96e9-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="e96e9-103">Entity SQL, Kullanıcı tanımlı işlevleri, kurallı işlevleri ve sağlayıcıya özgü işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="e96e9-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="e96e9-104">Kullanıcı tanımlı işlevler, kavramsal modelde veya sorgudaki satır içi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e96e9-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="e96e9-105">Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e96e9-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="e96e9-106">Kurallı işlevler Entity Framework önceden tanımlanmıştır ve veri sağlayıcıları tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e96e9-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="e96e9-107">Bir Kullanıcı bir sağlayıcı tarafından desteklenmeyen bir işlevi çağırırsa Entity SQL komutları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e96e9-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="e96e9-108">Bu nedenle, kurallı işlevler genellikle sağlayıcıya özgü bir ad alanında bulunan mağazaya özgü işlevlerde önerilir.</span><span class="sxs-lookup"><span data-stu-id="e96e9-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="e96e9-109">Daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e96e9-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="e96e9-110">Microsoft SQL Istemci tarafından yönetilen sağlayıcı, sağlayıcıya özgü işlevler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96e9-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="e96e9-111">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e96e9-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e96e9-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e96e9-112">In This Section</span></span>  
 [<span data-ttu-id="e96e9-113">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="e96e9-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="e96e9-114">İşlev Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="e96e9-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="e96e9-115">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e96e9-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="e96e9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e96e9-116">See also</span></span>

- [<span data-ttu-id="e96e9-117">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e96e9-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
