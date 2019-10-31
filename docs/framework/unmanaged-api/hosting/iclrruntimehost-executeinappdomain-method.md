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
ms.openlocfilehash: c847f177f48d72f28192d1efabe93c65a7b3f4b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120499"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="896fa-102">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="896fa-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="896fa-103">Belirtilen yönetilen kodun çalıştırılacağı <xref:System.AppDomain> belirtir.</span><span class="sxs-lookup"><span data-stu-id="896fa-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="896fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="896fa-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="896fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="896fa-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="896fa-106">'ndaki Belirtilen metodun çalıştırılacağı <xref:System.AppDomain> sayısal KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="896fa-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="896fa-107">'ndaki Belirtilen <xref:System.AppDomain>yürütmek için işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="896fa-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="896fa-108">'ndaki Donuk, çağırana ayrılan belleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="896fa-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="896fa-109">Bu parametre, ortak dil çalışma zamanı (CLR) tarafından etki alanı geri çağırması ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="896fa-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="896fa-110">Çalışma zamanı tarafından yönetilen yığın belleği değildir; Bu belleğin ayırma ve yaşam süresi çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="896fa-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="896fa-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="896fa-111">Return Value</span></span>  
  
|<span data-ttu-id="896fa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="896fa-112">HRESULT</span></span>|<span data-ttu-id="896fa-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="896fa-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="896fa-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="896fa-114">S_OK</span></span>|<span data-ttu-id="896fa-115">`ExecuteInAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="896fa-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="896fa-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="896fa-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="896fa-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="896fa-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="896fa-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="896fa-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="896fa-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="896fa-119">The call timed out.</span></span>|  
|<span data-ttu-id="896fa-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="896fa-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="896fa-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="896fa-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="896fa-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="896fa-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="896fa-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="896fa-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="896fa-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="896fa-124">E_FAIL</span></span>|<span data-ttu-id="896fa-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="896fa-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="896fa-126">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="896fa-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="896fa-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="896fa-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="896fa-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="896fa-128">Remarks</span></span>  
 <span data-ttu-id="896fa-129">`ExecuteInAppDomain`, konağın belirtilen yönetilen yöntemin üzerinde yürütülmesi gereken yönetilen <xref:System.AppDomain> denetimi üzerinde çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="896fa-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="896fa-130">[GetCurrentAppDomainId metodunu](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, <xref:System.AppDomain.Id%2A> özelliğinin değerine karşılık gelen bir uygulama etki alanı tanımlayıcısının değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="896fa-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="896fa-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="896fa-131">Requirements</span></span>  
 <span data-ttu-id="896fa-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="896fa-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="896fa-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="896fa-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="896fa-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="896fa-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="896fa-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="896fa-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="896fa-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="896fa-136">See also</span></span>

- [<span data-ttu-id="896fa-137">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="896fa-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
