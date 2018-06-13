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
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441354"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="bfa46-102">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfa46-102">IHostMalloc Interface</span></span>
<span data-ttu-id="bfa46-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden öbek hassas ayırmaları istemesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfa46-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfa46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bfa46-104">Methods</span></span>  
  
|<span data-ttu-id="bfa46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bfa46-105">Method</span></span>|<span data-ttu-id="bfa46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfa46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bfa46-107">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfa46-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="bfa46-108">Ana bilgisayar yığınından istenilen bellek miktarını tahsis istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="bfa46-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="bfa46-109">DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfa46-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="bfa46-110">Konak istenilen bellek miktarını yığınından ayırın ve ayrıca burada belleği ayrıldı izlemek ister.</span><span class="sxs-lookup"><span data-stu-id="bfa46-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="bfa46-111">Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfa46-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="bfa46-112">Kullanarak ayrılmış bellek boşaltır `Alloc` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bfa46-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfa46-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfa46-113">Remarks</span></span>  
 <span data-ttu-id="bfa46-114">CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bfa46-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa46-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfa46-115">Requirements</span></span>  
 <span data-ttu-id="bfa46-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa46-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa46-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfa46-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfa46-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bfa46-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfa46-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa46-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa46-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfa46-120">See Also</span></span>  
 [<span data-ttu-id="bfa46-121">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfa46-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="bfa46-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bfa46-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
