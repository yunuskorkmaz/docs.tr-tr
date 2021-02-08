---
description: ': ICLRHostBindingPolicyManager:: ModifyApplicationPolicy Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3f7d992f4b7d24233da175814f991106bb97a937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789937"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="b2001-103">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2001-103">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>

<span data-ttu-id="b2001-104">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2001-104">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2001-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2001-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b2001-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2001-106">Parameters</span></span>  

 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="b2001-107">'ndaki Değiştirilecek derlemenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="b2001-107">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="b2001-108">'ndaki Değiştirilen derlemenin yeni kimliği.</span><span class="sxs-lookup"><span data-stu-id="b2001-108">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="b2001-109">'ndaki Değiştirilecek derleme için bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b2001-109">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="b2001-110">'ndaki Değiştirilmekte olan bağlama ilkesinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b2001-110">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="b2001-111">'ndaki Yeniden yönlendirme denetimini gösteren [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) DEĞERLERININ mantıksal veya birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b2001-111">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="b2001-112">dışı Yeni bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b2001-112">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="b2001-113">[in, out] Yeni bağlama ilkesi arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2001-113">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2001-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2001-114">Return Value</span></span>  
  
|<span data-ttu-id="b2001-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2001-115">HRESULT</span></span>|<span data-ttu-id="b2001-116">Description</span><span class="sxs-lookup"><span data-stu-id="b2001-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2001-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2001-117">S_OK</span></span>|<span data-ttu-id="b2001-118">İlke başarıyla değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="b2001-118">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="b2001-119">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2001-119">E_INVALIDARG</span></span>|<span data-ttu-id="b2001-120">`pwzSourceAssemblyIdentity` ya da `pwzTargetAssemblyIdentity` null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="b2001-120">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="b2001-121">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b2001-121">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b2001-122">`pbNewApplicationPolicy` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="b2001-122">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="b2001-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2001-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2001-124">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b2001-124">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2001-125">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2001-125">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2001-126">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b2001-126">The call timed out.</span></span>|  
|<span data-ttu-id="b2001-127">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2001-127">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2001-128">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b2001-128">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2001-129">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2001-129">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2001-130">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b2001-130">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2001-131">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2001-131">E_FAIL</span></span>|<span data-ttu-id="b2001-132">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b2001-132">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2001-133">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2001-133">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2001-134">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2001-134">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2001-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2001-135">Remarks</span></span>  

 <span data-ttu-id="b2001-136">`ModifyApplicationPolicy`Yöntemi iki kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2001-136">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="b2001-137">İlk çağrı, parametre için null değer sağlamalıdır `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="b2001-137">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="b2001-138">Bu çağrı için gerekli olan değer ile birlikte döndürülür `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="b2001-138">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="b2001-139">İkinci çağrı için bu değeri sağlamalı `pcbNewAppPolicySize` ve için bu boyut için bir arabellek göstermelidir `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="b2001-139">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2001-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2001-140">Requirements</span></span>  

 <span data-ttu-id="b2001-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2001-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2001-142">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2001-142">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2001-143">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b2001-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2001-144">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2001-144">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2001-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2001-145">See also</span></span>

- [<span data-ttu-id="b2001-146">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2001-146">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
