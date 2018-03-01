---
title: "IHostSecurityManager::SetSecurityContext Yöntemi"
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
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29a7652e20c08b9de584a9e11ac343ad92f40653
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="c1dfd-102">IHostSecurityManager::SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="c1dfd-103">Şu anda yürütülen iş parçacığı güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1dfd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1dfd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1dfd-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="c1dfd-106">[in] Aşağıdakilerden birini [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerleri, konakta yerleştirme ne ortak dil çalışma zamanı (CLR) bağlamında türünü gösteren.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="c1dfd-107">[out] Yeni bir adresini gösteren bir işaretçi [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1dfd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1dfd-108">Return Value</span></span>  
  
|<span data-ttu-id="c1dfd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1dfd-109">HRESULT</span></span>|<span data-ttu-id="c1dfd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1dfd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1dfd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1dfd-111">S_OK</span></span>|<span data-ttu-id="c1dfd-112">`SetSecurityContext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="c1dfd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1dfd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1dfd-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1dfd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1dfd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1dfd-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-116">The call timed out.</span></span>|  
|<span data-ttu-id="c1dfd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1dfd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1dfd-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1dfd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1dfd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1dfd-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1dfd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1dfd-121">E_FAIL</span></span>|<span data-ttu-id="c1dfd-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1dfd-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1dfd-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1dfd-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1dfd-125">Remarks</span></span>  
 <span data-ttu-id="c1dfd-126">CLR çağrıları `SetSecurityContext` çeşitli senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="c1dfd-127">Sınıf ve modül oluşturucular ve sonlandırıcılar yürütülmeden önce CLR çağırır `SetSecurityContext` konak yürütme arızasına karşı korumak için.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="c1dfd-128">Bunu daha sonra güvenlik bağlamı özgün durumuna geri oluşturucunun ya da sonlandırıcıyı, yürütme sonrasında başka bir çağrıyı kullanarak sıfırlar `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="c1dfd-129">Benzer bir desen ile g/ç tamamlama oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="c1dfd-130">Ana bilgisayar uyguluyorsa [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), CLR çağrıları `SetSecurityContext` konak çağrıları sonra [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="c1dfd-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="c1dfd-131">Çalışan iş parçacığı içinde zaman uyumsuz noktalarda CLR çağırır `SetSecurityContext` içinde <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> veya içinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)olup iş parçacığı havuzu ana bilgisayar veya CLR uygulamaya bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1dfd-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1dfd-132">Requirements</span></span>  
 <span data-ttu-id="c1dfd-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1dfd-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1dfd-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1dfd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1dfd-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1dfd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1dfd-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1dfd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1dfd-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="c1dfd-138">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="c1dfd-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c1dfd-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="c1dfd-141">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="c1dfd-142">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="c1dfd-143">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1dfd-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
