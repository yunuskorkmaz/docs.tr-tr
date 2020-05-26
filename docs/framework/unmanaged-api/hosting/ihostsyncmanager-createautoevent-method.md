---
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
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803497"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="99fa7-102">IHostSyncManager::CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99fa7-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="99fa7-103">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99fa7-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fa7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99fa7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99fa7-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="99fa7-106">dışı Konak tarafından uygulanan [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="99fa7-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99fa7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99fa7-107">Return Value</span></span>  
  
|<span data-ttu-id="99fa7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99fa7-108">HRESULT</span></span>|<span data-ttu-id="99fa7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99fa7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99fa7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99fa7-110">S_OK</span></span>|<span data-ttu-id="99fa7-111">`CreateAutoEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="99fa7-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="99fa7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99fa7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99fa7-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99fa7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99fa7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99fa7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99fa7-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="99fa7-115">The call timed out.</span></span>|  
|<span data-ttu-id="99fa7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99fa7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99fa7-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99fa7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99fa7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99fa7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99fa7-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="99fa7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99fa7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99fa7-120">E_FAIL</span></span>|<span data-ttu-id="99fa7-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99fa7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99fa7-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99fa7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99fa7-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99fa7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99fa7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="99fa7-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="99fa7-125">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="99fa7-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99fa7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99fa7-126">Remarks</span></span>  
 <span data-ttu-id="99fa7-127">`CreateAutoEvent`bekleyen iş parçacığı yayımlandıktan sonra durumu otomatik olarak, sinyalsiz olarak değiştirilen bir otomatik olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99fa7-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="99fa7-128">Bu yöntem, Win32 `CreateEvent` işlevini `false` parametresi için belirtilen bir değerle yansıtır `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="99fa7-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fa7-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99fa7-129">Requirements</span></span>  
 <span data-ttu-id="99fa7-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fa7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fa7-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99fa7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99fa7-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="99fa7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fa7-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fa7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fa7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99fa7-134">See also</span></span>

- [<span data-ttu-id="99fa7-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="99fa7-136">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="99fa7-137">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="99fa7-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
