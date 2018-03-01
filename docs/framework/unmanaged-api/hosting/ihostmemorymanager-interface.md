---
title: IHostMemoryManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b39a43874bc1808928f21e0a35638aae9a99ca8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="6025e-102">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6025e-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="6025e-103">Standart Win32 sanal bellek işlevleri kullanmak yerine ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden sanal bellek istekler yapmasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6025e-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6025e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6025e-104">Methods</span></span>  
  
|<span data-ttu-id="6025e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6025e-105">Method</span></span>|<span data-ttu-id="6025e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6025e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6025e-107">AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="6025e-108">Ana bilgisayar işletim sisteminden belirtilen bellek ortak dil çalışma zamanı (CLR) geçirmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="6025e-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="6025e-109">CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="6025e-110">Bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) ana bilgisayar tarafından oluşturulan bir yığın bellek ayırmaları istemesini kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="6025e-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="6025e-111">GetMemoryLoad Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="6025e-112">Şu anda kullanılıyor, fiziksel bellek miktarı, ana bilgisayar tarafından bildirilen alır.</span><span class="sxs-lookup"><span data-stu-id="6025e-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="6025e-113">NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="6025e-114">Ana bilgisayar CLR belirtilen bellek kullanma girişimi gittiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="6025e-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="6025e-115">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="6025e-116">Konak bilgisayardaki geçerli bellek yükü CLR bildirmek için çağıran bir geri çağırma işlevini gösteren bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6025e-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="6025e-117">ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="6025e-118">Ana bilgisayar CLR belirtilen bellek kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6025e-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="6025e-119">VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="6025e-120">Mantıksal bir sarmalayıcı ayırır veya bir bölge çağırma işleminin sanal adres alanındaki sayfaların tamamlar karşılık gelen Win32 işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="6025e-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6025e-121">VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="6025e-122">Serbest, decommits, veya serbest bırakır ve çağırma işleminin sanal adres alanı içinde sayfalar bölgesi decommits karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6025e-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6025e-123">VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="6025e-124">Bir bölge koruma çağırma işleminin sanal adres alanındaki taahhüt sayfaların değişiklikleri karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6025e-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6025e-125">VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6025e-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="6025e-126">Çağırma işleminin sanal adres alanındaki sayfaları bir dizi ilgili bilgileri alır karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6025e-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6025e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6025e-127">Remarks</span></span>  
 <span data-ttu-id="6025e-128">`IHostMemoryManager`Ayrıca ana bilgisayar tarafından bildirilen içinden öbek üzerinde bellek istekler yapmasını ve işleminde, bellek baskısı düzeyini almak için bir işaretçi almak CLR için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6025e-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6025e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6025e-129">Requirements</span></span>  
 <span data-ttu-id="6025e-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6025e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6025e-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6025e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6025e-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6025e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6025e-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6025e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6025e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6025e-134">See Also</span></span>  
 [<span data-ttu-id="6025e-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6025e-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="6025e-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6025e-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
