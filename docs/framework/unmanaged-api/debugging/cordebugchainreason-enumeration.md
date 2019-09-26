---
title: CorDebugChainReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fce803544b393ac2c441779183cbf49d4c39bdae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273986"
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason Numaralandırması
Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CHAIN_NONE`|Hiçbir çağrı zinciri başlatılmadı.|  
|`CHAIN_CLASS_INIT`|Zincir bir Oluşturucu tarafından başlatıldı.|  
|`CHAIN_EXCEPTION_FILTER`|Zincir bir özel durum filtresi tarafından başlatıldı.|  
|`CHAIN_SECURITY`|Zincir, güvenliği zorlayan kod tarafından başlatıldı.|  
|`CHAIN_CONTEXT_POLICY`|Zincir bir bağlam ilkesi tarafından başlatıldı.|  
|`CHAIN_INTERCEPTION`|Kullanılmadı.|  
|`CHAIN_PROCESS_START`|Kullanılmadı.|  
|`CHAIN_THREAD_START`|Zincir, iş parçacığı yürütme başlangıcı tarafından başlatıldı.|  
|`CHAIN_ENTER_MANAGED`|Zincir, yönetilen koda giriş tarafından başlatıldı.|  
|`CHAIN_ENTER_UNMANAGED`|Zincir, yönetilmeyen koda giriş tarafından başlatıldı.|  
|`CHAIN_DEBUGGER_EVAL`|Kullanılmadı.|  
|`CHAIN_CONTEXT_SWITCH`|Kullanılmadı.|  
|`CHAIN_FUNC_EVAL`|Zincir bir işlev değerlendirmesi tarafından başlatıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir çağrı zincirinin başlatılması nedenlerini belirlemek için [ıcordebugzincirine:: GetReason](icordebugchain-getreason-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
