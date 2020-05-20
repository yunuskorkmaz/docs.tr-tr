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
ms.openlocfilehash: ea66c142afc097d1003df4e7f5f5b960a91e2ab0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703391"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="f6100-102">ICLRProbingAssemblyEnum::Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6100-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="f6100-103">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f6100-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6100-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f6100-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6100-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6100-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="f6100-106">'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.</span><span class="sxs-lookup"><span data-stu-id="f6100-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f6100-107">dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f6100-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f6100-108">[in, out] `pwzBuffer`Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f6100-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6100-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f6100-109">Return Value</span></span>  
  
|<span data-ttu-id="f6100-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6100-110">HRESULT</span></span>|<span data-ttu-id="f6100-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6100-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6100-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6100-112">S_OK</span></span>|<span data-ttu-id="f6100-113">`Get`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f6100-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="f6100-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f6100-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f6100-115">`pwzBuffer`çok küçük.</span><span class="sxs-lookup"><span data-stu-id="f6100-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f6100-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="f6100-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="f6100-117">Sabit listesi daha fazla öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="f6100-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="f6100-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6100-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6100-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f6100-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6100-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6100-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6100-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f6100-121">The call timed out.</span></span>|  
|<span data-ttu-id="f6100-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6100-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6100-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f6100-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6100-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6100-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6100-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f6100-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6100-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6100-126">E_FAIL</span></span>|<span data-ttu-id="f6100-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f6100-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6100-128">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f6100-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6100-129">Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6100-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6100-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6100-130">Remarks</span></span>  
 <span data-ttu-id="f6100-131">0 dizinindeki kimlik, işlemci mimarisine özgü kimliktir.</span><span class="sxs-lookup"><span data-stu-id="f6100-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="f6100-132">Dizin 1 ' deki kimlik, Microsoft ara dili (MSIL) için mimari olarak nötr derlemedir.</span><span class="sxs-lookup"><span data-stu-id="f6100-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="f6100-133">Dizin 2 ' deki kimlik hiçbir mimari bilgisi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="f6100-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="f6100-134">`Get`genellikle iki kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f6100-134">`Get` is typically called twice.</span></span> <span data-ttu-id="f6100-135">İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="f6100-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="f6100-136">İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f6100-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6100-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6100-137">Requirements</span></span>  
 <span data-ttu-id="f6100-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6100-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6100-139">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f6100-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6100-140">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f6100-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6100-141">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6100-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6100-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6100-142">See also</span></span>

- [<span data-ttu-id="f6100-143">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6100-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="f6100-144">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6100-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
