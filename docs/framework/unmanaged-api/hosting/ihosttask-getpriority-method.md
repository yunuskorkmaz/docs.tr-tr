---
title: IHostTask::GetPriority Metodu
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: e41fcf2f03b024c1b4ae0032c0ff025d6e2aa1c3
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842510"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="04e1e-102">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="04e1e-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="04e1e-103">Geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="04e1e-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e1e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="04e1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04e1e-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="04e1e-106">dışı Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini gösteren bir tamsayı işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="04e1e-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04e1e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04e1e-107">Return Value</span></span>  
  
|<span data-ttu-id="04e1e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04e1e-108">HRESULT</span></span>|<span data-ttu-id="04e1e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04e1e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04e1e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="04e1e-110">S_OK</span></span>|<span data-ttu-id="04e1e-111">`GetPriority`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="04e1e-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="04e1e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04e1e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04e1e-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="04e1e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04e1e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04e1e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04e1e-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="04e1e-115">The call timed out.</span></span>|  
|<span data-ttu-id="04e1e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04e1e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04e1e-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="04e1e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04e1e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04e1e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04e1e-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="04e1e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04e1e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04e1e-120">E_FAIL</span></span>|<span data-ttu-id="04e1e-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="04e1e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04e1e-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="04e1e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04e1e-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="04e1e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04e1e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04e1e-124">Remarks</span></span>  
 <span data-ttu-id="04e1e-125">İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="04e1e-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e1e-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e1e-126">Requirements</span></span>  
 <span data-ttu-id="04e1e-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e1e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e1e-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04e1e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04e1e-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="04e1e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04e1e-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e1e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e1e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e1e-131">See also</span></span>

- [<span data-ttu-id="04e1e-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e1e-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="04e1e-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e1e-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="04e1e-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e1e-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="04e1e-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e1e-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
