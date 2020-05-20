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
ms.openlocfilehash: 5b537d59014afa783d3f8c5046cc02dad7ea7740
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616001"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="1663c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1663c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="1663c-103">Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="1663c-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1663c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1663c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1663c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1663c-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1663c-106">'ndaki Değerlendirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="1663c-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1663c-107">'ndaki Bir derlemenin kimlik türünü gösteren [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="1663c-107">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="1663c-108">Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1663c-108">Provided for future extensibility.</span></span> <span data-ttu-id="1663c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanı (CLR) sürüm 2,0 ' nin desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="1663c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="1663c-110">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1663c-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="1663c-111">[in, out] Boyutu için bir işaretçi `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="1663c-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1663c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1663c-112">Return Value</span></span>  
  
|<span data-ttu-id="1663c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1663c-113">HRESULT</span></span>|<span data-ttu-id="1663c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1663c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1663c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1663c-115">S_OK</span></span>|<span data-ttu-id="1663c-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1663c-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="1663c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1663c-117">E_INVALIDARG</span></span>|<span data-ttu-id="1663c-118">Sağlanan `pwzFilePath` değer null.</span><span class="sxs-lookup"><span data-stu-id="1663c-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="1663c-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1663c-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1663c-120">Boyutu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="1663c-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="1663c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1663c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1663c-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1663c-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1663c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1663c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1663c-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1663c-124">The call timed out.</span></span>|  
|<span data-ttu-id="1663c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1663c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1663c-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1663c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1663c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1663c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1663c-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1663c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1663c-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1663c-129">E_FAIL</span></span>|<span data-ttu-id="1663c-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1663c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1663c-131">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1663c-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1663c-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1663c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1663c-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1663c-133">Remarks</span></span>  
 <span data-ttu-id="1663c-134">`GetBindingIdentityFromFile`genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1663c-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="1663c-135">İlk çağrı için null bir değer sağlar `pwzBuffer` ve yöntemi içinde uygun boyutu döndürür `pcchBufferSize` .</span><span class="sxs-lookup"><span data-stu-id="1663c-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="1663c-136">İkinci çağrı uygun bir ayrılmış arabellek sağlar ve Yöntem tamamlandığında gerçek arabellek verileriyle birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="1663c-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1663c-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1663c-137">Requirements</span></span>  
 <span data-ttu-id="1663c-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1663c-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1663c-139">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1663c-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1663c-140">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1663c-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1663c-141">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1663c-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1663c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1663c-142">See also</span></span>

- [<span data-ttu-id="1663c-143">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1663c-143">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1663c-144">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1663c-144">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1663c-145">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1663c-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
