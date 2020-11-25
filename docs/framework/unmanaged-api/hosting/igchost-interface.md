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
ms.openlocfilehash: 8965797321e68443c01d05f97d147f2320a76739
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724305"
---
# <a name="igchost-interface"></a><span data-ttu-id="9ec52-102">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ec52-102">IGCHost Interface</span></span>

<span data-ttu-id="9ec52-103">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ec52-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ec52-104">4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınırdan daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ec52-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ec52-105">Bu arabirim yalnızca uzman kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="9ec52-105">This interface is for expert usage only.</span></span> <span data-ttu-id="9ec52-106">Yanlış kullanılırsa, bir uygulamanın performansını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9ec52-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ec52-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9ec52-107">Methods</span></span>  
  
|<span data-ttu-id="9ec52-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9ec52-108">Method</span></span>|<span data-ttu-id="9ec52-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ec52-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ec52-110">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec52-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="9ec52-111">Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="9ec52-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="9ec52-112">GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="9ec52-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="9ec52-113">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="9ec52-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="9ec52-114">GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec52-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="9ec52-115">Çöp toplama için iş parçacığı başına istatistikleri alır.</span><span class="sxs-lookup"><span data-stu-id="9ec52-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="9ec52-116">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec52-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="9ec52-117">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9ec52-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="9ec52-118">SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec52-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="9ec52-119">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9ec52-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ec52-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ec52-120">Requirements</span></span>  

 <span data-ttu-id="9ec52-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec52-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec52-122">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="9ec52-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9ec52-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9ec52-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ec52-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec52-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec52-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec52-125">See also</span></span>

- [<span data-ttu-id="9ec52-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9ec52-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9ec52-127">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="9ec52-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
