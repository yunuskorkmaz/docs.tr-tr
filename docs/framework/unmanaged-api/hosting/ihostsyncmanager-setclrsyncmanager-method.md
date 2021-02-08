---
description: ': IHostSyncManager:: SetCLRSyncManager yöntemi hakkında daha fazla bilgi edinin'
title: IHostSyncManager::SetCLRSyncManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: e2a6a54334f7b8a63696ead918f4f34e0c36e438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784723"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="f9197-103">IHostSyncManager::SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9197-103">IHostSyncManager::SetCLRSyncManager Method</span></span>

<span data-ttu-id="f9197-104">[ICLRSyncManager](iclrsyncmanager-interface.md) örneğini geçerli [IHostSyncManager](ihostsyncmanager-interface.md) örneğiyle ilişkilendirilecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9197-104">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9197-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9197-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9197-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9197-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="f9197-107">'ndaki `ICLRSyncManager` Ortak dil çalışma zamanı (CLR) tarafından sağlanan örneğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9197-107">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9197-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9197-108">Return Value</span></span>  
  
|<span data-ttu-id="f9197-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9197-109">HRESULT</span></span>|<span data-ttu-id="f9197-110">Description</span><span class="sxs-lookup"><span data-stu-id="f9197-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9197-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9197-111">S_OK</span></span>|<span data-ttu-id="f9197-112">`SetCLRSyncManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f9197-112">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="f9197-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9197-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9197-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f9197-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9197-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9197-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9197-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f9197-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9197-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9197-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9197-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9197-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9197-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9197-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9197-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f9197-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9197-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9197-121">E_FAIL</span></span>|<span data-ttu-id="f9197-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9197-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9197-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f9197-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9197-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9197-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9197-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9197-125">Remarks</span></span>  

 <span data-ttu-id="f9197-126">Konak ve CLR arasındaki iletişimi kolaylaştırmak için barındırma arabirimleri genellikle çiftler halinde gelir.</span><span class="sxs-lookup"><span data-stu-id="f9197-126">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="f9197-127">Çiftin bir üyesi konak tarafından uygulanır ve diğer üye CLR tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f9197-127">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="f9197-128">Ana bilgisayar tarafı uygulama olarak, `IHostSyncManager` ARABIRIMI `ICLRSyncManager` clr tarafından uygulanan arabirime karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f9197-128">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="f9197-129">CLR, `SetCLRSyncManager` `ICLRSyncManager` ana bilgisayar için geçerli örnekle ilişkilendirilecek bir örnek sağlamak için çağırır `IHostSyncManager` .</span><span class="sxs-lookup"><span data-stu-id="f9197-129">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9197-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9197-130">Requirements</span></span>  

 <span data-ttu-id="f9197-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9197-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9197-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9197-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9197-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f9197-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9197-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9197-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9197-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9197-135">See also</span></span>

- [<span data-ttu-id="f9197-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9197-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f9197-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9197-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
