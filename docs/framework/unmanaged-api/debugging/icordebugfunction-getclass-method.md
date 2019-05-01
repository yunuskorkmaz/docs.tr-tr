---
title: ICorDebugFunction::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea71e984be42e3b1a7b4b9fa6df878aca911c412
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995767"
---
# <a name="icordebugfunctiongetclass-method"></a>ICorDebugFunction::GetClass Yöntemi
Bu işlev bir üyesi, sınıfın temsil ettiği bir Icordebugclass nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppClass`  
 [out] Adresini bir işaretçiye `ICorDebugClass` bu işlev bir sınıfın üyesi değilse, sınıf veya null temsil eden nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
