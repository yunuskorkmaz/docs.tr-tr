---
title: CorPropertyAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007539"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr Numaralandırması
Bir özelliğin meta verilerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`prSpecialName`|Özelliğin özel olduğunu ve adının nasıl kullanıldığını belirtir.|  
|`prReservedMask`|Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.|  
|`prRTSpecialName`|Ortak dil çalışma zamanı meta veri iç API 'Lerinin, özellik adının kodlamasını denetlemesi gerektiğini belirtir.|  
|`prHasDefault`|Özelliğin varsayılan bir değere sahip olduğunu belirtir.|  
|`prUnused`|Kullanılmıyor.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
