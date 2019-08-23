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
ms.openlocfilehash: 6fa8de1a561e59e00d5bd9e78172d78b417aeff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951963"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind Numaralandırması
Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.  
  
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
|`CODE_INVOKE_KIND_NONE`|Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekecektir.<br /><br /> --veya--<br /><br /> Üzerinde durmanın kolay bir yolu olmadığından, bu yöntemin çağırdığı bazı yönetilen koddan bazılarını kaçırabilir.<br /><br /> --veya--<br /><br /> Yöntemi hiçbir şekilde yönetilen kodu çağırmayabilir.|  
|`CODE_INVOKE_KIND_RETURN`|Bu yöntem, bir dönüş yönergesi aracılığıyla yönetilen kodu çağırır. Adımlama, sonraki yönetilen koda ulaşmalıdır.|  
|`CODE_INVOKE_KIND_TAILCALL`|Bu yöntem, bir tail çağrısı aracılığıyla yönetilen kodu çağırır. Tüm çağrı yönergelerinin tek adımlamayı ve adımlamayı yönetilen koda ulaşmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
