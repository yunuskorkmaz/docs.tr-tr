---
title: IHostTaskManager::SetCLRTaskManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: c674cc43065bf8ea102bec1c5134757380454913
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141232"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="f0f4e-102">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="f0f4e-103">Ana bilgisayarı, ortak dil çalışma zamanı (CLR) tarafından uygulanan bir [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) örneğine bir arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0f4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0f4e-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="f0f4e-106">'ndaki Ortak dil çalışma zamanı tarafından uygulanan `ICLRTaskManager` örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0f4e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0f4e-107">Return Value</span></span>  
  
|<span data-ttu-id="f0f4e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0f4e-108">HRESULT</span></span>|<span data-ttu-id="f0f4e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0f4e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0f4e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0f4e-110">S_OK</span></span>|<span data-ttu-id="f0f4e-111">`SetCLRTaskManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="f0f4e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0f4e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0f4e-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0f4e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0f4e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0f4e-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-115">The call timed out.</span></span>|  
|<span data-ttu-id="f0f4e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0f4e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0f4e-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0f4e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0f4e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0f4e-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0f4e-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="f0f4e-120">E_FAIL</span></span>|<span data-ttu-id="f0f4e-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0f4e-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0f4e-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0f4e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0f4e-124">Remarks</span></span>  
 <span data-ttu-id="f0f4e-125">Çalışma zamanı, ana bilgisayarı bir `ICLRTaskManager` örneği için arabirim işaretçiyle sağlamak üzere `SetCLRTaskManager` çağırır.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f4e-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0f4e-126">Requirements</span></span>  
 <span data-ttu-id="f0f4e-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0f4e-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0f4e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0f4e-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f0f4e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0f4e-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0f4e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f4e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0f4e-131">See also</span></span>

- [<span data-ttu-id="f0f4e-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f0f4e-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f0f4e-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f0f4e-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0f4e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
