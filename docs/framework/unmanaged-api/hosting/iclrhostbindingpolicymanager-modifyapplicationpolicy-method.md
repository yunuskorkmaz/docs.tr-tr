---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a221b286ada97c3c03387556cb30ee6ddd2c453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436260"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="18981-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18981-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="18981-103">Bağlama ilkesi için belirtilen derlemeyi değiştirir ve ilke yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18981-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18981-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18981-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18981-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18981-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="18981-106">[in] Değiştirmek için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="18981-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="18981-107">[in] Değiştirilen derleme yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="18981-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="18981-108">[in] Veri bağlama ilkesini değiştirmek derleme içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18981-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="18981-109">[in] Değiştirilecek bağlama ilkesi boyutu.</span><span class="sxs-lookup"><span data-stu-id="18981-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="18981-110">[in] Mantıksal OR bileşimini [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) yeniden yönlendirme denetimini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="18981-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="18981-111">[out] Yeni bağlama ilke verilerini içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18981-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="18981-112">[içinde out] Yeni bağlama ilkesi arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18981-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18981-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="18981-113">Return Value</span></span>  
  
|<span data-ttu-id="18981-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18981-114">HRESULT</span></span>|<span data-ttu-id="18981-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18981-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18981-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="18981-116">S_OK</span></span>|<span data-ttu-id="18981-117">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="18981-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="18981-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="18981-118">E_INVALIDARG</span></span>|<span data-ttu-id="18981-119">`pwzSourceAssemblyIdentity` veya `pwzTargetAssemblyIdentity` null bir başvuru olduğundan.</span><span class="sxs-lookup"><span data-stu-id="18981-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="18981-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="18981-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="18981-121">`pbNewApplicationPolicy` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="18981-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="18981-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18981-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18981-123">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="18981-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18981-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18981-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18981-125">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="18981-125">The call timed out.</span></span>|  
|<span data-ttu-id="18981-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18981-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18981-127">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="18981-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18981-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18981-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18981-129">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="18981-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18981-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18981-130">E_FAIL</span></span>|<span data-ttu-id="18981-131">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="18981-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18981-132">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="18981-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18981-133">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="18981-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18981-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18981-134">Remarks</span></span>  
 <span data-ttu-id="18981-135">`ModifyApplicationPolicy` Yöntemi iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="18981-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="18981-136">İlk çağrı için boş bir değer sağlamanız `pbNewApplicationPolicy` parametresi.</span><span class="sxs-lookup"><span data-stu-id="18981-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="18981-137">Bu çağrı için gerekli değerle döndürülecek `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="18981-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="18981-138">Bu değer için ikinci çağrı sağlamanız `pcbNewAppPolicySize`ve bu boyut için bir arabellek noktasına `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="18981-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18981-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18981-139">Requirements</span></span>  
 <span data-ttu-id="18981-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18981-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18981-141">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18981-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18981-142">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="18981-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18981-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18981-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18981-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18981-144">See Also</span></span>  
 [<span data-ttu-id="18981-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18981-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
