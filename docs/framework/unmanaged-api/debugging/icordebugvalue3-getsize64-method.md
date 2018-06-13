---
title: ICorDebugValue3::GetSize64 Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d3925741e9777e4fcd1752d8e24bf71ad1579f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422643"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 Metodu
Bu bayt cinsinden boyutu alır [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pSize  
 [out] Bu nesnenin bayt cinsinden boyutu için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerinin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçi boyutu döndürür.  
  
 `ICorDebugValue3::GetSize` Yönteminden farklıdır [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) türü, çıktı parametresi olarak yöntemi. İçinde [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), çıktı parametresi bir `ULONG32`; `ICorDebugValue3::GetSize`, bu bir `ULONG64`. Böylece [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) boyutu 2 GB aşan dizi bildirmek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
