---
title: ICorDebugVariableHome::GetCode yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4cadae7a43d0cd965e51535eae2c95e59900d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993622"
---
# <a name="icordebugvariablehomegetcode-method"></a>ICorDebugVariableHome::GetCode yöntemi
Bu içeren "ICorDebugCode" örneğini alır [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bu içeren "ICorDebugCode" örneğini adresini bir işaretçiye [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
