---
title: ICorDebugVariableHome::GetLocationType yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af879cbbf8edfd05e79d9b77b0c1fb71b2c835c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993661"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a>ICorDebugVariableHome::GetLocationType yöntemi
Yerel değişkenin konumun türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pLocationType`  
 [out] Yerel değişkenin konum türü bir işaretçi.  Bkz: [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) daha fazla bilgi için sabit listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
