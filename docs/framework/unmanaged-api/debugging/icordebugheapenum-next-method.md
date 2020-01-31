---
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
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782487"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="3dd8e-102">ICorDebugHeapEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dd8e-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="3dd8e-103">Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dd8e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dd8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dd8e-105">Parameters</span></span>  
 <span data-ttu-id="3dd8e-106">celt</span><span class="sxs-lookup"><span data-stu-id="3dd8e-106">celt</span></span>  
 <span data-ttu-id="3dd8e-107">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="3dd8e-108">nesneleri</span><span class="sxs-lookup"><span data-stu-id="3dd8e-108">objects</span></span>  
 <span data-ttu-id="3dd8e-109">dışı Her biri yönetilen yığında bir nesne hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="3dd8e-110">Pceltfettiz</span><span class="sxs-lookup"><span data-stu-id="3dd8e-110">pceltFetched</span></span>  
 <span data-ttu-id="3dd8e-111">dışı Aslında `objects`döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="3dd8e-112">Bu değer, `celt` 1 ise `null` olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd8e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dd8e-113">Remarks</span></span>  
 <span data-ttu-id="3dd8e-114">`COR_HEAPOBJECT.type` alanı, iç içe geçmiş bir başvuru sayılı COM arabiriminin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="3dd8e-115">Bu başvuru, `ICorDebugHeapEnum::Next`çağıranı tarafından yayınlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd8e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dd8e-116">Requirements</span></span>  
 <span data-ttu-id="3dd8e-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd8e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd8e-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3dd8e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd8e-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3dd8e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd8e-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd8e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd8e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dd8e-121">See also</span></span>

- [<span data-ttu-id="3dd8e-122">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dd8e-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="3dd8e-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3dd8e-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
