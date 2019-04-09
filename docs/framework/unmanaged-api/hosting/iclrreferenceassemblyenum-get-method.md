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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d26ed6249bad8a7e2fbaab01264c1b32e1ff55
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194480"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="8c229-102">ICLRReferenceAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c229-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="8c229-103">Derleme kimliği sağlanan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="8c229-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c229-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c229-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c229-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c229-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="8c229-106">[in] Derleme kimliği döndürmek için sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="8c229-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8c229-107">[out] Derlemeyi kimlik verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="8c229-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8c229-108">[out içinde] Boyutu `pwzBuffer` arabellek.</span><span class="sxs-lookup"><span data-stu-id="8c229-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c229-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c229-109">Return Value</span></span>  
  
|<span data-ttu-id="8c229-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c229-110">HRESULT</span></span>|<span data-ttu-id="8c229-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c229-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c229-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c229-112">S_OK</span></span>|`Get` <span data-ttu-id="8c229-113">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8c229-113">returned successfully.</span></span>|  
|<span data-ttu-id="8c229-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8c229-114">ERROR_INSUFFICIENT_BUFFER</span></span>|`pwzBuffer` <span data-ttu-id="8c229-115">çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="8c229-115">is too small.</span></span>|  
|<span data-ttu-id="8c229-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="8c229-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="8c229-117">Numaralandırma, daha fazla öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8c229-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="8c229-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c229-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c229-119">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="8c229-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c229-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c229-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c229-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8c229-121">The call timed out.</span></span>|  
|<span data-ttu-id="8c229-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c229-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c229-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8c229-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c229-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c229-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c229-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="8c229-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c229-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c229-126">E_FAIL</span></span>|<span data-ttu-id="8c229-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8c229-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c229-128">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8c229-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c229-129">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c229-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c229-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c229-130">Remarks</span></span>  
 `Get` <span data-ttu-id="8c229-131">genellikle iki kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8c229-131">is typically called twice.</span></span> <span data-ttu-id="8c229-132">İlk çağrı için bir null değer sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` boyuta uygun `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8c229-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="8c229-133">İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra derleme kurallı kimlik verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8c229-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c229-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c229-134">Requirements</span></span>  
 <span data-ttu-id="8c229-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c229-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c229-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c229-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c229-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8c229-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8c229-138">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8c229-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c229-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c229-139">See also</span></span>

- [<span data-ttu-id="8c229-140">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c229-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8c229-141">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c229-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
