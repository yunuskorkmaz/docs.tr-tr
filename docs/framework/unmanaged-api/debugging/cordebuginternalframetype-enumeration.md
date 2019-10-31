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
ms.openlocfilehash: e76800316885c27c697421d454341d5f0789c611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097945"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType Numaralandırması
Yığın çerçevesinin türünü tanımlar. Bu numaralandırma [ICorDebugInternalFrame:: GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi tarafından kullanılır.  
  
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
|`STUBFRAME_NONE`|Null değer. `ICorDebugInternalFrame::GetFrameType` yöntemi bu değeri hiçbir şekilde döndürmez.|  
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
