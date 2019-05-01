---
title: ICorDebugFunction::GetCurrentVersionNumber Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea615eacb30fd4e7a0fd7d730094c2ab4f9dc285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988734"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber Metodu
Bu ICorDebugFunction nesnesiyle temsil edilen işlevine yapılan en son düzenleme sürüm numarasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnCurrentVersion`  
 [out] Bu işleve yapılan en son düzenleme sürüm sayısı bir tamsayı değeri için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işleve yapılan en son düzenleme sürüm numarasını işlevi sürüm numarasından daha büyük olabilir. Hangisini [Icordebugfunction2::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) yöntemi veya [Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) işlevi sürüm numarasını almak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
