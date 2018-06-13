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
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421664"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize Metodu
Bu "ICorDebugValue" nesne bayt cinsinden boyutu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSize`  
 [out] Bu değer nesnesinin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Değer türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçi boyutu döndürür.  
  
 `ICorDebugValue::GetSize` Yöntemi döndürür `COR_E_OVERFLOW` 64 bit platformlarda 4 GB'den büyük nesneler için. Kullanım [Icordebugvalue3::getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi yerine nesneler için 4 GB'den büyük.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
 [GetSize64 Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
