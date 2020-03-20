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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179257"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind Numaralandırması
Dışa aktarılan bir işlevin yönetilen kodu nasıl çağırdığını açıklar.  
  
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
|`CODE_INVOKE_KIND_NONE`|Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekir.<br /><br /> --veya--<br /><br /> Bu yöntemin aradığı yönetilen kodun bazılarını kaçırabiliriz, çünkü bunu durdurmanın kolay bir yolu yoktur.<br /><br /> --veya--<br /><br /> Yöntem yönetilen kodu hiçbir zaman çağıramayabilir.|  
|`CODE_INVOKE_KIND_RETURN`|Bu yöntem, bir iade yönergesi aracılığıyla yönetilen kodu çağırır. Dışarı çıkmak bir sonraki yönetilen koda ulaşmalıdır.|  
|`CODE_INVOKE_KIND_TAILCALL`|Bu yöntem, bir kuyruk çağrısı ile yönetilen kodu çağırır. Tek adımve herhangi bir çağrı yönergeleri üzerinden adım yönetilen kod almalısınız.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, yönetilen kodüzerinden adım atma hakkında bilgi sağlamak için [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Yerel hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata ayıklama](index.md)
