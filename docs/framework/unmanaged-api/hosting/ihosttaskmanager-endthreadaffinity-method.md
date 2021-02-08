---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: Endthreadadffinity yöntemi'
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
ms.openlocfilehash: 0bbe42d8e14d20fb5be18fe7ebb266100ae72fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789430"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="22d8a-103">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22d8a-103">IHostTaskManager::EndThreadAffinity Method</span></span>

<span data-ttu-id="22d8a-104">Şu anda [IHostTaskManager:: Beginthreaerffinity](ihosttaskmanager-beginthreadaffinity-method.md)çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="22d8a-104">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d8a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="22d8a-105">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="22d8a-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22d8a-106">Return Value</span></span>  
  
|<span data-ttu-id="22d8a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22d8a-107">HRESULT</span></span>|<span data-ttu-id="22d8a-108">Description</span><span class="sxs-lookup"><span data-stu-id="22d8a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22d8a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="22d8a-109">S_OK</span></span>|<span data-ttu-id="22d8a-110">`EndThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="22d8a-110">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="22d8a-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22d8a-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22d8a-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="22d8a-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22d8a-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22d8a-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22d8a-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="22d8a-114">The call timed out.</span></span>|  
|<span data-ttu-id="22d8a-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22d8a-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22d8a-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="22d8a-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22d8a-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22d8a-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22d8a-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="22d8a-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22d8a-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22d8a-119">E_FAIL</span></span>|<span data-ttu-id="22d8a-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="22d8a-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22d8a-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22d8a-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22d8a-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="22d8a-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="22d8a-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="22d8a-123">E_UNEXPECTED</span></span>|<span data-ttu-id="22d8a-124">`EndThreadAffinity` daha önceden karşılık gelen bir çağrısı olmadan çağrıldı `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="22d8a-124">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d8a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22d8a-125">Remarks</span></span>  

 <span data-ttu-id="22d8a-126">CLR `BeginThreadAffinity` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="22d8a-126">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="22d8a-127">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED döndürmelidir ve hiçbir işlem almaz.</span><span class="sxs-lookup"><span data-stu-id="22d8a-127">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d8a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22d8a-128">Requirements</span></span>  

 <span data-ttu-id="22d8a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d8a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d8a-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22d8a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22d8a-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="22d8a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d8a-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d8a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d8a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22d8a-133">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="22d8a-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22d8a-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="22d8a-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22d8a-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="22d8a-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22d8a-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="22d8a-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22d8a-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
