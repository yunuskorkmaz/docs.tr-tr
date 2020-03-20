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
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178992"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="01207-102">ICorDebugCode::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="01207-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="01207-103">Belirtilen işlevin tüm kodunu alır, sökme için biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01207-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="01207-104">Bu yöntem .NET Framework sürüm 2.0'da amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01207-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="01207-105">Bunun yerine [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="01207-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01207-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01207-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="01207-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01207-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="01207-108">[içinde] Fonksiyonun başlangıcının mahsup.</span><span class="sxs-lookup"><span data-stu-id="01207-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="01207-109">[içinde] Fonksiyonun sonu mahsup.</span><span class="sxs-lookup"><span data-stu-id="01207-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="01207-110">[içinde] Kodun `buffer` döndürüleceği dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="01207-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="01207-111">[çıkış] Kodun döndürüleceği dizi.</span><span class="sxs-lookup"><span data-stu-id="01207-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="01207-112">[çıkış] Döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="01207-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01207-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01207-113">Remarks</span></span>  
 <span data-ttu-id="01207-114">İşlevin kodu birden çok parçaya bölündüyse, yerel ofset'i artırmak amacıyla kısıtlanırlar.</span><span class="sxs-lookup"><span data-stu-id="01207-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="01207-115">Talimat sınırları denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="01207-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01207-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01207-116">Requirements</span></span>  
 <span data-ttu-id="01207-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01207-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01207-118">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01207-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01207-119">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01207-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01207-120">**.NET Çerçeve Sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="01207-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01207-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01207-121">See also</span></span>

- [<span data-ttu-id="01207-122">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01207-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
