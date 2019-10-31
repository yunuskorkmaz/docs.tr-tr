---
title: ICLRReferenceAssemblyEnum::Get Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 8f479443e168c3fc7c627c3227e59f1e8b54f0e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120512"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="16cf8-102">ICLRReferenceAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16cf8-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="16cf8-103">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="16cf8-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cf8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16cf8-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16cf8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16cf8-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="16cf8-106">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="16cf8-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="16cf8-107">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="16cf8-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="16cf8-108">[in, out] `pwzBuffer` arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="16cf8-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16cf8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="16cf8-109">Return Value</span></span>  
  
|<span data-ttu-id="16cf8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16cf8-110">HRESULT</span></span>|<span data-ttu-id="16cf8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16cf8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16cf8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="16cf8-112">S_OK</span></span>|<span data-ttu-id="16cf8-113">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="16cf8-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="16cf8-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="16cf8-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="16cf8-115">`pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="16cf8-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="16cf8-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="16cf8-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="16cf8-117">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="16cf8-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="16cf8-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16cf8-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16cf8-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="16cf8-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16cf8-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16cf8-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16cf8-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="16cf8-121">The call timed out.</span></span>|  
|<span data-ttu-id="16cf8-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16cf8-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16cf8-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="16cf8-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16cf8-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16cf8-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16cf8-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="16cf8-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16cf8-126">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="16cf8-126">E_FAIL</span></span>|<span data-ttu-id="16cf8-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="16cf8-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16cf8-128">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16cf8-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16cf8-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cf8-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16cf8-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16cf8-130">Remarks</span></span>  
 <span data-ttu-id="16cf8-131">`Get` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="16cf8-131">`Get` is typically called twice.</span></span> <span data-ttu-id="16cf8-132">İlk çağrı `pwzBuffer`için null değer sağlar ve `pcchBufferSize` `pwzBuffer`için uygun boyuta ayarlar.</span><span class="sxs-lookup"><span data-stu-id="16cf8-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="16cf8-133">İkinci çağrı uygun boyutta bir `pwzBuffer`sağlar ve tamamlama sonrasında kurallı derleme kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="16cf8-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16cf8-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16cf8-134">Requirements</span></span>  
 <span data-ttu-id="16cf8-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16cf8-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16cf8-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="16cf8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16cf8-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="16cf8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16cf8-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16cf8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cf8-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16cf8-139">See also</span></span>

- [<span data-ttu-id="16cf8-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16cf8-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="16cf8-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16cf8-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
