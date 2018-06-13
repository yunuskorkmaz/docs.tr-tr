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
ms.openlocfilehash: c7dba595953a305c9da33e255676c4b2dcae7a96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435588"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="b1d61-102">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1d61-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="b1d61-103">Yönetilen bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b1d61-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1d61-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1d61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1d61-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="b1d61-106">[in] Kaldırmak için uygulama etki alanı sayısal tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b1d61-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="b1d61-107">[in] `true` ortak dil çalışma zamanı (CLR) uygulamanın geçerli uygulama etki alanını boşaltma denemeden önce iş parçacığının tamamlanana kadar beklemeniz gerekir belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b1d61-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1d61-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1d61-108">Return Value</span></span>  
  
|<span data-ttu-id="b1d61-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1d61-109">HRESULT</span></span>|<span data-ttu-id="b1d61-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1d61-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1d61-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1d61-111">S_OK</span></span>|<span data-ttu-id="b1d61-112">`UnloadAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b1d61-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="b1d61-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1d61-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1d61-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b1d61-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1d61-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1d61-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1d61-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b1d61-116">The call timed out.</span></span>|  
|<span data-ttu-id="b1d61-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1d61-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1d61-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b1d61-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1d61-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1d61-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1d61-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b1d61-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1d61-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1d61-121">E_FAIL</span></span>|<span data-ttu-id="b1d61-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b1d61-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1d61-123">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b1d61-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1d61-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1d61-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1d61-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1d61-125">Remarks</span></span>  
 <span data-ttu-id="b1d61-126">Uygulama etki alanı, geçerli iş parçacığının Yürütülüyor çağırarak sayısal tanıtıcısı alabilirsiniz [Getcurrentappdomainıd](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="b1d61-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="b1d61-127">Bu tanımlayıcı karşılık gelen <xref:System.AppDomain.Id%2A> yönetilen özelliği <xref:System.AppDomain> türü.</span><span class="sxs-lookup"><span data-stu-id="b1d61-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d61-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1d61-128">Requirements</span></span>  
 <span data-ttu-id="b1d61-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1d61-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d61-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1d61-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1d61-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b1d61-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1d61-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d61-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d61-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1d61-133">See Also</span></span>  
 [<span data-ttu-id="b1d61-134">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1d61-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
