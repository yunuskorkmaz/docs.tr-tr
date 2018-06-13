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
ms.openlocfilehash: cf777214c015f0bbc434e3123d3ec7ef7f723549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405658"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind Numaralandırması
Yönetilen kod nasıl verilen işlevi çağırır açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`CODE_INVOKE_KIND_NONE`|Bu yöntem tarafından yönetilen kod çağrılırsa, açık olayları veya kesme noktaları tarafından daha sonra bulunması gerekir.<br /><br /> --veya--<br /><br /> Biz yalnızca üzerinde durdurmak için kolay bir yolu olduğundan bu yöntemi çağırır yönetilen kod bazıları kaçırabilir.<br /><br /> --veya--<br /><br /> Yöntemi, hiçbir zaman yönetilen kod çağırabilir.|  
|`CODE_INVOKE_KIND_RETURN`|Bu yöntemin dönüş yönergesi aracılığıyla yönetilen koda çağıracaktır. Atlama sonraki yönetilen koda ulaşması.|  
|`CODE_INVOKE_KIND_TAILCALL`|Bu yöntem, yönetilen kodu bir kuyruk çağrısı aracılığıyla çağırır. Tek atlama ve herhangi bir Adımlama çağrısı yönergeleri yönetilen kodu ulaşması.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi doğruluk hakkında bilgi sağlamak için yönetilen kod.  
  
> [!NOTE]
>  Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
