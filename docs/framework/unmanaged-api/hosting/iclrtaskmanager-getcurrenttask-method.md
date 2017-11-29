---
title: ICLRTaskManager::GetCurrentTask Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1adf2959beb8687dc3d08ceb7a118bb19a5fa68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="c1431-102">ICLRTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="c1431-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="c1431-103">Alır [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) yöntem çağrısının kaynaklandığı işletim sistemi iş parçacığı üzerinde çalışmakta olan örneği.</span><span class="sxs-lookup"><span data-stu-id="c1431-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1431-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1431-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1431-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1431-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="c1431-106">[out] Adresine bir işaretçi bir `ICLRTask` çağrı kaynaklandığı işletim sistemi iş parçacığı üzerinde şu anda yürütülmekte örneği veya hiçbir görev şu anda bu iş parçacığında yürütüyor yoksa null.</span><span class="sxs-lookup"><span data-stu-id="c1431-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1431-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1431-107">Return Value</span></span>  
  
|<span data-ttu-id="c1431-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1431-108">HRESULT</span></span>|<span data-ttu-id="c1431-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1431-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1431-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1431-110">S_OK</span></span>|<span data-ttu-id="c1431-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c1431-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="c1431-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1431-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1431-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c1431-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1431-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1431-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1431-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c1431-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1431-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1431-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1431-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c1431-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1431-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1431-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1431-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c1431-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1431-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1431-120">E_FAIL</span></span>|<span data-ttu-id="c1431-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c1431-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1431-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1431-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1431-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1431-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1431-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1431-124">Remarks</span></span>  
 <span data-ttu-id="c1431-125">`ICLRTask` Örneğine `ppTask` parametresi şu anda yürütülen görev için temsil için CLR noktaları.</span><span class="sxs-lookup"><span data-stu-id="c1431-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="c1431-126">`ICLRTask` Örneğidir karşılık gelen ile ilişkili [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) ana bilgisayar için görev temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="c1431-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1431-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1431-127">Requirements</span></span>  
 <span data-ttu-id="c1431-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1431-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1431-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1431-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1431-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1431-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1431-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1431-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1431-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1431-132">See Also</span></span>  
 [<span data-ttu-id="c1431-133">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1431-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1431-134">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1431-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1431-135">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1431-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c1431-136">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1431-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
