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
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126746"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="67b56-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67b56-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="67b56-103">Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="67b56-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67b56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67b56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67b56-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="67b56-106">'ndaki Değerlendirilecek derleme akışı.</span><span class="sxs-lookup"><span data-stu-id="67b56-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="67b56-107">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67b56-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="67b56-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="67b56-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="67b56-109">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="67b56-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="67b56-110">[in, out] `pwzBuffer`boyutu.</span><span class="sxs-lookup"><span data-stu-id="67b56-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67b56-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67b56-111">Return Value</span></span>  
  
|<span data-ttu-id="67b56-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67b56-112">HRESULT</span></span>|<span data-ttu-id="67b56-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67b56-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67b56-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="67b56-114">S_OK</span></span>|<span data-ttu-id="67b56-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="67b56-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="67b56-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="67b56-116">E_INVALIDARG</span></span>|<span data-ttu-id="67b56-117">Sağlanan `pStream` null.</span><span class="sxs-lookup"><span data-stu-id="67b56-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="67b56-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="67b56-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="67b56-119">`pwzBuffer` boyutu çok küçük.</span><span class="sxs-lookup"><span data-stu-id="67b56-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="67b56-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67b56-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67b56-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="67b56-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="67b56-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="67b56-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="67b56-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="67b56-123">The call timed out.</span></span>|  
|<span data-ttu-id="67b56-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="67b56-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="67b56-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="67b56-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="67b56-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="67b56-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="67b56-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="67b56-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="67b56-128">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="67b56-128">E_FAIL</span></span>|<span data-ttu-id="67b56-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="67b56-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67b56-130">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="67b56-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="67b56-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="67b56-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67b56-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67b56-132">Requirements</span></span>  
 <span data-ttu-id="67b56-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67b56-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b56-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="67b56-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67b56-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="67b56-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67b56-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b56-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b56-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b56-137">See also</span></span>

- [<span data-ttu-id="67b56-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67b56-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="67b56-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67b56-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
