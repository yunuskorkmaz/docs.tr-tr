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
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176181"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr Numaralandırması
<xref:System.Type> [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)çağrılarında kullanıldığı gibi, genel türlerin parametrelerini açıklayan değerleri içerir.  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`gpVarianceMask`|Parametre varyansı yalnızca arabirimler ve temsilciler için genel parametreleriçin geçerlidir.|  
|`gpNonVariant`|Varyans yokluğunu gösterir.|  
|`gpCovariant`|Tutarlılık gösterir.|  
|`gpContravariant`|Zıtlığı gösterir.|  
|`gpSpecialConstraintMask`|Herhangi bir <xref:System.Type> parametreye özel kısıtlamalar uygulanabilir.|  
|`gpNoSpecialConstraint`|<xref:System.Type> Parametreiçin kısıtlama uygulanmadığını gösterir.|  
|`gpReferenceTypeConstraint`|Parametrenin <xref:System.Type> bir başvuru türü olması gerektiğini gösterir.|  
|`gpNotNullableValueTypeConstraint`|Parametrenin <xref:System.Type> null değeri olmayan bir değer türü olması gerektiğini gösterir.|  
|`gpDefaultConstructorConstraint`|Parametrenin <xref:System.Type> hiçbir parametre almayacak varsayılan bir ortak oluşturucuya sahip olması gerektiğini gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorHdr.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
