---
title: "CorRefToDefCheck Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 366110eca3c4621866213b2c9fc4bcf99103d0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck Numaralandırması
Hangi başvurulan öğelerin tanımlarını için kod iyileştirmek üzere dönüştürülür denetim bayrakları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`MDRefToDefDefault`|Tür başvuruları ve üye başvuruları tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir. Bu varsayılan değerdir (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Başvurulan tüm öğeleri tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir.|  
|`MDRefToDefNone`|Başvuruda bulunulan öğe tanımları dönüştürülüp dönüştürülmeyeceğini belirtir.|  
|`MDTypeRefToDef`|Yalnızca tür başvuruları tür tanımı için dönüştürüleceğini belirtir.|  
|`MDMemberRefToDef`|Yalnızca üye başvurular tanımlarını dönüştürülüp dönüştürülmeyeceğini belirtir. Diğer bir deyişle, üye başvuruları yöntemi tanımları veya alan tanımları için dönüştürülmelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
