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
ms.openlocfilehash: 821f524cc8ff7f9983f811f539e2badb2306be26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437709"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="2e5da-102">ICLRTask::YieldTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e5da-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="2e5da-103">Ortak dil çalışma zamanı (CLR) kenara görev put isteği, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder ve işlemci zamanı diğer görevler için kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="2e5da-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e5da-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2e5da-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e5da-105">Return Value</span></span>  
  
|<span data-ttu-id="2e5da-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e5da-106">HRESULT</span></span>|<span data-ttu-id="2e5da-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5da-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e5da-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e5da-108">S_OK</span></span>|<span data-ttu-id="2e5da-109">`YieldTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2e5da-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="2e5da-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e5da-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e5da-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2e5da-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e5da-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e5da-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e5da-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2e5da-113">The call timed out.</span></span>|  
|<span data-ttu-id="2e5da-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e5da-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e5da-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2e5da-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e5da-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e5da-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e5da-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2e5da-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e5da-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e5da-118">E_FAIL</span></span>|<span data-ttu-id="2e5da-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2e5da-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e5da-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e5da-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e5da-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e5da-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e5da-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e5da-122">Remarks</span></span>  
 <span data-ttu-id="2e5da-123">Bir konak çağırır `YieldTask` için diğer görevlerin veya işlemlerin isteği işlemci kaynakları.</span><span class="sxs-lookup"><span data-stu-id="2e5da-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="2e5da-124">Bu yöntem, öncelikle CPU süresi vermek uzun süre çalışan kod sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2e5da-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="2e5da-125">Çalışma zamanı görev put dener, geçerli `ICLRTask` örneği burada işleme süresi sağlayabilen, ancak başarı garanti etmez bir durumda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e5da-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e5da-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e5da-126">Requirements</span></span>  
 <span data-ttu-id="2e5da-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e5da-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e5da-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e5da-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e5da-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e5da-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e5da-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e5da-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5da-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e5da-131">See Also</span></span>  
 [<span data-ttu-id="2e5da-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5da-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2e5da-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5da-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2e5da-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5da-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2e5da-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5da-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
