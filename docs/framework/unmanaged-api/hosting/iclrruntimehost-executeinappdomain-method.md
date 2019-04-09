---
title: ICLRRuntimeHost::ExecuteInAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86348c35a023e22d10c4ad2e08f5cb1104b895a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165509"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="94224-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94224-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="94224-103">Belirtir <xref:System.AppDomain> burada belirtilen yönetilen kodu yürütmek.</span><span class="sxs-lookup"><span data-stu-id="94224-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94224-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94224-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94224-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94224-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="94224-106">[in] Sayısal kimliği <xref:System.AppDomain> burada belirtilen yöntem yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="94224-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="94224-107">[in] İçinde belirtilen yürütülecek bir işlevi işaretçisi <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="94224-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="94224-108">[in] Donuk arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94224-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="94224-109">Bu parametre, ortak dil çalışma zamanı tarafından (CLR) için etki alanı geri iletilir.</span><span class="sxs-lookup"><span data-stu-id="94224-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="94224-110">Çalışma zamanı Yönetilen yığın bellek değil; hem ayırma hem de bu bellek kullanım ömrünü çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="94224-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94224-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94224-111">Return Value</span></span>  
  
|<span data-ttu-id="94224-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94224-112">HRESULT</span></span>|<span data-ttu-id="94224-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94224-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94224-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="94224-114">S_OK</span></span>|`ExecuteInAppDomain` <span data-ttu-id="94224-115">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="94224-115">returned successfully.</span></span>|  
|<span data-ttu-id="94224-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94224-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94224-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="94224-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94224-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94224-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94224-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="94224-119">The call timed out.</span></span>|  
|<span data-ttu-id="94224-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94224-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94224-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="94224-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94224-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94224-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94224-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="94224-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94224-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94224-124">E_FAIL</span></span>|<span data-ttu-id="94224-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="94224-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94224-126">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="94224-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94224-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="94224-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94224-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94224-128">Remarks</span></span>  
 `ExecuteInAppDomain` <span data-ttu-id="94224-129">Denetim uygulamak amacıyla ana bilgisayar sağlayan yönetilen üzerinden <xref:System.AppDomain> belirtilen Yönetilen yöntemi içinde yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="94224-129">allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="94224-130">Değerine karşılık gelen bir uygulama etki alanının tanımlayıcısının değer elde edebileceği <xref:System.AppDomain.Id%2A> çağırarak özelliği [Getcurrentappdomainıd metodu](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="94224-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94224-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94224-131">Requirements</span></span>  
 <span data-ttu-id="94224-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94224-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94224-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94224-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94224-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="94224-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="94224-135">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="94224-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94224-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94224-136">See also</span></span>

- [<span data-ttu-id="94224-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94224-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
