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
ms.openlocfilehash: f3dc6f707511f9d6f4883aecbd2a26a587a902c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="99dcf-102">ICLRControl::GetCLRManager Metodu</span><span class="sxs-lookup"><span data-stu-id="99dcf-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="99dcf-103">Arabirim işaretçisi herhangi bir ana bilgisayar ortak dil çalışma zamanı (CLR) yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="99dcf-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99dcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99dcf-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99dcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99dcf-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="99dcf-106">[in] `IID` Döndürülecek Yöneticisi türü.</span><span class="sxs-lookup"><span data-stu-id="99dcf-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="99dcf-107">Aşağıdaki `IID` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="99dcf-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="99dcf-108">IID_ICLRDebugManager: belirleyen `ppObject` türünün [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-109">IID_ICLRErrorReportingManager: belirleyen `ppObject` türünün [Iclrerrorreportingmanager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-110">IID_ICLRGCManager: belirleyen `ppObject` türünün [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-111">IID_ICLRHostProtectionManager: belirleyen `ppObject` türünün [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-112">IID_ICLROnEventManager: belirleyen `ppObject` türünün [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-113">IID_ICLRPolicyManager: belirleyen `ppObject` türünün [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="99dcf-114">IID_ICLRTaskManager: speciries, `ppObject` türünün [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="99dcf-115">[out] Arabirim işaretçisi istenen Yöneticisi ya da geçersiz Yöneticisi türü istendi yoksa null.</span><span class="sxs-lookup"><span data-stu-id="99dcf-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99dcf-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99dcf-116">Return Value</span></span>  
  
|<span data-ttu-id="99dcf-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99dcf-117">HRESULT</span></span>|<span data-ttu-id="99dcf-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99dcf-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99dcf-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="99dcf-119">S_OK</span></span>|<span data-ttu-id="99dcf-120">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="99dcf-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="99dcf-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99dcf-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99dcf-122">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99dcf-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99dcf-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99dcf-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99dcf-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="99dcf-124">The call timed out.</span></span>|  
|<span data-ttu-id="99dcf-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99dcf-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99dcf-126">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="99dcf-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99dcf-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99dcf-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99dcf-128">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="99dcf-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99dcf-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99dcf-129">E_FAIL</span></span>|<span data-ttu-id="99dcf-130">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99dcf-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99dcf-131">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99dcf-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99dcf-132">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99dcf-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99dcf-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="99dcf-133">E_NOINTERFACE</span></span>|<span data-ttu-id="99dcf-134">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="99dcf-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99dcf-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99dcf-135">Requirements</span></span>  
 <span data-ttu-id="99dcf-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99dcf-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99dcf-137">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99dcf-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99dcf-138">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="99dcf-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99dcf-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99dcf-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99dcf-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99dcf-140">See Also</span></span>  
 [<span data-ttu-id="99dcf-141">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="99dcf-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="99dcf-142">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="99dcf-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
