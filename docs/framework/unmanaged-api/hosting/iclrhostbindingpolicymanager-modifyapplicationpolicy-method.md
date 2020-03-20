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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178096"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="076bf-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="076bf-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="076bf-103">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="076bf-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="076bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="076bf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="076bf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="076bf-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="076bf-106">[içinde] Değiştirilen derlemenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="076bf-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="076bf-107">[içinde] Değiştirilen derlemenin yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="076bf-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="076bf-108">[içinde] Derlemenin değiştirilen bağlama ilkesi verilerini içeren arabelleğe işaretçi.</span><span class="sxs-lookup"><span data-stu-id="076bf-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="076bf-109">[içinde] Değiştirilecek bağlama ilkesinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="076bf-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="076bf-110">[içinde] [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) değerlerinin mantıksal veya birleşimi, yeniden yönlendirme denetimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="076bf-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="076bf-111">[çıkış] Yeni bağlama ilkesi verilerini içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="076bf-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="076bf-112">[içinde, dışarı] Yeni bağlama ilkesi arabelleği boyutuna bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="076bf-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="076bf-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="076bf-113">Return Value</span></span>  
  
|<span data-ttu-id="076bf-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="076bf-114">HRESULT</span></span>|<span data-ttu-id="076bf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="076bf-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="076bf-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="076bf-116">S_OK</span></span>|<span data-ttu-id="076bf-117">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="076bf-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="076bf-118">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="076bf-118">E_INVALIDARG</span></span>|<span data-ttu-id="076bf-119">`pwzSourceAssemblyIdentity`ya `pwzTargetAssemblyIdentity` da null bir referans oldu.</span><span class="sxs-lookup"><span data-stu-id="076bf-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="076bf-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="076bf-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="076bf-121">`pbNewApplicationPolicy`çok küçük.</span><span class="sxs-lookup"><span data-stu-id="076bf-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="076bf-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="076bf-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="076bf-123">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="076bf-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="076bf-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="076bf-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="076bf-125">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="076bf-125">The call timed out.</span></span>|  
|<span data-ttu-id="076bf-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="076bf-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="076bf-127">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="076bf-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="076bf-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="076bf-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="076bf-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="076bf-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="076bf-130">E_faıl</span><span class="sxs-lookup"><span data-stu-id="076bf-130">E_FAIL</span></span>|<span data-ttu-id="076bf-131">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="076bf-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="076bf-132">Bir yöntem E_FAIL döndükten sonra, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="076bf-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="076bf-133">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="076bf-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="076bf-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="076bf-134">Remarks</span></span>  
 <span data-ttu-id="076bf-135">Yöntem `ModifyApplicationPolicy` iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="076bf-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="076bf-136">İlk çağrı `pbNewApplicationPolicy` parametre için null bir değer sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="076bf-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="076bf-137">Bu çağrı için `pcbNewAppPolicySize`gerekli değer ile dönecektir.</span><span class="sxs-lookup"><span data-stu-id="076bf-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="076bf-138">İkinci çağrı için `pcbNewAppPolicySize`bu değeri sağlamalı ve bu boyuttabir `pbNewApplicationPolicy`arabelleğe işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="076bf-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="076bf-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="076bf-139">Requirements</span></span>  
 <span data-ttu-id="076bf-140">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="076bf-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="076bf-141">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="076bf-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="076bf-142">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="076bf-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="076bf-143">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="076bf-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="076bf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="076bf-144">See also</span></span>

- [<span data-ttu-id="076bf-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="076bf-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
