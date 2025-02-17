---
description: ': ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 97918d280299fae16eb55185baee19c27d99005b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693284"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi

Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 ppCallStackEnum  
 dışı Yönetilen bir özel durum nesnesi için yığın izleme numaralandırıcısı olan [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Hiçbir çağrı yığını bilgisi yoksa, yöntemi döndürür `S_OK` ve [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , 0 uzunluğunda geçerli bir Numaralandırıcı olur. Yöntem yığın izleme bilgilerini alamadığında, dönüş değeri olur `E_FAIL` ve hiçbir Numaralandırıcı döndürülmez.  
  
 [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) nesnesi, `_stackTrace` özel durum nesnesinin alanından yığın izleme verilerinin kodunu çözmekten sorumludur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionObjectValue Arabirimi](icordebugexceptionobjectvalue-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
