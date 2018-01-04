---
title: "ICLRTask::RudeAbort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.RudeAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="52bf6-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52bf6-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="52bf6-103">Ortak dil çalışma zamanı (CLR) geçerli tarafından temsil edilen görev iptal etmek için bildirir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) hemen ve koşulsuz olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="52bf6-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bf6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52bf6-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="52bf6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52bf6-105">Return Value</span></span>  
  
|<span data-ttu-id="52bf6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52bf6-106">HRESULT</span></span>|<span data-ttu-id="52bf6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52bf6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52bf6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="52bf6-108">S_OK</span></span>|<span data-ttu-id="52bf6-109">`RudeAbort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="52bf6-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="52bf6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52bf6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52bf6-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="52bf6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52bf6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52bf6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52bf6-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="52bf6-113">The call timed out.</span></span>|  
|<span data-ttu-id="52bf6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52bf6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52bf6-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="52bf6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52bf6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52bf6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52bf6-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="52bf6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52bf6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52bf6-118">E_FAIL</span></span>|<span data-ttu-id="52bf6-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="52bf6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52bf6-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="52bf6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52bf6-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="52bf6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52bf6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52bf6-122">Remarks</span></span>  
 <span data-ttu-id="52bf6-123">Bir konak çağırır `RudeAbort` görev hemen durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="52bf6-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="52bf6-124">Sonlandırıcılar ve özel durum işleme rutinleri yürütülecek garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="52bf6-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52bf6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52bf6-125">Requirements</span></span>  
 <span data-ttu-id="52bf6-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52bf6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52bf6-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52bf6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52bf6-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="52bf6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52bf6-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52bf6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bf6-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52bf6-130">See Also</span></span>  
 [<span data-ttu-id="52bf6-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52bf6-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="52bf6-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52bf6-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="52bf6-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52bf6-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="52bf6-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52bf6-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
