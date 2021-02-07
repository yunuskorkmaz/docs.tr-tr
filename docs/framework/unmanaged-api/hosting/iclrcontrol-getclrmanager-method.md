---
description: ': ICLRControl:: GetCLRManager Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: fc24cbdfd4bebfff5c2f8d73a9cd6961a8c94e94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716724"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="c1d93-103">ICLRControl::GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1d93-103">ICLRControl::GetCLRManager Method</span></span>

<span data-ttu-id="c1d93-104">Konağın ortak dil çalışma zamanını (CLR) yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c1d93-104">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1d93-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1d93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1d93-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1d93-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="c1d93-107">'ndaki `IID` Döndürülecek yönetici türü.</span><span class="sxs-lookup"><span data-stu-id="c1d93-107">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="c1d93-108">Aşağıdaki `IID` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-108">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="c1d93-109">IID_ICLRDebugManager: `ppObject` [ICLRDebugManager](iclrdebugmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-109">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-110">IID_ICLRErrorReportingManager: `ppObject` [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-110">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-111">IID_ICLRGCManager: `ppObject` [ICLRGCManager](iclrgcmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-111">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-112">IID_ICLRHostProtectionManager: `ppObject` [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-112">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-113">IID_ICLROnEventManager: `ppObject` [ICLROnEventManager](iclroneventmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-113">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-114">IID_ICLRPolicyManager: `ppObject` [ICLRPolicyManager](iclrpolicymanager-interface.md)türünde olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-114">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="c1d93-115">IID_ICLRTaskManager: `ppObject` [ICLRTaskManager](iclrtaskmanager-interface.md)türünden olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1d93-115">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c1d93-116">dışı İstenen yöneticinin arabirim işaretçisi veya geçersiz bir yönetici türü isteniyorsa null.</span><span class="sxs-lookup"><span data-stu-id="c1d93-116">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1d93-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1d93-117">Return Value</span></span>  
  
|<span data-ttu-id="c1d93-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1d93-118">HRESULT</span></span>|<span data-ttu-id="c1d93-119">Description</span><span class="sxs-lookup"><span data-stu-id="c1d93-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1d93-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1d93-120">S_OK</span></span>|<span data-ttu-id="c1d93-121">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c1d93-121">The method returned successfully.</span></span>|  
|<span data-ttu-id="c1d93-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1d93-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1d93-123">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c1d93-123">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1d93-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1d93-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1d93-125">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c1d93-125">The call timed out.</span></span>|  
|<span data-ttu-id="c1d93-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1d93-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1d93-127">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c1d93-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1d93-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1d93-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1d93-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c1d93-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1d93-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1d93-130">E_FAIL</span></span>|<span data-ttu-id="c1d93-131">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c1d93-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1d93-132">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1d93-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1d93-133">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1d93-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1d93-134">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c1d93-134">E_NOINTERFACE</span></span>|<span data-ttu-id="c1d93-135">Arabirim türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c1d93-135">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1d93-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1d93-136">Requirements</span></span>  

 <span data-ttu-id="c1d93-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1d93-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1d93-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c1d93-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1d93-139">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c1d93-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1d93-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1d93-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d93-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1d93-141">See also</span></span>

- [<span data-ttu-id="c1d93-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1d93-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c1d93-143">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1d93-143">IHostControl Interface</span></span>](ihostcontrol-interface.md)
