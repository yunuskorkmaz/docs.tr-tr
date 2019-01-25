---
title: ICLRGCManager2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9897526882a8ae53410a7744f78c558dfa6981e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708590"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="302fd-102">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="302fd-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="302fd-103">Ortak dil çalışma zamanının atık toplama sistem ile etkileşimde bulunmak konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="302fd-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="302fd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="302fd-104">Methods</span></span>  
  
|<span data-ttu-id="302fd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="302fd-105">Method</span></span>|<span data-ttu-id="302fd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="302fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="302fd-107">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="302fd-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="302fd-108">Bir çöp toplama kesim boyutunu ve çöp toplama sistemin nesil 0 en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="302fd-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="302fd-109">Nesil 0 ve büyük kesim boyutları sağlayan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="302fd-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="302fd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="302fd-110">Remarks</span></span>  
 <span data-ttu-id="302fd-111">Bu arabirimin devraldığı [Iclrgcmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="302fd-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="302fd-112">Ortak dil çalışma zamanı (CLR) yönetilen, atık toplama mekanizması uygular <xref:System.GC> türü.</span><span class="sxs-lookup"><span data-stu-id="302fd-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="302fd-113">Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="302fd-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302fd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="302fd-114">Requirements</span></span>  
 <span data-ttu-id="302fd-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="302fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="302fd-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="302fd-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="302fd-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="302fd-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="302fd-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="302fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302fd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="302fd-119">See also</span></span>
- [<span data-ttu-id="302fd-120">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="302fd-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="302fd-121">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="302fd-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="302fd-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="302fd-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="302fd-123">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="302fd-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="302fd-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="302fd-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="302fd-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="302fd-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
