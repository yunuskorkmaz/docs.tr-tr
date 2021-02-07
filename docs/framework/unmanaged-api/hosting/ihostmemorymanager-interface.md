---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager arabirimi'
title: IHostMemoryManager Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: c9b6f83b5c70a53388e886e1047798f660b826e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707898"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="cafee-103">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cafee-103">IHostMemoryManager Interface</span></span>

<span data-ttu-id="cafee-104">Ortak dil çalışma zamanının (CLR), standart Win32 sanal bellek işlevlerini kullanmak yerine ana bilgisayar üzerinden sanal bellek istekleri yapmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cafee-104">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cafee-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cafee-105">Methods</span></span>  
  
|<span data-ttu-id="cafee-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cafee-106">Method</span></span>|<span data-ttu-id="cafee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cafee-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cafee-108">AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-108">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="cafee-109">Ana bilgisayara ortak dil çalışma zamanının (CLR) belirtilen belleği işletim sisteminden almış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="cafee-109">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="cafee-110">CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-110">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="cafee-111">Ana bilgisayar tarafından oluşturulan bir yığından bellek ayırmaları istemek için kullanılan bir [IHostMAlloc](ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="cafee-111">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="cafee-112">GetMemoryLoad Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-112">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="cafee-113">Ana bilgisayar tarafından bildirilen şu anda kullanılmakta olan fiziksel bellek miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="cafee-113">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="cafee-114">NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-114">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="cafee-115">Konağa CLR 'nin belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cafee-115">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="cafee-116">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-116">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="cafee-117">Ana bilgisayarın, bilgisayardaki geçerli bellek yükünün CLR 'sini bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cafee-117">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="cafee-118">ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-118">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="cafee-119">Konağa, belirtilen belleği kullanarak CLR 'nin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cafee-119">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="cafee-120">VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-120">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="cafee-121">, Çağıran işlemin sanal adres alanındaki bir sayfa bölgesini saklı veya işleme alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="cafee-121">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="cafee-122">VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-122">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="cafee-123">, Çağıran işlemin sanal adres alanı içindeki bir sayfa bölgesini serbest bırakır, serbest bırakır ya da yayınlar ve bunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cafee-123">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="cafee-124">VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-124">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="cafee-125">, İlgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür ve bu işlem, çağıran işlemin sanal adres alanındaki kaydedilmiş sayfaların bir bölgesindeki korumayı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cafee-125">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="cafee-126">VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafee-126">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="cafee-127">, Çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="cafee-127">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cafee-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cafee-128">Remarks</span></span>  

 <span data-ttu-id="cafee-129">`IHostMemoryManager` Ayrıca, CLR 'nin yığın üzerinde bellek istekleri yapması ve işlem içindeki bellek baskısı düzeyini, ana bilgisayar tarafından bildirilen bir işaretçiye ulaşmak üzere CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cafee-129">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cafee-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cafee-130">Requirements</span></span>  

 <span data-ttu-id="cafee-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cafee-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cafee-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cafee-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cafee-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cafee-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cafee-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cafee-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cafee-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cafee-135">See also</span></span>

- [<span data-ttu-id="cafee-136">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cafee-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="cafee-137">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cafee-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
