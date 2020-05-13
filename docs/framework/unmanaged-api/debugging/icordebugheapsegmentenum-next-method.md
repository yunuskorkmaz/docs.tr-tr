---
title: ICorDebugHeapSegmentEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210182"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="d809e-102">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d809e-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="d809e-103">Yönetilen yığının bellek bölgeleri hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d809e-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d809e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d809e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d809e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d809e-105">Parameters</span></span>  
 <span data-ttu-id="d809e-106">celt</span><span class="sxs-lookup"><span data-stu-id="d809e-106">celt</span></span>  
 <span data-ttu-id="d809e-107">'ndaki Alınacak parçaların sayısı.</span><span class="sxs-lookup"><span data-stu-id="d809e-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="d809e-108">segmentler</span><span class="sxs-lookup"><span data-stu-id="d809e-108">segments</span></span>  
 <span data-ttu-id="d809e-109">dışı Her biri yönetilen yığında bir bellek bölgesi hakkında bilgi sağlayan bir [cor_heapobject](cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="d809e-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="d809e-110">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="d809e-110">pceltFetched</span></span>  
 <span data-ttu-id="d809e-111">dışı Aslında ' de döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi `segments` .</span><span class="sxs-lookup"><span data-stu-id="d809e-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="d809e-112">Bu değer 1 ise `null` olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="d809e-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d809e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d809e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d809e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d809e-114">Requirements</span></span>  
 <span data-ttu-id="d809e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d809e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d809e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d809e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d809e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d809e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d809e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d809e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d809e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d809e-119">See also</span></span>

- [<span data-ttu-id="d809e-120">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d809e-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="d809e-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d809e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
