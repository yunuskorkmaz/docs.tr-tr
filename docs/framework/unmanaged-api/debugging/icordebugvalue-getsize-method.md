---
title: ICorDebugValue::GetSize Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41a9ff2c94c98a5acc930d68e648b0ea577a82c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986849"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize Metodu
Bu "ICorDebugValue" nesnesinin bayt cinsinden boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pSize`  
 [out] Bu değer nesnesinin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Değer türü bir başvuru türü ise, bu yöntem, nesnenin boyutu yerine işaretçinin boyutu döndürür.  
  
 `ICorDebugValue::GetSize` Yöntemi döndürür `COR_E_OVERFLOW` 64-bit platformlarda 4 GB'den büyük olan nesneler için. Kullanım [Icordebugvalue3::getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi yerine nesneler için 4 GB'den büyük.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetSize64 Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
