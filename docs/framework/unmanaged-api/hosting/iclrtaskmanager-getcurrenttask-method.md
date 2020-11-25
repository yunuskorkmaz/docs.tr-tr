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
ms.openlocfilehash: af855e3ba47dc329a4fb722c3e13d5f1816beba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723285"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="a629d-102">ICLRTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="a629d-102">ICLRTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="a629d-103">Yöntem çağrısının başlatıldığı işletim sistemi iş parçacığında çalışmakta olan [ICLRTask](iclrtask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="a629d-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a629d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a629d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a629d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a629d-105">Parameters</span></span>  

 `ppTask`  
 <span data-ttu-id="a629d-106">dışı `ICLRTask` Şu anda, çağrının kaynaklandığı işletim sistemi iş parçacığında yürütülmekte olan bir örneğin adresine yönelik bir işaretçi veya şu anda bu iş parçacığında yürütülen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="a629d-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a629d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a629d-107">Return Value</span></span>  
  
|<span data-ttu-id="a629d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a629d-108">HRESULT</span></span>|<span data-ttu-id="a629d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a629d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a629d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a629d-110">S_OK</span></span>|<span data-ttu-id="a629d-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a629d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="a629d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a629d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a629d-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a629d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a629d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a629d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a629d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a629d-115">The call timed out.</span></span>|  
|<span data-ttu-id="a629d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a629d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a629d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a629d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a629d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a629d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a629d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a629d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a629d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a629d-120">E_FAIL</span></span>|<span data-ttu-id="a629d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a629d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a629d-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a629d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a629d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a629d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a629d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a629d-124">Remarks</span></span>  

 <span data-ttu-id="a629d-125">`ICLRTask`Parametresinin işaret ettiği örnek, `ppTask` clr için şu anda yürütülmekte olan görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a629d-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="a629d-126">`ICLRTask`Örnek, ana bilgisayar için görevi temsil eden karşılık gelen bir [IHostTask](ihosttask-interface.md) örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="a629d-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a629d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a629d-127">Requirements</span></span>  

 <span data-ttu-id="a629d-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a629d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a629d-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a629d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a629d-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a629d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a629d-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a629d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a629d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a629d-132">See also</span></span>

- [<span data-ttu-id="a629d-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a629d-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a629d-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a629d-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a629d-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a629d-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a629d-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a629d-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
