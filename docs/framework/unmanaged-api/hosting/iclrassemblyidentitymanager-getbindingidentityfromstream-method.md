---
description: ': ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: aed5968a5f5c22a2f5cbea66a350dbe452368325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716898"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="28d2a-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28d2a-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="28d2a-104">Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="28d2a-104">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28d2a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28d2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28d2a-106">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="28d2a-107">'ndaki Değerlendirilecek derleme akışı.</span><span class="sxs-lookup"><span data-stu-id="28d2a-107">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="28d2a-108">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="28d2a-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="28d2a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="28d2a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="28d2a-110">dışı Donuk derleme kimliği verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="28d2a-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="28d2a-111">[in, out] Boyutu `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="28d2a-111">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28d2a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28d2a-112">Return Value</span></span>  
  
|<span data-ttu-id="28d2a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28d2a-113">HRESULT</span></span>|<span data-ttu-id="28d2a-114">Description</span><span class="sxs-lookup"><span data-stu-id="28d2a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28d2a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="28d2a-115">S_OK</span></span>|<span data-ttu-id="28d2a-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="28d2a-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="28d2a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28d2a-117">E_INVALIDARG</span></span>|<span data-ttu-id="28d2a-118">Sağlanan `pStream` değer null.</span><span class="sxs-lookup"><span data-stu-id="28d2a-118">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="28d2a-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="28d2a-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="28d2a-120">Boyutu `pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="28d2a-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="28d2a-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28d2a-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28d2a-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="28d2a-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28d2a-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28d2a-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28d2a-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="28d2a-124">The call timed out.</span></span>|  
|<span data-ttu-id="28d2a-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28d2a-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28d2a-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="28d2a-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28d2a-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28d2a-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28d2a-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="28d2a-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28d2a-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28d2a-129">E_FAIL</span></span>|<span data-ttu-id="28d2a-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="28d2a-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28d2a-131">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="28d2a-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28d2a-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="28d2a-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28d2a-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28d2a-133">Requirements</span></span>  

 <span data-ttu-id="28d2a-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d2a-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d2a-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="28d2a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28d2a-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="28d2a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28d2a-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d2a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d2a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28d2a-138">See also</span></span>

- [<span data-ttu-id="28d2a-139">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28d2a-139">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="28d2a-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28d2a-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
