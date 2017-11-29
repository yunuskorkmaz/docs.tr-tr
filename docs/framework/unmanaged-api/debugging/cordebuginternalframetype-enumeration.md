---
title: "CorDebugInternalFrameType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInternalFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugInternalFrameType
helpviewer_keywords: CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b21e50c86a09092e7df65e5fddefb515f6838b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType Numaralandırması
Yığın çerçevesi türünü tanımlar. Bu numaralandırma tarafından kullanılan [Icordebugınternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Bir null değer. `ICorDebugInternalFrame::GetFrameType` Yöntemi, hiçbir zaman bu değeri döndürür.|  
|`STUBFRAME_M2U`|Yönetilmeyen saplama çerçevesi.|  
|`STUBFRAME_U2M`|Bir yönetilen için yönetilmeyen saplama çerçevesi.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Uygulama etki alanları arasında geçiş.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Basit yöntem çağrısı.|  
|`STUBFRAME_FUNC_EVAL`|İşlev değerlendirmesi başlangıcı.|  
|`STUBFRAME_INTERNALCALL`|Ortak dil çalışma zamanı iç çağrısından.|  
|`STUBFRAME_CLASS_INIT`|Bir sınıf başlatma başlangıcı.|  
|`STUBFRAME_EXCEPTION`|Oluşturulan bir özel durum.|  
|`STUBFRAME_SECURITY`|Kod erişim güvenliği için kullanılan çerçeve.|  
|`STUBFRAME_JIT_COMPILATION`|Çalışma zamanı JIT-derleme bir yöntem ' dir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
