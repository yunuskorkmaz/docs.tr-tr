---
title: "CorDebugJITCompilerFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfb78a160a7a6b9f50174fc8bb177cfd8d3f9383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags Numaralandırması
Yönetilen tam zamanında (JIT) derleyici davranışını etkilemek değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|Derleyici derleme verileri izlemek ve iyileştirmeler sağlar belirtir.|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|Derleyici devre dışı bırakır iyileştirmeler ancak derleme verileri izlemek belirtir.|  
|`CORDEBUG_JIT_ENABLE_ENC`|Derleme verileri, devre dışı bırakır iyileştirmeler derleyici izlemek ve etkinleştirir Düzenle ve devam teknolojileri belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
