---
title: "CorDebugChainReason Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1951983c9d167862169bd6178dc65693d724dc0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason Numaralandırması
Neden veya çağrı zincirine başlatma nedenlerle gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`CHAIN_NONE`|Hiçbir çağrı zincirine başlatıldı.|  
|`CHAIN_CLASS_INIT`|Zincirdeki bir Oluşturucu tarafından başlatıldı.|  
|`CHAIN_EXCEPTION_FILTER`|Zincirdeki bir özel durum Filtresi tarafından başlatıldı.|  
|`CHAIN_SECURITY`|Zincir güvenlik zorlar kodu tarafından başlatıldı.|  
|`CHAIN_CONTEXT_POLICY`|Zincirdeki bir bağlam İlkesi tarafından başlatıldı.|  
|`CHAIN_INTERCEPTION`|Kullanılmadı.|  
|`CHAIN_PROCESS_START`|Kullanılmadı.|  
|`CHAIN_THREAD_START`|Zincirdeki bir iş parçacığı yürütme başlangıç tarafından başlatıldı.|  
|`CHAIN_ENTER_MANAGED`|Zincir giriş yönetilen koda tarafından başlatıldı.|  
|`CHAIN_ENTER_UNMANAGED`|Zincir giriş yönetilmeyen koda tarafından başlatıldı.|  
|`CHAIN_DEBUGGER_EVAL`|Kullanılmadı.|  
|`CHAIN_CONTEXT_SWITCH`|Kullanılmadı.|  
|`CHAIN_FUNC_EVAL`|Zincirdeki bir işlev değerlendirmesi tarafından başlatıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) çağrı zincirine başlatma nedenlerle onaylaması için yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
