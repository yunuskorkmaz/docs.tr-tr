---
title: "COR_ARRAY_LAYOUT Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b936b1b2187ec68db7f5fdecb0344e6cac211ab1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT Yapısı
Bellekte bir dizi nesnesi düzen hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`componentID`|Dizinin içerdiği nesnelerin türü tanımlayıcısı.|  
|`componentType`|Bileşen bir atık toplama başvuru, bir değer sınıfı ya da basit bir tür olup olmadığını belirten bir CorElementType numaralandırması değer.|  
|`firstElementOffset`|Dizinin ilk öğe uzaklık.|  
|`elementSize`|Her öğe boyutu.|  
|`countOffset`|Dizideki öğelerin sayısı uzaklık.|  
|`rankSize`|Derecesini bayt cinsinden boyutu.|  
|`numRanks`|Dizideki sıralar sayısı.|  
|`rankOffset`|Hangi sıralar başlangıç uzaklığı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `rankSize` Alan çok boyutlu bir dizi sırası boyutunu belirtir. De tek boyutlu diziler doğru olur.  
  
 Değeri `numRanks` tek boyutlu bir dizi için 1'dir ve `N` çok boyutlu bir dizi için `N` boyutları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
