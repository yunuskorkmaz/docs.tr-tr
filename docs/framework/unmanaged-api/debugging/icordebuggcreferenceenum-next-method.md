---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıtcggcreferenceenum:: Next yöntemi'
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
ms.openlocfilehash: aec135fcb737a200d5a267529fa812c0852a24df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803704"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="5d6aa-103">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6aa-103">ICorDebugGCReferenceEnum::Next Method</span></span>

<span data-ttu-id="5d6aa-104">Atık olarak toplanabilecek nesneler hakkında bilgi içeren [cor_gc_reference](cor-gc-reference-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5d6aa-104">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6aa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d6aa-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d6aa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d6aa-106">Parameters</span></span>  

 <span data-ttu-id="5d6aa-107">celt</span><span class="sxs-lookup"><span data-stu-id="5d6aa-107">celt</span></span>  
 <span data-ttu-id="5d6aa-108">'ndaki Alınacak köklerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d6aa-108">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="5d6aa-109">kök</span><span class="sxs-lookup"><span data-stu-id="5d6aa-109">roots</span></span>  
 <span data-ttu-id="5d6aa-110">dışı Her biri, atık toplanan bir nesnenin kökünü temsil eden bir [cor_gc_reference](cor-gc-reference-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="5d6aa-110">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="5d6aa-111">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="5d6aa-111">pceltFetched</span></span>  
 <span data-ttu-id="5d6aa-112">dışı Aslında ' de döndürülen [cor_gc_reference](cor-gc-reference-structure.md) nesnelerinin sayısına yönelik bir işaretçi `roots` .</span><span class="sxs-lookup"><span data-stu-id="5d6aa-112">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="5d6aa-113">Bu değer 1 ise `null` olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="5d6aa-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d6aa-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d6aa-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d6aa-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d6aa-115">Requirements</span></span>  

 <span data-ttu-id="5d6aa-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6aa-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6aa-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d6aa-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d6aa-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d6aa-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d6aa-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d6aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6aa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6aa-120">See also</span></span>

- [<span data-ttu-id="5d6aa-121">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d6aa-121">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="5d6aa-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d6aa-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
