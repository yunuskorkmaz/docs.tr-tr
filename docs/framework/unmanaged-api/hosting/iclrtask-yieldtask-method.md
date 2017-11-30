---
title: "ICLRTask::YieldTask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.YieldTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a02a69329958593aec546ca9c60e3d201ce2a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="4684a-102">ICLRTask::YieldTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4684a-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="4684a-103">Ortak dil çalışma zamanı (CLR) kenara görev put isteği, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder ve işlemci zamanı diğer görevler için kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="4684a-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4684a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4684a-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4684a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4684a-105">Return Value</span></span>  
  
|<span data-ttu-id="4684a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4684a-106">HRESULT</span></span>|<span data-ttu-id="4684a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4684a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4684a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4684a-108">S_OK</span></span>|<span data-ttu-id="4684a-109">`YieldTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4684a-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="4684a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4684a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4684a-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4684a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4684a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4684a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4684a-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4684a-113">The call timed out.</span></span>|  
|<span data-ttu-id="4684a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4684a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4684a-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4684a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4684a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4684a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4684a-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4684a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4684a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4684a-118">E_FAIL</span></span>|<span data-ttu-id="4684a-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4684a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4684a-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4684a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4684a-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4684a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4684a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4684a-122">Remarks</span></span>  
 <span data-ttu-id="4684a-123">Bir konak çağırır `YieldTask` için diğer görevlerin veya işlemlerin isteği işlemci kaynakları.</span><span class="sxs-lookup"><span data-stu-id="4684a-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="4684a-124">Bu yöntem, öncelikle CPU süresi vermek uzun süre çalışan kod sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4684a-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="4684a-125">Çalışma zamanı görev put dener, geçerli `ICLRTask` örneği burada işleme süresi sağlayabilen, ancak başarı garanti etmez bir durumda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4684a-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4684a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4684a-126">Requirements</span></span>  
 <span data-ttu-id="4684a-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4684a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4684a-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4684a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4684a-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4684a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4684a-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4684a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4684a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4684a-131">See Also</span></span>  
 [<span data-ttu-id="4684a-132">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="4684a-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4684a-133">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4684a-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4684a-134">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="4684a-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4684a-135">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4684a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
