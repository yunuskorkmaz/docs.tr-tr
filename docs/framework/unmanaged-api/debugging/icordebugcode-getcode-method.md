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
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode Metodu
Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır. Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="parameters"></a>Parametreler  
 `startOffset`  
 'ndaki İşlevin başlangıcının boşluğu.  
  
 `endOffset`  
 'ndaki İşlevin sonundaki fark.  
  
 `cBufferAlloc`  
 'ndaki Kodun döndürüleceği `buffer` dizisinin boyutu.  
  
 `buffer`  
 dışı Kodun döndürüleceği dizi.  
  
 `pcBufferSize`  
 dışı Döndürülen bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevin kodu birden çok Öbekle ayrılmışsa, bu değerler artan yerel uzaklığa göre birleştirilir. Yönerge sınırları denetlenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeChunks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
