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
ms.openlocfilehash: 4c28c4a5cc64b20c9ac9c57e1aef5e7b90a20e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728894"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="5321d-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5321d-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="5321d-103"><xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5321d-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5321d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5321d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5321d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5321d-105">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="5321d-106">'ndaki Belirtilen metodun çalıştırılacağı sayısal KIMLIĞI <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5321d-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="5321d-107">'ndaki Belirtilen içinde yürütülecek işleve yönelik bir işaretçi <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5321d-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="5321d-108">'ndaki Donuk, çağırana ayrılan belleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5321d-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="5321d-109">Bu parametre, ortak dil çalışma zamanı (CLR) tarafından etki alanı geri çağırması ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5321d-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="5321d-110">Çalışma zamanı tarafından yönetilen yığın belleği değildir; Bu belleğin ayırma ve yaşam süresi çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="5321d-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5321d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5321d-111">Return Value</span></span>  
  
|<span data-ttu-id="5321d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5321d-112">HRESULT</span></span>|<span data-ttu-id="5321d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5321d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5321d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5321d-114">S_OK</span></span>|<span data-ttu-id="5321d-115">`ExecuteInAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5321d-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="5321d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5321d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5321d-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5321d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5321d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5321d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5321d-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5321d-119">The call timed out.</span></span>|  
|<span data-ttu-id="5321d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5321d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5321d-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5321d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5321d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5321d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5321d-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5321d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5321d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5321d-124">E_FAIL</span></span>|<span data-ttu-id="5321d-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5321d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5321d-126">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5321d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5321d-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5321d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5321d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5321d-128">Remarks</span></span>  

 <span data-ttu-id="5321d-129">`ExecuteInAppDomain` Konağın, <xref:System.AppDomain> belirtilen yönetilen yöntemin üzerinde yürütülmesi gereken yönetilen yöntemi kontrol etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5321d-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="5321d-130"><xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId metodunu](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, özelliğin değerine karşılık gelen bir uygulama etki alanı tanımlayıcısının değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5321d-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5321d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5321d-131">Requirements</span></span>  

 <span data-ttu-id="5321d-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5321d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5321d-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5321d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5321d-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5321d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5321d-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5321d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5321d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5321d-136">See also</span></span>

- [<span data-ttu-id="5321d-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5321d-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
