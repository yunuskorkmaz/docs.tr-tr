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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d60cdee0a5357f7e117dc902b073049f3bbaea9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198484"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="e750f-102">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e750f-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="e750f-103">Geçerli örneği tarafından temsil edilen kritik bölüm bırakır [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e750f-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e750f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e750f-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e750f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e750f-105">Return Value</span></span>  
  
|<span data-ttu-id="e750f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e750f-106">HRESULT</span></span>|<span data-ttu-id="e750f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e750f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e750f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e750f-108">S_OK</span></span>|`Leave` <span data-ttu-id="e750f-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e750f-109">returned successfully.</span></span>|  
|<span data-ttu-id="e750f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e750f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e750f-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e750f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e750f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e750f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e750f-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e750f-113">The call timed out.</span></span>|  
|<span data-ttu-id="e750f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e750f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e750f-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e750f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e750f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e750f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e750f-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e750f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e750f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e750f-118">E_FAIL</span></span>|<span data-ttu-id="e750f-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e750f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e750f-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e750f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e750f-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e750f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e750f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e750f-122">Remarks</span></span>  
 `Leave` <span data-ttu-id="e750f-123">doğrudan ana bilgisayarın uygulama iş parçacığı yerine ile ilgili Win32 kullanarak iletişim kurmak CLR sağlayan `LeaveCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="e750f-123">allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="e750f-124">Geçerli tarafından temsil edilen kritik bölüm sahipliğini bir iş parçacığı `IHostCrst` örneği çağırmalıdır `Leave` isteğe bağlı olarak her zaman için bu kritik bölüm girdikten sonra.</span><span class="sxs-lookup"><span data-stu-id="e750f-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e750f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e750f-125">Requirements</span></span>  
 <span data-ttu-id="e750f-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e750f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e750f-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e750f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e750f-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e750f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e750f-129">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e750f-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e750f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e750f-130">See also</span></span>

- [<span data-ttu-id="e750f-131">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e750f-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e750f-132">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e750f-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="e750f-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e750f-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
