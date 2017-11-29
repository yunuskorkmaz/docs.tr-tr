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
ms.openlocfilehash: df1f688ec3f58ae7317a4fed0dd70cffc1647045
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="7b6ef-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="7b6ef-103">Ortak dil çalışma zamanı (CLR) geçerli tarafından temsil edilen görev iptal etmek için bildirir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) hemen ve koşulsuz olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="7b6ef-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b6ef-105">Return Value</span></span>  
  
|<span data-ttu-id="7b6ef-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b6ef-106">HRESULT</span></span>|<span data-ttu-id="7b6ef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b6ef-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b6ef-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b6ef-108">S_OK</span></span>|<span data-ttu-id="7b6ef-109">`RudeAbort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="7b6ef-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b6ef-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b6ef-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b6ef-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b6ef-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b6ef-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-113">The call timed out.</span></span>|  
|<span data-ttu-id="7b6ef-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b6ef-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b6ef-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b6ef-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b6ef-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b6ef-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b6ef-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b6ef-118">E_FAIL</span></span>|<span data-ttu-id="7b6ef-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b6ef-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b6ef-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b6ef-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b6ef-122">Remarks</span></span>  
 <span data-ttu-id="7b6ef-123">Bir konak çağırır `RudeAbort` görev hemen durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="7b6ef-124">Sonlandırıcılar ve özel durum işleme rutinleri yürütülecek garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b6ef-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b6ef-125">Requirements</span></span>  
 <span data-ttu-id="7b6ef-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b6ef-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b6ef-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b6ef-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b6ef-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7b6ef-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b6ef-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b6ef-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6ef-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b6ef-130">See Also</span></span>  
 [<span data-ttu-id="7b6ef-131">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7b6ef-132">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7b6ef-133">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7b6ef-134">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b6ef-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
