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
ms.openlocfilehash: 23d0679599c681468caa2507518d0ae3144ac26a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669815"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="25e5c-102">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25e5c-102">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="25e5c-103">Ana bilgisayarı, ortak dil çalışma zamanı (CLR) tarafından uygulanan bir [ICLRTaskManager](iclrtaskmanager-interface.md) örneğine bir arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="25e5c-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e5c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="25e5c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25e5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25e5c-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="25e5c-106">'ndaki `ICLRTaskManager` Ortak dil çalışma zamanı tarafından uygulanan bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25e5c-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25e5c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25e5c-107">Return Value</span></span>  
  
|<span data-ttu-id="25e5c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25e5c-108">HRESULT</span></span>|<span data-ttu-id="25e5c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25e5c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25e5c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="25e5c-110">S_OK</span></span>|<span data-ttu-id="25e5c-111">`SetCLRTaskManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="25e5c-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="25e5c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25e5c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25e5c-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="25e5c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25e5c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25e5c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25e5c-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="25e5c-115">The call timed out.</span></span>|  
|<span data-ttu-id="25e5c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25e5c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25e5c-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="25e5c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25e5c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25e5c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25e5c-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="25e5c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25e5c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25e5c-120">E_FAIL</span></span>|<span data-ttu-id="25e5c-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="25e5c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25e5c-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25e5c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25e5c-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="25e5c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25e5c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25e5c-124">Remarks</span></span>  

 <span data-ttu-id="25e5c-125">Çalışma zamanı, `SetCLRTaskManager` konağa bir örnek için arabirim işaretçisi sağlamak için çağırır `ICLRTaskManager` .</span><span class="sxs-lookup"><span data-stu-id="25e5c-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25e5c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25e5c-126">Requirements</span></span>  

 <span data-ttu-id="25e5c-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e5c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e5c-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25e5c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25e5c-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="25e5c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25e5c-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25e5c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e5c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25e5c-131">See also</span></span>

- [<span data-ttu-id="25e5c-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25e5c-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="25e5c-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25e5c-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="25e5c-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25e5c-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="25e5c-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25e5c-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
