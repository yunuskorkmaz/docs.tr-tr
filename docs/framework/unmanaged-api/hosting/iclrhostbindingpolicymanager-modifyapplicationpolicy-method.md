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
ms.openlocfilehash: 07a4998f86958e21fffc8ba8657ec9f2a170f43e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984665"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="f9025-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9025-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="f9025-103">Belirtilen derleme için bağlama ilkesi değiştirir ve ilke yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9025-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9025-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9025-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f9025-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9025-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="f9025-106">[in] Değiştirilecek derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="f9025-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="f9025-107">[in] Değiştirilen derlemenin yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="f9025-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="f9025-108">[in] Değiştirilecek derleme için bağlama ilkesi verileri içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9025-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="f9025-109">[in] Değiştirilecek bağlama ilkesi boyutu.</span><span class="sxs-lookup"><span data-stu-id="f9025-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="f9025-110">[in] Bir mantıksal OR kombinasyonudur [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) yeniden yönlendirme denetimini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="f9025-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="f9025-111">[out] Yeni veri bağlama ilkesi içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9025-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="f9025-112">[out içinde] Yeni bağlama ilkesi arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9025-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9025-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9025-113">Return Value</span></span>  
  
|<span data-ttu-id="f9025-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9025-114">HRESULT</span></span>|<span data-ttu-id="f9025-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9025-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9025-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9025-116">S_OK</span></span>|<span data-ttu-id="f9025-117">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f9025-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="f9025-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9025-118">E_INVALIDARG</span></span>|<span data-ttu-id="f9025-119">`pwzSourceAssemblyIdentity` veya `pwzTargetAssemblyIdentity` null başvuru oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9025-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="f9025-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f9025-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f9025-121">`pbNewApplicationPolicy` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="f9025-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="f9025-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9025-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9025-123">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="f9025-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9025-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9025-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9025-125">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f9025-125">The call timed out.</span></span>|  
|<span data-ttu-id="f9025-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9025-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9025-127">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f9025-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9025-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9025-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9025-129">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="f9025-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9025-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9025-130">E_FAIL</span></span>|<span data-ttu-id="f9025-131">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9025-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9025-132">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f9025-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9025-133">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9025-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9025-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9025-134">Remarks</span></span>  
 <span data-ttu-id="f9025-135">`ModifyApplicationPolicy` Yöntemi iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9025-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="f9025-136">İlk çağrı için bir null değer sağlamanız `pbNewApplicationPolicy` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f9025-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="f9025-137">Bu çağrı için gerekli olan değerle döndüreceği `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="f9025-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="f9025-138">Bu değer için yapılan ikinci çağrı sunmalıdır `pcbNewAppPolicySize`ve bu boyut için bir arabellek işaret `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="f9025-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9025-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9025-139">Requirements</span></span>  
 <span data-ttu-id="f9025-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9025-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9025-141">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9025-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9025-142">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f9025-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9025-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9025-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9025-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9025-144">See also</span></span>

- [<span data-ttu-id="f9025-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9025-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
