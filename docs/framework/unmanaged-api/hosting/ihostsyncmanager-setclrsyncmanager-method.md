---
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
ms.openlocfilehash: 9c08a790d4dad748e5d09271bd870add22255b4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132618"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="c3fe4-102">IHostSyncManager::SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3fe4-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="c3fe4-103">[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) örneğini geçerli [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) örneğiyle ilişkilendirilecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3fe4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3fe4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3fe4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3fe4-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="c3fe4-106">'ndaki Ortak dil çalışma zamanı (CLR) tarafından sağlanan `ICLRSyncManager` örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3fe4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3fe4-107">Return Value</span></span>  
  
|<span data-ttu-id="c3fe4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3fe4-108">HRESULT</span></span>|<span data-ttu-id="c3fe4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3fe4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3fe4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3fe4-110">S_OK</span></span>|<span data-ttu-id="c3fe4-111">`SetCLRSyncManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="c3fe4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3fe4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3fe4-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3fe4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3fe4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3fe4-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-115">The call timed out.</span></span>|  
|<span data-ttu-id="c3fe4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3fe4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3fe4-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3fe4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3fe4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3fe4-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3fe4-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c3fe4-120">E_FAIL</span></span>|<span data-ttu-id="c3fe4-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3fe4-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3fe4-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3fe4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3fe4-124">Remarks</span></span>  
 <span data-ttu-id="c3fe4-125">Konak ve CLR arasındaki iletişimi kolaylaştırmak için barındırma arabirimleri genellikle çiftler halinde gelir.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="c3fe4-126">Çiftin bir üyesi konak tarafından uygulanır ve diğer üye CLR tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="c3fe4-127">Ana bilgisayar tarafı uygulama olarak, `IHostSyncManager` arabirimi CLR tarafından uygulanan `ICLRSyncManager` arabirimine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="c3fe4-128">CLR, ana bilgisayar için geçerli `IHostSyncManager` örneğiyle ilişkilendirilecek bir `ICLRSyncManager` örneği sağlamak üzere `SetCLRSyncManager` çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3fe4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3fe4-129">Requirements</span></span>  
 <span data-ttu-id="c3fe4-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3fe4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3fe4-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3fe4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3fe4-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c3fe4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3fe4-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3fe4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fe4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3fe4-134">See also</span></span>

- [<span data-ttu-id="c3fe4-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3fe4-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c3fe4-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3fe4-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
