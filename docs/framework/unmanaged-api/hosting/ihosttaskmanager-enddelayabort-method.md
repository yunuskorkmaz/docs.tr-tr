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
ms.openlocfilehash: 156626ce907c13987c0cca15016263291961037d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841982"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="089d4-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="089d4-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="089d4-103">Şu anda [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)' e daha önceki bir çağrıdan sonra, yönetilen kodun, geçerli görevin durdurulmadıkları dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="089d4-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="089d4-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="089d4-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="089d4-105">Return Value</span></span>  
  
|<span data-ttu-id="089d4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="089d4-106">HRESULT</span></span>|<span data-ttu-id="089d4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="089d4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="089d4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="089d4-108">S_OK</span></span>|<span data-ttu-id="089d4-109">`EndDelayAbort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="089d4-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="089d4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="089d4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="089d4-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="089d4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="089d4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="089d4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="089d4-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="089d4-113">The call timed out.</span></span>|  
|<span data-ttu-id="089d4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="089d4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="089d4-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="089d4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="089d4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="089d4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="089d4-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="089d4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="089d4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="089d4-118">E_FAIL</span></span>|<span data-ttu-id="089d4-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="089d4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="089d4-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="089d4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="089d4-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="089d4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="089d4-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="089d4-122">E_UNEXPECTED</span></span>|<span data-ttu-id="089d4-123">`EndDelayAbort`öğesine karşılık gelen bir çağrısı olmadan çağrıldı `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="089d4-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="089d4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="089d4-124">Remarks</span></span>  
 <span data-ttu-id="089d4-125">CLR `BeginDelayAbort` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="089d4-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="089d4-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED ' den döndürmelidir `EndDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="089d4-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="089d4-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="089d4-127">Requirements</span></span>  
 <span data-ttu-id="089d4-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="089d4-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089d4-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="089d4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="089d4-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="089d4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="089d4-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089d4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089d4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="089d4-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="089d4-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="089d4-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="089d4-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="089d4-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="089d4-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="089d4-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="089d4-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="089d4-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
