---
title: IHostSecurityManager::SetSecurityContext Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41b472d96c4db088c7ab34d9abb0940f3461c844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734561"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="9e4de-102">IHostSecurityManager::SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e4de-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="9e4de-103">Yürütülmekte olan iş parçacığını güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e4de-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e4de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e4de-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="9e4de-106">[in] Aşağıdakilerden birini [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerleri, konakta yerleştirme ortak dil çalışma zamanı (CLR) bağlamında ne tür belirten.</span><span class="sxs-lookup"><span data-stu-id="9e4de-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="9e4de-107">[out] Yeni bir adresini bir işaretçiye [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="9e4de-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e4de-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e4de-108">Return Value</span></span>  
  
|<span data-ttu-id="9e4de-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e4de-109">HRESULT</span></span>|<span data-ttu-id="9e4de-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e4de-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e4de-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e4de-111">S_OK</span></span>|<span data-ttu-id="9e4de-112">`SetSecurityContext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9e4de-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="9e4de-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e4de-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e4de-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9e4de-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e4de-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e4de-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e4de-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9e4de-116">The call timed out.</span></span>|  
|<span data-ttu-id="9e4de-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e4de-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e4de-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9e4de-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e4de-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e4de-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e4de-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="9e4de-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e4de-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e4de-121">E_FAIL</span></span>|<span data-ttu-id="9e4de-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e4de-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e4de-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e4de-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e4de-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e4de-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e4de-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e4de-125">Remarks</span></span>  
 <span data-ttu-id="9e4de-126">CLR çağrıları `SetSecurityContext` çeşitli senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="9e4de-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="9e4de-127">Sınıf ve modül oluşturucular ve sonlandırıcılar yürütülmeden önce CLR çağırır `SetSecurityContext` konak yürütme arızasına karşı korumak için.</span><span class="sxs-lookup"><span data-stu-id="9e4de-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="9e4de-128">Ardından güvenlik bağlamı özgün durumuna oluşturucu veya sonlandırıcının yürütülmesini sonra başka bir çağrısını kullanarak sıfırlar `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="9e4de-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="9e4de-129">Benzer bir desen ile g/ç tamamlama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9e4de-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="9e4de-130">Konak uyguluyorsa [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), CLR çağrıları `SetSecurityContext` konak çağırdıktan sonra [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="9e4de-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="9e4de-131">CLR çalışan iş parçacığı zaman uyumsuz noktalarda, çağıran `SetSecurityContext` içinde <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> veya içinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)olup iş parçacığı havuzu konak veya CLR uygulama bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="9e4de-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e4de-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e4de-132">Requirements</span></span>  
 <span data-ttu-id="9e4de-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e4de-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e4de-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e4de-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e4de-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9e4de-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e4de-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e4de-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4de-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e4de-137">See also</span></span>
- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="9e4de-138">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9e4de-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="9e4de-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9e4de-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="9e4de-141">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="9e4de-142">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="9e4de-143">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e4de-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
