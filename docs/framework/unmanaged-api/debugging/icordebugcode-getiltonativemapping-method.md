---
title: ICorDebugCode::GetILToNativeMapping Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetILToNativeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54937e8d5d7a2e345ebcbccadbc592b12e3ee9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="19265-102">ICorDebugCode::GetILToNativeMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="19265-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="19265-103">Eşlemeleri Ara dili (MSIL) kaydırır Microsoft'tan yerel uzaklıkları temsil "Cor_debug_ıl_to_natıve_map" örnekleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="19265-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19265-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19265-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19265-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="19265-106">[in] Boyutunu `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="19265-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="19265-107">[out] Döndürülen öğe gerçek sayısını gösteren bir işaretçi `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="19265-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="19265-108">[out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, her biri bir yerel uzaklığı MSIL uzaklığı bir eşleme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19265-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="19265-109">Döndürülen öğeleri dizisi sıralamaya yoktur.</span><span class="sxs-lookup"><span data-stu-id="19265-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19265-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19265-110">Remarks</span></span>  
 <span data-ttu-id="19265-111">`GetILToNativeMapping` Yöntemi yalnızca bu "ICorDebugCode" örneğinin yalnızca MSIL koddan derlenmiş zamanında (JIT) olan yerel kod temsil ediyorsa anlamlı sonuçlar döndürür.</span><span class="sxs-lookup"><span data-stu-id="19265-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19265-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19265-112">Requirements</span></span>  
 <span data-ttu-id="19265-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19265-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19265-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19265-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19265-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19265-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19265-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19265-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19265-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19265-117">See Also</span></span>  
 [<span data-ttu-id="19265-118">Icordebugcode Interface1</span><span class="sxs-lookup"><span data-stu-id="19265-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
