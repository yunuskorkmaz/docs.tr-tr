---
title: ICLRReferenceAssemblyEnum::Get Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3cdf6a8eb761367d23e1ce61cd24727e7a3d6ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="5a780-102">ICLRReferenceAssemblyEnum::Get Metodu</span><span class="sxs-lookup"><span data-stu-id="5a780-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="5a780-103">Sağlanan dizininde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="5a780-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a780-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a780-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a780-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a780-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="5a780-106">[in] Döndürülecek derleme kimliği sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="5a780-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="5a780-107">[out] Derleme kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="5a780-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="5a780-108">[içinde out] Boyutunu `pwzBuffer` arabellek.</span><span class="sxs-lookup"><span data-stu-id="5a780-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a780-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a780-109">Return Value</span></span>  
  
|<span data-ttu-id="5a780-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a780-110">HRESULT</span></span>|<span data-ttu-id="5a780-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a780-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a780-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a780-112">S_OK</span></span>|<span data-ttu-id="5a780-113">`Get`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5a780-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="5a780-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5a780-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5a780-115">`pwzBuffer`çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="5a780-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="5a780-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="5a780-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="5a780-117">Numaralandırma daha fazla öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5a780-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="5a780-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a780-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a780-119">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5a780-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a780-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a780-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a780-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5a780-121">The call timed out.</span></span>|  
|<span data-ttu-id="5a780-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a780-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a780-123">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="5a780-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a780-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a780-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a780-125">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="5a780-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a780-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a780-126">E_FAIL</span></span>|<span data-ttu-id="5a780-127">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5a780-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a780-128">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a780-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a780-129">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a780-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a780-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a780-130">Remarks</span></span>  
 <span data-ttu-id="5a780-131">`Get`genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5a780-131">`Get` is typically called twice.</span></span> <span data-ttu-id="5a780-132">İlk çağrıda null değerini sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` için uygun bir boyut `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5a780-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="5a780-133">İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra kurallı derleme kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a780-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a780-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a780-134">Requirements</span></span>  
 <span data-ttu-id="5a780-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a780-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a780-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a780-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a780-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5a780-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a780-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a780-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a780-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a780-139">See Also</span></span>  
 [<span data-ttu-id="5a780-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a780-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="5a780-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a780-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
