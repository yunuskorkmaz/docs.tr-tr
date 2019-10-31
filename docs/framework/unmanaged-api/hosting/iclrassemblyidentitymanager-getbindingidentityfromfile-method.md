---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi
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
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126749"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="fc03b-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc03b-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="fc03b-103">Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="fc03b-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc03b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc03b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc03b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc03b-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="fc03b-106">'ndaki Değerlendirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="fc03b-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fc03b-107">'ndaki Bir derlemenin kimlik türünü gösteren [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="fc03b-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="fc03b-108">Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc03b-108">Provided for future extensibility.</span></span> <span data-ttu-id="fc03b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanı (CLR) sürüm 2,0 ' nin desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="fc03b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="fc03b-110">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="fc03b-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="fc03b-111">[in, out] `pwzBuffer`boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc03b-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc03b-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc03b-112">Return Value</span></span>  
  
|<span data-ttu-id="fc03b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc03b-113">HRESULT</span></span>|<span data-ttu-id="fc03b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc03b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc03b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc03b-115">S_OK</span></span>|<span data-ttu-id="fc03b-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fc03b-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="fc03b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fc03b-117">E_INVALIDARG</span></span>|<span data-ttu-id="fc03b-118">Sağlanan `pwzFilePath` null.</span><span class="sxs-lookup"><span data-stu-id="fc03b-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="fc03b-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fc03b-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fc03b-120">`pwzBuffer` boyutu çok küçük.</span><span class="sxs-lookup"><span data-stu-id="fc03b-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="fc03b-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc03b-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc03b-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fc03b-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc03b-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc03b-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc03b-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fc03b-124">The call timed out.</span></span>|  
|<span data-ttu-id="fc03b-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc03b-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc03b-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc03b-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc03b-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc03b-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc03b-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fc03b-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc03b-129">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="fc03b-129">E_FAIL</span></span>|<span data-ttu-id="fc03b-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fc03b-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc03b-131">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc03b-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc03b-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc03b-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc03b-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc03b-133">Remarks</span></span>  
 <span data-ttu-id="fc03b-134">`GetBindingIdentityFromFile` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="fc03b-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="fc03b-135">İlk çağrı `pwzBuffer`için null değer sağlar ve Yöntem `pcchBufferSize`uygun boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc03b-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="fc03b-136">İkinci çağrı uygun bir ayrılmış arabellek sağlar ve Yöntem tamamlandığında gerçek arabellek verileriyle birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc03b-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc03b-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc03b-137">Requirements</span></span>  
 <span data-ttu-id="fc03b-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc03b-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc03b-139">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc03b-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc03b-140">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fc03b-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc03b-141">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc03b-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc03b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc03b-142">See also</span></span>

- [<span data-ttu-id="fc03b-143">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc03b-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fc03b-144">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc03b-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="fc03b-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc03b-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
