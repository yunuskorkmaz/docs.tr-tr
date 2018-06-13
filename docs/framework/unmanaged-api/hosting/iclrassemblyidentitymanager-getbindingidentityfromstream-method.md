---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Metodu
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
ms.openlocfilehash: 57cf4e9f79be8e705869cf986a586fcfb3359584
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435345"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="b28b9-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Metodu</span><span class="sxs-lookup"><span data-stu-id="b28b9-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="b28b9-103">Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b28b9-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b28b9-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b28b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b28b9-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="b28b9-106">[in] Değerlendirilecek derleme akış.</span><span class="sxs-lookup"><span data-stu-id="b28b9-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b28b9-107">[in] Gelecekteki genişletilebilirliği için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b28b9-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="b28b9-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) geçerli sürümünü destekleyen tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="b28b9-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="b28b9-109">[out] Katı derleme kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b28b9-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="b28b9-110">[içinde out] Boyutunu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b28b9-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b28b9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b28b9-111">Return Value</span></span>  
  
|<span data-ttu-id="b28b9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b28b9-112">HRESULT</span></span>|<span data-ttu-id="b28b9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28b9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b28b9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b28b9-114">S_OK</span></span>|<span data-ttu-id="b28b9-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b28b9-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="b28b9-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b28b9-116">E_INVALIDARG</span></span>|<span data-ttu-id="b28b9-117">Sağlanan `pStream` null.</span><span class="sxs-lookup"><span data-stu-id="b28b9-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="b28b9-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b28b9-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b28b9-119">Boyutunu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="b28b9-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="b28b9-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b28b9-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b28b9-121">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b28b9-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b28b9-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b28b9-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b28b9-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b28b9-123">The call timed out.</span></span>|  
|<span data-ttu-id="b28b9-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b28b9-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b28b9-125">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b28b9-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b28b9-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b28b9-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b28b9-127">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b28b9-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b28b9-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b28b9-128">E_FAIL</span></span>|<span data-ttu-id="b28b9-129">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b28b9-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b28b9-130">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b28b9-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b28b9-131">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b28b9-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b28b9-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b28b9-132">Requirements</span></span>  
 <span data-ttu-id="b28b9-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b28b9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b28b9-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b28b9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b28b9-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b28b9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b28b9-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b28b9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28b9-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b28b9-137">See Also</span></span>  
 [<span data-ttu-id="b28b9-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b28b9-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b28b9-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b28b9-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
