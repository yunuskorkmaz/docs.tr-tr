---
title: COR_HEAPINFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fb1ae367c30bb038bfe25961e91f02f172f486c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405762"
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
|`areGCStructuresValid`|`true` Çöp toplama yapıları geçerlidir ve Öbek numaralandırılabilir; Aksi takdirde `false`.|  
|`pointerSize`|Hedef mimari işaretçilerde bayt boyutu.|  
|`numHeaps`|Mantıksal çöp toplama yığınlardaki işlem sayısı.|  
|`concurrent`|`TRUE` eşzamanlı varsa (arka plan) çöp toplama etkinleştirilir; Aksi takdirde `FALSE`.|  
|`gcType`|Üye [cordebuggctype sabit](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösteren numaralandırma.|  
  
## <a name="remarks"></a>Açıklamalar  
 Örneği `COR_HEAPINFO` yapısı çağırarak döndürülür [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.  
  
 Her zaman kontrol gerekir atık toplama yığın nesnelerde numaralandırma önce `areGCStructuresValid` alan öbek numaralandırılabilir bir durumda olduğundan emin olun. Daha fazla bilgi için bkz: [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
