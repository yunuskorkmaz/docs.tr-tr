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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450282"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr Numaralandırması
[IMetaDataEmit2::D efineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)çağrılarında kullanılan genel türler için <xref:System.Type> parametrelerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`gpVarianceMask`|Parametre varyansı yalnızca arabirimler ve temsilciler için genel parametreler için geçerlidir.|  
|`gpNonVariant`|Varyans yokluğunu gösterir.|  
|`gpCovariant`|Kovaryansı gösterir.|  
|`gpContravariant`|Değişken varyansı gösterir.|  
|`gpSpecialConstraintMask`|Özel kısıtlamalar, herhangi bir <xref:System.Type> parametresi için uygulanabilir.|  
|`gpNoSpecialConstraint`|<xref:System.Type> parametresine hiçbir kısıtlamanın uygulanacağını gösterir.|  
|`gpReferenceTypeConstraint`|<xref:System.Type> parametresinin bir başvuru türü olması gerektiğini belirtir.|  
|`gpNotNullableValueTypeConstraint`|<xref:System.Type> parametresinin null değer olmayan bir değer türü olması gerektiğini belirtir.|  
|`gpDefaultConstructorConstraint`|<xref:System.Type> parametresinin, hiçbir parametre alan bir varsayılan genel oluşturucuya sahip olması gerektiğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
