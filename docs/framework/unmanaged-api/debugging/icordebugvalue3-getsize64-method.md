---
title: ICorDebugValue3::GetSize64 Yöntemi
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
ms.openlocfilehash: 7ae06d825565faff70b0c8be2ccbee5228737e41
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791096"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 Yöntemi
Bu [ICorDebugValue3](icordebugvalue3-interface.md) nesnesinin bayt cinsinden boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 Psıze  
 dışı Bu nesnenin bayt cinsinden boyutu için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.  
  
 `ICorDebugValue3::GetSize` yöntemi, çıkış parametresinin türü içindeki [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) yönteminden farklıdır. [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)içinde, çıkış parametresi bir `ULONG32`; `ICorDebugValue3::GetSize`, bir `ULONG64`. Bu, [ICorDebugValue3](icordebugvalue3-interface.md) arabiriminin 2GB ' i aşan dizilerin boyutunu rapor etmesini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugValue3 Arabirimi](icordebugvalue3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
