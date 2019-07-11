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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ae87dd4538a9a8e88591f498c0ce77b51bfa852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781615"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck Numaralandırması
Başvurulan öğeleri kod iyileştirmek için tanımları için dönüştürülür denetim bayrakları belirtir.  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDRefToDefDefault`|Tür başvurularını ve üye başvuruları tanımlara dönüştürülüp dönüştürülmeyeceğini belirtir. Varsayılan değer budur (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Tüm başvurulan öğelerin tanımlarını dönüştürülmesi gerektiğini belirtir.|  
|`MDRefToDefNone`|Başvurulan öğe tanımlarını dönüştürülmesi gerektiğini belirtir.|  
|`MDTypeRefToDef`|Yalnızca tür başvurularını tür tanımlarına dönüştürülmesi gerektiğini belirtir.|  
|`MDMemberRefToDef`|Yalnızca üye başvuruları tanımlara dönüştürülmesi gerektiğini belirtir. Diğer bir deyişle, üye başvuruları yöntemi tanımları veya alan tanımları dönüştürülmelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
