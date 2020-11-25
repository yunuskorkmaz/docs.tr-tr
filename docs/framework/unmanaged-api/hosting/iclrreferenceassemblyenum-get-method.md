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
ms.openlocfilehash: 3968adf418fcea847ee2be5a412385d041a53544
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728917"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="78e5b-102">ICLRReferenceAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78e5b-102">ICLRReferenceAssemblyEnum::Get Method</span></span>

<span data-ttu-id="78e5b-103">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="78e5b-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e5b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="78e5b-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78e5b-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="78e5b-106">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="78e5b-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="78e5b-107">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="78e5b-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="78e5b-108">[in, out] `pwzBuffer` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="78e5b-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78e5b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78e5b-109">Return Value</span></span>  
  
|<span data-ttu-id="78e5b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78e5b-110">HRESULT</span></span>|<span data-ttu-id="78e5b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e5b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78e5b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="78e5b-112">S_OK</span></span>|<span data-ttu-id="78e5b-113">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="78e5b-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="78e5b-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="78e5b-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="78e5b-115">`pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="78e5b-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="78e5b-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="78e5b-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="78e5b-117">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="78e5b-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="78e5b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78e5b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78e5b-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="78e5b-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78e5b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78e5b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78e5b-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="78e5b-121">The call timed out.</span></span>|  
|<span data-ttu-id="78e5b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78e5b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78e5b-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="78e5b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78e5b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78e5b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78e5b-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="78e5b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78e5b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78e5b-126">E_FAIL</span></span>|<span data-ttu-id="78e5b-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="78e5b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78e5b-128">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="78e5b-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78e5b-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="78e5b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e5b-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78e5b-130">Remarks</span></span>  

 <span data-ttu-id="78e5b-131">`Get` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="78e5b-131">`Get` is typically called twice.</span></span> <span data-ttu-id="78e5b-132">İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="78e5b-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="78e5b-133">İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="78e5b-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e5b-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78e5b-134">Requirements</span></span>  

 <span data-ttu-id="78e5b-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e5b-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e5b-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="78e5b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78e5b-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="78e5b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78e5b-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e5b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e5b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78e5b-139">See also</span></span>

- [<span data-ttu-id="78e5b-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78e5b-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="78e5b-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78e5b-141">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
