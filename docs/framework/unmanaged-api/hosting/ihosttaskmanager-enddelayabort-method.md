---
description: ': IHostTaskManager:: EndDelayAbort Yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: e0d1c4231d381baf2ff92d187d33714f1c6f3003
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784567"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="e8f69-103">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8f69-103">IHostTaskManager::EndDelayAbort Method</span></span>

<span data-ttu-id="e8f69-104">Şu anda [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)' e daha önceki bir çağrıdan sonra, yönetilen kodun, geçerli görevin durdurulmadıkları dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e8f69-104">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f69-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8f69-105">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e8f69-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8f69-106">Return Value</span></span>  
  
|<span data-ttu-id="e8f69-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8f69-107">HRESULT</span></span>|<span data-ttu-id="e8f69-108">Description</span><span class="sxs-lookup"><span data-stu-id="e8f69-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8f69-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8f69-109">S_OK</span></span>|<span data-ttu-id="e8f69-110">`EndDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e8f69-110">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="e8f69-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8f69-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8f69-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e8f69-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8f69-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8f69-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8f69-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e8f69-114">The call timed out.</span></span>|  
|<span data-ttu-id="e8f69-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8f69-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8f69-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8f69-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8f69-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8f69-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8f69-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e8f69-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8f69-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8f69-119">E_FAIL</span></span>|<span data-ttu-id="e8f69-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e8f69-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8f69-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e8f69-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8f69-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8f69-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8f69-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="e8f69-123">E_UNEXPECTED</span></span>|<span data-ttu-id="e8f69-124">`EndDelayAbort` öğesine karşılık gelen bir çağrısı olmadan çağrıldı `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="e8f69-124">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f69-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8f69-125">Remarks</span></span>  

 <span data-ttu-id="e8f69-126">CLR `BeginDelayAbort` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="e8f69-126">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="e8f69-127">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED ' den döndürmelidir `EndDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e8f69-127">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8f69-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8f69-128">Requirements</span></span>  

 <span data-ttu-id="e8f69-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f69-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f69-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8f69-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8f69-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e8f69-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8f69-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f69-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f69-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8f69-133">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="e8f69-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8f69-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e8f69-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8f69-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e8f69-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8f69-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e8f69-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8f69-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
