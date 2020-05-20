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
ms.openlocfilehash: e32714bba2403752f1ac2551ab182f2655f1fa75
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703862"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="6fc77-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6fc77-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="6fc77-103">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fc77-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc77-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6fc77-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6fc77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6fc77-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="6fc77-106">'ndaki Değiştirilecek derlemenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="6fc77-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="6fc77-107">'ndaki Değiştirilen derlemenin yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="6fc77-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="6fc77-108">'ndaki Değiştirilecek derleme için bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="6fc77-109">'ndaki Değiştirilmekte olan bağlama ilkesinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="6fc77-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="6fc77-110">'ndaki Yeniden yönlendirme denetimini gösteren [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) DEĞERLERININ mantıksal veya birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="6fc77-111">dışı Yeni bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="6fc77-112">[in, out] Yeni bağlama ilkesi arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fc77-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6fc77-113">Return Value</span></span>  
  
|<span data-ttu-id="6fc77-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6fc77-114">HRESULT</span></span>|<span data-ttu-id="6fc77-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fc77-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6fc77-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="6fc77-116">S_OK</span></span>|<span data-ttu-id="6fc77-117">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="6fc77-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6fc77-118">E_INVALIDARG</span></span>|<span data-ttu-id="6fc77-119">`pwzSourceAssemblyIdentity`ya da `pwzTargetAssemblyIdentity` null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="6fc77-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="6fc77-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6fc77-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6fc77-121">`pbNewApplicationPolicy`çok küçük.</span><span class="sxs-lookup"><span data-stu-id="6fc77-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="6fc77-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6fc77-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6fc77-123">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6fc77-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6fc77-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6fc77-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6fc77-125">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6fc77-125">The call timed out.</span></span>|  
|<span data-ttu-id="6fc77-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6fc77-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6fc77-127">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6fc77-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6fc77-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6fc77-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6fc77-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6fc77-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6fc77-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6fc77-130">E_FAIL</span></span>|<span data-ttu-id="6fc77-131">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6fc77-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6fc77-132">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6fc77-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6fc77-133">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6fc77-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fc77-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fc77-134">Remarks</span></span>  
 <span data-ttu-id="6fc77-135">`ModifyApplicationPolicy`Yöntemi iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6fc77-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="6fc77-136">İlk çağrı, parametre için null değer sağlamalıdır `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="6fc77-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="6fc77-137">Bu çağrı için gerekli olan değer ile birlikte döndürülür `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="6fc77-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="6fc77-138">İkinci çağrı için bu değeri sağlamalı `pcbNewAppPolicySize` ve için bu boyut için bir arabellek göstermelidir `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="6fc77-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fc77-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fc77-139">Requirements</span></span>  
 <span data-ttu-id="6fc77-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fc77-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fc77-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6fc77-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fc77-142">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6fc77-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fc77-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fc77-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc77-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fc77-144">See also</span></span>

- [<span data-ttu-id="6fc77-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6fc77-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
