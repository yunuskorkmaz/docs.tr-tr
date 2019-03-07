---
title: ICLRControl::GetCLRManager Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d3712b9a2100d4efcefe691d68989a1971b045d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488433"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="7cb0c-102">ICLRControl::GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cb0c-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="7cb0c-103">Ortak dil çalışma zamanı (CLR) yapılandırmak için konak kullanabilirsiniz manager türlerinden herhangi birinin bir örneği için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cb0c-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cb0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cb0c-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="7cb0c-106">[in] `IID` Döndürülecek Yöneticisi türü.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="7cb0c-107">Aşağıdaki `IID` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="7cb0c-108">IID_ICLRDebugManager: Belirten `ppObject` türünün [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-109">IID_ICLRErrorReportingManager: Belirten `ppObject` türünün [Iclrerrorreportingmanager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-110">IID_ICLRGCManager: Belirten `ppObject` türünün [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-111">IID_ICLRHostProtectionManager: Belirten `ppObject` türünün [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-112">IID_ICLROnEventManager: Belirten `ppObject` türünün [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-113">IID_ICLRPolicyManager: Belirten `ppObject` türünün [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7cb0c-114">IID_ICLRTaskManager: speciries, `ppObject` türünün [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="7cb0c-115">[out] İstenen Yöneticisi veya null bir geçersiz Yöneticisi türü istendi, bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cb0c-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7cb0c-116">Return Value</span></span>  
  
|<span data-ttu-id="7cb0c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cb0c-117">HRESULT</span></span>|<span data-ttu-id="7cb0c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cb0c-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cb0c-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cb0c-119">S_OK</span></span>|<span data-ttu-id="7cb0c-120">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="7cb0c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cb0c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cb0c-122">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cb0c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cb0c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cb0c-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-124">The call timed out.</span></span>|  
|<span data-ttu-id="7cb0c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cb0c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cb0c-126">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cb0c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cb0c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cb0c-128">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cb0c-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cb0c-129">E_FAIL</span></span>|<span data-ttu-id="7cb0c-130">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cb0c-131">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cb0c-132">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7cb0c-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="7cb0c-133">E_NOINTERFACE</span></span>|<span data-ttu-id="7cb0c-134">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cb0c-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cb0c-135">Requirements</span></span>  
 <span data-ttu-id="7cb0c-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb0c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb0c-137">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7cb0c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cb0c-138">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7cb0c-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cb0c-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb0c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb0c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cb0c-140">See also</span></span>
- [<span data-ttu-id="7cb0c-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cb0c-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7cb0c-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cb0c-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
