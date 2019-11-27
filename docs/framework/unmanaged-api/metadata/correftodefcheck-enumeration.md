---
title: CorRefToDefCheck Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450126"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck Numaralandırması
Kodu iyileştirmek için hangi başvurulan öğelerin tanımlarına dönüştürüleceğini denetleyen bayrakları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`MDRefToDefDefault`|Tür başvurularının ve üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir. Bu varsayılan değerdir (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Başvurulan tüm öğelerin tanımlara dönüştürülmesi gerektiğini belirtir.|  
|`MDRefToDefNone`|Başvurulan hiçbir öğenin tanımlara dönüştürülmesi gerektiğini belirtir.|  
|`MDTypeRefToDef`|Yalnızca tür başvurularının tür tanımlarına dönüştürülmesi gerektiğini belirtir.|  
|`MDMemberRefToDef`|Yalnızca üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir. Diğer bir deyişle, üye başvuruları Yöntem tanımlarına veya alan tanımlarına dönüştürülmelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
