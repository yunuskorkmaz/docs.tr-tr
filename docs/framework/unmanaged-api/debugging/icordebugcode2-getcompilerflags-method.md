---
title: ICorDebugCode2::GetCompilerFlags Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0e8d36b3551b3520213e1c2ffa7e2d215e8535b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcompilerflags-method"></a>ICorDebugCode2::GetCompilerFlags Metodu
Bu kod nesnesi ya da sadece derlenmiş veya yerel Görüntü Oluşturucu (Ngen.exe) kullanılarak oluşturulan zamanında (JIT) altında olduğu koşulları belirten bayrakları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwFlags`  
 [out] Değerini gösteren bir işaretçi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) JIT Derleyici veya yerel Görüntü Oluşturucu davranışını belirtir numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
