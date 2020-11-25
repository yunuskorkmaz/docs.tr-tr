---
title: IHostTaskManager::EndDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: 6add3cf4d83796b2d95de46cb64f5880a835b6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731676"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="ac46e-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac46e-102">IHostTaskManager::EndDelayAbort Method</span></span>

<span data-ttu-id="ac46e-103">Şu anda [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)' e daha önceki bir çağrıdan sonra, yönetilen kodun, geçerli görevin durdurulmadıkları dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ac46e-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac46e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac46e-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ac46e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac46e-105">Return Value</span></span>  
  
|<span data-ttu-id="ac46e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac46e-106">HRESULT</span></span>|<span data-ttu-id="ac46e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac46e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac46e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac46e-108">S_OK</span></span>|<span data-ttu-id="ac46e-109">`EndDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac46e-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="ac46e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac46e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac46e-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ac46e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac46e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac46e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac46e-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac46e-113">The call timed out.</span></span>|  
|<span data-ttu-id="ac46e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac46e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac46e-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac46e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac46e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac46e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac46e-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ac46e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac46e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac46e-118">E_FAIL</span></span>|<span data-ttu-id="ac46e-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac46e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac46e-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac46e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac46e-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac46e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac46e-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="ac46e-122">E_UNEXPECTED</span></span>|<span data-ttu-id="ac46e-123">`EndDelayAbort` öğesine karşılık gelen bir çağrısı olmadan çağrıldı `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="ac46e-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac46e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac46e-124">Remarks</span></span>  

 <span data-ttu-id="ac46e-125">CLR `BeginDelayAbort` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="ac46e-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="ac46e-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED ' den döndürmelidir `EndDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ac46e-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac46e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac46e-127">Requirements</span></span>  

 <span data-ttu-id="ac46e-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac46e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac46e-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac46e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac46e-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ac46e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac46e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac46e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac46e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac46e-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="ac46e-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac46e-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ac46e-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac46e-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ac46e-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac46e-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ac46e-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac46e-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
