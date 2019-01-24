---
title: CorDebugStateChange Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513795"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange Numaralandırması
Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`PROCESS_RUNNING`|İşlem, iletme yürütme aracılığıyla yeni bir bellek durumuna erişmedi.|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|İşlem bellek öncekinden rasgele farklı olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye `CorDebugStateChange` numaralandırma hata ayıklayıcı çağırdığında bir bağımsız değişken olarak sağlanan [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) yöntemi  
  
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
