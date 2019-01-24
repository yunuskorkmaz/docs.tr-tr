---
title: ICLRRuntimeHost::UnloadAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6194478922bb1634f8a96de420fb17af10666322
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560964"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="97c6f-102">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97c6f-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="97c6f-103">Yönetilen bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="97c6f-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c6f-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97c6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97c6f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="97c6f-106">[in] Uygulama etki alanını kaldırmak için sayısal tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="97c6f-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="97c6f-107">[in] `true` belirten ortak dil çalışma zamanı (CLR), uygulama etki alanını boşaltma çalışmadan önce uygulamanın geçerli iş parçacığının yürütmesini bitirene kadar beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="97c6f-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97c6f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97c6f-108">Return Value</span></span>  
  
|<span data-ttu-id="97c6f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97c6f-109">HRESULT</span></span>|<span data-ttu-id="97c6f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97c6f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97c6f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="97c6f-111">S_OK</span></span>|<span data-ttu-id="97c6f-112">`UnloadAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="97c6f-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="97c6f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97c6f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97c6f-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="97c6f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97c6f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97c6f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97c6f-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="97c6f-116">The call timed out.</span></span>|  
|<span data-ttu-id="97c6f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97c6f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97c6f-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="97c6f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97c6f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97c6f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97c6f-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="97c6f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97c6f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97c6f-121">E_FAIL</span></span>|<span data-ttu-id="97c6f-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="97c6f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97c6f-123">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97c6f-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97c6f-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="97c6f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97c6f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97c6f-125">Remarks</span></span>  
 <span data-ttu-id="97c6f-126">Sayısal tanımlayıcı, geçerli iş parçacığının yürütülmekte çağırarak uygulama etki alanının alabilirsiniz [Getcurrentappdomainıd](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="97c6f-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="97c6f-127">Bu tanımlayıcı karşılık gelen <xref:System.AppDomain.Id%2A> yönetilen özellik <xref:System.AppDomain> türü.</span><span class="sxs-lookup"><span data-stu-id="97c6f-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c6f-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97c6f-128">Requirements</span></span>  
 <span data-ttu-id="97c6f-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97c6f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c6f-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97c6f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97c6f-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="97c6f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97c6f-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c6f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c6f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c6f-133">See also</span></span>
- [<span data-ttu-id="97c6f-134">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97c6f-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
