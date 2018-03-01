---
title: "ICLRTask::ExitTask Yöntemi"
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
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff2adafa41ce68a824f6b01888c3565bf054c031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="43820-102">ICLRTask::ExitTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43820-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="43820-103">Geçerli görev temsil ortak dil çalışma zamanı (CLR) bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği sona eriyor ve görev düzgün biçimde kapatılamadı dener.</span><span class="sxs-lookup"><span data-stu-id="43820-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43820-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43820-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43820-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43820-105">Return Value</span></span>  
  
|<span data-ttu-id="43820-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43820-106">HRESULT</span></span>|<span data-ttu-id="43820-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43820-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43820-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="43820-108">S_OK</span></span>|<span data-ttu-id="43820-109">`ExitTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="43820-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="43820-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43820-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43820-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="43820-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43820-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43820-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43820-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="43820-113">The call timed out.</span></span>|  
|<span data-ttu-id="43820-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43820-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43820-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="43820-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43820-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43820-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43820-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="43820-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43820-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43820-118">E_FAIL</span></span>|<span data-ttu-id="43820-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="43820-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43820-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43820-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43820-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="43820-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43820-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43820-122">Remarks</span></span>  
 <span data-ttu-id="43820-123">`ExitTask`bir iş parçacığı bir yönetilmeyen tür kitaplığından ayırmak için benzer bir şekilde bir görevin temiz kapatma çalışır.</span><span class="sxs-lookup"><span data-stu-id="43820-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43820-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43820-124">Requirements</span></span>  
 <span data-ttu-id="43820-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43820-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43820-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43820-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43820-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="43820-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43820-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43820-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43820-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43820-129">See Also</span></span>  
 [<span data-ttu-id="43820-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43820-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="43820-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43820-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="43820-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43820-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="43820-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43820-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
