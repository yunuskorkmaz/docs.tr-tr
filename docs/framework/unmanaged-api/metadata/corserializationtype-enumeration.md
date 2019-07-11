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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9b7138d403bc84ab377301b82d697fd137416c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781589"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType Numaralandırması
Ortak dil çalışma zamanı tarafından bir nesne seri nasıl belirtir.  
  
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
|`SERIALIZATION_TYPE_UNDEFINED`|Nesnenin seri hale getirme tanımsızdır.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Bir Boolean türünde nesne seri hale getirilmiş|  
|`SERIALIZATION_TYPE_CHAR`|Nesnesi, bir karakter türü olarak seri hale getirilir.|  
|`SERIALIZATION_TYPE_I1`|İmzalı bir 1 baytlık tamsayı olarak serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_U1`|Nesne, işaretsiz bir 1 baytlık tamsayı olarak sıralanır.|  
|`SERIALIZATION_TYPE_I2`|Nesne bir imzalı 2 baytlık tamsayı olarak sıralanır.|  
|`SERIALIZATION_TYPE_U2`|Nesne, işaretsiz 2 baytlık tamsayı olarak sıralanır.|  
|`SERIALIZATION_TYPE_I4`|İmzalı bir 4 baytlık tamsayı olarak serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_U4`|Nesne, işaretsiz bir 4 baytlık tamsayı olarak sıralanır.|  
|`SERIALIZATION_TYPE_I8`|Nesne bir işaretli 8 baytlık tamsayı sıralanır.|  
|`SERIALIZATION_TYPE_U8`|İmzalanmamış 8 baytlık tamsayı olarak serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_R4`|4-bayt kayan nokta serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_R8`|8-bayt kayan nokta serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_STRING`|Nesne System.String türünde seri hale getirilir.|  
|`SERIALIZATION_TYPE_SZARRAY`|Nesne seri hale getirilmiş bir tek boyutlu, sıfır alt sınırı dizisi.|  
|`SERIALIZATION_TYPE_TYPE`|Nesne genel bir tür seri hale getirilir.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Nesne etiketli bir nesnesi olarak seri hale getirilir.|  
|`SERIALIZATION_TYPE_FIELD`|Bir alan olarak serileştirilmiş nesne.|  
|`SERIALIZATION_TYPE_PROPERTY`|Nesnenin bir özellik olarak seri hale getirilir.|  
|`SERIALIZATION_TYPE_ENUM`|Nesne sabit olarak seri hale getirilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
