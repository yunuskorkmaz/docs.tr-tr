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
ms.openlocfilehash: db24228de7e8c98fd97f890b1e408515172299b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125665"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="4c0b1-102">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="4c0b1-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="4c0b1-103">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="4c0b1-104">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4c0b1-105">Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0b1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c0b1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c0b1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c0b1-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="4c0b1-108">'ndaki İşlevin başlangıcının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="4c0b1-109">'ndaki İşlevin sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="4c0b1-110">'ndaki Kodun döndürüleceği `buffer` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4c0b1-111">dışı Kodun döndürüleceği dizi.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="4c0b1-112">dışı Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c0b1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c0b1-113">Remarks</span></span>  
 <span data-ttu-id="4c0b1-114">İşlevin kodu birden çok Öbekle ayrılmışsa, bu değerler artan yerel uzaklığa göre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="4c0b1-115">Yönerge sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0b1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c0b1-116">Requirements</span></span>  
 <span data-ttu-id="4c0b1-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0b1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0b1-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c0b1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c0b1-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c0b1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c0b1-120">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="4c0b1-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0b1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c0b1-121">See also</span></span>

- [<span data-ttu-id="4c0b1-122">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c0b1-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
