---
title: ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141185"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="76f9d-102">ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76f9d-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="76f9d-103">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="76f9d-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76f9d-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76f9d-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="76f9d-106">'ndaki İlke değerlendirmesinden önce derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="76f9d-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="76f9d-107">'ndaki İlke verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="76f9d-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="76f9d-108">'ndaki `pbApplicationPolicy` arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="76f9d-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="76f9d-109">dışı Yeni ilke verileri değerlendirmesinden sonra derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="76f9d-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="76f9d-110">[in, out] Yeni ilke verilerinin değerlendirilmesinden sonra, derleme kimliği başvuru arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76f9d-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="76f9d-111">dışı Hangi ilkelerin uygulandığını belirten, [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) DEĞERLERININ mantıksal veya birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76f9d-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76f9d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76f9d-112">Return Value</span></span>  
  
|<span data-ttu-id="76f9d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76f9d-113">HRESULT</span></span>|<span data-ttu-id="76f9d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76f9d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76f9d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="76f9d-115">S_OK</span></span>|<span data-ttu-id="76f9d-116">Değerlendirme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="76f9d-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="76f9d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="76f9d-117">E_INVALIDARG</span></span>|<span data-ttu-id="76f9d-118">`pwzReferenceIdentity` ya da `pbApplicationPolicy` null bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="76f9d-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="76f9d-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="76f9d-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="76f9d-120">`cbAppPolicySize` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="76f9d-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="76f9d-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76f9d-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76f9d-122">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="76f9d-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76f9d-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76f9d-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76f9d-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="76f9d-124">The call timed out.</span></span>|  
|<span data-ttu-id="76f9d-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76f9d-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76f9d-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="76f9d-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76f9d-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76f9d-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76f9d-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="76f9d-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76f9d-129">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="76f9d-129">E_FAIL</span></span>|<span data-ttu-id="76f9d-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="76f9d-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76f9d-131">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="76f9d-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76f9d-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="76f9d-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f9d-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76f9d-133">Remarks</span></span>  
 <span data-ttu-id="76f9d-134">`EvaluatePolicy` yöntemi konağın konağa özgü derleme sürümü oluşturma gereksinimlerini korumak için bağlama ilkesini etkilemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="76f9d-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="76f9d-135">İlke altyapısının kendisi CLR içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="76f9d-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f9d-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76f9d-136">Requirements</span></span>  
 <span data-ttu-id="76f9d-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f9d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f9d-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="76f9d-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76f9d-139">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="76f9d-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76f9d-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f9d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f9d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76f9d-141">See also</span></span>

- [<span data-ttu-id="76f9d-142">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76f9d-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
