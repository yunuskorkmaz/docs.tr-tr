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
ms.openlocfilehash: 1e94e4da0eea06ce9cc0110002b1def9e4dd4989
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939152"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="7b4ee-102">ICorDebugBlockingObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b4ee-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="7b4ee-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesnelerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b4ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b4ee-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b4ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b4ee-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7b4ee-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="7b4ee-107">dışı [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesnelerine yönelik işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7b4ee-108">dışı Alınan nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b4ee-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b4ee-109">Return Value</span></span>  
 <span data-ttu-id="7b4ee-110">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="7b4ee-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b4ee-111">HRESULT</span></span>|<span data-ttu-id="7b4ee-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b4ee-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b4ee-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b4ee-113">S_OK</span></span>|<span data-ttu-id="7b4ee-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7b4ee-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7b4ee-115">S_FALSE</span></span>|<span data-ttu-id="7b4ee-116">`pceltFetched`eşit `celt`değildir.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b4ee-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b4ee-117">Remarks</span></span>  
 <span data-ttu-id="7b4ee-118">Bu yöntem tipik bir COM numaralandırıcısı gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="7b4ee-119">Giriş dizisi değerleri en az boyutta `celt`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="7b4ee-120">Dizi, Numaralandırmadaki bir sonraki `celt` değerle veya `celt` daha az kalırsa kalan tüm değerlerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="7b4ee-121">Bu yöntem döndüğünde, `pceltFetched` alınan değer sayısıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="7b4ee-122">Geçersiz işaretçiler `celt`içeriyorsaveyadaha küçük olan bir arabelleğe işaret ediyorsa ya `pceltFetched` da geçersiz bir işaretçisiyse, sonuç tanımsızdır. `values`</span><span class="sxs-lookup"><span data-stu-id="7b4ee-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b4ee-123">[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısının serbest bırakılması gerekmez, ancak Içindeki "ICorDebugValue" arabiriminin serbest bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b4ee-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b4ee-124">Requirements</span></span>  
 <span data-ttu-id="7b4ee-125">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b4ee-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b4ee-126">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b4ee-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b4ee-127">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7b4ee-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b4ee-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b4ee-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4ee-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b4ee-129">See also</span></span>

- [<span data-ttu-id="7b4ee-130">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b4ee-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="7b4ee-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7b4ee-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7b4ee-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7b4ee-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
