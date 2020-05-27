---
title: CorSerializationType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009177"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType Numaralandırması
Bir nesnenin ortak dil çalışma zamanı tarafından nasıl serileştirildiği belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`SERIALIZATION_TYPE_UNDEFINED`|Nesnenin serileştirilmesi tanımsız.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Nesne, Boole türü olarak serileştirilir|  
|`SERIALIZATION_TYPE_CHAR`|Nesne bir karakter türü olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I1`|Nesne, işaretli bir 1 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U1`|Nesne işaretsiz bir 1 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I2`|Nesne, işaretli bir 2 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U2`|Nesne işaretsiz bir 2 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I4`|Nesne, imzalanmış 4 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U4`|Nesne işaretsiz 4 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_I8`|Nesne, imzalanmış 8 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_U8`|Nesne işaretsiz 8 baytlık tamsayı olarak serileştirilir.|  
|`SERIALIZATION_TYPE_R4`|Nesne 4 baytlık kayan nokta olarak serileştirilir.|  
|`SERIALIZATION_TYPE_R8`|Nesne 8 baytlık kayan nokta olarak serileştirilir.|  
|`SERIALIZATION_TYPE_STRING`|Nesne bir System. String türü olarak serileştirilir.|  
|`SERIALIZATION_TYPE_SZARRAY`|Nesne tek boyutlu, sıfır alt sınır dizisi olarak serileştirilir.|  
|`SERIALIZATION_TYPE_TYPE`|Nesne genel bir tür olarak serileştirilir.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Nesne etiketli bir nesne olarak serileştirilir.|  
|`SERIALIZATION_TYPE_FIELD`|Nesne bir alan olarak serileştirilir.|  
|`SERIALIZATION_TYPE_PROPERTY`|Nesne bir özellik olarak serileştirilir.|  
|`SERIALIZATION_TYPE_ENUM`|Nesne bir sabit listesi olarak serileştirilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
