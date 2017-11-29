---
title: ICorDebugCode::GetCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12820d0be725c92754640aaa4eebca56bbc33ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="cedaa-102">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="cedaa-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="cedaa-103">Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır.</span><span class="sxs-lookup"><span data-stu-id="cedaa-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="cedaa-104">Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="cedaa-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="cedaa-105">Kullanım [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="cedaa-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cedaa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cedaa-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cedaa-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cedaa-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="cedaa-108">[in] İşlev başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="cedaa-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="cedaa-109">[in] İşlevin sonuna uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="cedaa-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="cedaa-110">[in] Boyutunu `buffer` dizi kodu, döndürülecek içine.</span><span class="sxs-lookup"><span data-stu-id="cedaa-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="cedaa-111">[out] Dizi içine kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cedaa-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="cedaa-112">[out] Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="cedaa-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cedaa-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cedaa-113">Remarks</span></span>  
 <span data-ttu-id="cedaa-114">İşlevin kodunu birden çok parçalara bölünür varsa, bunlar, yerel uzaklığı artan sırada birleşir.</span><span class="sxs-lookup"><span data-stu-id="cedaa-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="cedaa-115">Yönerge sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="cedaa-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cedaa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cedaa-116">Requirements</span></span>  
 <span data-ttu-id="cedaa-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cedaa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cedaa-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cedaa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cedaa-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cedaa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cedaa-120">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="cedaa-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedaa-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cedaa-121">See Also</span></span>  
 [<span data-ttu-id="cedaa-122">GetCodeChunks yöntemi</span><span class="sxs-lookup"><span data-stu-id="cedaa-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
