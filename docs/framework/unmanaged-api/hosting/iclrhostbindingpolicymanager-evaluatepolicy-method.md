---
description: ': ICLRHostBindingPolicyManager:: EvaluatePolicy yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e92126a8c12d03ee21e4867754b1a418ef11d463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789976"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="e821d-103">ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e821d-103">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>

<span data-ttu-id="e821d-104">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e821d-104">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e821d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e821d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e821d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e821d-106">Parameters</span></span>  

 `pwzReferenceIdentity`  
 <span data-ttu-id="e821d-107">'ndaki İlke değerlendirmesinden önce derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="e821d-107">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="e821d-108">'ndaki İlke verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e821d-108">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="e821d-109">'ndaki `pbApplicationPolicy` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e821d-109">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="e821d-110">dışı Yeni ilke verileri değerlendirmesinden sonra derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="e821d-110">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="e821d-111">[in, out] Yeni ilke verilerinin değerlendirilmesinden sonra, derleme kimliği başvuru arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e821d-111">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="e821d-112">dışı Hangi ilkelerin uygulandığını belirten, [EBindPolicyLevels](ebindpolicylevels-enumeration.md) DEĞERLERININ mantıksal veya birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e821d-112">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e821d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e821d-113">Return Value</span></span>  
  
|<span data-ttu-id="e821d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e821d-114">HRESULT</span></span>|<span data-ttu-id="e821d-115">Description</span><span class="sxs-lookup"><span data-stu-id="e821d-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e821d-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e821d-116">S_OK</span></span>|<span data-ttu-id="e821d-117">Değerlendirme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e821d-117">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="e821d-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e821d-118">E_INVALIDARG</span></span>|<span data-ttu-id="e821d-119">`pwzReferenceIdentity`Ya da `pbApplicationPolicy` null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="e821d-119">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="e821d-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e821d-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e821d-121">`cbAppPolicySize` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="e821d-121">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="e821d-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e821d-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e821d-123">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e821d-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e821d-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e821d-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e821d-125">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e821d-125">The call timed out.</span></span>|  
|<span data-ttu-id="e821d-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e821d-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e821d-127">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e821d-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e821d-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e821d-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e821d-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e821d-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e821d-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e821d-130">E_FAIL</span></span>|<span data-ttu-id="e821d-131">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e821d-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e821d-132">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e821d-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e821d-133">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e821d-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e821d-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e821d-134">Remarks</span></span>  

 <span data-ttu-id="e821d-135">`EvaluatePolicy`Yöntemi, konağın konağa özgü derleme sürümü oluşturma gereksinimlerini korumak için bağlama ilkesini etkilemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e821d-135">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="e821d-136">İlke altyapısının kendisi CLR içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="e821d-136">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e821d-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e821d-137">Requirements</span></span>  

 <span data-ttu-id="e821d-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e821d-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e821d-139">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e821d-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e821d-140">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e821d-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e821d-141">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e821d-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e821d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e821d-142">See also</span></span>

- [<span data-ttu-id="e821d-143">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e821d-143">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
