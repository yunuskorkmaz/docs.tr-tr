---
title: ICorDebugCode2::GetCodeChunks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ab475ecb538dcf5bd24c750dfe9c993ea5a0ee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470906"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="43f91-102">ICorDebugCode2::GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43f91-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="43f91-103">Bu kod nesnesi oluşan kod öbekleriyle alır.</span><span class="sxs-lookup"><span data-stu-id="43f91-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43f91-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43f91-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="43f91-106">[in] Boyutu `chunks` dizisi.</span><span class="sxs-lookup"><span data-stu-id="43f91-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="43f91-107">[out] Döndürülen öbeği sayısı `chunks` dizisi.</span><span class="sxs-lookup"><span data-stu-id="43f91-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="43f91-108">[out] Her biri tek bir öbek kodunu temsil eden bir dizi "Codechunkınfo" yapıları.</span><span class="sxs-lookup"><span data-stu-id="43f91-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="43f91-109">Varsa değerini `cbufSize` 0'dır, bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="43f91-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43f91-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43f91-110">Remarks</span></span>  
 <span data-ttu-id="43f91-111">Kod öbekleri hiçbir zaman çakışır ve bunlar, bunlar birleştirilmiş tarafından sırasını takip [Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="43f91-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="43f91-112">.NET Framework sürüm 2.0 Microsoft Ara dili (MSIL) kodu nesnesinde tek kod öbek oluşur.</span><span class="sxs-lookup"><span data-stu-id="43f91-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f91-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43f91-113">Requirements</span></span>  
 <span data-ttu-id="43f91-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f91-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f91-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43f91-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43f91-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43f91-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43f91-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f91-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f91-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43f91-118">See also</span></span>

