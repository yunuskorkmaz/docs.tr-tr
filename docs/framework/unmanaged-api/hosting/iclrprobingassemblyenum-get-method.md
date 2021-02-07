---
description: ': ICLRProbingAssemblyEnum:: get yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 77fb93b30a3b9b01b32fef9af661c84f484ef758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716529"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="039e5-103">ICLRProbingAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="039e5-103">ICLRProbingAssemblyEnum::Get Method</span></span>

<span data-ttu-id="039e5-104">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="039e5-104">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="039e5-105">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="039e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="039e5-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="039e5-107">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="039e5-107">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="039e5-108">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="039e5-108">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="039e5-109">[in, out] `pwzBuffer` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="039e5-109">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="039e5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="039e5-110">Return Value</span></span>  
  
|<span data-ttu-id="039e5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="039e5-111">HRESULT</span></span>|<span data-ttu-id="039e5-112">Description</span><span class="sxs-lookup"><span data-stu-id="039e5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="039e5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="039e5-113">S_OK</span></span>|<span data-ttu-id="039e5-114">`Get` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="039e5-114">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="039e5-115">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="039e5-115">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="039e5-116">`pwzBuffer` çok küçük.</span><span class="sxs-lookup"><span data-stu-id="039e5-116">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="039e5-117">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="039e5-117">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="039e5-118">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="039e5-118">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="039e5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="039e5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="039e5-120">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="039e5-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="039e5-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="039e5-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="039e5-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="039e5-122">The call timed out.</span></span>|  
|<span data-ttu-id="039e5-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="039e5-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="039e5-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="039e5-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="039e5-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="039e5-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="039e5-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="039e5-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="039e5-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="039e5-127">E_FAIL</span></span>|<span data-ttu-id="039e5-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="039e5-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="039e5-129">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="039e5-129">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="039e5-130">Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="039e5-130">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="039e5-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="039e5-131">Remarks</span></span>  

 <span data-ttu-id="039e5-132">0 dizinindeki kimlik, işlemci mimarisine özgü kimliktir.</span><span class="sxs-lookup"><span data-stu-id="039e5-132">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="039e5-133">Dizin 1 ' deki kimlik, Microsoft ara dili (MSIL) için mimari olarak nötr derlemedir.</span><span class="sxs-lookup"><span data-stu-id="039e5-133">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="039e5-134">Dizin 2 ' deki kimlik hiçbir mimari bilgisi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="039e5-134">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="039e5-135">`Get` genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="039e5-135">`Get` is typically called twice.</span></span> <span data-ttu-id="039e5-136">İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="039e5-136">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="039e5-137">İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="039e5-137">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="039e5-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="039e5-138">Requirements</span></span>  

 <span data-ttu-id="039e5-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="039e5-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="039e5-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="039e5-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="039e5-141">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="039e5-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="039e5-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="039e5-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039e5-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="039e5-143">See also</span></span>

- [<span data-ttu-id="039e5-144">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="039e5-144">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="039e5-145">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="039e5-145">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
