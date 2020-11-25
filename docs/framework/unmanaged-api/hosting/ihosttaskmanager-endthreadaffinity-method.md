---
title: IHostTaskManager::EndThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: c662e242cf6745223b1e87716ce4f64971347d2a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731663"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="68493-102">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68493-102">IHostTaskManager::EndThreadAffinity Method</span></span>

<span data-ttu-id="68493-103">Şu anda [IHostTaskManager:: Beginthreaerffinity](ihosttaskmanager-beginthreadaffinity-method.md)çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="68493-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68493-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="68493-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="68493-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68493-105">Return Value</span></span>  
  
|<span data-ttu-id="68493-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68493-106">HRESULT</span></span>|<span data-ttu-id="68493-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68493-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68493-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="68493-108">S_OK</span></span>|<span data-ttu-id="68493-109">`EndThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="68493-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="68493-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68493-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68493-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="68493-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68493-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68493-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68493-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="68493-113">The call timed out.</span></span>|  
|<span data-ttu-id="68493-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68493-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68493-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="68493-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68493-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68493-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68493-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="68493-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68493-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68493-118">E_FAIL</span></span>|<span data-ttu-id="68493-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="68493-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68493-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="68493-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68493-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="68493-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="68493-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="68493-122">E_UNEXPECTED</span></span>|<span data-ttu-id="68493-123">`EndThreadAffinity` daha önceden karşılık gelen bir çağrısı olmadan çağrıldı `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="68493-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68493-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68493-124">Remarks</span></span>  

 <span data-ttu-id="68493-125">CLR `BeginThreadAffinity` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="68493-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="68493-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED döndürmelidir ve hiçbir işlem almaz.</span><span class="sxs-lookup"><span data-stu-id="68493-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68493-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68493-127">Requirements</span></span>  

 <span data-ttu-id="68493-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68493-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68493-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68493-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68493-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="68493-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68493-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68493-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68493-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68493-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="68493-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68493-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="68493-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68493-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="68493-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68493-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="68493-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68493-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
