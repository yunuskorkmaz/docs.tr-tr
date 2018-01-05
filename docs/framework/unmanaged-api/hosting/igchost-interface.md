---
title: IGCHost Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77a2cab35785aa39571d39bdd369fa26cdbcd1d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="igchost-interface"></a><span data-ttu-id="54ac5-102">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54ac5-102">IGCHost Interface</span></span>
<span data-ttu-id="54ac5-103">Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="54ac5-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54ac5-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) bir atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak için yöntemi `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54ac5-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54ac5-105">Yalnızca Uzman kullanım arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="54ac5-105">This interface is for expert usage only.</span></span> <span data-ttu-id="54ac5-106">Yanlış kullandıysanız, bir uygulamanın performansını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="54ac5-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54ac5-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54ac5-107">Methods</span></span>  
  
|<span data-ttu-id="54ac5-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="54ac5-108">Method</span></span>|<span data-ttu-id="54ac5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54ac5-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54ac5-110">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac5-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="54ac5-111">Geçerli çöp toplama durumu bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.</span><span class="sxs-lookup"><span data-stu-id="54ac5-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="54ac5-112">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac5-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="54ac5-113">İstatistikleri çöp toplama sistemi için geçerli durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="54ac5-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="54ac5-114">GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac5-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="54ac5-115">İş parçacığı başına istatistiklerini atık toplama için alır.</span><span class="sxs-lookup"><span data-stu-id="54ac5-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="54ac5-116">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac5-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="54ac5-117">Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="54ac5-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="54ac5-118">SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54ac5-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="54ac5-119">En büyük çalışma zamanı'nın sanal bellek boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="54ac5-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54ac5-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54ac5-120">Requirements</span></span>  
 <span data-ttu-id="54ac5-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54ac5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ac5-122">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="54ac5-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="54ac5-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54ac5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54ac5-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54ac5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ac5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54ac5-125">See Also</span></span>  
 [<span data-ttu-id="54ac5-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54ac5-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="54ac5-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="54ac5-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
