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
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441658"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="e4f30-102">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4f30-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="e4f30-103">Geçerli örneği tarafından temsil edilen kritik bölüm bırakır [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e4f30-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4f30-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e4f30-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4f30-105">Return Value</span></span>  
  
|<span data-ttu-id="e4f30-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4f30-106">HRESULT</span></span>|<span data-ttu-id="e4f30-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4f30-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4f30-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4f30-108">S_OK</span></span>|<span data-ttu-id="e4f30-109">`Leave` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4f30-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="e4f30-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4f30-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4f30-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e4f30-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4f30-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4f30-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4f30-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e4f30-113">The call timed out.</span></span>|  
|<span data-ttu-id="e4f30-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4f30-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4f30-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e4f30-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4f30-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4f30-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4f30-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e4f30-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4f30-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4f30-118">E_FAIL</span></span>|<span data-ttu-id="e4f30-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4f30-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4f30-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4f30-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4f30-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4f30-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f30-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4f30-122">Remarks</span></span>  
 <span data-ttu-id="e4f30-123">`Leave` doğrudan ana bilgisayarın uygulama iş parçacığı oluşturma yerine ile ilgili Win32 kullanarak iletişim kurmak CLR verir `LeaveCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="e4f30-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="e4f30-124">Geçerli tarafından temsil edilen kritik bölüm sahipliğini bir iş parçacığı `IHostCrst` örneği çağırmalıdır `Leave` isteğe bağlı olarak her zaman için bu kritik bölüm girdikten sonra.</span><span class="sxs-lookup"><span data-stu-id="e4f30-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f30-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4f30-125">Requirements</span></span>  
 <span data-ttu-id="e4f30-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f30-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f30-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4f30-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4f30-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e4f30-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4f30-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f30-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f30-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f30-130">See Also</span></span>  
 [<span data-ttu-id="e4f30-131">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f30-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e4f30-132">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f30-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="e4f30-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f30-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
