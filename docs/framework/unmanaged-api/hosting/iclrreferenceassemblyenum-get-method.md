---
description: ': ICLRReferenceAssemblyEnum:: get yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ea4e71631a9ebb381f721b78f17507603891a032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637306"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="f3e78-103">ICLRReferenceAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3e78-103">ICLRReferenceAssemblyEnum::Get Method</span></span>

<span data-ttu-id="f3e78-104">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f3e78-104">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3e78-105">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e78-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3e78-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="f3e78-107">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="f3e78-107">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f3e78-108">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f3e78-108">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f3e78-109">[in, out] `pwzBuffer` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f3e78-109">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3e78-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3e78-110">Return Value</span></span>  
  
|<span data-ttu-id="f3e78-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3e78-111">HRESULT</span></span>|<span data-ttu-id="f3e78-112">Description</span><span class="sxs-lookup"><span data-stu-id="f3e78-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3e78-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3e78-113">S_OK</span></span>|<span data-ttu-id="f3e78-114">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f3e78-114">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="f3e78-115">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f3e78-115">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f3e78-116">`pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="f3e78-116">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f3e78-117">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="f3e78-117">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="f3e78-118">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="f3e78-118">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="f3e78-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3e78-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3e78-120">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f3e78-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3e78-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3e78-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3e78-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f3e78-122">The call timed out.</span></span>|  
|<span data-ttu-id="f3e78-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3e78-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3e78-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f3e78-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3e78-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3e78-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3e78-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f3e78-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3e78-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3e78-127">E_FAIL</span></span>|<span data-ttu-id="f3e78-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f3e78-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3e78-129">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f3e78-129">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3e78-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3e78-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3e78-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3e78-131">Remarks</span></span>  

 <span data-ttu-id="f3e78-132">`Get` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f3e78-132">`Get` is typically called twice.</span></span> <span data-ttu-id="f3e78-133">İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="f3e78-133">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="f3e78-134">İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f3e78-134">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e78-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3e78-135">Requirements</span></span>  

 <span data-ttu-id="f3e78-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e78-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e78-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3e78-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3e78-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f3e78-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3e78-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e78-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e78-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3e78-140">See also</span></span>

- [<span data-ttu-id="f3e78-141">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3e78-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f3e78-142">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3e78-142">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
