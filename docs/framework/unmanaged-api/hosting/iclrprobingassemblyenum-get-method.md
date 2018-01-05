---
title: ICLRProbingAssemblyEnum::Get Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum.Get
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd54558eeb49ebf7a2a2e9304830b09a08d1038e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="fa55c-102">ICLRProbingAssemblyEnum::Get Metodu</span><span class="sxs-lookup"><span data-stu-id="fa55c-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="fa55c-103">Belirtilen dizindeki derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="fa55c-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa55c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa55c-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa55c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa55c-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="fa55c-106">[in] Döndürülecek derleme kimliği sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="fa55c-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="fa55c-107">[out] Derleme kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="fa55c-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="fa55c-108">[içinde out] Boyutunu `pwzBuffer` arabellek.</span><span class="sxs-lookup"><span data-stu-id="fa55c-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa55c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa55c-109">Return Value</span></span>  
  
|<span data-ttu-id="fa55c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa55c-110">HRESULT</span></span>|<span data-ttu-id="fa55c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa55c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa55c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa55c-112">S_OK</span></span>|<span data-ttu-id="fa55c-113">`Get`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fa55c-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="fa55c-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fa55c-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fa55c-115">`pwzBuffer`çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="fa55c-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="fa55c-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="fa55c-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="fa55c-117">Numaralandırma daha fazla öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="fa55c-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="fa55c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa55c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa55c-119">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fa55c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa55c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa55c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa55c-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fa55c-121">The call timed out.</span></span>|  
|<span data-ttu-id="fa55c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa55c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa55c-123">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="fa55c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa55c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa55c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa55c-125">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="fa55c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa55c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa55c-126">E_FAIL</span></span>|<span data-ttu-id="fa55c-127">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fa55c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa55c-128">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fa55c-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa55c-129">Herhangi bir barındırma yöntem yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa55c-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa55c-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa55c-130">Remarks</span></span>  
 <span data-ttu-id="fa55c-131">İşlemci mimarisi için belirli kimlik dizin 0 konumunda kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="fa55c-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="fa55c-132">Dizin 1 Microsoft Ara dili (MSIL) için Mimari Tarafsız derleme kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="fa55c-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="fa55c-133">Dizin 2 konumunda kimlik mimari bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fa55c-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="fa55c-134">`Get`genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fa55c-134">`Get` is typically called twice.</span></span> <span data-ttu-id="fa55c-135">İlk çağrıda null değerini sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` için uygun bir boyut `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="fa55c-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="fa55c-136">İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra kurallı derleme kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fa55c-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa55c-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa55c-137">Requirements</span></span>  
 <span data-ttu-id="fa55c-138">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa55c-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa55c-139">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa55c-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa55c-140">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fa55c-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa55c-141">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa55c-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa55c-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa55c-142">See Also</span></span>  
 [<span data-ttu-id="fa55c-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa55c-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="fa55c-144">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa55c-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
