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
ms.openlocfilehash: f037a28f0417f5607cd5b5637da4ca62e34e0edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132259"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>CorDebugCodeInvokePurpose Numaralandırması
Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.  
  
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
|`CODE_INVOKE_PURPOSE_NONE`|Hiçbiri veya bilinmiyor.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Yönetilen kod, ters p-Invoke gibi herhangi bir yönetilen giriş noktasını çalıştırır. Daha ayrıntılı bir amaç çalışma zamanı tarafından bilinmiyor.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Yönetilen kod statik bir Oluşturucu çalıştıracak.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Yönetilen kod, çağrılan bazı arabirim yöntemleri için uygulamayı çalıştırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
