---
title: CorDebugCodeInvokeKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059e823110686a2b939c9664fa5b67e4041c3486
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740319"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind Numaralandırması
Dışarı aktarılan bir işlevin yönetilen kod nasıl çağırır açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Herhangi bir yönetilen kod tarafından bu yöntemi çağrılırsa, açık olayları veya kesme noktaları tarafından daha sonra yer alması gerekir.<br /><br /> --veya--<br /><br /> Biz yalnızca bazı üzerinde durdurmak için kolay bir yolu yoktur çünkü bu yöntemi çağırır. yönetilen kodun kaçırabilir.<br /><br /> --veya--<br /><br /> Yöntemi, yönetilen kod asla çağırabilir.|  
|`CODE_INVOKE_KIND_RETURN`|Bu yöntem dönüş yönerge aracılığıyla yönetilen kodu çağırır. Adımlama sonraki yönetilen koda ulaşacak.|  
|`CODE_INVOKE_KIND_TAILCALL`|Bir kuyruk çağrısı aracılığıyla yönetilen kodu bu yöntemi çağırır. Tek adımlama ve herhangi bir Adımlama yönetilen koda çağrı yönergeleri ulaşacak.|  
  
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
