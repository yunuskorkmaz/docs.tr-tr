---
title: IHostTaskManager::EndThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: c40febb78c1bc78a5a724f559eb95869e90bdad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133081"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="903b0-102">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="903b0-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="903b0-103">Şu anda [IHostTaskManager:: Beginthreaerffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="903b0-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="903b0-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="903b0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="903b0-105">Return Value</span></span>  
  
|<span data-ttu-id="903b0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="903b0-106">HRESULT</span></span>|<span data-ttu-id="903b0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="903b0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="903b0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="903b0-108">S_OK</span></span>|<span data-ttu-id="903b0-109">`EndThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="903b0-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="903b0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="903b0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="903b0-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="903b0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="903b0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="903b0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="903b0-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="903b0-113">The call timed out.</span></span>|  
|<span data-ttu-id="903b0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="903b0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="903b0-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="903b0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="903b0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="903b0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="903b0-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="903b0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="903b0-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="903b0-118">E_FAIL</span></span>|<span data-ttu-id="903b0-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="903b0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="903b0-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="903b0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="903b0-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="903b0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="903b0-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="903b0-122">E_UNEXPECTED</span></span>|<span data-ttu-id="903b0-123">`EndThreadAffinity`, `BeginThreadAffinity`daha önce karşılık gelen bir çağrı olmadan çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="903b0-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="903b0-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="903b0-124">Remarks</span></span>  
 <span data-ttu-id="903b0-125">CLR, `EndThreadAffinity`çağrılmadan önce geçerli görevde `BeginThreadAffinity` için karşılık gelen bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="903b0-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="903b0-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED döndürmelidir ve hiçbir işlem almaz.</span><span class="sxs-lookup"><span data-stu-id="903b0-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="903b0-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="903b0-127">Requirements</span></span>  
 <span data-ttu-id="903b0-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="903b0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="903b0-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="903b0-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="903b0-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="903b0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="903b0-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="903b0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903b0-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="903b0-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="903b0-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="903b0-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="903b0-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="903b0-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="903b0-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="903b0-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="903b0-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="903b0-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
