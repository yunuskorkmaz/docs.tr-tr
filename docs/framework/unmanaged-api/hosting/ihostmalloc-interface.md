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
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136773"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="91bbd-102">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91bbd-102">IHostMalloc Interface</span></span>
<span data-ttu-id="91bbd-103">Ortak dil çalışma zamanının (CLR) ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bbd-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91bbd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="91bbd-104">Methods</span></span>  
  
|<span data-ttu-id="91bbd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="91bbd-105">Method</span></span>|<span data-ttu-id="91bbd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91bbd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91bbd-107">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91bbd-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="91bbd-108">Konağın, istenen bellek miktarını yığından ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="91bbd-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="91bbd-109">DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91bbd-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="91bbd-110">Konağın, istenen bellek miktarını yığından ayırmasını ister ve ayrıca belleğin nerede ayrıldığını izler.</span><span class="sxs-lookup"><span data-stu-id="91bbd-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="91bbd-111">Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91bbd-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="91bbd-112">`Alloc` yöntemi kullanılarak ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="91bbd-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91bbd-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91bbd-113">Remarks</span></span>  
 <span data-ttu-id="91bbd-114">CLR, [IHostMemoryManager:: Createmayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir `IHostMalloc` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="91bbd-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91bbd-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91bbd-115">Requirements</span></span>  
 <span data-ttu-id="91bbd-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91bbd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91bbd-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91bbd-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91bbd-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="91bbd-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91bbd-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91bbd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bbd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91bbd-120">See also</span></span>

- [<span data-ttu-id="91bbd-121">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91bbd-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="91bbd-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91bbd-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
