---
description: ': ICLRRuntimeHost:: ExecuteInAppDomain yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6640713b55e05817f39af819d5e41ee1f2a10b68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799752"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="82665-103">ICLRRuntimeHost::ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82665-103">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="82665-104"><xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82665-104">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82665-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82665-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82665-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82665-106">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="82665-107">'ndaki Belirtilen metodun çalıştırılacağı sayısal KIMLIĞI <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="82665-107">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="82665-108">'ndaki Belirtilen içinde yürütülecek işleve yönelik bir işaretçi <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="82665-108">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="82665-109">'ndaki Donuk, çağırana ayrılan belleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82665-109">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="82665-110">Bu parametre, ortak dil çalışma zamanı (CLR) tarafından etki alanı geri çağırması ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="82665-110">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="82665-111">Çalışma zamanı tarafından yönetilen yığın belleği değildir; Bu belleğin ayırma ve yaşam süresi çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="82665-111">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82665-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82665-112">Return Value</span></span>  
  
|<span data-ttu-id="82665-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82665-113">HRESULT</span></span>|<span data-ttu-id="82665-114">Description</span><span class="sxs-lookup"><span data-stu-id="82665-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82665-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="82665-115">S_OK</span></span>|<span data-ttu-id="82665-116">`ExecuteInAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="82665-116">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="82665-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82665-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82665-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="82665-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82665-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82665-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82665-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="82665-120">The call timed out.</span></span>|  
|<span data-ttu-id="82665-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82665-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82665-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="82665-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82665-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82665-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82665-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="82665-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82665-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82665-125">E_FAIL</span></span>|<span data-ttu-id="82665-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="82665-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82665-127">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="82665-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82665-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="82665-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82665-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82665-129">Remarks</span></span>  

 <span data-ttu-id="82665-130">`ExecuteInAppDomain` Konağın, <xref:System.AppDomain> belirtilen yönetilen yöntemin üzerinde yürütülmesi gereken yönetilen yöntemi kontrol etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="82665-130">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="82665-131"><xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId metodunu](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, özelliğin değerine karşılık gelen bir uygulama etki alanı tanımlayıcısının değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82665-131">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82665-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82665-132">Requirements</span></span>  

 <span data-ttu-id="82665-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82665-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82665-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="82665-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82665-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="82665-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82665-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82665-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82665-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82665-137">See also</span></span>

- [<span data-ttu-id="82665-138">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82665-138">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
