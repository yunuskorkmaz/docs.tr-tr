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
ms.openlocfilehash: d5323538447e083a0c727e43261dd68337182b9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141082"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="ac692-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac692-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="ac692-103">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac692-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac692-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac692-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ac692-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac692-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="ac692-106">'ndaki Değiştirilecek derlemenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="ac692-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="ac692-107">'ndaki Değiştirilen derlemenin yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="ac692-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="ac692-108">'ndaki Değiştirilecek derleme için bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac692-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="ac692-109">'ndaki Değiştirilmekte olan bağlama ilkesinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac692-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="ac692-110">'ndaki Yeniden yönlendirme denetimini gösteren [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) DEĞERLERININ mantıksal veya birleşimi.</span><span class="sxs-lookup"><span data-stu-id="ac692-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="ac692-111">dışı Yeni bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac692-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="ac692-112">[in, out] Yeni bağlama ilkesi arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac692-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac692-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac692-113">Return Value</span></span>  
  
|<span data-ttu-id="ac692-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac692-114">HRESULT</span></span>|<span data-ttu-id="ac692-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac692-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac692-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac692-116">S_OK</span></span>|<span data-ttu-id="ac692-117">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ac692-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="ac692-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ac692-118">E_INVALIDARG</span></span>|<span data-ttu-id="ac692-119">`pwzSourceAssemblyIdentity` veya `pwzTargetAssemblyIdentity` null bir başvuruya sahip.</span><span class="sxs-lookup"><span data-stu-id="ac692-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="ac692-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ac692-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ac692-121">`pbNewApplicationPolicy` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="ac692-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="ac692-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac692-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac692-123">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ac692-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac692-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac692-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac692-125">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac692-125">The call timed out.</span></span>|  
|<span data-ttu-id="ac692-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac692-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac692-127">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac692-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac692-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac692-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac692-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ac692-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac692-130">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="ac692-130">E_FAIL</span></span>|<span data-ttu-id="ac692-131">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac692-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac692-132">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac692-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac692-133">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac692-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac692-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac692-134">Remarks</span></span>  
 <span data-ttu-id="ac692-135">`ModifyApplicationPolicy` yöntemi iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac692-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="ac692-136">İlk çağrı `pbNewApplicationPolicy` parametresi için null değer sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac692-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="ac692-137">Bu çağrı, `pcbNewAppPolicySize`için gereken değerle birlikte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ac692-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="ac692-138">İkinci çağrı `pcbNewAppPolicySize`için bu değeri sağlamalı ve `pbNewApplicationPolicy`için bu boyuttaki bir arabelleğe işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac692-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac692-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac692-139">Requirements</span></span>  
 <span data-ttu-id="ac692-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac692-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac692-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac692-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac692-142">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ac692-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac692-143">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac692-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac692-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac692-144">See also</span></span>

- [<span data-ttu-id="ac692-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac692-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
