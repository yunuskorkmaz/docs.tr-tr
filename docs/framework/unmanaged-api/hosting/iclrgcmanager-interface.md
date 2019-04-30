---
title: ICLRGCManager Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9519f7c2df5cf078bac6be038275527d7741edb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700845"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="658a2-102">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="658a2-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="658a2-103">Ortak dil çalışma zamanının atık toplama sistem ile etkileşimde bulunmak konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="658a2-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="658a2-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) bir çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerine büyük ayarlamak için yöntemi daha `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="658a2-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="658a2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="658a2-105">Methods</span></span>  
  
|<span data-ttu-id="658a2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="658a2-106">Method</span></span>|<span data-ttu-id="658a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="658a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="658a2-108">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="658a2-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="658a2-109">Bir çöp toplama işlemi için belirtilen oluşturmanın zorlar.</span><span class="sxs-lookup"><span data-stu-id="658a2-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="658a2-110">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="658a2-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="658a2-111">Çöp toplama sistemi geçerli İstatistikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="658a2-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="658a2-112">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="658a2-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="658a2-113">Bir çöp toplama kesim boyutunu ve çöp toplama sistemin nesil 0 en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="658a2-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="658a2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="658a2-114">Remarks</span></span>  
 <span data-ttu-id="658a2-115">Ortak dil çalışma zamanı (CLR) yönetilen, atık toplama mekanizması uygular <xref:System.GC> türü.</span><span class="sxs-lookup"><span data-stu-id="658a2-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="658a2-116">Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="658a2-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="658a2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="658a2-117">Requirements</span></span>  
 <span data-ttu-id="658a2-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="658a2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="658a2-119">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="658a2-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="658a2-120">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="658a2-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="658a2-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="658a2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658a2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="658a2-122">See also</span></span>

- [<span data-ttu-id="658a2-123">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="658a2-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="658a2-124">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="658a2-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="658a2-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="658a2-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="658a2-126">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="658a2-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="658a2-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="658a2-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="658a2-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="658a2-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
