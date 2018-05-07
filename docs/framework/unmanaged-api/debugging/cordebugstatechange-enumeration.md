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
ms.openlocfilehash: 841108457293e3377ee87f9c7d7c6898340e51b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange Numaralandırması
Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.  
  
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
|`PROCESS_RUNNING`|İşlem ileriye doğru yürütme aracılığıyla yeni bir bellek durum sınırına ulaşıldı.|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|İşlem bellek öncekinden daha rasgele farklı olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye `CorDebugStateChange` numaralandırma, bağımsız değişken olarak sağlanır, hata ayıklayıcı çağırdığında [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) yöntemi  
  
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
