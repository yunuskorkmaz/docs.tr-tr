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
ms.openlocfilehash: 676a1d50202333203c13fcf916dbb14a6d91fb8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121439"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="1dc6b-102">IHostSecurityManager::SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="1dc6b-103">Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc6b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc6b-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="1dc6b-106">'ndaki Ortak dil çalışma zamanının (CLR) konağa ne tür bir içerik yerleştirmekte olduğunu gösteren [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="1dc6b-107">dışı Yeni bir [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dc6b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1dc6b-108">Return Value</span></span>  
  
|<span data-ttu-id="1dc6b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dc6b-109">HRESULT</span></span>|<span data-ttu-id="1dc6b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dc6b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dc6b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dc6b-111">S_OK</span></span>|<span data-ttu-id="1dc6b-112">`SetSecurityContext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="1dc6b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dc6b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dc6b-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dc6b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dc6b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dc6b-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-116">The call timed out.</span></span>|  
|<span data-ttu-id="1dc6b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dc6b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dc6b-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dc6b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dc6b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dc6b-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dc6b-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1dc6b-121">E_FAIL</span></span>|<span data-ttu-id="1dc6b-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dc6b-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dc6b-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dc6b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dc6b-125">Remarks</span></span>  
 <span data-ttu-id="1dc6b-126">CLR, çeşitli senaryolarda `SetSecurityContext` çağırır.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="1dc6b-127">Sınıfı ve modül oluşturucularını ve sonlandırıcıları yürütmeden önce CLR, Konağı yürütme hatalarından korumak için `SetSecurityContext` çağırır.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="1dc6b-128">Daha sonra, `SetSecurityContext`için başka bir çağrı kullanarak, oluşturucunun veya sonlandırıcının yürütülmesi sonrasında güvenlik bağlamını özgün durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="1dc6b-129">G/ç tamamlanırken benzer bir model oluşur.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="1dc6b-130">Ana bilgisayar [ıhostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)'ı uygularsa, ana bilgisayar [ıclriocompletionmanager:: ONTAMAMLANMıŞ öğesini çağırarak](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)clr `SetSecurityContext` çağırır.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="1dc6b-131">Çalışan iş parçacıklarının zaman uyumsuz noktalarında, CLR, konak veya CLR 'nin iş parçacığı havuzunu uygulamadığına bağlı olarak <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> veya [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)içinde `SetSecurityContext` çağırır.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc6b-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc6b-132">Requirements</span></span>  
 <span data-ttu-id="1dc6b-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc6b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc6b-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1dc6b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dc6b-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1dc6b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dc6b-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc6b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc6b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="1dc6b-138">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="1dc6b-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1dc6b-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1dc6b-141">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="1dc6b-142">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="1dc6b-143">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc6b-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
