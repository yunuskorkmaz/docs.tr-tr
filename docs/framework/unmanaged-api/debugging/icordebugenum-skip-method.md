---
title: "ICorDebugEnum::Skip Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum.Skip
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c2e0065b8dd16e32ed624dd073276e7885c1a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumskip-method"></a>ICorDebugEnum::Skip Yöntemi
İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] İmleç ilerlemek, öğe sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
