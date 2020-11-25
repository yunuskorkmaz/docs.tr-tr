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
ms.openlocfilehash: e55c53b9610dcadee92ba9871bf52e3dacb5796b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726242"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="42858-102">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42858-102">ICorDebugGCReferenceEnum::Next Method</span></span>

<span data-ttu-id="42858-103">Atık olarak toplanabilecek nesneler hakkında bilgi içeren [cor_gc_reference](cor-gc-reference-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="42858-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42858-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="42858-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42858-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42858-105">Parameters</span></span>  

 <span data-ttu-id="42858-106">celt</span><span class="sxs-lookup"><span data-stu-id="42858-106">celt</span></span>  
 <span data-ttu-id="42858-107">'ndaki Alınacak köklerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="42858-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="42858-108">kök</span><span class="sxs-lookup"><span data-stu-id="42858-108">roots</span></span>  
 <span data-ttu-id="42858-109">dışı Her biri, atık toplanan bir nesnenin kökünü temsil eden bir [cor_gc_reference](cor-gc-reference-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="42858-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="42858-110">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="42858-110">pceltFetched</span></span>  
 <span data-ttu-id="42858-111">dışı Aslında ' de döndürülen [cor_gc_reference](cor-gc-reference-structure.md) nesnelerinin sayısına yönelik bir işaretçi `roots` .</span><span class="sxs-lookup"><span data-stu-id="42858-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="42858-112">Bu değer 1 ise `null` olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="42858-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42858-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42858-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42858-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42858-114">Requirements</span></span>  

 <span data-ttu-id="42858-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42858-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42858-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42858-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42858-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="42858-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42858-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42858-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42858-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42858-119">See also</span></span>

- [<span data-ttu-id="42858-120">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42858-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="42858-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="42858-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
