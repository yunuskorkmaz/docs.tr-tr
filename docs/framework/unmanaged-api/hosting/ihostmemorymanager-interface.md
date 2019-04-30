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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760187"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="01bf6-102">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01bf6-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="01bf6-103">Standart Win32 sanal bellek işlevleri kullanmak yerine, ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden sanal bellek isteğinde bulunmak için izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01bf6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01bf6-104">Methods</span></span>  
  
|<span data-ttu-id="01bf6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="01bf6-105">Method</span></span>|<span data-ttu-id="01bf6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01bf6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01bf6-107">AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="01bf6-108">Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek işletim sisteminden almışsa bildirir.</span><span class="sxs-lookup"><span data-stu-id="01bf6-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="01bf6-109">CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="01bf6-110">Bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) ana bilgisayar tarafından oluşturulan bir yığın bellek ayırmaları istek için kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="01bf6-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="01bf6-111">GetMemoryLoad Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="01bf6-112">Şu anda kullanılıyor, fiziksel bellek miktarı, konak tarafından bildirilen alır.</span><span class="sxs-lookup"><span data-stu-id="01bf6-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="01bf6-113">NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="01bf6-114">Konak, CLR belirtilen bellek kullanma girişimi gittiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="01bf6-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="01bf6-115">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="01bf6-116">Konak bilgisayardaki geçerli bellek yükü CLR bildirmek için çağıran bir geri çağırma işlevi işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="01bf6-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="01bf6-117">ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="01bf6-118">Ana bilgisayar, belirtilen bellek kullanarak CLR tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="01bf6-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="01bf6-119">VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="01bf6-120">Ayırır veya çağırma işleminin sanal adres alanı sayfalarında bölgesi işlemeler karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01bf6-121">VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="01bf6-122">Serbest bırakır, kaydeder, veya serbest bırakır ve çağıran işlemin sanal adres alanı içinde sayfalar bölgesini kaydeder karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01bf6-123">VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="01bf6-124">Bir bölge üzerindeki korumayı taahhüt edilen sayfa çağırma işleminin sanal adres alanı değişiklikleri karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01bf6-125">VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bf6-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="01bf6-126">Sayfaları çağırma işleminin sanal adres alanı içinde bir dizi hakkındaki bilgileri alır karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01bf6-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01bf6-127">Remarks</span></span>  
 <span data-ttu-id="01bf6-128">`IHostMemoryManager` Ayrıca ana bilgisayar tarafından belirlendiği şekilde, yığında bellek isteğinde bulunmak için ve işleminde, bellek baskısı düzeyini almak için bir işaretçi alma CLR'nin için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bf6-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01bf6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01bf6-129">Requirements</span></span>  
 <span data-ttu-id="01bf6-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01bf6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01bf6-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01bf6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01bf6-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="01bf6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01bf6-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01bf6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bf6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01bf6-134">See also</span></span>

- [<span data-ttu-id="01bf6-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01bf6-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="01bf6-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="01bf6-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
