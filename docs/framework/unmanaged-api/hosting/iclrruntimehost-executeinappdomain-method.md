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
ms.openlocfilehash: 505c16cb7ead7950b6d2d6d401730cc3368fb6aa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703300"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="ce7d6-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce7d6-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="ce7d6-103"><xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7d6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ce7d6-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce7d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce7d6-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="ce7d6-106">'ndaki Belirtilen metodun çalıştırılacağı sayısal KIMLIĞI <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ce7d6-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="ce7d6-107">'ndaki Belirtilen içinde yürütülecek işleve yönelik bir işaretçi <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ce7d6-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="ce7d6-108">'ndaki Donuk, çağırana ayrılan belleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="ce7d6-109">Bu parametre, ortak dil çalışma zamanı (CLR) tarafından etki alanı geri çağırması ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="ce7d6-110">Çalışma zamanı tarafından yönetilen yığın belleği değildir; Bu belleğin ayırma ve yaşam süresi çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce7d6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ce7d6-111">Return Value</span></span>  
  
|<span data-ttu-id="ce7d6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce7d6-112">HRESULT</span></span>|<span data-ttu-id="ce7d6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce7d6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce7d6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce7d6-114">S_OK</span></span>|<span data-ttu-id="ce7d6-115">`ExecuteInAppDomain`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="ce7d6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ce7d6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce7d6-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce7d6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce7d6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce7d6-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-119">The call timed out.</span></span>|  
|<span data-ttu-id="ce7d6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce7d6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce7d6-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce7d6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce7d6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce7d6-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce7d6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce7d6-124">E_FAIL</span></span>|<span data-ttu-id="ce7d6-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce7d6-126">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce7d6-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce7d6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce7d6-128">Remarks</span></span>  
 <span data-ttu-id="ce7d6-129">`ExecuteInAppDomain`Konağın, <xref:System.AppDomain> belirtilen yönetilen yöntemin üzerinde yürütülmesi gereken yönetilen yöntemi kontrol etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="ce7d6-130"><xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId metodunu](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, özelliğin değerine karşılık gelen bir uygulama etki alanı tanımlayıcısının değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7d6-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce7d6-131">Requirements</span></span>  
 <span data-ttu-id="ce7d6-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7d6-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7d6-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce7d6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce7d6-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ce7d6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce7d6-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce7d6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7d6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce7d6-136">See also</span></span>

- [<span data-ttu-id="ce7d6-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce7d6-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
