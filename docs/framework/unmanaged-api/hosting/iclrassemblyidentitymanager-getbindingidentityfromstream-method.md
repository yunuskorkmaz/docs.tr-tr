---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dc4e3adf5adec1aa4626a31b6a9391e2a04f1ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098598"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="72b6c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72b6c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="72b6c-103">Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="72b6c-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72b6c-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72b6c-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="72b6c-106">[in] Değerlendirilecek derleme akış.</span><span class="sxs-lookup"><span data-stu-id="72b6c-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="72b6c-107">[in] Sonra genişletilebilmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="72b6c-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="72b6c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="72b6c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="72b6c-109">[out] Donuk derleme kimlik verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="72b6c-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="72b6c-110">[out içinde] Boyutu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="72b6c-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72b6c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72b6c-111">Return Value</span></span>  
  
|<span data-ttu-id="72b6c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72b6c-112">HRESULT</span></span>|<span data-ttu-id="72b6c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72b6c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72b6c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="72b6c-114">S_OK</span></span>|<span data-ttu-id="72b6c-115">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="72b6c-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="72b6c-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="72b6c-116">E_INVALIDARG</span></span>|<span data-ttu-id="72b6c-117">Sağlanan `pStream` null.</span><span class="sxs-lookup"><span data-stu-id="72b6c-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="72b6c-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="72b6c-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="72b6c-119">Boyutu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="72b6c-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="72b6c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72b6c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72b6c-121">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="72b6c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72b6c-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72b6c-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72b6c-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="72b6c-123">The call timed out.</span></span>|  
|<span data-ttu-id="72b6c-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72b6c-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72b6c-125">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="72b6c-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72b6c-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72b6c-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72b6c-127">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="72b6c-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72b6c-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72b6c-128">E_FAIL</span></span>|<span data-ttu-id="72b6c-129">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72b6c-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72b6c-130">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72b6c-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72b6c-131">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72b6c-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72b6c-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72b6c-132">Requirements</span></span>  
 <span data-ttu-id="72b6c-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72b6c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b6c-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72b6c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72b6c-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="72b6c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72b6c-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b6c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b6c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b6c-137">See also</span></span>

- [<span data-ttu-id="72b6c-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72b6c-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="72b6c-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72b6c-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
