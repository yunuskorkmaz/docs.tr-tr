---
description: 'Hakkında daha fazla bilgi edinin: Işlevler (Entity SQL)'
title: İşlevler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: c557d264587a1d40194971d756e6b5c75a3856aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786309"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="c346c-103">İşlevler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c346c-103">Functions (Entity SQL)</span></span>

<span data-ttu-id="c346c-104">Entity SQL, Kullanıcı tanımlı işlevleri, kurallı işlevleri ve sağlayıcıya özgü işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c346c-104">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="c346c-105">Kullanıcı tanımlı işlevler, kavramsal modelde veya sorgudaki satır içi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c346c-105">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="c346c-106">Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c346c-106">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c346c-107">Kurallı işlevler Entity Framework önceden tanımlanmıştır ve veri sağlayıcıları tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c346c-107">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="c346c-108">Bir Kullanıcı bir sağlayıcı tarafından desteklenmeyen bir işlevi çağırırsa Entity SQL komutları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c346c-108">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="c346c-109">Bu nedenle, kurallı işlevler genellikle sağlayıcıya özgü bir ad alanında bulunan mağazaya özgü işlevlerde önerilir.</span><span class="sxs-lookup"><span data-stu-id="c346c-109">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="c346c-110">Daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c346c-110">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="c346c-111">Microsoft SQL Istemci tarafından yönetilen sağlayıcı, sağlayıcıya özgü işlevler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c346c-111">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="c346c-112">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c346c-112">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c346c-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c346c-113">In This Section</span></span>  

 [<span data-ttu-id="c346c-114">Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="c346c-114">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="c346c-115">İşlev Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="c346c-115">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="c346c-116">Toplama Işlevleri</span><span class="sxs-lookup"><span data-stu-id="c346c-116">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="c346c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c346c-117">See also</span></span>

- [<span data-ttu-id="c346c-118">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c346c-118">Entity SQL Overview</span></span>](entity-sql-overview.md)
