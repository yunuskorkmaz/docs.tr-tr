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
ms.openlocfilehash: 4a65a98ee04c3870dae2f49b3da2a8e72b1ffae4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795839"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType Numaralandırması
Yığın çerçevesinin türünü tanımlar. Bu numaralandırma [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) yöntemi tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`STUBFRAME_NONE`|Null değer. `ICorDebugInternalFrame::GetFrameType` Yöntem hiçbir şekilde bu değeri döndürmez.|  
|`STUBFRAME_M2U`|Yönetilen-yönetilmeyen bir saplama çerçevesi.|  
|`STUBFRAME_U2M`|Yönetilmeyenden yönetilene bir saplama çerçevesi.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Uygulama etki alanları arasında geçiş.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Hafif bir yöntem çağrısı.|  
|`STUBFRAME_FUNC_EVAL`|İşlev değerlendirmesinin başlangıcı.|  
|`STUBFRAME_INTERNALCALL`|Ortak dil çalışma zamanına bir iç çağrı.|  
|`STUBFRAME_CLASS_INIT`|Bir sınıf başlatma başlangıcı.|  
|`STUBFRAME_EXCEPTION`|Oluşturulan özel durum.|  
|`STUBFRAME_SECURITY`|Kod erişim güvenliği için kullanılan çerçeve.|  
|`STUBFRAME_JIT_COMPILATION`|Çalışma zamanı JıT olarak bir yöntemi derlemedir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
