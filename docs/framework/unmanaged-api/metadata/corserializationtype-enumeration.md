---
title: "CorSerializationType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType Numaralandırması
Bir nesne ortak dil çalışma zamanı tarafından nasıl serileştirilmiş belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Nesnenin seri hale getirme tanımlanmamıştır.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Boolean türünde nesne seri hale getirilmiş|  
|`SERIALIZATION_TYPE_CHAR`|Nesne bir karakter türü olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I1`|Nesne imzalı 1-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U1`|Nesne imzasız 1-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I2`|Nesne olarak imzalanmış bir 2-bayt tamsayı serileştirilir.|  
|`SERIALIZATION_TYPE_U2`|Nesne imzasız 2-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I4`|Nesne imzalı 4-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U4`|Nesne imzasız 4-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I8`|Nesne işaretli 8-bayt tamsayı serileştirilir.|  
|`SERIALIZATION_TYPE_U8`|Nesne imzasız 8-bayt tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_R4`|Nesne 4-bayt kayan nokta serileştirilir.|  
|`SERIALIZATION_TYPE_R8`|Nesne 8-bayt kayan nokta serileştirilir.|  
|`SERIALIZATION_TYPE_STRING`|Nesne System.String türünde serileştirilir.|  
|`SERIALIZATION_TYPE_SZARRAY`|Nesne seri hale getirilmiş bir tek boyutlu, sıfır alt sınır dizi.|  
|`SERIALIZATION_TYPE_TYPE`|Nesne genel bir tür serileştirilir.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Nesne etiketli bir nesne olarak seri değildir.|  
|`SERIALIZATION_TYPE_FIELD`|Nesne bir alan olarak serileştirilir.|  
|`SERIALIZATION_TYPE_PROPERTY`|Nesne bir özellik olarak serileştirilir.|  
|`SERIALIZATION_TYPE_ENUM`|Nesne sabit olarak serileştirilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
