---
title: "ICLRTask::Abort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e417e329b38c8f57dedf2926c0d6ff02a0170f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="6b31f-102">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b31f-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="6b31f-103">Ortak dil çalışma zamanı (CLR) görevi iptal isteklerini, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6b31f-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b31f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b31f-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6b31f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b31f-105">Return Value</span></span>  
  
|<span data-ttu-id="6b31f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b31f-106">HRESULT</span></span>|<span data-ttu-id="6b31f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b31f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b31f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b31f-108">S_OK</span></span>|<span data-ttu-id="6b31f-109">`Abort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6b31f-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="6b31f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b31f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b31f-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6b31f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b31f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b31f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b31f-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6b31f-113">The call timed out.</span></span>|  
|<span data-ttu-id="6b31f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b31f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b31f-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="6b31f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b31f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b31f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b31f-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="6b31f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b31f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b31f-118">E_FAIL</span></span>|<span data-ttu-id="6b31f-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6b31f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b31f-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6b31f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b31f-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b31f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b31f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b31f-122">Remarks</span></span>  
 <span data-ttu-id="6b31f-123">CLR başlatır bir <xref:System.Threading.ThreadAbortException> konak çağırdığında `Abort`.</span><span class="sxs-lookup"><span data-stu-id="6b31f-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="6b31f-124">Hemen özel durum bilgilerini, sonlandırıcılar veya özel durum mekanizmaları işleme yürütülecek gibi kullanıcı kodu beklemeden başlatıldıktan sonra döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b31f-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="6b31f-125">Çağrılar `Abort` böylece hızlı bir şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b31f-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b31f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b31f-126">Requirements</span></span>  
 <span data-ttu-id="6b31f-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b31f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b31f-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b31f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b31f-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6b31f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b31f-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b31f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b31f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b31f-131">See Also</span></span>  
 [<span data-ttu-id="6b31f-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b31f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6b31f-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b31f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6b31f-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b31f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6b31f-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b31f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
