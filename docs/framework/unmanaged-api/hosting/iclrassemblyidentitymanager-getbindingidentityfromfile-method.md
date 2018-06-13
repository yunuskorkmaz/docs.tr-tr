---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28e97289eda5949e6d124426eb58105e2e3ad33e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435048"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="9c2cc-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="9c2cc-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="9c2cc-103">Belirtilen dosya yolu konumunda derlemesi için veri bağlama derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c2cc-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c2cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c2cc-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="9c2cc-106">[in] Değerlendirilecek dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9c2cc-107">[in] Değerini [Eclrassemblyıdentityflags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) bir derlemenin kimlik türünü gösteren numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="9c2cc-108">Gelecekteki genişletilebilirliği için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-108">Provided for future extensibility.</span></span> <span data-ttu-id="9c2cc-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) sürüm 2.0 destekleyen tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9c2cc-110">[out] Katı derleme kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="9c2cc-111">[içinde out] Bir işaretçi boyutunu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c2cc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c2cc-112">Return Value</span></span>  
  
|<span data-ttu-id="9c2cc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c2cc-113">HRESULT</span></span>|<span data-ttu-id="9c2cc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c2cc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c2cc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c2cc-115">S_OK</span></span>|<span data-ttu-id="9c2cc-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="9c2cc-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9c2cc-117">E_INVALIDARG</span></span>|<span data-ttu-id="9c2cc-118">Sağlanan `pwzFilePath` null.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="9c2cc-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9c2cc-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9c2cc-120">Boyutunu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="9c2cc-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c2cc-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c2cc-122">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c2cc-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c2cc-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c2cc-124">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-124">The call timed out.</span></span>|  
|<span data-ttu-id="9c2cc-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c2cc-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c2cc-126">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c2cc-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c2cc-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c2cc-128">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c2cc-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c2cc-129">E_FAIL</span></span>|<span data-ttu-id="9c2cc-130">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c2cc-131">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c2cc-132">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c2cc-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c2cc-133">Remarks</span></span>  
 <span data-ttu-id="9c2cc-134">`GetBindingIdentityFromFile` genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="9c2cc-135">İlk çağrıda null değerini sağlayan `pwzBuffer`, ve uygun boyutta yöntemi döndürür `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="9c2cc-136">İkinci çağrı uygun şekilde ayrılmış bir arabellek sağlar ve tamamlandıktan sonra gerçek arabellek verilerle yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c2cc-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c2cc-137">Requirements</span></span>  
 <span data-ttu-id="9c2cc-138">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c2cc-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c2cc-139">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c2cc-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c2cc-140">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9c2cc-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c2cc-141">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c2cc-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2cc-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c2cc-142">See Also</span></span>  
 [<span data-ttu-id="9c2cc-143">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c2cc-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="9c2cc-144">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c2cc-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="9c2cc-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c2cc-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
