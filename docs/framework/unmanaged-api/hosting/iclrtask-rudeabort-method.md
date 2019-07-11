---
title: ICLRTask::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7750d50b772ff17cf9dcd05de2e2f34556714e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770481"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="70145-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70145-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="70145-103">Ortak dil çalışma zamanı (CLR) geçerli tarafından temsil edilen bir görev iptal etmek için bildirir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) koşulsuz olarak ve hemen örneği.</span><span class="sxs-lookup"><span data-stu-id="70145-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70145-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70145-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="70145-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70145-105">Return Value</span></span>  
  
|<span data-ttu-id="70145-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70145-106">HRESULT</span></span>|<span data-ttu-id="70145-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70145-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70145-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="70145-108">S_OK</span></span>|<span data-ttu-id="70145-109">`RudeAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="70145-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="70145-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70145-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70145-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="70145-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70145-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70145-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70145-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="70145-113">The call timed out.</span></span>|  
|<span data-ttu-id="70145-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70145-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70145-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="70145-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70145-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70145-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70145-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="70145-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70145-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70145-118">E_FAIL</span></span>|<span data-ttu-id="70145-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="70145-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70145-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="70145-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70145-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="70145-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70145-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70145-122">Remarks</span></span>  
 <span data-ttu-id="70145-123">Bir konak çağırır `RudeAbort` hemen bir görevi iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="70145-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="70145-124">Sonlandırıcı ve özel durum işleme rutinleri yürütülecek garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="70145-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70145-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70145-125">Requirements</span></span>  
 <span data-ttu-id="70145-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70145-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70145-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70145-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70145-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="70145-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70145-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70145-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70145-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70145-130">See also</span></span>

- [<span data-ttu-id="70145-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70145-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="70145-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70145-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="70145-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70145-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="70145-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70145-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
