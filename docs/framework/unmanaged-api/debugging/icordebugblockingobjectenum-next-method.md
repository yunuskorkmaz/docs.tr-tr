---
title: ICorDebugBlockingObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b28dec0f016d44692665fb0ce95a7e496f103c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200528"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="ad294-102">ICorDebugBlockingObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad294-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="ad294-103">Belirtilen sayıda alır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri geçerli konumunda başlayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="ad294-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad294-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad294-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad294-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad294-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ad294-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="ad294-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="ad294-107">[out] Bir işaretçiler dizisi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ad294-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ad294-108">[out] Alınan nesne sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad294-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad294-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad294-109">Return Value</span></span>  
 <span data-ttu-id="ad294-110">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad294-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="ad294-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad294-111">HRESULT</span></span>|<span data-ttu-id="ad294-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad294-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad294-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad294-113">S_OK</span></span>|<span data-ttu-id="ad294-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ad294-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ad294-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ad294-115">S_FALSE</span></span>|<span data-ttu-id="ad294-116">`pceltFetched` eşit değildir `celt`.</span><span class="sxs-lookup"><span data-stu-id="ad294-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad294-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad294-117">Remarks</span></span>  
 <span data-ttu-id="ad294-118">Tipik bir COM Numaralandırıcı gibi bu yöntem çalışır.</span><span class="sxs-lookup"><span data-stu-id="ad294-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="ad294-119">Giriş dizisinin en az olmalıdır boyutunun `celt`.</span><span class="sxs-lookup"><span data-stu-id="ad294-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="ad294-120">Dizi ile birlikte sonraki doldurulur `celt` değerleri sabit listesi veya tüm kalan değerler ile az olursa `celt` kalır.</span><span class="sxs-lookup"><span data-stu-id="ad294-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="ad294-121">Bu yöntem döndürüldüğünde, `pceltFetched` alınan değer sayısı ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ad294-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="ad294-122">Varsa `values` geçersiz işaretçi içerir ya da daha küçük olan bir arabellek işaret `celt`, veya `pceltFetched` geçersiz bir işaretçi sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="ad294-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad294-123">Ancak [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı yayımlanması gerekmez, içindeki "ICorDebugValue" arabirimi serbest bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad294-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad294-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad294-124">Requirements</span></span>  
 <span data-ttu-id="ad294-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad294-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad294-126">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad294-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad294-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad294-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad294-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad294-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad294-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad294-129">See Also</span></span>  
 [<span data-ttu-id="ad294-130">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad294-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="ad294-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad294-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ad294-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ad294-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
