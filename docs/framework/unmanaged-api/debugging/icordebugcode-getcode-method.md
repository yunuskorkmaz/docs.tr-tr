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
ms.openlocfilehash: 20eac75a1f1d13b6a30267d56ff66024725e6f33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674781"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="1b0d8-102">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="1b0d8-102">ICorDebugCode::GetCode Method</span></span>

<span data-ttu-id="1b0d8-103">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="1b0d8-104">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1b0d8-105">Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0d8-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1b0d8-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1b0d8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b0d8-107">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="1b0d8-108">'ndaki İşlevin başlangıcının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="1b0d8-109">'ndaki İşlevin sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="1b0d8-110">'ndaki `buffer` Kodun döndürüleceği dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="1b0d8-111">dışı Kodun döndürüleceği dizi.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="1b0d8-112">dışı Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b0d8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b0d8-113">Remarks</span></span>  

 <span data-ttu-id="1b0d8-114">İşlevin kodu birden çok Öbekle ayrılmışsa, bu değerler artan yerel uzaklığa göre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="1b0d8-115">Yönerge sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b0d8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b0d8-116">Requirements</span></span>  

 <span data-ttu-id="1b0d8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b0d8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0d8-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b0d8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b0d8-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b0d8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b0d8-120">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="1b0d8-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0d8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b0d8-121">See also</span></span>

- [<span data-ttu-id="1b0d8-122">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b0d8-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
