---
title: ICLRProbingAssemblyEnum::Get Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3225e42df44e719ecde31c26fae70f26731fa157
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761590"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="4b391-102">ICLRProbingAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b391-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="4b391-103">Belirtilen dizindeki derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="4b391-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b391-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b391-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b391-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="4b391-106">[in] Derleme kimliği döndürmek için sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="4b391-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="4b391-107">[out] Derlemeyi kimlik verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="4b391-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="4b391-108">[out içinde] Boyutu `pwzBuffer` arabellek.</span><span class="sxs-lookup"><span data-stu-id="4b391-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b391-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b391-109">Return Value</span></span>  
  
|<span data-ttu-id="4b391-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b391-110">HRESULT</span></span>|<span data-ttu-id="4b391-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b391-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b391-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b391-112">S_OK</span></span>|<span data-ttu-id="4b391-113">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4b391-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="4b391-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4b391-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4b391-115">`pwzBuffer` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="4b391-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="4b391-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="4b391-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="4b391-117">Numaralandırma, daha fazla öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="4b391-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="4b391-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b391-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b391-119">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="4b391-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b391-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b391-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b391-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4b391-121">The call timed out.</span></span>|  
|<span data-ttu-id="4b391-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b391-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b391-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4b391-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b391-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b391-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b391-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="4b391-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b391-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b391-126">E_FAIL</span></span>|<span data-ttu-id="4b391-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4b391-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b391-128">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b391-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b391-129">Herhangi bir barındırma yöntemini yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b391-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b391-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b391-130">Remarks</span></span>  
 <span data-ttu-id="4b391-131">İşlemci mimarisi için belirli kimlik dizin 0 konumunda kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="4b391-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="4b391-132">Microsoft Ara dilini (MSIL) mimarisi nötr bütünleştirilmiş kod dizin 1 kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="4b391-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="4b391-133">Dizin 2 konumunda kimlik mimarisi bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b391-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="4b391-134">`Get` genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b391-134">`Get` is typically called twice.</span></span> <span data-ttu-id="4b391-135">İlk çağrı için bir null değer sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` boyuta uygun `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4b391-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="4b391-136">İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra derleme kurallı kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4b391-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b391-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b391-137">Requirements</span></span>  
 <span data-ttu-id="4b391-138">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b391-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b391-139">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b391-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b391-140">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4b391-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b391-141">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b391-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b391-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b391-142">See also</span></span>

- [<span data-ttu-id="4b391-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b391-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="4b391-144">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b391-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
