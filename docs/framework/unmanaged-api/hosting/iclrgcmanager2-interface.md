---
title: ICLRGCManager2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2
helpviewer_keywords: ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b025ec31e3797fec3ac184929f1274cb5f68501b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="f35a1-102">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f35a1-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="f35a1-103">Ortak dil çalışma zamanı 's çöp toplama sistemi ile etkileşim kurmak bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f35a1-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f35a1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f35a1-104">Methods</span></span>  
  
|<span data-ttu-id="f35a1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f35a1-105">Method</span></span>|<span data-ttu-id="f35a1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f35a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f35a1-107">SetGCStartupLimitsEx yöntemi</span><span class="sxs-lookup"><span data-stu-id="f35a1-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="f35a1-108">Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f35a1-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="f35a1-109">Kuşak 0 ve büyük kesim boyutları sağlayan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="f35a1-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f35a1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f35a1-110">Remarks</span></span>  
 <span data-ttu-id="f35a1-111">Bu arabirim devraldığı [Iclrgcmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f35a1-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="f35a1-112">Ortak dil çalışma zamanı (CLR), atık toplama mekanizmasıyla yönetilen uygulayan <xref:System.GC> türü.</span><span class="sxs-lookup"><span data-stu-id="f35a1-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="f35a1-113">Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f35a1-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f35a1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f35a1-114">Requirements</span></span>  
 <span data-ttu-id="f35a1-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f35a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f35a1-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f35a1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f35a1-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f35a1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f35a1-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f35a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35a1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f35a1-119">See Also</span></span>  
 [<span data-ttu-id="f35a1-120">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="f35a1-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="f35a1-121">COR_GC_STATS yapısı</span><span class="sxs-lookup"><span data-stu-id="f35a1-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="f35a1-122">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="f35a1-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="f35a1-123">.NET Framework 4 ve 4.5 eklenen CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f35a1-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="f35a1-124">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f35a1-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f35a1-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f35a1-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
