---
title: 'Icordebugvariablehome:: GetLocationType yöntemi'
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
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125107"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a>Icordebugvariablehome:: GetLocationType yöntemi
Değişkenin yerel konumunun türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pLocationType`  
 dışı Değişkenin yerel konumunun türüne yönelik bir işaretçi.  Daha fazla bilgi için, bkz. [Variablelocationtype](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) sabit listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
