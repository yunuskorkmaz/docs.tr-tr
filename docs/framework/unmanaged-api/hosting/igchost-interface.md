---
description: 'Daha fazla bilgi edinin: IGCHost Arabirimi'
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
ms.openlocfilehash: 73b1125eb66a38373da85769ab80ddcaf0b955c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709600"
---
# <a name="igchost-interface"></a><span data-ttu-id="cdbc0-103">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-103">IGCHost Interface</span></span>

<span data-ttu-id="cdbc0-104">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdbc0-105">4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınırdan daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-105">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdbc0-106">Bu arabirim yalnızca uzman kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-106">This interface is for expert usage only.</span></span> <span data-ttu-id="cdbc0-107">Yanlış kullanılırsa, bir uygulamanın performansını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-107">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cdbc0-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cdbc0-108">Methods</span></span>  
  
|<span data-ttu-id="cdbc0-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cdbc0-109">Method</span></span>|<span data-ttu-id="cdbc0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdbc0-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cdbc0-111">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-111">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="cdbc0-112">Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-112">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="cdbc0-113">GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="cdbc0-113">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="cdbc0-114">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-114">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="cdbc0-115">GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-115">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="cdbc0-116">Çöp toplama için iş parçacığı başına istatistikleri alır.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-116">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="cdbc0-117">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-117">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="cdbc0-118">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-118">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="cdbc0-119">SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-119">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="cdbc0-120">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-120">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdbc0-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdbc0-121">Requirements</span></span>  

 <span data-ttu-id="cdbc0-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbc0-123">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="cdbc0-123">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cdbc0-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cdbc0-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbc0-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbc0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbc0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdbc0-126">See also</span></span>

- [<span data-ttu-id="cdbc0-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cdbc0-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="cdbc0-128">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="cdbc0-128">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
