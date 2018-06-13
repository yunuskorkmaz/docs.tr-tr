---
title: ICorDebugFunction::GetClass Metodu
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
ms.openlocfilehash: 184e578efb549a1dc2e9ec1e30a29ff289b68719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411709"
---
# <a name="icordebugfunctiongetclass-method"></a>ICorDebugFunction::GetClass Metodu
Bu işlev bir üyesidir sınıfı temsil eden bir Icordebugclass nesnesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppClass`  
 [out] Bir işaretçi adresine `ICorDebugClass` bu işlev bir sınıf üyesi değilse sınıf veya null, temsil eden nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
