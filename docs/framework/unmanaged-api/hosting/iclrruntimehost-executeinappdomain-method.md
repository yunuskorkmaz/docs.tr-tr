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
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176428"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="d07d5-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d07d5-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="d07d5-103">Belirtilen yönetilen <xref:System.AppDomain> kodun yürütülmek için hangi sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d07d5-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d07d5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d07d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d07d5-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="d07d5-106">[içinde] Belirtilen yöntemin <xref:System.AppDomain> yürütülmesi için sayısal kimlik.</span><span class="sxs-lookup"><span data-stu-id="d07d5-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="d07d5-107">[içinde] Belirtilen <xref:System.AppDomain>içinde yürütmek için işlev için bir işaretçi .</span><span class="sxs-lookup"><span data-stu-id="d07d5-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="d07d5-108">[içinde] Opak arayan ayrılmış bellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d07d5-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="d07d5-109">Bu parametre ortak dil çalışma süresi (CLR) tarafından etki alanı geri arama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d07d5-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="d07d5-110">Çalışma zamanı yönetilen yığın belleği değildir; bu belleğin hem tahsisi hem de kullanım ömrü arayan tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="d07d5-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d07d5-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d07d5-111">Return Value</span></span>  
  
|<span data-ttu-id="d07d5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d07d5-112">HRESULT</span></span>|<span data-ttu-id="d07d5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d07d5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d07d5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d07d5-114">S_OK</span></span>|<span data-ttu-id="d07d5-115">`ExecuteInAppDomain`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d07d5-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="d07d5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d07d5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d07d5-117">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="d07d5-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d07d5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d07d5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d07d5-119">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="d07d5-119">The call timed out.</span></span>|  
|<span data-ttu-id="d07d5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d07d5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d07d5-121">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="d07d5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d07d5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d07d5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d07d5-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d07d5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d07d5-124">E_faıl</span><span class="sxs-lookup"><span data-stu-id="d07d5-124">E_FAIL</span></span>|<span data-ttu-id="d07d5-125">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="d07d5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d07d5-126">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d07d5-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d07d5-127">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="d07d5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d07d5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d07d5-128">Remarks</span></span>  
 <span data-ttu-id="d07d5-129">`ExecuteInAppDomain`ev sahibinin, belirtilen yönetilen <xref:System.AppDomain> yöntemin hangi şekilde yönetildiği üzerinde yürütülmesi gerektiğini denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07d5-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="d07d5-130"><xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId Yöntemi'ni](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)arayarak, bir uygulama etki alanının özelliğinin değerine karşılık gelen tanımlayıcısının değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d07d5-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d07d5-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d07d5-131">Requirements</span></span>  
 <span data-ttu-id="d07d5-132">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d07d5-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d07d5-133">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d07d5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d07d5-134">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="d07d5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d07d5-135">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d07d5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07d5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d07d5-136">See also</span></span>

- [<span data-ttu-id="d07d5-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d07d5-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
