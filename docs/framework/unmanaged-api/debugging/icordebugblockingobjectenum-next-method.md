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
ms.openlocfilehash: 8fd82418da26ab0cd32b007b4613d588dfa695eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745298"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="e58b9-102">ICorDebugBlockingObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e58b9-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="e58b9-103">Belirtilen sayıda alır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri geçerli konumunda başlayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e58b9-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e58b9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e58b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e58b9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e58b9-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="e58b9-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="e58b9-107">[out] Bir işaretçiler dizisi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e58b9-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e58b9-108">[out] Alınan nesne sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e58b9-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e58b9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e58b9-109">Return Value</span></span>  
 <span data-ttu-id="e58b9-110">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e58b9-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="e58b9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e58b9-111">HRESULT</span></span>|<span data-ttu-id="e58b9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e58b9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e58b9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e58b9-113">S_OK</span></span>|<span data-ttu-id="e58b9-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e58b9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e58b9-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e58b9-115">S_FALSE</span></span>|<span data-ttu-id="e58b9-116">`pceltFetched` eşit değildir `celt`.</span><span class="sxs-lookup"><span data-stu-id="e58b9-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e58b9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e58b9-117">Remarks</span></span>  
 <span data-ttu-id="e58b9-118">Tipik bir COM Numaralandırıcı gibi bu yöntem çalışır.</span><span class="sxs-lookup"><span data-stu-id="e58b9-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="e58b9-119">Giriş dizisinin en az olmalıdır boyutunun `celt`.</span><span class="sxs-lookup"><span data-stu-id="e58b9-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="e58b9-120">Dizi ile birlikte sonraki doldurulur `celt` değerleri sabit listesi veya tüm kalan değerler ile az olursa `celt` kalır.</span><span class="sxs-lookup"><span data-stu-id="e58b9-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="e58b9-121">Bu yöntem döndürüldüğünde, `pceltFetched` alınan değer sayısı ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e58b9-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="e58b9-122">Varsa `values` geçersiz işaretçi içerir ya da daha küçük olan bir arabellek işaret `celt`, veya `pceltFetched` geçersiz bir işaretçi sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e58b9-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58b9-123">Ancak [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı yayımlanması gerekmez, içindeki "ICorDebugValue" arabirimi serbest bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e58b9-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58b9-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e58b9-124">Requirements</span></span>  
 <span data-ttu-id="e58b9-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e58b9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e58b9-126">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e58b9-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e58b9-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e58b9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e58b9-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e58b9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58b9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e58b9-129">See also</span></span>

- [<span data-ttu-id="e58b9-130">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e58b9-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="e58b9-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e58b9-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e58b9-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e58b9-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
