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
ms.openlocfilehash: ad7856a9376880f867e35f1e63bc2cac1ca216fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794491"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="732cd-102">ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="732cd-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="732cd-103">Bağlama ilkesi, konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="732cd-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="732cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="732cd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="732cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="732cd-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="732cd-106">[in] İlke değerlendirmesi önce derlemeyi bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="732cd-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="732cd-107">[in] İlke verilerini içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="732cd-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="732cd-108">[in] Boyutu `pbApplicationPolicy` arabellek.</span><span class="sxs-lookup"><span data-stu-id="732cd-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="732cd-109">[out] Yeni ilke verilerini değerlendirmesi sonra derlemesine bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="732cd-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="732cd-110">[out içinde] Yeni ilke verilerini değerlendirmesi sonra derleme kimliği başvurusu arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="732cd-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="732cd-111">[out] Mantıksal OR birleşimi için bir işaretçi [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hangi ilkeleri uygulanmış olduğunu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="732cd-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="732cd-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="732cd-112">Return Value</span></span>  
  
|<span data-ttu-id="732cd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="732cd-113">HRESULT</span></span>|<span data-ttu-id="732cd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="732cd-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="732cd-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="732cd-115">S_OK</span></span>|<span data-ttu-id="732cd-116">Değerlendirme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="732cd-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="732cd-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="732cd-117">E_INVALIDARG</span></span>|<span data-ttu-id="732cd-118">Ya da `pwzReferenceIdentity` veya `pbApplicationPolicy` bir null başvurudur.</span><span class="sxs-lookup"><span data-stu-id="732cd-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="732cd-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="732cd-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="732cd-120">`cbAppPolicySize` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="732cd-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="732cd-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="732cd-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="732cd-122">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="732cd-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="732cd-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="732cd-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="732cd-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="732cd-124">The call timed out.</span></span>|  
|<span data-ttu-id="732cd-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="732cd-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="732cd-126">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="732cd-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="732cd-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="732cd-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="732cd-128">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="732cd-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="732cd-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="732cd-129">E_FAIL</span></span>|<span data-ttu-id="732cd-130">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="732cd-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="732cd-131">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="732cd-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="732cd-132">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="732cd-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="732cd-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="732cd-133">Remarks</span></span>  
 <span data-ttu-id="732cd-134">`EvaluatePolicy` Yöntemi özel ana bilgisayar bütünleştirilmiş kod korumak için bağlama ilkesi etkilemek için ana sürüm gereksinimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="732cd-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="732cd-135">İlke altyapısı CLR içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="732cd-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="732cd-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="732cd-136">Requirements</span></span>  
 <span data-ttu-id="732cd-137">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="732cd-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="732cd-138">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="732cd-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="732cd-139">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="732cd-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="732cd-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="732cd-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732cd-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="732cd-141">See also</span></span>

- [<span data-ttu-id="732cd-142">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="732cd-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
