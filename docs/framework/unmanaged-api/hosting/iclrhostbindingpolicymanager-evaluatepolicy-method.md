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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e37d56a321e6529812045e37c4f1929818b38a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433613"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="2d50d-102">ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d50d-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="2d50d-103">Ana bilgisayar adına bağlama ilkeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2d50d-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d50d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d50d-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d50d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d50d-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="2d50d-106">[in] İlke değerlendirmesi önce derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="2d50d-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="2d50d-107">[in] İlke verilerini içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d50d-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="2d50d-108">[in] Boyutunu `pbApplicationPolicy` arabellek.</span><span class="sxs-lookup"><span data-stu-id="2d50d-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="2d50d-109">[out] Yeni ilke verilerini değerlendirme sonra derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="2d50d-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="2d50d-110">[içinde out] Yeni ilke verilerini değerlendirme sonra derleme kimlik başvuru arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d50d-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="2d50d-111">[out] Mantıksal OR birleşimi için bir işaretçi [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hangi ilkelerin uygulanmış olduğunu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2d50d-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d50d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d50d-112">Return Value</span></span>  
  
|<span data-ttu-id="2d50d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d50d-113">HRESULT</span></span>|<span data-ttu-id="2d50d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d50d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d50d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d50d-115">S_OK</span></span>|<span data-ttu-id="2d50d-116">Değerlendirme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2d50d-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="2d50d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2d50d-117">E_INVALIDARG</span></span>|<span data-ttu-id="2d50d-118">Ya da `pwzReferenceIdentity` veya `pbApplicationPolicy` bir null başvuru.</span><span class="sxs-lookup"><span data-stu-id="2d50d-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="2d50d-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2d50d-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2d50d-120">`cbAppPolicySize` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="2d50d-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="2d50d-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d50d-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d50d-122">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2d50d-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d50d-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d50d-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d50d-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2d50d-124">The call timed out.</span></span>|  
|<span data-ttu-id="2d50d-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d50d-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d50d-126">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2d50d-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d50d-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d50d-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d50d-128">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2d50d-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d50d-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d50d-129">E_FAIL</span></span>|<span data-ttu-id="2d50d-130">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2d50d-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d50d-131">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2d50d-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d50d-132">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d50d-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d50d-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d50d-133">Remarks</span></span>  
 <span data-ttu-id="2d50d-134">`EvaluatePolicy` Yöntemi ana bilgisayara özgü derleme korumak için bağlama ilkesi etkilemek için ana sürüm gereksinimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d50d-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="2d50d-135">İlke altyapısı CLR'nin içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="2d50d-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d50d-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d50d-136">Requirements</span></span>  
 <span data-ttu-id="2d50d-137">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d50d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d50d-138">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d50d-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d50d-139">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d50d-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d50d-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d50d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d50d-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d50d-141">See Also</span></span>  
 [<span data-ttu-id="2d50d-142">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d50d-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
