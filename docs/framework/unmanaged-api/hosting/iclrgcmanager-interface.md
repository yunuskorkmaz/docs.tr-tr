---
title: ICLRGCManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7215ce1423e8541b23daae7b9e051ade6e25f1b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="5f4c3-102">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="5f4c3-103">Ortak dil çalışma zamanı 's çöp toplama sistemi ile etkileşim kurmak bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f4c3-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) bir atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak için yöntemi ' den `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f4c3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5f4c3-105">Methods</span></span>  
  
|<span data-ttu-id="5f4c3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5f4c3-106">Method</span></span>|<span data-ttu-id="5f4c3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f4c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f4c3-108">Collect yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="5f4c3-109">Çöp toplama belirtilen oluşturma için zorlar.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="5f4c3-110">GetStats yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="5f4c3-111">Çöp toplama sistemi hakkında geçerli istatistiklerini kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="5f4c3-112">SetGCStartupLimits yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="5f4c3-113">Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f4c3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f4c3-114">Remarks</span></span>  
 <span data-ttu-id="5f4c3-115">Ortak dil çalışma zamanı (CLR), atık toplama mekanizmasıyla yönetilen uygulayan <xref:System.GC> türü.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="5f4c3-116">Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f4c3-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4c3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f4c3-117">Requirements</span></span>  
 <span data-ttu-id="5f4c3-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f4c3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f4c3-119">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f4c3-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f4c3-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5f4c3-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f4c3-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f4c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4c3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f4c3-122">See Also</span></span>  
 [<span data-ttu-id="5f4c3-123">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="5f4c3-124">COR_GC_STATS yapısı</span><span class="sxs-lookup"><span data-stu-id="5f4c3-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="5f4c3-125">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f4c3-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="5f4c3-126">CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5f4c3-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="5f4c3-127">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5f4c3-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="5f4c3-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="5f4c3-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
