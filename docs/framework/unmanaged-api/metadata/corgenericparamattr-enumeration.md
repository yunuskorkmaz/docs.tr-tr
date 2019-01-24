---
title: CorGenericParamAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf73f382c1da15e0285ee95be9e8bce39575ae0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557372"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr Numaralandırması
Açıklayan değerleri içeren <xref:System.Type> kullanılan çağrıları olarak genel türler için parametreleri [Imetadataemit2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`gpVarianceMask`|Parametre değişikliklerinin yalnızca arabirimlerde ve temsilcilerde genel parametreleri geçerlidir.|  
|`gpNonVariant`|Fark olmaması gösterir.|  
|`gpCovariant`|Birlikte değişkenlik gösterir.|  
|`gpContravariant`|Kontravaryans gösterir.|  
|`gpSpecialConstraintMask`|Özel kısıtlamalar için uygulayabileceğiniz <xref:System.Type> parametresi.|  
|`gpNoSpecialConstraint`|Hiçbir kısıtlaması için geçerli olduğunu gösterir <xref:System.Type> parametresi.|  
|`gpReferenceTypeConstraint`|Bildiren <xref:System.Type> parametresi, bir başvuru türü olmalıdır.|  
|`gpNotNullableValueTypeConstraint`|Bildiren <xref:System.Type> parametre bir null değer olamaz bir değer türü olması gerekir.|  
|`gpDefaultConstructorConstraint`|Bildiren <xref:System.Type> parametresi, parametre almayan varsayılan bir public Oluşturucu olması gerekir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
