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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 858dfe9b15422680a261fef9e22d8c89d9d7fe45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155577"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>CorDebugCodeInvokePurpose Numaralandırması
Neden yönetilen kod dışa aktarılan bir işlevin çağrıları açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`CODE_INVOKE_PURPOSE_NONE`|Yok veya bilinmeyen.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Yönetilen kod ters p-invoke gibi herhangi bir yönetilen giriş noktasını çalışır. Daha ayrıntılı herhangi bir amaç, çalışma zamanı tarafından bilinmiyor.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Yönetilen kod, bir statik Oluşturucu çalışır.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Yönetilen kod çağrıldı bazı arabirim yöntemi için uygulama çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu sabit listesi tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi üzerinden Adımlama hakkında bilgi sağlamak için yönetilen kod.  
  
> [!NOTE]
>  Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
