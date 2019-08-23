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
ms.openlocfilehash: 76d1071ddde1509f16fd786afa4c05c05224d051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966218"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="86c12-102">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86c12-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="86c12-103">Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c12-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86c12-104">4,5 .NET Framework başlayarak, [ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu 0 ' dan `DWORD`dahabüyükdeğerlereayarlayın. [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınır.</span><span class="sxs-lookup"><span data-stu-id="86c12-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86c12-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="86c12-105">Methods</span></span>  
  
|<span data-ttu-id="86c12-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="86c12-106">Method</span></span>|<span data-ttu-id="86c12-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86c12-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86c12-108">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86c12-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="86c12-109">Belirtilen oluşturma için bir çöp toplamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="86c12-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="86c12-110">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86c12-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="86c12-111">Çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="86c12-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="86c12-112">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86c12-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="86c12-113">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86c12-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86c12-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86c12-114">Remarks</span></span>  
 <span data-ttu-id="86c12-115">Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen <xref:System.GC> türle uygular.</span><span class="sxs-lookup"><span data-stu-id="86c12-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="86c12-116">Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="86c12-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c12-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86c12-117">Requirements</span></span>  
 <span data-ttu-id="86c12-118">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c12-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c12-119">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86c12-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86c12-120">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="86c12-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86c12-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c12-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c12-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c12-122">See also</span></span>

- [<span data-ttu-id="86c12-123">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="86c12-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="86c12-124">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="86c12-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="86c12-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86c12-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="86c12-126">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86c12-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="86c12-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86c12-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="86c12-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="86c12-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
