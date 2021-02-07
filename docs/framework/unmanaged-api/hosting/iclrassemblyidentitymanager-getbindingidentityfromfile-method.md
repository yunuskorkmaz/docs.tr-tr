---
description: ': ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 82e72155b38f71fe2c024994f07178638095be9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689556"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="3cd59-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cd59-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>

<span data-ttu-id="3cd59-104">Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="3cd59-104">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cd59-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cd59-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cd59-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="3cd59-107">'ndaki Değerlendirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="3cd59-107">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3cd59-108">'ndaki Bir derlemenin kimlik türünü gösteren [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="3cd59-108">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="3cd59-109">Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cd59-109">Provided for future extensibility.</span></span> <span data-ttu-id="3cd59-110">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanı (CLR) sürüm 2,0 ' nin desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="3cd59-110">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="3cd59-111">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3cd59-111">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="3cd59-112">[in, out] Boyutu için bir işaretçi `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="3cd59-112">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cd59-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3cd59-113">Return Value</span></span>  
  
|<span data-ttu-id="3cd59-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cd59-114">HRESULT</span></span>|<span data-ttu-id="3cd59-115">Description</span><span class="sxs-lookup"><span data-stu-id="3cd59-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cd59-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cd59-116">S_OK</span></span>|<span data-ttu-id="3cd59-117">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3cd59-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="3cd59-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3cd59-118">E_INVALIDARG</span></span>|<span data-ttu-id="3cd59-119">Sağlanan `pwzFilePath` değer null.</span><span class="sxs-lookup"><span data-stu-id="3cd59-119">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="3cd59-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3cd59-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3cd59-121">Boyutu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="3cd59-121">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="3cd59-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3cd59-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3cd59-123">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3cd59-123">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3cd59-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3cd59-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3cd59-125">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3cd59-125">The call timed out.</span></span>|  
|<span data-ttu-id="3cd59-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3cd59-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3cd59-127">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3cd59-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3cd59-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3cd59-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3cd59-129">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3cd59-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3cd59-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3cd59-130">E_FAIL</span></span>|<span data-ttu-id="3cd59-131">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3cd59-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3cd59-132">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3cd59-132">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3cd59-133">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cd59-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cd59-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cd59-134">Remarks</span></span>  

 <span data-ttu-id="3cd59-135">`GetBindingIdentityFromFile` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3cd59-135">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="3cd59-136">İlk çağrı için null bir değer sağlar `pwzBuffer` ve yöntemi içinde uygun boyutu döndürür `pcchBufferSize` .</span><span class="sxs-lookup"><span data-stu-id="3cd59-136">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="3cd59-137">İkinci çağrı uygun bir ayrılmış arabellek sağlar ve Yöntem tamamlandığında gerçek arabellek verileriyle birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cd59-137">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cd59-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cd59-138">Requirements</span></span>  

 <span data-ttu-id="3cd59-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cd59-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cd59-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3cd59-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cd59-141">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3cd59-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cd59-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cd59-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd59-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cd59-143">See also</span></span>

- [<span data-ttu-id="3cd59-144">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cd59-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3cd59-145">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cd59-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3cd59-146">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cd59-146">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
