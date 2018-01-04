---
title: ICorDebugCode::GetFunction Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d05d5d7172a43ebaa04155fb42c2711eaf1ac085
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetfunction-method"></a>ICorDebugCode::GetFunction Metodu
"Bu"Icordebugcode"ile ilişkili ICorDebugFunction" alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppFunction`  
 [out] İşlevin adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode`ve `ICorDebugFunction` bire bir ilişki korumak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
