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
ms.openlocfilehash: f396881ef16f63eaf198aec168e5e94ed887698b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750327"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode Metodu
Ayrıştırma için biçimlendirilmiş belirtilen işlevi tüm kod alır. Bu yöntem .NET Framework 2.0 sürümünde kullanım dışı bırakıldı. Kullanım [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="parameters"></a>Parametreler  
 `startOffset`  
 [in] İşlevin başlangıcına uzaklık.  
  
 `endOffset`  
 [in] İşlevin sonuna uzaklığı.  
  
 `cBufferAlloc`  
 [in] Boyutu `buffer` dizi kod, döndürülecek içine.  
  
 `buffer`  
 [out] Dizi içine kod döndürülür.  
  
 `pcBufferSize`  
 [out] Döndürülen bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden çok öbeklere işlevin kodunu bölünmüş, bunlar, yerel uzaklık artan sırada bitiştirilir. Yönerge sınırları denetlenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeChunks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
