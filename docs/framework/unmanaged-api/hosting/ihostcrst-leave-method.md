---
title: IHostCrst::Leave Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: 050af068579d84b984ed83377d0c201e281bd154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130541"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="efcfc-102">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efcfc-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="efcfc-103">Geçerli [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)örneği tarafından temsil edilen kritik bölümü bırakır.</span><span class="sxs-lookup"><span data-stu-id="efcfc-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efcfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efcfc-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="efcfc-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="efcfc-105">Return Value</span></span>  
  
|<span data-ttu-id="efcfc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efcfc-106">HRESULT</span></span>|<span data-ttu-id="efcfc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efcfc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efcfc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="efcfc-108">S_OK</span></span>|<span data-ttu-id="efcfc-109">`Leave` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="efcfc-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="efcfc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efcfc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efcfc-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="efcfc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="efcfc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="efcfc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="efcfc-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="efcfc-113">The call timed out.</span></span>|  
|<span data-ttu-id="efcfc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="efcfc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="efcfc-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="efcfc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="efcfc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="efcfc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="efcfc-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="efcfc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="efcfc-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="efcfc-118">E_FAIL</span></span>|<span data-ttu-id="efcfc-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="efcfc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="efcfc-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="efcfc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="efcfc-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="efcfc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efcfc-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efcfc-122">Remarks</span></span>  
 <span data-ttu-id="efcfc-123">`Leave`, CLR 'nin karşılık gelen Win32 `LeaveCriticalSection` işlevini kullanmak yerine, konağın iş parçacığı uygulamasıyla doğrudan iletişim kurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="efcfc-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="efcfc-124">Geçerli `IHostCrst` örneği tarafından temsil edilen kritik bölümün sahipliğini alan iş parçacığı, bu kritik bölümü her girdiğinde her seferinde `Leave` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efcfc-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efcfc-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efcfc-125">Requirements</span></span>  
 <span data-ttu-id="efcfc-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efcfc-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efcfc-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efcfc-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efcfc-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="efcfc-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efcfc-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efcfc-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efcfc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efcfc-130">See also</span></span>

- [<span data-ttu-id="efcfc-131">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efcfc-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="efcfc-132">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efcfc-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="efcfc-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efcfc-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
