---
title: CorDebugCodeInvokePurpose Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179237"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>CorDebugCodeInvokePurpose Numaralandırması
Dışa aktarılan bir işlevin yönetilen kodu neden aradığını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|Hiç ya da bilinmeyen.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Yönetilen kod, ters p-çağırma gibi yönetilen herhangi bir giriş noktasını çalıştıracaktır. Daha ayrıntılı bir amaç çalışma süresine göre bilinmemektedir.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Yönetilen kod statik bir oluşturucu çalıştıracak.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Yönetilen kod, çağrılan bazı arabirim yöntemi için uygulamayı çalıştıracaktır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, yönetilen kodüzerinden adım atma hakkında bilgi sağlamak için [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Yerel hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
