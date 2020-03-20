---
title: ICorDebugStringValue::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: e23133176cbd703a58c92f9bf1ead530b0bbb8a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178508"
---
# <a name="icordebugstringvaluegetstring-method"></a>ICorDebugStringValue::GetString Yöntemi
Bu ICorDebugStringValue tarafından başvurulan dize alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchString`  
 [içinde] `szString` Dizinin boyutu.  
  
 `pcchString`  
 [çıkış] Dizide döndürülen karakter sayısına `szString` işaretçi.  
  
 `szString`  
 [çıkış] Alınan dizeyi depolayan bir dizi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
