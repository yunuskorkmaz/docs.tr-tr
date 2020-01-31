---
title: ICorDebugCode::GetILToNativeMapping Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 98709c0ce7469db1d0365d71e10d2d021cd3b3f0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777883"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="677eb-102">ICorDebugCode::GetILToNativeMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="677eb-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="677eb-103">Microsoft ara dili (MSIL) uzaklıklarından yerel uzaklıklara olan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="677eb-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="677eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="677eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="677eb-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="677eb-106">'ndaki `map` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="677eb-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="677eb-107">dışı `map` dizide döndürülen gerçek öğe sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="677eb-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="677eb-108">dışı Her biri MSIL 'den yerel bir uzaklığa bir eşlemeyi temsil eden `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarının bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="677eb-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="677eb-109">Döndürülen öğelerin dizisinde bir sıralama yoktur.</span><span class="sxs-lookup"><span data-stu-id="677eb-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677eb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="677eb-110">Remarks</span></span>  
 <span data-ttu-id="677eb-111">`GetILToNativeMapping` yöntemi, yalnızca bu "ICorDebugCode" örneği, MSIL kodundan derlenen yerel kodu temsil ediyorsa anlamlı sonuçlar döndürür.</span><span class="sxs-lookup"><span data-stu-id="677eb-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677eb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="677eb-112">Requirements</span></span>  
 <span data-ttu-id="677eb-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677eb-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="677eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="677eb-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="677eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677eb-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677eb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="677eb-117">See also</span></span>

- [<span data-ttu-id="677eb-118">ICorDebugCode arabirimi</span><span class="sxs-lookup"><span data-stu-id="677eb-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
