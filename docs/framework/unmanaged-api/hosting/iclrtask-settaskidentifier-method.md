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
ms.openlocfilehash: abd8848ed54b26b66090e4865f9c3a0e5c4d20db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078323"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="314c2-102">ICLRTask::SetTaskIdentifier Yöntemi</span><span class="sxs-lookup"><span data-stu-id="314c2-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="314c2-103">Ortak dil çalışma zamanı (CLR) belirtilen tanımlayıcı değerini geçerli tarafından temsil edilen bir görev ile ilişkilendirilecek bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="314c2-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="314c2-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="314c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="314c2-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="314c2-106">[in] Geçerli tarafından temsil edilen bir görev ile ilişkilendirmek ortak dil çalışma zamanı için benzersiz tanımlayıcı `ICLRTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="314c2-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="314c2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="314c2-107">Return Value</span></span>  
  
|<span data-ttu-id="314c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="314c2-108">HRESULT</span></span>|<span data-ttu-id="314c2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="314c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="314c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="314c2-110">S_OK</span></span>|`SetTaskIdentifier` <span data-ttu-id="314c2-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="314c2-111">returned successfully.</span></span>|  
|<span data-ttu-id="314c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="314c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="314c2-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="314c2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="314c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="314c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="314c2-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="314c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="314c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="314c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="314c2-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="314c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="314c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="314c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="314c2-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="314c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="314c2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="314c2-120">E_FAIL</span></span>|<span data-ttu-id="314c2-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="314c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="314c2-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="314c2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="314c2-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="314c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="314c2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="314c2-124">Remarks</span></span>  
 <span data-ttu-id="314c2-125">Konak, bir tanımlayıcı, bir görev CLR ve hata ayıklama ortamında konak tümleştirmenize yardımcı olmaya ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="314c2-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="314c2-126">Tanımlayıcı için CLR anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="314c2-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="314c2-127">CLR bu boyunca bir hata ayıklayıcı uygulamaya geçirir.</span><span class="sxs-lookup"><span data-stu-id="314c2-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="314c2-128">Hata ayıklayıcı bir CLR çağrı yığını konak çağrı yığını ile ilişkilendirmek için bu tanımlayıcıyı kullanın ve hata ayıklayıcı'nın kullanıcı arabiriminde görüntülendiğinde birleşik, ilgili izleme bilgileri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="314c2-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="314c2-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="314c2-129">Requirements</span></span>  
 <span data-ttu-id="314c2-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314c2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314c2-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="314c2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="314c2-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="314c2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="314c2-133">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="314c2-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="314c2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314c2-134">See also</span></span>

- [<span data-ttu-id="314c2-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314c2-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="314c2-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314c2-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="314c2-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314c2-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="314c2-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314c2-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
