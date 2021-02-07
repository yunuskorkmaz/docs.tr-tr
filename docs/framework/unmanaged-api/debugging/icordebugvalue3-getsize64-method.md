---
description: 'Daha fazla bilgi edinin: ICorDebugValue3:: GetSize64 Yöntemi'
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
ms.openlocfilehash: ce7db5211c6a8fc16b58e0197fa3142b5b744d96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690203"
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
  
 `ICorDebugValue3::GetSize`Yöntemi, çıkış parametresinin türündeki [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) yönteminden farklıdır. [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md), çıkış parametresi bir `ULONG32` ; içinde, `ICorDebugValue3::GetSize` bir `ULONG64` . Bu, [ICorDebugValue3](icordebugvalue3-interface.md) arabiriminin 2GB ' i aşan dizilerin boyutunu rapor etmesini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugValue3 Arabirimi](icordebugvalue3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
