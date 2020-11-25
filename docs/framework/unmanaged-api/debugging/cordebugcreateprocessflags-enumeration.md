---
title: CorDebugCreateProcessFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: f6f589656a3063fc89bd276b32d0ed751fd8d2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733405"
---
# <a name="cordebugcreateprocessflags-enumeration"></a>CorDebugCreateProcessFlags Numaralandırması

[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|Hiçbir özel seçenek ayarlanmadı.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
