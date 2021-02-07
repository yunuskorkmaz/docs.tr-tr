---
description: ': ICorDebugCode:: GetCode yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 329770fac4f2b375c01dd68e4ea7114e59c609b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711290"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="acad0-103">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="acad0-103">ICorDebugCode::GetCode Method</span></span>

<span data-ttu-id="acad0-104">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="acad0-104">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="acad0-105">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="acad0-105">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="acad0-106">Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="acad0-106">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acad0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acad0-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="acad0-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acad0-108">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="acad0-109">'ndaki İşlevin başlangıcının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="acad0-109">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="acad0-110">'ndaki İşlevin sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="acad0-110">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="acad0-111">'ndaki `buffer` Kodun döndürüleceği dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="acad0-111">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="acad0-112">dışı Kodun döndürüleceği dizi.</span><span class="sxs-lookup"><span data-stu-id="acad0-112">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="acad0-113">dışı Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="acad0-113">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acad0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acad0-114">Remarks</span></span>  

 <span data-ttu-id="acad0-115">İşlevin kodu birden çok Öbekle ayrılmışsa, bu değerler artan yerel uzaklığa göre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="acad0-115">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="acad0-116">Yönerge sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="acad0-116">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acad0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acad0-117">Requirements</span></span>  

 <span data-ttu-id="acad0-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acad0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acad0-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acad0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acad0-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acad0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acad0-121">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="acad0-121">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acad0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acad0-122">See also</span></span>

- [<span data-ttu-id="acad0-123">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acad0-123">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
