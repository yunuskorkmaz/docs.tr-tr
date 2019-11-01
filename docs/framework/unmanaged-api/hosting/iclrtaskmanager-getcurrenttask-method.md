---
title: ICLRTaskManager::GetCurrentTask Metodu
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: a57610d1b41d80d54a245b9744aafd78a1e88177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195905"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="1a297-102">ICLRTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="1a297-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="1a297-103">Yöntem çağrısının başlatıldığı işletim sistemi iş parçacığında çalışmakta olan [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="1a297-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a297-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a297-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a297-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a297-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="1a297-106">dışı Şu anda, çağrının kaynaklandığı işletim sistemi iş parçacığında yürütülmekte olan bir `ICLRTask` örneğinin adresine yönelik bir işaretçi veya şu anda bu iş parçacığında yürütülen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="1a297-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a297-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a297-107">Return Value</span></span>  
  
|<span data-ttu-id="1a297-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a297-108">HRESULT</span></span>|<span data-ttu-id="1a297-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a297-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a297-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a297-110">S_OK</span></span>|<span data-ttu-id="1a297-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1a297-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="1a297-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a297-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a297-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1a297-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1a297-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1a297-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1a297-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1a297-115">The call timed out.</span></span>|  
|<span data-ttu-id="1a297-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1a297-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1a297-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1a297-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1a297-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1a297-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1a297-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1a297-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1a297-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1a297-120">E_FAIL</span></span>|<span data-ttu-id="1a297-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1a297-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1a297-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a297-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1a297-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a297-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a297-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a297-124">Remarks</span></span>  
 <span data-ttu-id="1a297-125">`ppTask` parametresinin işaret ettiği `ICLRTask` örneği, CLR için şu anda yürütülmekte olan görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a297-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="1a297-126">`ICLRTask` örneği, ana bilgisayar için görevi temsil eden karşılık gelen bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="1a297-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a297-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a297-127">Requirements</span></span>  
 <span data-ttu-id="1a297-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a297-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a297-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a297-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a297-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1a297-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a297-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a297-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a297-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a297-132">See also</span></span>

- [<span data-ttu-id="1a297-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a297-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1a297-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a297-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1a297-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a297-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1a297-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a297-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
