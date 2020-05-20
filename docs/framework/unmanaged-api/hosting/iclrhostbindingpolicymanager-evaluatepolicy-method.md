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
ms.openlocfilehash: f72a66354bfc907dab7ebc24de515bdfb20ddfb2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703600"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="05610-102">ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05610-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="05610-103">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="05610-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05610-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="05610-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="05610-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05610-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="05610-106">'ndaki İlke değerlendirmesinden önce derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="05610-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="05610-107">'ndaki İlke verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="05610-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="05610-108">'ndaki `pbApplicationPolicy`Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="05610-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="05610-109">dışı Yeni ilke verileri değerlendirmesinden sonra derlemeye bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="05610-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="05610-110">[in, out] Yeni ilke verilerinin değerlendirilmesinden sonra, derleme kimliği başvuru arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05610-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="05610-111">dışı Hangi ilkelerin uygulandığını belirten, [EBindPolicyLevels](ebindpolicylevels-enumeration.md) DEĞERLERININ mantıksal veya birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05610-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05610-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05610-112">Return Value</span></span>  
  
|<span data-ttu-id="05610-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05610-113">HRESULT</span></span>|<span data-ttu-id="05610-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05610-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05610-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="05610-115">S_OK</span></span>|<span data-ttu-id="05610-116">Değerlendirme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="05610-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="05610-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="05610-117">E_INVALIDARG</span></span>|<span data-ttu-id="05610-118">`pwzReferenceIdentity`Ya da `pbApplicationPolicy` null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="05610-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="05610-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="05610-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="05610-120">`cbAppPolicySize`çok küçük.</span><span class="sxs-lookup"><span data-stu-id="05610-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="05610-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05610-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05610-122">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="05610-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05610-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05610-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05610-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="05610-124">The call timed out.</span></span>|  
|<span data-ttu-id="05610-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05610-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05610-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="05610-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05610-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05610-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05610-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="05610-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05610-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05610-129">E_FAIL</span></span>|<span data-ttu-id="05610-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="05610-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05610-131">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05610-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05610-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="05610-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05610-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05610-133">Remarks</span></span>  
 <span data-ttu-id="05610-134">`EvaluatePolicy`Yöntemi, konağın konağa özgü derleme sürümü oluşturma gereksinimlerini korumak için bağlama ilkesini etkilemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="05610-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="05610-135">İlke altyapısının kendisi CLR içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="05610-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05610-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05610-136">Requirements</span></span>  
 <span data-ttu-id="05610-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05610-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05610-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05610-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05610-139">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="05610-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05610-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05610-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05610-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05610-141">See also</span></span>

- [<span data-ttu-id="05610-142">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05610-142">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
