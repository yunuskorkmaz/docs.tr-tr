---
title: ICorDebugCode2::GetCodeChunks Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 950fd5c19e8827a63dcf075c42d3e0c18ff91261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="5ed3e-102">ICorDebugCode2::GetCodeChunks Metodu</span><span class="sxs-lookup"><span data-stu-id="5ed3e-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="5ed3e-103">Bu kod nesnesi oluşan kod parçalarını alır.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ed3e-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ed3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ed3e-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="5ed3e-106">[in] Boyutunu `chunks` dizi.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="5ed3e-107">[out] Döndürülen öbeği sayısı `chunks` dizi.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="5ed3e-108">[out] Her biri tek bir öbek kodunun temsil eden bir dizi "Codechunkınfo" yapıları.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="5ed3e-109">Varsa değerini `cbufSize` 0'dır, bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed3e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ed3e-110">Remarks</span></span>  
 <span data-ttu-id="5ed3e-111">Kod öbekleri hiçbir zaman çakışır ve, bunlar birleştirilmiş tarafından sipariş izleyeceği [Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="5ed3e-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="5ed3e-112">.NET Framework sürüm 2.0 Microsoft Ara dili (MSIL) kod nesnesinde bir tek bir kod öbek oluşturan.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed3e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ed3e-113">Requirements</span></span>  
 <span data-ttu-id="5ed3e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed3e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ed3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed3e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed3e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed3e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed3e-118">See Also</span></span>  
 
