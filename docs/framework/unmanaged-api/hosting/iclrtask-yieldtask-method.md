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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc8d936ac4fca704e7e3069209d8ff75d46b044d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113678"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="4ab2b-102">ICLRTask::YieldTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="4ab2b-103">Ortak dil çalışma zamanı (CLR) kenara görev put isteği, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğinin temsil ettiği ve işlemci zamanı, diğer görevlerin kullanımına.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4ab2b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ab2b-105">Return Value</span></span>  
  
|<span data-ttu-id="4ab2b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ab2b-106">HRESULT</span></span>|<span data-ttu-id="4ab2b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ab2b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ab2b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ab2b-108">S_OK</span></span>|`YieldTask` <span data-ttu-id="4ab2b-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-109">returned successfully.</span></span>|  
|<span data-ttu-id="4ab2b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ab2b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ab2b-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ab2b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ab2b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ab2b-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-113">The call timed out.</span></span>|  
|<span data-ttu-id="4ab2b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ab2b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ab2b-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ab2b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ab2b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ab2b-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ab2b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ab2b-118">E_FAIL</span></span>|<span data-ttu-id="4ab2b-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ab2b-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ab2b-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ab2b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ab2b-122">Remarks</span></span>  
 <span data-ttu-id="4ab2b-123">Bir konak çağırır `YieldTask` için diğer görevlerin veya işlemlerin isteği işlemci kaynakları.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="4ab2b-124">Bu yöntem, öncelikli olarak süre vermek uzun süre çalışan kod olanak sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="4ab2b-125">Çalışma zamanı görevi yerleştirmek çalışır, geçerli `ICLRTask` örneği burada işleme süresi sağlayabilir, ancak başarı garanti etmez durumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab2b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ab2b-126">Requirements</span></span>  
 <span data-ttu-id="4ab2b-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab2b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab2b-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ab2b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ab2b-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4ab2b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4ab2b-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4ab2b-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4ab2b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ab2b-131">See also</span></span>

- [<span data-ttu-id="4ab2b-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4ab2b-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4ab2b-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4ab2b-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab2b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
