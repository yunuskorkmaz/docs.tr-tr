---
title: IMetaDataImport2 Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211939"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 Arabirimi
Genişletir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) genel türleri ile çalışmaktan yeteneği sağlamak için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumGenericParamConstraints Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.|  
|[EnumGenericParams Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Bir numaralandırıcı genel parametre belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizisi için belirteç alır.|  
|[EnumMethodSpecs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Bir numaralandırıcı MethodSpec Neobsahuje belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizisi için belirteç alır.|  
|[GetGenericParamConstraintProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlama ile ilişkili meta verileri alır.|  
|[GetGenericParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Belirtilen belirteç tarafından temsil edilen genel parametre ile ilişkili meta verileri alır.|  
|[GetMethodSpecProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.|  
|[GetPEKind Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Alır bir taşınabilir yürütülebilir (PE) kod yapısını tanımlayan bir değer dosya, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyası|  
|[GetVersionString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Derlemesi oluşturmak için kullanılan çalışma zamanı sürüm numarasını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.PortableExecutableKinds>
- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
