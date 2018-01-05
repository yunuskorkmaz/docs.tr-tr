---
title: ICLRControl::GetCLRManager Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.GetCLRManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 197a3818de8d0b17331a9f9ac422ecaabb230a50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="e2fca-102">ICLRControl::GetCLRManager Metodu</span><span class="sxs-lookup"><span data-stu-id="e2fca-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="e2fca-103">Arabirim işaretçisi herhangi bir ana bilgisayar ortak dil çalışma zamanı (CLR) yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="e2fca-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2fca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2fca-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2fca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2fca-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e2fca-106">[in] `IID` Döndürülecek Yöneticisi türü.</span><span class="sxs-lookup"><span data-stu-id="e2fca-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="e2fca-107">Aşağıdaki `IID` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e2fca-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="e2fca-108">IID_ICLRDebugManager: belirleyen `ppObject` türünün [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-109">IID_ICLRErrorReportingManager: belirleyen `ppObject` türünün [Iclrerrorreportingmanager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-110">IID_ICLRGCManager: belirleyen `ppObject` türünün [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-111">IID_ICLRHostProtectionManager: belirleyen `ppObject` türünün [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-112">IID_ICLROnEventManager: belirleyen `ppObject` türünün [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-113">IID_ICLRPolicyManager: belirleyen `ppObject` türünün [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="e2fca-114">IID_ICLRTaskManager: speciries, `ppObject` türünün [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="e2fca-115">[out] Arabirim işaretçisi istenen Yöneticisi ya da geçersiz Yöneticisi türü istendi yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e2fca-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2fca-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2fca-116">Return Value</span></span>  
  
|<span data-ttu-id="e2fca-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2fca-117">HRESULT</span></span>|<span data-ttu-id="e2fca-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2fca-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2fca-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2fca-119">S_OK</span></span>|<span data-ttu-id="e2fca-120">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e2fca-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="e2fca-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2fca-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2fca-122">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e2fca-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e2fca-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2fca-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2fca-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e2fca-124">The call timed out.</span></span>|  
|<span data-ttu-id="e2fca-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2fca-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2fca-126">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e2fca-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2fca-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2fca-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2fca-128">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e2fca-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2fca-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2fca-129">E_FAIL</span></span>|<span data-ttu-id="e2fca-130">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e2fca-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2fca-131">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e2fca-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2fca-132">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2fca-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e2fca-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e2fca-133">E_NOINTERFACE</span></span>|<span data-ttu-id="e2fca-134">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e2fca-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2fca-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2fca-135">Requirements</span></span>  
 <span data-ttu-id="e2fca-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2fca-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2fca-137">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2fca-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2fca-138">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e2fca-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2fca-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2fca-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fca-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2fca-140">See Also</span></span>  
 [<span data-ttu-id="e2fca-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2fca-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="e2fca-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2fca-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
