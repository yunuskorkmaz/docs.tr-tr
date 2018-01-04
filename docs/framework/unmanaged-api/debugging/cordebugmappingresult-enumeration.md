---
title: "CorDebugMappingResult Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 924cfec87b99cba9621af02d4e78e72094060ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult Numaralandırması
Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Yerel kod giriş bölümünde olduğundan, IP değeri 0'dır.|  
|`MAPPING_EPILOG`|Yerel kod bir bitiş içinde olduğundan, yönteminin son yönerge adresi IP değeri.|  
|`MAPPING_NO_INFO`|0 IP değeri için hiçbir eşleme bilgilerini yöntemi için kullanılabilir.|  
|`MAPPING_UNMAPPED_ADDRESS`|Geçerli adres yöntemi için eşleme bilgilerini olsa da, Microsoft Ara dili (MSIL) kodu eşlenemez. IP değeri 0'dır.|  
|`MAPPING_EXACT`|Tam olarak MSIL koda yöntemi eşler ya da IP değeri doğru biçimde çerçeve, yorumlanan.|  
|`MAPPING_APPROXIMATE`|Yöntem başarıyla eşlendi, ancak IP değerini yaklaşık olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz [Icordebugılframe::getıp](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) yönerge işaretçisi değeri elde etmek için yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
