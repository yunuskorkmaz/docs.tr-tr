---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugPlatform numaralandırması'
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
ms.openlocfilehash: d6a78ec00f99ff34158f784e039372c8937e6d16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661863"
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform Numaralandırması

[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
|Üye|Description|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|Hedef platform, Intel x86 donanımında çalışan bir Windows.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Hedef platform, AMD64 veya Intel EM64T donanımında çalışan 64 bitlik bir Windows.|  
|CORDB_PLATFORM_WINDOWS_IA64|Hedef platform Intel IA-64 donanımında çalışan 32 bit Windows.|  
|CORDB_PLATFORM_MAC_PPC|Hedef platform, PowerPC donanımında çalışan Macintosh işletim sistemidir.|  
|CORDB_PLATFORM_MAC_X86|Hedef platform, Intel x86 donanımında çalışan Macintosh işletim sistemidir.|  
|CORDB_PLATFORM_WINDOWS_ARM|Hedef platform, Windows ARM donanımında çalışan Macintosh işletim sistemidir.|  
|CORDB_PLATFORM_MAC_AMD64|Hedef platform, AMD64 donanımında çalışan Macintosh işletim sistemidir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM`Ve `CORDB_PLATFORM_MAC_AMD64` üyeleri .NET Framework 4.5.2 ve sonraki sürümlerde kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
