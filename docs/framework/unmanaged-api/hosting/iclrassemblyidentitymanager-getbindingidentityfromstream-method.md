---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd16f13bd77127953bdd17b258c7be518088f899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="13f7d-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Metodu</span><span class="sxs-lookup"><span data-stu-id="13f7d-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="13f7d-103">Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="13f7d-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13f7d-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13f7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13f7d-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="13f7d-106">[in] Değerlendirilecek derleme akış.</span><span class="sxs-lookup"><span data-stu-id="13f7d-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="13f7d-107">[in] Gelecekteki genişletilebilirliği için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="13f7d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="13f7d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) geçerli sürümünü destekleyen tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="13f7d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="13f7d-109">[out] Katı derleme kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="13f7d-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="13f7d-110">[içinde out] Boyutunu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="13f7d-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13f7d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13f7d-111">Return Value</span></span>  
  
|<span data-ttu-id="13f7d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13f7d-112">HRESULT</span></span>|<span data-ttu-id="13f7d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f7d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13f7d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="13f7d-114">S_OK</span></span>|<span data-ttu-id="13f7d-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13f7d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="13f7d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="13f7d-116">E_INVALIDARG</span></span>|<span data-ttu-id="13f7d-117">Sağlanan `pStream` null.</span><span class="sxs-lookup"><span data-stu-id="13f7d-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="13f7d-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="13f7d-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="13f7d-119">Boyutunu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="13f7d-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="13f7d-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13f7d-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13f7d-121">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="13f7d-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13f7d-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13f7d-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13f7d-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13f7d-123">The call timed out.</span></span>|  
|<span data-ttu-id="13f7d-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13f7d-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13f7d-125">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="13f7d-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13f7d-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13f7d-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13f7d-127">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="13f7d-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13f7d-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13f7d-128">E_FAIL</span></span>|<span data-ttu-id="13f7d-129">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13f7d-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13f7d-130">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13f7d-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13f7d-131">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13f7d-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13f7d-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f7d-132">Requirements</span></span>  
 <span data-ttu-id="13f7d-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f7d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f7d-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13f7d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13f7d-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13f7d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13f7d-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f7d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f7d-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13f7d-137">See Also</span></span>  
 [<span data-ttu-id="13f7d-138">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f7d-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="13f7d-139">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f7d-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
