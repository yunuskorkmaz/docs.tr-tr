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
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137091"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize Metodu
Bu "ICorDebugValue" nesnesinin bayt cinsinden boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pSize`  
 dışı Bu değer nesnesinin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.  
  
 `ICorDebugValue::GetSize` yöntemi 64-bit platformlarda 4 GB 'den büyük nesneler için `COR_E_OVERFLOW` döndürür. 4 GB 'den büyük nesneler için yerine [ICorDebugValue3:: GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetSize64 Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
