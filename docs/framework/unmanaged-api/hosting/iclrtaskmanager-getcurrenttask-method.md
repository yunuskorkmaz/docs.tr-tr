---
description: ': ICLRTaskManager:: GetCurrentTask Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d7435f9099d6a8ceb173afbf79c1d0f5d4005980
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728554"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="57fe6-103">ICLRTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="57fe6-103">ICLRTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="57fe6-104">Yöntem çağrısının başlatıldığı işletim sistemi iş parçacığında çalışmakta olan [ICLRTask](iclrtask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="57fe6-104">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57fe6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57fe6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57fe6-106">Parameters</span></span>  

 `ppTask`  
 <span data-ttu-id="57fe6-107">dışı `ICLRTask` Şu anda, çağrının kaynaklandığı işletim sistemi iş parçacığında yürütülmekte olan bir örneğin adresine yönelik bir işaretçi veya şu anda bu iş parçacığında yürütülen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="57fe6-107">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57fe6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57fe6-108">Return Value</span></span>  
  
|<span data-ttu-id="57fe6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57fe6-109">HRESULT</span></span>|<span data-ttu-id="57fe6-110">Description</span><span class="sxs-lookup"><span data-stu-id="57fe6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57fe6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57fe6-111">S_OK</span></span>|<span data-ttu-id="57fe6-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="57fe6-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="57fe6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57fe6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57fe6-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="57fe6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57fe6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57fe6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57fe6-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="57fe6-116">The call timed out.</span></span>|  
|<span data-ttu-id="57fe6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57fe6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57fe6-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="57fe6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57fe6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57fe6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57fe6-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="57fe6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57fe6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57fe6-121">E_FAIL</span></span>|<span data-ttu-id="57fe6-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="57fe6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57fe6-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="57fe6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57fe6-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="57fe6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57fe6-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57fe6-125">Remarks</span></span>  

 <span data-ttu-id="57fe6-126">`ICLRTask`Parametresinin işaret ettiği örnek, `ppTask` clr için şu anda yürütülmekte olan görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57fe6-126">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="57fe6-127">`ICLRTask`Örnek, ana bilgisayar için görevi temsil eden karşılık gelen bir [IHostTask](ihosttask-interface.md) örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="57fe6-127">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57fe6-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57fe6-128">Requirements</span></span>  

 <span data-ttu-id="57fe6-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57fe6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57fe6-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57fe6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57fe6-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="57fe6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57fe6-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57fe6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fe6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57fe6-133">See also</span></span>

- [<span data-ttu-id="57fe6-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="57fe6-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="57fe6-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="57fe6-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
