---
title: ICLRReferenceAssemblyEnum::Get Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac7e551cad12766f3472289889907d6972663567
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617375"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="ec907-102">ICLRReferenceAssemblyEnum::Get Metodu</span><span class="sxs-lookup"><span data-stu-id="ec907-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="ec907-103">Derleme kimliği sağlanan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="ec907-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec907-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec907-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec907-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec907-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="ec907-106">[in] Derleme kimliği döndürmek için sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="ec907-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ec907-107">[out] Derlemeyi kimlik verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="ec907-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ec907-108">[out içinde] Boyutu `pwzBuffer` arabellek.</span><span class="sxs-lookup"><span data-stu-id="ec907-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec907-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ec907-109">Return Value</span></span>  
  
|<span data-ttu-id="ec907-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec907-110">HRESULT</span></span>|<span data-ttu-id="ec907-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec907-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec907-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec907-112">S_OK</span></span>|<span data-ttu-id="ec907-113">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ec907-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="ec907-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ec907-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ec907-115">`pwzBuffer` çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="ec907-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ec907-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="ec907-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="ec907-117">Numaralandırma, daha fazla öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ec907-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="ec907-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec907-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec907-119">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ec907-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec907-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec907-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec907-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ec907-121">The call timed out.</span></span>|  
|<span data-ttu-id="ec907-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec907-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec907-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ec907-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec907-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec907-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec907-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ec907-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec907-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec907-126">E_FAIL</span></span>|<span data-ttu-id="ec907-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ec907-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec907-128">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec907-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec907-129">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec907-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec907-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec907-130">Remarks</span></span>  
 <span data-ttu-id="ec907-131">`Get` genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ec907-131">`Get` is typically called twice.</span></span> <span data-ttu-id="ec907-132">İlk çağrı için bir null değer sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` boyuta uygun `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ec907-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="ec907-133">İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra derleme kurallı kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ec907-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec907-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec907-134">Requirements</span></span>  
 <span data-ttu-id="ec907-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec907-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec907-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec907-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec907-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ec907-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec907-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec907-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec907-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec907-139">See also</span></span>
- [<span data-ttu-id="ec907-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec907-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ec907-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec907-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
