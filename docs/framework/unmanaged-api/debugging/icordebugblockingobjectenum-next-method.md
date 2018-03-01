---
title: "ICorDebugBlockingObjectEnum::Next Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f2e2168ea1b03e5a2339baf019da59f1e83a71a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="e201e-102">ICorDebugBlockingObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e201e-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="e201e-103">Belirtilen sayıda alır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) geçerli konumdan başlayarak numaralandırması nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e201e-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e201e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e201e-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e201e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e201e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e201e-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="e201e-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="e201e-107">[out] İşaretçiler bir dizi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e201e-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e201e-108">[out] Alındı nesne sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e201e-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e201e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e201e-109">Return Value</span></span>  
 <span data-ttu-id="e201e-110">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e201e-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="e201e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e201e-111">HRESULT</span></span>|<span data-ttu-id="e201e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e201e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e201e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e201e-113">S_OK</span></span>|<span data-ttu-id="e201e-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e201e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e201e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e201e-115">S_FALSE</span></span>|<span data-ttu-id="e201e-116">`pceltFetched`eşit değil `celt`.</span><span class="sxs-lookup"><span data-stu-id="e201e-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e201e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e201e-117">Remarks</span></span>  
 <span data-ttu-id="e201e-118">Bu yöntem işlevleri tipik bir COM Numaralandırıcı ister.</span><span class="sxs-lookup"><span data-stu-id="e201e-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="e201e-119">Giriş dizisi değerleri en az olmalıdır boyutunu `celt`.</span><span class="sxs-lookup"><span data-stu-id="e201e-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="e201e-120">Dizi ile ya da sonraki doldurulur `celt` değerleri numaralandırma veya diğer tüm değerleri varsa, daha az `celt` kalır.</span><span class="sxs-lookup"><span data-stu-id="e201e-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="e201e-121">Bu yöntem döndürüldüğünde, `pceltFetched` alındı değerleri numarasıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e201e-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="e201e-122">Varsa `values` geçersiz işaretçileri içerir veya daha küçük olan bir arabellek işaret `celt`, veya `pceltFetched` geçersiz bir işaretçi sonucu tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="e201e-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e201e-123">Ancak [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı yayımlanması gerekmez, bu içinde "ICorDebugValue" arabirimi yayımlanması gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e201e-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
-  
  
## <a name="requirements"></a><span data-ttu-id="e201e-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e201e-124">Requirements</span></span>  
 <span data-ttu-id="e201e-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e201e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e201e-126">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e201e-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e201e-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e201e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e201e-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e201e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e201e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e201e-129">See Also</span></span>  
 [<span data-ttu-id="e201e-130">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e201e-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="e201e-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e201e-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e201e-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e201e-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
