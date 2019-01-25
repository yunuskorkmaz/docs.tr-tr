---
title: ICLRTask::ExitTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9913618f597d8e456d8db4d13883ee049c21fb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726383"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="8877b-102">ICLRTask::ExitTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8877b-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="8877b-103">Görev geçerli tarafından temsil edilen ortak dil çalışma zamanı (CLR) bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği sona eriyor ve görev düzgün biçimde kapatılamadı çalışır.</span><span class="sxs-lookup"><span data-stu-id="8877b-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8877b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8877b-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8877b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8877b-105">Return Value</span></span>  
  
|<span data-ttu-id="8877b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8877b-106">HRESULT</span></span>|<span data-ttu-id="8877b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8877b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8877b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8877b-108">S_OK</span></span>|<span data-ttu-id="8877b-109">`ExitTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8877b-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="8877b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8877b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8877b-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8877b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8877b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8877b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8877b-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8877b-113">The call timed out.</span></span>|  
|<span data-ttu-id="8877b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8877b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8877b-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8877b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8877b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8877b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8877b-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="8877b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8877b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8877b-118">E_FAIL</span></span>|<span data-ttu-id="8877b-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8877b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8877b-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8877b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8877b-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8877b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8877b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8877b-122">Remarks</span></span>  
 <span data-ttu-id="8877b-123">`ExitTask` bir yönetilmeyen tür kitaplığından bir iş parçacığı ayırma için benzer şekilde, görevin temiz kapatma çalışır.</span><span class="sxs-lookup"><span data-stu-id="8877b-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8877b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8877b-124">Requirements</span></span>  
 <span data-ttu-id="8877b-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8877b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8877b-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8877b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8877b-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8877b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8877b-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8877b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8877b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8877b-129">See also</span></span>
- [<span data-ttu-id="8877b-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8877b-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8877b-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8877b-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8877b-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8877b-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8877b-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8877b-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
