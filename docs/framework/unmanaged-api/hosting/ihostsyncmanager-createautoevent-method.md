---
description: ': IHostSyncManager:: Createoto olay yöntemi hakkında daha fazla bilgi edinin'
title: IHostSyncManager::CreateAutoEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: 69767f1e01ead93c874eecf01c3167a5dc0e4b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784853"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="aedd3-103">IHostSyncManager::CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aedd3-103">IHostSyncManager::CreateAutoEvent Method</span></span>

<span data-ttu-id="aedd3-104">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aedd3-104">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedd3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aedd3-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedd3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aedd3-106">Parameters</span></span>  

 `ppEvent`  
 <span data-ttu-id="aedd3-107">dışı Konak tarafından uygulanan [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="aedd3-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedd3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aedd3-108">Return Value</span></span>  
  
|<span data-ttu-id="aedd3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aedd3-109">HRESULT</span></span>|<span data-ttu-id="aedd3-110">Description</span><span class="sxs-lookup"><span data-stu-id="aedd3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aedd3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aedd3-111">S_OK</span></span>|<span data-ttu-id="aedd3-112">`CreateAutoEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aedd3-112">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="aedd3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aedd3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aedd3-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aedd3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aedd3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aedd3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aedd3-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aedd3-116">The call timed out.</span></span>|  
|<span data-ttu-id="aedd3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aedd3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aedd3-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="aedd3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aedd3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aedd3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aedd3-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aedd3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aedd3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aedd3-121">E_FAIL</span></span>|<span data-ttu-id="aedd3-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aedd3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aedd3-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aedd3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aedd3-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aedd3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aedd3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aedd3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aedd3-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="aedd3-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aedd3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aedd3-127">Remarks</span></span>  

 <span data-ttu-id="aedd3-128">`CreateAutoEvent` bekleyen iş parçacığı yayımlandıktan sonra durumu otomatik olarak, sinyalsiz olarak değiştirilen bir otomatik olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aedd3-128">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="aedd3-129">Bu yöntem, Win32 `CreateEvent` işlevini `false` parametresi için belirtilen bir değerle yansıtır `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="aedd3-129">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedd3-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aedd3-130">Requirements</span></span>  

 <span data-ttu-id="aedd3-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aedd3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedd3-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aedd3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aedd3-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="aedd3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aedd3-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedd3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedd3-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aedd3-135">See also</span></span>

- [<span data-ttu-id="aedd3-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedd3-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="aedd3-137">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedd3-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="aedd3-138">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedd3-138">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="aedd3-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedd3-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
