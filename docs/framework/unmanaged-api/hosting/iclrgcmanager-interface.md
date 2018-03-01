---
title: ICLRGCManager Arabirimi
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
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="8a5c7-102">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="8a5c7-103">Ortak dil çalışma zamanı 's çöp toplama sistemi ile etkileşim kurmak bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a5c7-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) bir atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak için yöntemi ' den `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a5c7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a5c7-105">Methods</span></span>  
  
|<span data-ttu-id="8a5c7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a5c7-106">Method</span></span>|<span data-ttu-id="8a5c7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a5c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a5c7-108">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="8a5c7-109">Çöp toplama belirtilen oluşturma için zorlar.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="8a5c7-110">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="8a5c7-111">Çöp toplama sistemi hakkında geçerli istatistiklerini kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="8a5c7-112">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="8a5c7-113">Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a5c7-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a5c7-114">Remarks</span></span>  
 <span data-ttu-id="8a5c7-115">Ortak dil çalışma zamanı (CLR), atık toplama mekanizmasıyla yönetilen uygulayan <xref:System.GC> türü.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="8a5c7-116">Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a5c7-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a5c7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a5c7-117">Requirements</span></span>  
 <span data-ttu-id="8a5c7-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a5c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a5c7-119">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a5c7-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a5c7-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8a5c7-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a5c7-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a5c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5c7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a5c7-122">See Also</span></span>  
 [<span data-ttu-id="8a5c7-123">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="8a5c7-124">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="8a5c7-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="8a5c7-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a5c7-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8a5c7-126">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a5c7-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="8a5c7-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a5c7-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="8a5c7-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="8a5c7-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
