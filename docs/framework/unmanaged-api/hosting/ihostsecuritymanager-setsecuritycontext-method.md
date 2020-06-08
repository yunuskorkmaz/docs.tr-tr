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
ms.openlocfilehash: 6a6b4d0351e22026dc873aad8281d0259d871a14
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501488"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="4e32c-102">IHostSecurityManager::SetSecurityContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e32c-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="4e32c-103">Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4e32c-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e32c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e32c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e32c-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="4e32c-106">'ndaki Ortak dil çalışma zamanının (CLR) konağa ne tür bir içerik yerleştirmekte olduğunu gösteren [EContextType](econtexttype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="4e32c-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="4e32c-107">dışı Yeni bir [IHostSecurityContext](ihostsecuritycontext-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e32c-107">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e32c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e32c-108">Return Value</span></span>  
  
|<span data-ttu-id="4e32c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e32c-109">HRESULT</span></span>|<span data-ttu-id="4e32c-110">Description</span><span class="sxs-lookup"><span data-stu-id="4e32c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e32c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e32c-111">S_OK</span></span>|<span data-ttu-id="4e32c-112">`SetSecurityContext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4e32c-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="4e32c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4e32c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4e32c-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4e32c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4e32c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4e32c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4e32c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4e32c-116">The call timed out.</span></span>|  
|<span data-ttu-id="4e32c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e32c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4e32c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e32c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4e32c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4e32c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4e32c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4e32c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4e32c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4e32c-121">E_FAIL</span></span>|<span data-ttu-id="4e32c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4e32c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4e32c-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4e32c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4e32c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e32c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e32c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e32c-125">Remarks</span></span>  
 <span data-ttu-id="4e32c-126">`SetSecurityContext`Çeşitli SENARYOLARDA clr çağrıları.</span><span class="sxs-lookup"><span data-stu-id="4e32c-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="4e32c-127">Sınıfı ve modül oluşturucularını ve sonlandırıcıları yürütmeden önce CLR, `SetSecurityContext` Konağı yürütme hatalarından korumak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="4e32c-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="4e32c-128">Daha sonra, başka bir çağrısı kullanarak, oluşturucunun veya sonlandırıcının yürütülmesi sonrasında güvenlik bağlamını özgün durumuna sıfırlar `SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="4e32c-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="4e32c-129">G/ç tamamlanırken benzer bir model oluşur.</span><span class="sxs-lookup"><span data-stu-id="4e32c-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="4e32c-130">Ana bilgisayar [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md)'ı uygularsa, `SetSecurityContext` ana bilgisayar [ıclriocompletionmanager:: ONTAMAMLANMıŞTıR](iclriocompletionmanager-oncomplete-method.md)öğesini çağırarak clr çağrıları.</span><span class="sxs-lookup"><span data-stu-id="4e32c-130">If the host implements [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="4e32c-131">Çalışan iş parçacıklarında zaman uyumsuz noktalarda, CLR 'nin `SetSecurityContext` veya <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> clr 'nin iş parçacığı havuzunu yapıp uygulamadığına bağlı olarak [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)içindeki veya içinde clr çağrıları.</span><span class="sxs-lookup"><span data-stu-id="4e32c-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e32c-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e32c-132">Requirements</span></span>  
 <span data-ttu-id="4e32c-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e32c-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e32c-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e32c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e32c-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4e32c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e32c-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e32c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e32c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e32c-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="4e32c-138">EContextType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4e32c-138">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="4e32c-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4e32c-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="4e32c-141">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-141">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="4e32c-142">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-142">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="4e32c-143">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e32c-143">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
