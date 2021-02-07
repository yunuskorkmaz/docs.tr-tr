---
description: ': ICLRTaskManager:: CreateTask Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTaskManager::CreateTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: 98a287f10a84b18579ebf2a4294cbb8a67cabc9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728619"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="f9786-103">ICLRTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9786-103">ICLRTaskManager::CreateTask Method</span></span>

<span data-ttu-id="f9786-104">Ortak dil çalışma zamanının (CLR) açık olarak yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="f9786-104">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9786-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9786-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9786-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9786-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="f9786-107">dışı Yeni oluşturulan bir [ICLRTask](iclrtask-interface.md)adresine yönelik bir işaretçi veya görev oluşturulmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="f9786-107">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9786-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9786-108">Return Value</span></span>  
  
|<span data-ttu-id="f9786-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9786-109">HRESULT</span></span>|<span data-ttu-id="f9786-110">Description</span><span class="sxs-lookup"><span data-stu-id="f9786-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9786-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9786-111">S_OK</span></span>|<span data-ttu-id="f9786-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f9786-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="f9786-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9786-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9786-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f9786-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9786-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9786-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9786-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f9786-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9786-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9786-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9786-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9786-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9786-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9786-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9786-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f9786-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9786-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9786-121">E_FAIL</span></span>|<span data-ttu-id="f9786-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9786-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9786-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f9786-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9786-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9786-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9786-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f9786-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f9786-126">İstenen kaynağı ayırmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="f9786-126">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9786-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9786-127">Remarks</span></span>  

 <span data-ttu-id="f9786-128">CLR, başlatma sonrasında otomatik olarak yeni bir görev oluşturur, Kullanıcı kodu ad alanındaki türleri kullanarak bir iş parçacığı oluşturduğunda <xref:System.Threading> veya iş parçacığı havuzunun boyutu arttığı zaman.</span><span class="sxs-lookup"><span data-stu-id="f9786-128">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="f9786-129">Yönetilmeyen kod yönetilen işleve çağrı yaptığında da görevler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9786-129">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="f9786-130">`CreateTask` Konağın, CLR 'nin yeni bir görev oluşturmasını sağlayan açık bir istek yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f9786-130">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="f9786-131">Örneğin, ana bilgisayar veri yapılarını önceden başlatmak için bu yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f9786-131">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9786-132">Yeni görev askıya alınmış durumda döndürülür ve ana bilgisayar açıkça [IHostTask:: Start](ihosttask-start-method.md)olarak çağrılana kadar askıda kalır.</span><span class="sxs-lookup"><span data-stu-id="f9786-132">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9786-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9786-133">Requirements</span></span>  

 <span data-ttu-id="f9786-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9786-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9786-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9786-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9786-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f9786-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9786-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9786-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9786-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9786-138">See also</span></span>

- [<span data-ttu-id="f9786-139">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9786-139">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f9786-140">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9786-140">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f9786-141">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9786-141">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f9786-142">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9786-142">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
