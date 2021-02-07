---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugBlockingObjectEnum:: Next yöntemi'
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
ms.openlocfilehash: 66999ebf333c7115790b56afc1dc1d1ab7c47d69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711823"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="9b6d5-103">ICorDebugBlockingObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b6d5-103">ICorDebugBlockingObjectEnum::Next Method</span></span>

<span data-ttu-id="9b6d5-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen [CorDebugBlockingObject](cordebugblockingobject-structure.md) nesnelerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-104">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6d5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b6d5-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b6d5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b6d5-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9b6d5-107">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-107">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="9b6d5-108">dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) nesnelerine yönelik işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-108">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9b6d5-109">dışı Alınan nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-109">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b6d5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b6d5-110">Return Value</span></span>  

 <span data-ttu-id="9b6d5-111">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-111">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="9b6d5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b6d5-112">HRESULT</span></span>|<span data-ttu-id="9b6d5-113">Description</span><span class="sxs-lookup"><span data-stu-id="9b6d5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b6d5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b6d5-114">S_OK</span></span>|<span data-ttu-id="9b6d5-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="9b6d5-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9b6d5-116">S_FALSE</span></span>|<span data-ttu-id="9b6d5-117">`pceltFetched` eşit değildir `celt` .</span><span class="sxs-lookup"><span data-stu-id="9b6d5-117">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b6d5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b6d5-118">Remarks</span></span>  

 <span data-ttu-id="9b6d5-119">Bu yöntem tipik bir COM numaralandırıcısı gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-119">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="9b6d5-120">Giriş dizisi değerleri en az boyutta olmalıdır `celt` .</span><span class="sxs-lookup"><span data-stu-id="9b6d5-120">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="9b6d5-121">Dizi, `celt` Numaralandırmadaki bir sonraki değerle veya daha az kalırsa kalan tüm değerlerle doldurulur `celt` .</span><span class="sxs-lookup"><span data-stu-id="9b6d5-121">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="9b6d5-122">Bu yöntem döndüğünde, `pceltFetched` alınan değer sayısıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-122">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="9b6d5-123">`values`Geçersiz işaretçiler içeriyorsa veya daha küçük olan bir arabelleğe işaret ediyorsa ya da `celt` `pceltFetched` geçersiz bir işaretçisiyse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-123">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b6d5-124">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısının serbest bırakılması gerekmez, ancak Içindeki "ICorDebugValue" arabiriminin serbest bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-124">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b6d5-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b6d5-125">Requirements</span></span>  

 <span data-ttu-id="9b6d5-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6d5-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6d5-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b6d5-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b6d5-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b6d5-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b6d5-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6d5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6d5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b6d5-130">See also</span></span>

- [<span data-ttu-id="9b6d5-131">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b6d5-131">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="9b6d5-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b6d5-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9b6d5-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9b6d5-133">Debugging</span></span>](index.md)
