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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b7540f166311bbc9e5efa21d136132cc72b7c12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768731"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="fc085-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc085-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="fc085-103">Belirtilen yönetilen derlemede belirtilen türdeki belirtilen yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc085-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc085-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc085-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc085-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc085-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="fc085-106">[in] Yolu <xref:System.Reflection.Assembly> tanımlayan <xref:System.Type> olan yöntemdir çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="fc085-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="fc085-107">[in] Adını <xref:System.Type> çağrılacak yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc085-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="fc085-108">[in] Çağrılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="fc085-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="fc085-109">[in] Yönteme dize parametresi.</span><span class="sxs-lookup"><span data-stu-id="fc085-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="fc085-110">[out] Çağrılan yöntem tarafından döndürülen tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="fc085-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc085-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc085-111">Return Value</span></span>  
  
|<span data-ttu-id="fc085-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc085-112">HRESULT</span></span>|<span data-ttu-id="fc085-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc085-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc085-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc085-114">S_OK</span></span>|<span data-ttu-id="fc085-115">`ExecuteInDefaultAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fc085-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="fc085-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc085-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc085-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="fc085-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc085-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc085-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc085-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fc085-119">The call timed out.</span></span>|  
|<span data-ttu-id="fc085-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc085-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc085-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="fc085-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc085-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc085-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc085-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="fc085-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc085-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc085-124">E_FAIL</span></span>|<span data-ttu-id="fc085-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fc085-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc085-126">Bir yöntem E_FAIL döndürürse, CRL artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc085-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="fc085-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc085-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc085-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc085-128">Remarks</span></span>  
 <span data-ttu-id="fc085-129">Çağrılan yöntemi aşağıdaki imzası sahip olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc085-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="fc085-130">Burada `pwzMethodName` çağrılan yöntemin adını temsil eder ve `pwzArgument` dize değeri, yöntem için parametre olarak geçen temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fc085-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="fc085-131">S_OK için HRESULT değerini ayarlarsanız `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc085-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="fc085-132">Aksi takdirde, `pReturnValue` ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="fc085-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc085-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc085-133">Requirements</span></span>  
 <span data-ttu-id="fc085-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc085-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc085-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc085-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc085-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fc085-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc085-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc085-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc085-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc085-138">See also</span></span>

- [<span data-ttu-id="fc085-139">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc085-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
