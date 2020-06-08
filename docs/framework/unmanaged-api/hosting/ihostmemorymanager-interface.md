---
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
ms.openlocfilehash: 09b4a06892cdc450eed9dead503a990b6f19804e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501514"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="6d2ec-102">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="6d2ec-103">Ortak dil çalışma zamanının (CLR), standart Win32 sanal bellek işlevlerini kullanmak yerine ana bilgisayar üzerinden sanal bellek istekleri yapmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d2ec-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d2ec-104">Methods</span></span>  
  
|<span data-ttu-id="6d2ec-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6d2ec-105">Method</span></span>|<span data-ttu-id="6d2ec-106">Description</span><span class="sxs-lookup"><span data-stu-id="6d2ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d2ec-107">AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="6d2ec-108">Ana bilgisayara ortak dil çalışma zamanının (CLR) belirtilen belleği işletim sisteminden almış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="6d2ec-109">CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-109">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="6d2ec-110">Ana bilgisayar tarafından oluşturulan bir yığından bellek ayırmaları istemek için kullanılan bir [IHostMAlloc](ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="6d2ec-111">GetMemoryLoad Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="6d2ec-112">Ana bilgisayar tarafından bildirilen şu anda kullanılmakta olan fiziksel bellek miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="6d2ec-113">NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="6d2ec-114">Konağa CLR 'nin belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="6d2ec-115">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="6d2ec-116">Ana bilgisayarın, bilgisayardaki geçerli bellek yükünün CLR 'sini bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="6d2ec-117">ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="6d2ec-118">Konağa, belirtilen belleği kullanarak CLR 'nin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="6d2ec-119">VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="6d2ec-120">, Çağıran işlemin sanal adres alanındaki bir sayfa bölgesini saklı veya işleme alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6d2ec-121">VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="6d2ec-122">, Çağıran işlemin sanal adres alanı içindeki bir sayfa bölgesini serbest bırakır, serbest bırakır ya da yayınlar ve bunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6d2ec-123">VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="6d2ec-124">, İlgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür ve bu işlem, çağıran işlemin sanal adres alanındaki kaydedilmiş sayfaların bir bölgesindeki korumayı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6d2ec-125">VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="6d2ec-126">, Çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d2ec-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d2ec-127">Remarks</span></span>  
 <span data-ttu-id="6d2ec-128">`IHostMemoryManager`Ayrıca, CLR 'nin yığın üzerinde bellek istekleri yapması ve işlem içindeki bellek baskısı düzeyini, ana bilgisayar tarafından bildirilen bir işaretçiye ulaşmak üzere CLR için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2ec-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d2ec-129">Requirements</span></span>  
 <span data-ttu-id="6d2ec-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2ec-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2ec-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d2ec-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d2ec-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6d2ec-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d2ec-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2ec-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2ec-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2ec-134">See also</span></span>

- [<span data-ttu-id="6d2ec-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2ec-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="6d2ec-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6d2ec-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
