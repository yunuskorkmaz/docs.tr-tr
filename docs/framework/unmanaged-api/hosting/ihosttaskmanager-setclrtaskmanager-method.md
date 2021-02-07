---
description: ': IHostTaskManager:: SetCLRTaskManager Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 438a5b56afd42eceafb484bdf0020efbad86d052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680882"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="6c518-103">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c518-103">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="6c518-104">Ana bilgisayarı, ortak dil çalışma zamanı (CLR) tarafından uygulanan bir [ICLRTaskManager](iclrtaskmanager-interface.md) örneğine bir arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c518-104">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c518-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c518-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c518-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c518-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="6c518-107">'ndaki `ICLRTaskManager` Ortak dil çalışma zamanı tarafından uygulanan bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c518-107">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c518-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c518-108">Return Value</span></span>  
  
|<span data-ttu-id="6c518-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c518-109">HRESULT</span></span>|<span data-ttu-id="6c518-110">Description</span><span class="sxs-lookup"><span data-stu-id="6c518-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c518-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c518-111">S_OK</span></span>|<span data-ttu-id="6c518-112">`SetCLRTaskManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c518-112">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="6c518-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c518-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c518-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6c518-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c518-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c518-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c518-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c518-116">The call timed out.</span></span>|  
|<span data-ttu-id="6c518-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c518-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c518-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c518-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c518-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c518-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c518-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6c518-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c518-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c518-121">E_FAIL</span></span>|<span data-ttu-id="6c518-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c518-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c518-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c518-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c518-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c518-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c518-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c518-125">Remarks</span></span>  

 <span data-ttu-id="6c518-126">Çalışma zamanı, `SetCLRTaskManager` konağa bir örnek için arabirim işaretçisi sağlamak için çağırır `ICLRTaskManager` .</span><span class="sxs-lookup"><span data-stu-id="6c518-126">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c518-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c518-127">Requirements</span></span>  

 <span data-ttu-id="6c518-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c518-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c518-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c518-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c518-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6c518-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c518-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c518-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c518-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c518-132">See also</span></span>

- [<span data-ttu-id="6c518-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c518-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6c518-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c518-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6c518-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c518-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6c518-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c518-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
