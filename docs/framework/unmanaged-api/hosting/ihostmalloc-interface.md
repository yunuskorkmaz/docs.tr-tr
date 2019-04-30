---
title: IHostMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757644"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="84498-102">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84498-102">IHostMalloc Interface</span></span>
<span data-ttu-id="84498-103">Ortak dil çalışma zamanı (CLR) yığın konağı üzerinden hassas ayırmaları istemesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="84498-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84498-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="84498-104">Methods</span></span>  
  
|<span data-ttu-id="84498-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="84498-105">Method</span></span>|<span data-ttu-id="84498-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84498-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84498-107">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84498-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="84498-108">İstekleri konak yığından istenen bellek miktarı ayırın.</span><span class="sxs-lookup"><span data-stu-id="84498-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="84498-109">DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84498-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="84498-110">Konak istenilen bellek miktarını yığından ayırmak ve ayrıca bellek ayrıldığı izlemek ister.</span><span class="sxs-lookup"><span data-stu-id="84498-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="84498-111">Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84498-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="84498-112">Kullanarak ayrılan bellek serbest bırakma `Alloc` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84498-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84498-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84498-113">Remarks</span></span>  
 <span data-ttu-id="84498-114">CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84498-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84498-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84498-115">Requirements</span></span>  
 <span data-ttu-id="84498-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84498-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84498-117">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84498-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84498-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="84498-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84498-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84498-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84498-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84498-120">See also</span></span>

- [<span data-ttu-id="84498-121">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84498-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="84498-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="84498-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
