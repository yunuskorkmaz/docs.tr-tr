---
title: "COR_PRF_GC_ROOT_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_ROOT_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords: COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f340f9ad83d28b00054a0997bf4b60c750192bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS Numaralandırması
Çöp toplama kök özelliğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|Kök nesne taşınmasını çöp toplama engeller.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Kök çöp toplama engellemez.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Kök nesne yerine Nesne bir alana başvuruyor.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Nesne başvuru sayısı belirli bir değere ise kök çöp toplama engeller.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_GC_ROOT_FLAGS`Özel kökleri hakkında ek bilgi sağlayan bir bit maskesi olan. Ancak, tüm kökleri özel değildir. Örneğin, bazı kökleri zayıf başvurular, sabitlenmiş veya başvuruları sayılan iç işaretçiler değildir. Bu tür kökler için iletmek için hiçbir bayrakları vardır. Bu nedenle, bu numaralandırma gibi kullandığınız yöntemleri [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) yöntemi, tüm bayraklar belirten bayrakları bit maskesi için Gönder 0 kapalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma numaralandırmaları](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
