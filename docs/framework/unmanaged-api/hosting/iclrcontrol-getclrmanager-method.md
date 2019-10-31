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
ms.openlocfilehash: fa9608423456caeb6020e883a14f2c41583ac4d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126608"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="c3c7c-102">ICLRControl::GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3c7c-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="c3c7c-103">Konağın ortak dil çalışma zamanını (CLR) yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3c7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3c7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3c7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3c7c-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c3c7c-106">'ndaki Döndürülecek yönetici türünün `IID`.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="c3c7c-107">Aşağıdaki `IID` değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="c3c7c-108">IID_ICLRDebugManager: `ppObject` [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-109">IID_ICLRErrorReportingManager: `ppObject` [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-110">IID_ICLRGCManager: `ppObject` [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-111">IID_ICLRHostProtectionManager: `ppObject` [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-112">IID_ICLROnEventManager: `ppObject` [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-113">IID_ICLRPolicyManager: `ppObject` [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="c3c7c-114">IID_ICLRTaskManager: `ppObject` [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c3c7c-115">dışı İstenen yöneticinin arabirim işaretçisi veya geçersiz bir yönetici türü isteniyorsa null.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3c7c-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3c7c-116">Return Value</span></span>  
  
|<span data-ttu-id="c3c7c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3c7c-117">HRESULT</span></span>|<span data-ttu-id="c3c7c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3c7c-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3c7c-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3c7c-119">S_OK</span></span>|<span data-ttu-id="c3c7c-120">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="c3c7c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3c7c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3c7c-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3c7c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3c7c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3c7c-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-124">The call timed out.</span></span>|  
|<span data-ttu-id="c3c7c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3c7c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3c7c-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3c7c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3c7c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3c7c-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3c7c-129">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c3c7c-129">E_FAIL</span></span>|<span data-ttu-id="c3c7c-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3c7c-131">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3c7c-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c3c7c-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c3c7c-133">E_NOINTERFACE</span></span>|<span data-ttu-id="c3c7c-134">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3c7c-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3c7c-135">Requirements</span></span>  
 <span data-ttu-id="c3c7c-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3c7c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3c7c-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3c7c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3c7c-138">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c3c7c-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3c7c-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3c7c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c7c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3c7c-140">See also</span></span>

- [<span data-ttu-id="c3c7c-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3c7c-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c3c7c-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3c7c-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
