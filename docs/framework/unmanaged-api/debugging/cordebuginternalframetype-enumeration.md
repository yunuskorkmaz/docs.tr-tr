---
title: CorDebugInternalFrameType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cf4c0eb3f9bb36cb45aa93c576b4efddaa93482
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736539"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType Numaralandırması
Yığın çerçevesinin türünü tanımlar. Bu sabit listesi tarafından kullanılan [Icordebugınternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi.  
  
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
|`STUBFRAME_NONE`|Bir null değer. `ICorDebugInternalFrame::GetFrameType` Yöntemi hiçbir zaman bu değeri döndürür.|  
|`STUBFRAME_M2U`|Bir saplama yönetilmeyen çerçevesi.|  
|`STUBFRAME_U2M`|Bir saplama yönetilene çerçevesi.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Uygulama etki alanları arasında geçiş.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Basit bir yöntem çağrısı.|  
|`STUBFRAME_FUNC_EVAL`|İşlev değerlendirmesi başlangıcı.|  
|`STUBFRAME_INTERNALCALL`|Ortak dil çalışma zamanı bir iç çağrı.|  
|`STUBFRAME_CLASS_INIT`|Sınıf başlatması başlangıcı.|  
|`STUBFRAME_EXCEPTION`|Oluşturulan bir özel durum.|  
|`STUBFRAME_SECURITY`|Kod erişimi güvenliği için kullanılan bir çerçeve.|  
|`STUBFRAME_JIT_COMPILATION`|Çalışma zamanı JIT-derleme bir yöntem var.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
