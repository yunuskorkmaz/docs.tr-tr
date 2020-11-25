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
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704922"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr Numaralandırması

<xref:System.Type> [Imetadataemit2::D efineGenericParam](imetadataemit2-definegenericparam-method.md)çağrılarında kullanılan genel türlerin parametrelerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
|`gpVarianceMask`|Parametre varyansı yalnızca arabirimler ve temsilciler için genel parametreler için geçerlidir.|  
|`gpNonVariant`|Varyans yokluğunu gösterir.|  
|`gpCovariant`|Kovaryansı gösterir.|  
|`gpContravariant`|Değişken varyansı gösterir.|  
|`gpSpecialConstraintMask`|Özel kısıtlamalar, herhangi bir <xref:System.Type> parametreye uygulanabilir.|  
|`gpNoSpecialConstraint`|Parametreye hiçbir kısıtlama uygulanacağını gösterir <xref:System.Type> .|  
|`gpReferenceTypeConstraint`|<xref:System.Type>Parametrenin bir başvuru türü olması gerektiğini belirtir.|  
|`gpNotNullableValueTypeConstraint`|<xref:System.Type>Parametrenin null değer olmayan bir değer türü olması gerektiğini belirtir.|  
|`gpDefaultConstructorConstraint`|<xref:System.Type>Parametresinin parametre alan bir varsayılan genel oluşturucuya sahip olması gerektiğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
