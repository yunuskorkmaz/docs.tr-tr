---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176415"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="31716-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31716-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="31716-103">Belirtilen yönetilen derlemede belirtilen türde belirtilen yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="31716-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31716-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31716-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31716-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31716-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="31716-106">[içinde] <xref:System.Reflection.Assembly> Kimin yönteminin <xref:System.Type> çağrılmasını tanımlayan yol.</span><span class="sxs-lookup"><span data-stu-id="31716-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="31716-107">[içinde] <xref:System.Type> Çağırmak için yöntemi tanımlayan adı.</span><span class="sxs-lookup"><span data-stu-id="31716-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="31716-108">[içinde] Çağırmak için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="31716-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="31716-109">[içinde] Yönteme geçmek için dize parametresi.</span><span class="sxs-lookup"><span data-stu-id="31716-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="31716-110">[çıkış] Çağrılan yöntem tarafından döndürülen tümseci değeri.</span><span class="sxs-lookup"><span data-stu-id="31716-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31716-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31716-111">Return Value</span></span>  
  
|<span data-ttu-id="31716-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31716-112">HRESULT</span></span>|<span data-ttu-id="31716-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31716-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31716-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="31716-114">S_OK</span></span>|<span data-ttu-id="31716-115">`ExecuteInDefaultAppDomain`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="31716-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="31716-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="31716-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="31716-117">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="31716-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="31716-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="31716-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="31716-119">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="31716-119">The call timed out.</span></span>|  
|<span data-ttu-id="31716-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31716-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="31716-121">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="31716-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="31716-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="31716-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="31716-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="31716-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="31716-124">E_faıl</span><span class="sxs-lookup"><span data-stu-id="31716-124">E_FAIL</span></span>|<span data-ttu-id="31716-125">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="31716-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="31716-126">Bir yöntem E_FAIL döndürürse, CRL artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31716-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="31716-127">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="31716-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31716-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31716-128">Remarks</span></span>  
 <span data-ttu-id="31716-129">Çağrılan yöntemaşağıdaki imzaya sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="31716-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="31716-130">çağrılan `pwzMethodName` yöntemin adını temsil eder `pwzArgument` ve bu yönteme parametre olarak geçen dize değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31716-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="31716-131">HRESULT değeri S_OK olarak ayarlanırsa, `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="31716-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="31716-132">Aksi `pReturnValue` takdirde, ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="31716-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31716-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31716-133">Requirements</span></span>  
 <span data-ttu-id="31716-134">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31716-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31716-135">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31716-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31716-136">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="31716-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31716-137">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31716-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31716-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31716-138">See also</span></span>

- [<span data-ttu-id="31716-139">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31716-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
