---
title: ICLRTask::YieldTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: 43f2048c8ab85fa7e94f73aad430400ad4c8352f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124587"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="abf27-102">ICLRTask::YieldTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abf27-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="abf27-103">Ortak dil çalışma zamanının (CLR) geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğinin temsil ettiği görevi yerleştirdiği ve işlemci süresini diğer görevler için kullanılabilir hale getirme istekleri.</span><span class="sxs-lookup"><span data-stu-id="abf27-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abf27-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="abf27-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="abf27-105">Return Value</span></span>  
  
|<span data-ttu-id="abf27-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abf27-106">HRESULT</span></span>|<span data-ttu-id="abf27-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abf27-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abf27-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="abf27-108">S_OK</span></span>|<span data-ttu-id="abf27-109">`YieldTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="abf27-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="abf27-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abf27-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abf27-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="abf27-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="abf27-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="abf27-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="abf27-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="abf27-113">The call timed out.</span></span>|  
|<span data-ttu-id="abf27-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="abf27-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="abf27-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="abf27-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="abf27-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="abf27-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="abf27-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="abf27-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="abf27-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="abf27-118">E_FAIL</span></span>|<span data-ttu-id="abf27-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="abf27-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="abf27-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="abf27-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="abf27-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="abf27-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abf27-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abf27-122">Remarks</span></span>  
 <span data-ttu-id="abf27-123">Bir konak, diğer görevler veya süreçler için işlemci kaynakları istemek üzere `YieldTask` çağırır.</span><span class="sxs-lookup"><span data-stu-id="abf27-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="abf27-124">Bu yöntem öncelikle uzun süre çalışan kodun CPU süresi vermesini sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abf27-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="abf27-125">Çalışma zamanı, geçerli `ICLRTask` örneğinin işlem süresini karşılayabileceği, ancak başarılı olma garantisi olmayan bir durumda, görevi koymaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="abf27-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abf27-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abf27-126">Requirements</span></span>  
 <span data-ttu-id="abf27-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abf27-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abf27-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="abf27-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abf27-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="abf27-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abf27-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abf27-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf27-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf27-131">See also</span></span>

- [<span data-ttu-id="abf27-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abf27-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="abf27-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abf27-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="abf27-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abf27-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="abf27-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abf27-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
