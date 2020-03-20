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
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode Metodu
Belirtilen işlevin tüm kodunu alır, sökme için biçimlendirilir. Bu yöntem .NET Framework sürüm 2.0'da amortismana hazırlanmıştır. Bunun yerine [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) kullanın.  
  
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
 [içinde] Fonksiyonun başlangıcının mahsup.  
  
 `endOffset`  
 [içinde] Fonksiyonun sonu mahsup.  
  
 `cBufferAlloc`  
 [içinde] Kodun `buffer` döndürüleceği dizinin boyutu.  
  
 `buffer`  
 [çıkış] Kodun döndürüleceği dizi.  
  
 `pcBufferSize`  
 [çıkış] Döndürülen bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevin kodu birden çok parçaya bölündüyse, yerel ofset'i artırmak amacıyla kısıtlanırlar. Talimat sınırları denetlenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeChunks Yöntemi](icordebugcode2-getcodechunks-method.md)
