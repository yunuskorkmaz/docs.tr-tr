---
title: "ICLRRuntimeHost::UnloadAppDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.UnloadAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 481f701ae4db15b66596c3af89c2e7aff7a28f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="28531-102">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28531-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="28531-103">Yönetilen bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="28531-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28531-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28531-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28531-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28531-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="28531-106">[in] Kaldırmak için uygulama etki alanı sayısal tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="28531-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="28531-107">[in] `true` ortak dil çalışma zamanı (CLR) uygulamanın geçerli uygulama etki alanını boşaltma denemeden önce iş parçacığının tamamlanana kadar beklemeniz gerekir belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="28531-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28531-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28531-108">Return Value</span></span>  
  
|<span data-ttu-id="28531-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28531-109">HRESULT</span></span>|<span data-ttu-id="28531-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28531-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28531-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28531-111">S_OK</span></span>|<span data-ttu-id="28531-112">`UnloadAppDomain`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="28531-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="28531-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28531-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28531-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="28531-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28531-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28531-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28531-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="28531-116">The call timed out.</span></span>|  
|<span data-ttu-id="28531-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28531-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28531-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="28531-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28531-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28531-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28531-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="28531-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28531-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28531-121">E_FAIL</span></span>|<span data-ttu-id="28531-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="28531-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28531-123">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="28531-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28531-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="28531-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28531-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28531-125">Remarks</span></span>  
 <span data-ttu-id="28531-126">Uygulama etki alanı, geçerli iş parçacığının Yürütülüyor çağırarak sayısal tanıtıcısı alabilirsiniz [Getcurrentappdomainıd](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="28531-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="28531-127">Bu tanımlayıcı karşılık gelen <xref:System.AppDomain.Id%2A> yönetilen özelliği <xref:System.AppDomain> türü.</span><span class="sxs-lookup"><span data-stu-id="28531-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28531-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28531-128">Requirements</span></span>  
 <span data-ttu-id="28531-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28531-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28531-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28531-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28531-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="28531-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28531-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28531-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28531-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28531-133">See Also</span></span>  
 [<span data-ttu-id="28531-134">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28531-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
