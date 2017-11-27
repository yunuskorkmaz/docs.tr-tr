---
title: "CorGenericParamAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95d7a6097766c8e2389e9828f54e81e37ffea454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr Numaralandırması
Açıklamak değerleri içeren <xref:System.Type> kullanılan çağrıları olarak genel türler için parametreleri [Imetadataemit2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|Parametre değişikliklerinin yalnızca genel parametreler arabirimleri ve temsilciler için uygulanır.|  
|`gpNonVariant`|Fark yokluğu gösterir.|  
|`gpCovariant`|Kovaryans gösterir.|  
|`gpContravariant`|Değişken karşıtı gösterir.|  
|`gpSpecialConstraintMask`|Özel kısıtlamalar için uygulayabileceğiniz <xref:System.Type> parametresi.|  
|`gpNoSpecialConstraint`|Hiçbir kısıtlama için geçerli olduğunu gösterir <xref:System.Type> parametresi.|  
|`gpReferenceTypeConstraint`|Belirten <xref:System.Type> parametresi, bir başvuru türü olmalıdır.|  
|`gpNotNullableValueTypeConstraint`|Belirten <xref:System.Type> parametresi null değer olamaz bir değer türü olmalıdır.|  
|`gpDefaultConstructorConstraint`|Belirten <xref:System.Type> parametre parametre almayan bir varsayılan ortak oluşturucu olması gerekir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
