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
ms.openlocfilehash: 123eda65510263951895f9c7ac4c6b1781bbd5f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736698"
---
# <a name="igchost-interface"></a><span data-ttu-id="d4803-102">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4803-102">IGCHost Interface</span></span>
<span data-ttu-id="d4803-103">Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4803-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4803-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) değerlere bir çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerinden ayarlamak için yöntemi `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4803-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4803-105">Uzman kullanım arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d4803-105">This interface is for expert usage only.</span></span> <span data-ttu-id="d4803-106">Yanlış kullandıysanız, bir uygulamanın performansını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d4803-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4803-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4803-107">Methods</span></span>  
  
|<span data-ttu-id="d4803-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4803-108">Method</span></span>|<span data-ttu-id="d4803-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4803-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4803-110">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4803-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="d4803-111">Geçerli çöp toplama durumundan bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.</span><span class="sxs-lookup"><span data-stu-id="d4803-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="d4803-112">GetStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4803-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="d4803-113">İstatistikleri çöp toplama sistemi için geçerli durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="d4803-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="d4803-114">GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4803-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="d4803-115">Çöp toplama iş parçacığı başına istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="d4803-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="d4803-116">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4803-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="d4803-117">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d4803-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="d4803-118">SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4803-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="d4803-119">Çalışma zamanının sanal bellek en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d4803-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4803-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4803-120">Requirements</span></span>  
 <span data-ttu-id="d4803-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4803-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4803-122">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d4803-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d4803-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4803-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4803-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4803-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4803-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4803-125">See also</span></span>
- [<span data-ttu-id="d4803-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4803-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d4803-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="d4803-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
