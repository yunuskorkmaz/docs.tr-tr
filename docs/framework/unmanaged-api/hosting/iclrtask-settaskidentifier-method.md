---
title: ICLRTask::SetTaskIdentifier Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a561c54f2d004d073fdfffffdb59cb2b5189e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435686"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="cc550-102">ICLRTask::SetTaskIdentifier Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc550-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="cc550-103">Ortak dil çalışma zamanı (CLR) belirtilen tanımlayıcı değeri geçerli tarafından temsil edilen görev ilişkilendirmek için bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="cc550-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc550-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc550-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc550-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc550-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="cc550-106">[in] Geçerli tarafından temsil edilen görev ilişkilendirmek ortak dil çalışma zamanı için benzersiz tanımlayıcı `ICLRTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="cc550-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc550-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc550-107">Return Value</span></span>  
  
|<span data-ttu-id="cc550-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc550-108">HRESULT</span></span>|<span data-ttu-id="cc550-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc550-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc550-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc550-110">S_OK</span></span>|<span data-ttu-id="cc550-111">`SetTaskIdentifier` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cc550-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="cc550-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc550-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc550-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cc550-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc550-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc550-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc550-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cc550-115">The call timed out.</span></span>|  
|<span data-ttu-id="cc550-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc550-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc550-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="cc550-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc550-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc550-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc550-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="cc550-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc550-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc550-120">E_FAIL</span></span>|<span data-ttu-id="cc550-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cc550-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc550-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cc550-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc550-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc550-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc550-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc550-124">Remarks</span></span>  
 <span data-ttu-id="cc550-125">Konak bir tanımlayıcı CLR ve hata ayıklama ortamında konak tümleştirmenize yardımcı olmak için bir görev ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc550-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="cc550-126">Tanımlayıcı için CLR anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc550-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="cc550-127">CLR bunu boyunca bir hata ayıklayıcı uygulamaya geçirir.</span><span class="sxs-lookup"><span data-stu-id="cc550-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="cc550-128">Hata ayıklayıcı CLR çağrı yığını konak çağrı yığını ile ilişkilendirmek için bu tanımlayıcı kullanın ve bunların ilgili izleme bilgileri Hata Ayıklayıcı'nın kullanıcı arabiriminde görüntülendiğinde birleşik etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="cc550-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc550-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc550-129">Requirements</span></span>  
 <span data-ttu-id="cc550-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc550-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc550-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc550-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc550-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cc550-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc550-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc550-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc550-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc550-134">See Also</span></span>  
 [<span data-ttu-id="cc550-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc550-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cc550-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc550-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cc550-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc550-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cc550-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc550-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
