---
title: "IHostCrst::Leave Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 391aff3920e7ea2ef010ce7d97bdedb4e636dc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="08fe0-102">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08fe0-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="08fe0-103">Geçerli örneği tarafından temsil edilen kritik bölüm bırakır [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="08fe0-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08fe0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08fe0-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="08fe0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08fe0-105">Return Value</span></span>  
  
|<span data-ttu-id="08fe0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08fe0-106">HRESULT</span></span>|<span data-ttu-id="08fe0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08fe0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08fe0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="08fe0-108">S_OK</span></span>|<span data-ttu-id="08fe0-109">`Leave`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="08fe0-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="08fe0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08fe0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08fe0-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="08fe0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08fe0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08fe0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08fe0-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="08fe0-113">The call timed out.</span></span>|  
|<span data-ttu-id="08fe0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08fe0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08fe0-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="08fe0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08fe0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08fe0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08fe0-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="08fe0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08fe0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08fe0-118">E_FAIL</span></span>|<span data-ttu-id="08fe0-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="08fe0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08fe0-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="08fe0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08fe0-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="08fe0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08fe0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08fe0-122">Remarks</span></span>  
 <span data-ttu-id="08fe0-123">`Leave`doğrudan ana bilgisayarın uygulama iş parçacığı oluşturma yerine ile ilgili Win32 kullanarak iletişim kurmak CLR verir `LeaveCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="08fe0-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="08fe0-124">Geçerli tarafından temsil edilen kritik bölüm sahipliğini bir iş parçacığı `IHostCrst` örneği çağırmalıdır `Leave` isteğe bağlı olarak her zaman için bu kritik bölüm girdikten sonra.</span><span class="sxs-lookup"><span data-stu-id="08fe0-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08fe0-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08fe0-125">Requirements</span></span>  
 <span data-ttu-id="08fe0-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08fe0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08fe0-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08fe0-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08fe0-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08fe0-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08fe0-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08fe0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fe0-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08fe0-130">See Also</span></span>  
 [<span data-ttu-id="08fe0-131">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08fe0-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="08fe0-132">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08fe0-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="08fe0-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08fe0-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
