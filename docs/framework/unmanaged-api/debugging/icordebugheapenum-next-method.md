---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugHeapEnum:: Next yöntemi'
title: ICorDebugHeapEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 22e81b9b0c4ac2027f932187b6f860d08adf6f97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691958"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="04708-103">ICorDebugHeapEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04708-103">ICorDebugHeapEnum::Next Method</span></span>

<span data-ttu-id="04708-104">Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="04708-104">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04708-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04708-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04708-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04708-106">Parameters</span></span>  

 <span data-ttu-id="04708-107">celt</span><span class="sxs-lookup"><span data-stu-id="04708-107">celt</span></span>  
 <span data-ttu-id="04708-108">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="04708-108">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="04708-109"> nesneleri</span><span class="sxs-lookup"><span data-stu-id="04708-109">objects</span></span>  
 <span data-ttu-id="04708-110">dışı Her biri yönetilen yığında bir nesne hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="04708-110">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="04708-111">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="04708-111">pceltFetched</span></span>  
 <span data-ttu-id="04708-112">dışı Aslında ' de döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi `objects` .</span><span class="sxs-lookup"><span data-stu-id="04708-112">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="04708-113">Bu değer 1 ise `null` olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="04708-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04708-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04708-114">Remarks</span></span>  

 <span data-ttu-id="04708-115">`COR_HEAPOBJECT.type`Alan, iç içe geçmiş bir başvuru SAYıLı com arabiriminin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="04708-115">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="04708-116">Bu başvuru, çağıran tarafından yayınlanmalıdır `ICorDebugHeapEnum::Next` .</span><span class="sxs-lookup"><span data-stu-id="04708-116">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04708-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04708-117">Requirements</span></span>  

 <span data-ttu-id="04708-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04708-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04708-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04708-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04708-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="04708-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04708-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04708-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04708-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04708-122">See also</span></span>

- [<span data-ttu-id="04708-123">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04708-123">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="04708-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04708-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
