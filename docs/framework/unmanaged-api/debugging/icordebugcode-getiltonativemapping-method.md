---
description: ': ICorDebugCode:: GetILToNativeMapping Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 808ed450fced8afecc2b637a3b990a894897b350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711199"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="6b921-103">ICorDebugCode::GetILToNativeMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="6b921-103">ICorDebugCode::GetILToNativeMapping Method</span></span>

<span data-ttu-id="6b921-104">Microsoft ara dili (MSIL) uzaklıklarından yerel uzaklıklara olan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="6b921-104">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b921-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b921-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b921-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b921-106">Parameters</span></span>  

 `cMap`  
 <span data-ttu-id="6b921-107">'ndaki `map` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="6b921-107">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="6b921-108">dışı Dizide döndürülen gerçek öğe sayısı için bir işaretçi `map` .</span><span class="sxs-lookup"><span data-stu-id="6b921-108">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="6b921-109">dışı `COR_DEBUG_IL_TO_NATIVE_MAP` Her biri BIR MSIL öğesinden yerel bir uzaklığa bir eşlemeyi temsil eden yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="6b921-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="6b921-110">Döndürülen öğelerin dizisinde bir sıralama yoktur.</span><span class="sxs-lookup"><span data-stu-id="6b921-110">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b921-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b921-111">Remarks</span></span>  

 <span data-ttu-id="6b921-112">`GetILToNativeMapping`Yöntemi, yalnızca bu "ICorDebugCode" örneği, MSIL kodundan derlenen yerel kodu (JIT) gösterirse anlamlı sonuçlar döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b921-112">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b921-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b921-113">Requirements</span></span>  

 <span data-ttu-id="6b921-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b921-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b921-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b921-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b921-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6b921-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b921-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b921-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b921-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b921-118">See also</span></span>

- [<span data-ttu-id="6b921-119">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b921-119">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
