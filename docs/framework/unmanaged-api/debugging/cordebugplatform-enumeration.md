---
title: CorDebugPlatform Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b6f1b29157889d0e84e5dddc94d5e3ae27efce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180951"
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform Numaralandırması
Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|Hedef, Intel x86 donanım üzerinde çalışan Windows platformudur.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Hedef, 64 bit Windows AMD64 veya Intel EM64T donanım üzerinde çalışan platformudur.|  
|CORDB_PLATFORM_WINDOWS_IA64|Hedef, Intel IA-64 donanım üzerinde çalışan 32 bit Windows platformudur.|  
|CORDB_PLATFORM_MAC_PPC|Hedef, PowerPC donanımda çalışan Macintosh işletim sistemi platformudur.|  
|CORDB_PLATFORM_MAC_X86|Hedef, Intel x86 donanımda çalışan Macintosh işletim sistemi platformudur.|  
|CORDB_PLATFORM_WINDOWS_ARM|Windows ARM donanım üzerinde çalışan Macintosh işletim sistemini hedef platformudur.|  
|CORDB_PLATFORM_MAC_AMD64|Hedef platform AMD64 donanımda çalışan Macintosh işletim sistemi ' dir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` Ve `CORDB_PLATFORM_MAC_AMD64` üyeleri olan .NET Framework 4.5.2 ve sonraki sürümlerinde kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
