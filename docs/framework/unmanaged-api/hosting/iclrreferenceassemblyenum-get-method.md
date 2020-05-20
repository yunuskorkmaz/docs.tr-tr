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
ms.openlocfilehash: 5afa7b37b804b6a11a894e0e6c7708c7787a20ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703358"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="c278d-102">ICLRReferenceAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c278d-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="c278d-103">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="c278d-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c278d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c278d-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c278d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c278d-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="c278d-106">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="c278d-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="c278d-107">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="c278d-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="c278d-108">[in, out] `pwzBuffer`Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c278d-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c278d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c278d-109">Return Value</span></span>  
  
|<span data-ttu-id="c278d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c278d-110">HRESULT</span></span>|<span data-ttu-id="c278d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c278d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c278d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c278d-112">S_OK</span></span>|<span data-ttu-id="c278d-113">`Get`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c278d-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="c278d-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c278d-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c278d-115">`pwzBuffer`çok küçük.</span><span class="sxs-lookup"><span data-stu-id="c278d-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="c278d-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="c278d-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="c278d-117">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="c278d-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="c278d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c278d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c278d-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c278d-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c278d-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c278d-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c278d-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c278d-121">The call timed out.</span></span>|  
|<span data-ttu-id="c278d-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c278d-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c278d-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c278d-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c278d-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c278d-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c278d-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c278d-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c278d-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c278d-126">E_FAIL</span></span>|<span data-ttu-id="c278d-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c278d-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c278d-128">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c278d-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c278d-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c278d-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c278d-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c278d-130">Remarks</span></span>  
 <span data-ttu-id="c278d-131">`Get`genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c278d-131">`Get` is typically called twice.</span></span> <span data-ttu-id="c278d-132">İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="c278d-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="c278d-133">İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c278d-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c278d-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c278d-134">Requirements</span></span>  
 <span data-ttu-id="c278d-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c278d-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c278d-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c278d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c278d-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c278d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c278d-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c278d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c278d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c278d-139">See also</span></span>

- [<span data-ttu-id="c278d-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c278d-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c278d-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c278d-141">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
