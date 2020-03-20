---
title: ICorDebugGCReferenceEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178860"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="59b05-102">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59b05-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="59b05-103">Çöp toplanacak nesneler hakkında bilgi içeren belirtilen [COR_GC_REFERENCE](cor-gc-reference-structure.md) örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="59b05-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59b05-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59b05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59b05-105">Parameters</span></span>  
 <span data-ttu-id="59b05-106">Celt</span><span class="sxs-lookup"><span data-stu-id="59b05-106">celt</span></span>  
 <span data-ttu-id="59b05-107">[içinde] Alınacak kök sayısı.</span><span class="sxs-lookup"><span data-stu-id="59b05-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="59b05-108">Kök</span><span class="sxs-lookup"><span data-stu-id="59b05-108">roots</span></span>  
 <span data-ttu-id="59b05-109">[çıkış] Her biri çöp toplanacak bir nesnenin kökünü temsil eden [bir COR_GC_REFERENCE](cor-gc-reference-structure.md) nesneyi işaret eden bir dizi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59b05-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="59b05-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="59b05-110">pceltFetched</span></span>  
 <span data-ttu-id="59b05-111">[çıkış] Gerçekte döndürülen `roots` [COR_GC_REFERENCE](cor-gc-reference-structure.md) nesne sayısına işaretçi</span><span class="sxs-lookup"><span data-stu-id="59b05-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="59b05-112">Bu değer `null` 1 `celt` ise olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b05-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59b05-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59b05-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b05-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59b05-114">Requirements</span></span>  
 <span data-ttu-id="59b05-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b05-116">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59b05-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59b05-117">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59b05-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59b05-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b05-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59b05-119">See also</span></span>

- [<span data-ttu-id="59b05-120">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59b05-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="59b05-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59b05-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
