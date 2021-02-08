---
description: ': ICLRTask:: SetTaskIdentifier yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e746d8ec96d16f7761dd49ac814ddbed073c2686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784957"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="bf88f-103">ICLRTask::SetTaskIdentifier Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf88f-103">ICLRTask::SetTaskIdentifier Method</span></span>

<span data-ttu-id="bf88f-104">Ortak dil çalışma zamanını (CLR), belirtilen tanımlayıcı değerini geçerli [ICLRTask](iclrtask-interface.md) örneğiyle temsil edilen görevle ilişkilendider.</span><span class="sxs-lookup"><span data-stu-id="bf88f-104">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf88f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf88f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf88f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf88f-106">Parameters</span></span>  

 `Asked`  
 <span data-ttu-id="bf88f-107">'ndaki Geçerli örnek tarafından temsil edilen görevle ilişkilendirilecek ortak dil çalışma zamanı için benzersiz tanımlayıcı `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="bf88f-107">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf88f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bf88f-108">Return Value</span></span>  
  
|<span data-ttu-id="bf88f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf88f-109">HRESULT</span></span>|<span data-ttu-id="bf88f-110">Description</span><span class="sxs-lookup"><span data-stu-id="bf88f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf88f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf88f-111">S_OK</span></span>|<span data-ttu-id="bf88f-112">`SetTaskIdentifier` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bf88f-112">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="bf88f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf88f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf88f-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bf88f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf88f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf88f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf88f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bf88f-116">The call timed out.</span></span>|  
|<span data-ttu-id="bf88f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf88f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf88f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf88f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf88f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf88f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf88f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bf88f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf88f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf88f-121">E_FAIL</span></span>|<span data-ttu-id="bf88f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bf88f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf88f-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf88f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf88f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf88f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf88f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf88f-125">Remarks</span></span>  

 <span data-ttu-id="bf88f-126">Konak, bir tanıtıcıyı bir tanıtıcı ile ilişkilendirebilir ve bir hata ayıklama ortamında CLR ve Konağı tümleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bf88f-126">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="bf88f-127">Tanımlayıcının CLR için anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf88f-127">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="bf88f-128">CLR onu bir hata ayıklayıcı uygulamasına geçirir.</span><span class="sxs-lookup"><span data-stu-id="bf88f-128">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="bf88f-129">Hata ayıklayıcı, bir CLR çağrı yığınını bir konak çağrı yığını ile ilişkilendirmek için bu tanımlayıcıyı kullanabilir ve hata ayıklayıcının Kullanıcı arabiriminde görüntülendiklerinde kendi izleme bilgilerini Birleşik hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf88f-129">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf88f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf88f-130">Requirements</span></span>  

 <span data-ttu-id="bf88f-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf88f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf88f-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bf88f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf88f-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bf88f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf88f-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf88f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf88f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf88f-135">See also</span></span>

- [<span data-ttu-id="bf88f-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf88f-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bf88f-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf88f-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bf88f-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf88f-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bf88f-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf88f-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
