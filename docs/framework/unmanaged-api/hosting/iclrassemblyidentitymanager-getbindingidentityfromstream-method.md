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
ms.openlocfilehash: f1e6a47c0838782ae0610d49ca7fce3eb8554458
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716714"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="fd001-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd001-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="fd001-103">Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="fd001-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd001-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd001-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd001-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd001-105">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="fd001-106">'ndaki Değerlendirilecek derleme akışı.</span><span class="sxs-lookup"><span data-stu-id="fd001-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fd001-107">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd001-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="fd001-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="fd001-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="fd001-109">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="fd001-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="fd001-110">[in, out] Boyutu `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="fd001-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd001-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd001-111">Return Value</span></span>  
  
|<span data-ttu-id="fd001-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd001-112">HRESULT</span></span>|<span data-ttu-id="fd001-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd001-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd001-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd001-114">S_OK</span></span>|<span data-ttu-id="fd001-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd001-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="fd001-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fd001-116">E_INVALIDARG</span></span>|<span data-ttu-id="fd001-117">Sağlanan `pStream` değer null.</span><span class="sxs-lookup"><span data-stu-id="fd001-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="fd001-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fd001-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fd001-119">Boyutu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="fd001-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="fd001-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd001-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd001-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fd001-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd001-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd001-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd001-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fd001-123">The call timed out.</span></span>|  
|<span data-ttu-id="fd001-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd001-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd001-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fd001-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd001-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd001-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd001-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fd001-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd001-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd001-128">E_FAIL</span></span>|<span data-ttu-id="fd001-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd001-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd001-130">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd001-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd001-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd001-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd001-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd001-132">Requirements</span></span>  

 <span data-ttu-id="fd001-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd001-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd001-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd001-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd001-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fd001-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd001-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd001-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd001-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd001-137">See also</span></span>

- [<span data-ttu-id="fd001-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd001-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fd001-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd001-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
