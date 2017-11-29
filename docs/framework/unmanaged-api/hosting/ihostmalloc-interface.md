---
title: IHostMalloc Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="64910-102">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64910-102">IHostMalloc Interface</span></span>
<span data-ttu-id="64910-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden öbek hassas ayırmaları istemesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="64910-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64910-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="64910-104">Methods</span></span>  
  
|<span data-ttu-id="64910-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="64910-105">Method</span></span>|<span data-ttu-id="64910-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64910-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64910-107">Alloc yöntemi</span><span class="sxs-lookup"><span data-stu-id="64910-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="64910-108">Ana bilgisayar yığınından istenilen bellek miktarını tahsis istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="64910-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="64910-109">DebugAlloc yöntemi</span><span class="sxs-lookup"><span data-stu-id="64910-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="64910-110">Konak istenilen bellek miktarını yığınından ayırın ve ayrıca burada belleği ayrıldı izlemek ister.</span><span class="sxs-lookup"><span data-stu-id="64910-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="64910-111">Free yöntemi</span><span class="sxs-lookup"><span data-stu-id="64910-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="64910-112">Kullanarak ayrılmış bellek boşaltır `Alloc` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="64910-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64910-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64910-113">Remarks</span></span>  
 <span data-ttu-id="64910-114">CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="64910-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64910-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64910-115">Requirements</span></span>  
 <span data-ttu-id="64910-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64910-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64910-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64910-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64910-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="64910-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64910-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64910-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64910-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64910-120">See Also</span></span>  
 [<span data-ttu-id="64910-121">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="64910-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="64910-122">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64910-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
