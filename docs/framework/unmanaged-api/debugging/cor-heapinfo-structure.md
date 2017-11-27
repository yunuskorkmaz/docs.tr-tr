---
title: "COR_HEAPINFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPINFO
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPINFO
helpviewer_keywords: COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e316b964e3e983f50b81228709623e162529b05c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corheapinfo-structure"></a>COR_HEAPINFO Yapısı
Numaralandırılabilir olup olmadığını atık toplama yığın hakkında genel bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`Çöp toplama yapıları geçerlidir ve Öbek numaralandırılabilir; Aksi takdirde `false`.|  
|`pointerSize`|Hedef mimari işaretçilerde bayt boyutu.|  
|`numHeaps`|Mantıksal çöp toplama yığınlardaki işlem sayısı.|  
|`concurrent`|`TRUE`eşzamanlı varsa (arka plan) çöp toplama etkinleştirilir; Aksi takdirde `FALSE`.|  
|`gcType`|Üye [cordebuggctype sabit](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösteren numaralandırma.|  
  
## <a name="remarks"></a>Açıklamalar  
 Örneği `COR_HEAPINFO` yapısı çağırarak döndürülür [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.  
  
 Her zaman kontrol gerekir atık toplama yığın nesnelerde numaralandırma önce `areGCStructuresValid` alan öbek numaralandırılabilir bir durumda olduğundan emin olun. Daha fazla bilgi için bkz: [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
