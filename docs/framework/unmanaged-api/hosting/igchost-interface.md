---
title: IGCHost Arabirimi
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d3f588bfc9799ed4591114b28d081ab417678b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914804"
---
# <a name="igchost-interface"></a><span data-ttu-id="7ceb0-102">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-102">IGCHost Interface</span></span>
<span data-ttu-id="7ceb0-103">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ceb0-104">4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu 0 ' dan `DWORD` daha büyük değerlere ayarlayın. [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınır.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ceb0-105">Bu arabirim yalnızca uzman kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-105">This interface is for expert usage only.</span></span> <span data-ttu-id="7ceb0-106">Yanlış kullanılırsa, bir uygulamanın performansını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ceb0-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ceb0-107">Methods</span></span>  
  
|<span data-ttu-id="7ceb0-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ceb0-108">Method</span></span>|<span data-ttu-id="7ceb0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ceb0-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ceb0-110">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="7ceb0-111">Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="7ceb0-112">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="7ceb0-113">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="7ceb0-114">GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="7ceb0-115">Çöp toplama için iş parçacığı başına istatistikleri alır.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="7ceb0-116">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="7ceb0-117">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="7ceb0-118">SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb0-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="7ceb0-119">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ceb0-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ceb0-120">Requirements</span></span>  
 <span data-ttu-id="7ceb0-121">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ceb0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ceb0-122">**Üst bilgi** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="7ceb0-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7ceb0-123">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7ceb0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ceb0-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ceb0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceb0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ceb0-125">See also</span></span>

- [<span data-ttu-id="7ceb0-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ceb0-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7ceb0-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="7ceb0-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
