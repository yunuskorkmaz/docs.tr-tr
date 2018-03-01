---
title: "IHostTaskManager::EndThreadAffinity Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b12bdc16d70b9e4ccaecbee1b8bcd4e8f05d59dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="19b14-102">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19b14-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="19b14-103">Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev değil taşınması gerekir başka bir işletim sistemi iş parçacığına dönemi çıkıyor bildirir [Ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="19b14-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19b14-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="19b14-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="19b14-105">Return Value</span></span>  
  
|<span data-ttu-id="19b14-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19b14-106">HRESULT</span></span>|<span data-ttu-id="19b14-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b14-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19b14-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="19b14-108">S_OK</span></span>|<span data-ttu-id="19b14-109">`EndThreadAffinity`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="19b14-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="19b14-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19b14-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19b14-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="19b14-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19b14-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19b14-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19b14-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="19b14-113">The call timed out.</span></span>|  
|<span data-ttu-id="19b14-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19b14-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19b14-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="19b14-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19b14-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19b14-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19b14-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="19b14-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19b14-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19b14-118">E_FAIL</span></span>|<span data-ttu-id="19b14-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="19b14-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19b14-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19b14-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19b14-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="19b14-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19b14-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="19b14-122">E_UNEXPECTED</span></span>|<span data-ttu-id="19b14-123">`EndThreadAffinity`Önceki karşılık gelen bir arama olmadan çağrıldı `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="19b14-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19b14-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19b14-124">Remarks</span></span>  
 <span data-ttu-id="19b14-125">CLR karşılık gelen çağrıyı yapar `BeginThreadAffinity` çağırmadan önce geçerli görevin üzerinde `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="19b14-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="19b14-126">Böyle bir karşılık gelen çağrısı olmadığında ana bilgisayarın uyarlamasını [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED dönün ve eylem yok.</span><span class="sxs-lookup"><span data-stu-id="19b14-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19b14-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19b14-127">Requirements</span></span>  
 <span data-ttu-id="19b14-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19b14-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19b14-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19b14-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19b14-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="19b14-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19b14-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19b14-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b14-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19b14-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="19b14-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19b14-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="19b14-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19b14-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="19b14-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19b14-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="19b14-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19b14-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
