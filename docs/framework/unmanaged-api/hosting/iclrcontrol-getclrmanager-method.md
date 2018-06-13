---
title: ICLRControl::GetCLRManager Metodu
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
ms.openlocfilehash: f375afde247c3a9b95e1220df747d3f2b95e2840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436435"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="5448d-102">ICLRControl::GetCLRManager Metodu</span><span class="sxs-lookup"><span data-stu-id="5448d-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="5448d-103">Arabirim işaretçisi herhangi bir ana bilgisayar ortak dil çalışma zamanı (CLR) yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5448d-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5448d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5448d-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5448d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5448d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="5448d-106">[in] `IID` Döndürülecek Yöneticisi türü.</span><span class="sxs-lookup"><span data-stu-id="5448d-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="5448d-107">Aşağıdaki `IID` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5448d-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="5448d-108">IID_ICLRDebugManager: belirleyen `ppObject` türünün [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-109">IID_ICLRErrorReportingManager: belirleyen `ppObject` türünün [Iclrerrorreportingmanager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-110">IID_ICLRGCManager: belirleyen `ppObject` türünün [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-111">IID_ICLRHostProtectionManager: belirleyen `ppObject` türünün [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-112">IID_ICLROnEventManager: belirleyen `ppObject` türünün [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-113">IID_ICLRPolicyManager: belirleyen `ppObject` türünün [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5448d-114">IID_ICLRTaskManager: speciries, `ppObject` türünün [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="5448d-115">[out] Arabirim işaretçisi istenen Yöneticisi ya da geçersiz Yöneticisi türü istendi yoksa null.</span><span class="sxs-lookup"><span data-stu-id="5448d-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5448d-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5448d-116">Return Value</span></span>  
  
|<span data-ttu-id="5448d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5448d-117">HRESULT</span></span>|<span data-ttu-id="5448d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5448d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5448d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="5448d-119">S_OK</span></span>|<span data-ttu-id="5448d-120">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5448d-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="5448d-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5448d-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5448d-122">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5448d-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5448d-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5448d-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5448d-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5448d-124">The call timed out.</span></span>|  
|<span data-ttu-id="5448d-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5448d-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5448d-126">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="5448d-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5448d-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5448d-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5448d-128">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="5448d-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5448d-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5448d-129">E_FAIL</span></span>|<span data-ttu-id="5448d-130">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5448d-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5448d-131">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5448d-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5448d-132">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5448d-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5448d-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="5448d-133">E_NOINTERFACE</span></span>|<span data-ttu-id="5448d-134">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5448d-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5448d-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5448d-135">Requirements</span></span>  
 <span data-ttu-id="5448d-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5448d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5448d-137">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5448d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5448d-138">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5448d-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5448d-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5448d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5448d-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5448d-140">See Also</span></span>  
 [<span data-ttu-id="5448d-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5448d-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="5448d-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5448d-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
