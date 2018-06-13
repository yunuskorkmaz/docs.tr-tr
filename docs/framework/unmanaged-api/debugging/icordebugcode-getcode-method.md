---
title: ICorDebugCode::GetCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d09681f97829f88bedf53af229298d5d57d764df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402695"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="b7196-102">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="b7196-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="b7196-103">Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır.</span><span class="sxs-lookup"><span data-stu-id="b7196-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="b7196-104">Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b7196-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b7196-105">Kullanım [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="b7196-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7196-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7196-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b7196-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7196-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="b7196-108">[in] İşlev başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="b7196-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b7196-109">[in] İşlevin sonuna uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="b7196-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="b7196-110">[in] Boyutunu `buffer` dizi kodu, döndürülecek içine.</span><span class="sxs-lookup"><span data-stu-id="b7196-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b7196-111">[out] Dizi içine kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b7196-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="b7196-112">[out] Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b7196-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7196-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7196-113">Remarks</span></span>  
 <span data-ttu-id="b7196-114">İşlevin kodunu birden çok parçalara bölünür varsa, bunlar, yerel uzaklığı artan sırada birleşir.</span><span class="sxs-lookup"><span data-stu-id="b7196-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="b7196-115">Yönerge sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="b7196-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7196-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7196-116">Requirements</span></span>  
 <span data-ttu-id="b7196-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7196-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7196-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7196-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7196-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7196-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7196-120">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="b7196-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7196-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7196-121">See Also</span></span>  
 [<span data-ttu-id="b7196-122">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7196-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
