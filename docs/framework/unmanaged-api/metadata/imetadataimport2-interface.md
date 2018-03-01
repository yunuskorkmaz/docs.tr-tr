---
title: IMetaDataImport2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cd9d2cd2837ff43fbb266717546db3aa98190e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 Arabirimi
Genişletir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi genel türleri ile çalışma özelliği sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumGenericParamConstraints Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili genel parametresi kısıtlamaları dizisi için bir numaralandırıcı alır.|  
|[EnumGenericParams Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Bir numaralandırıcı genel parametresini belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizi belirteci alır.|  
|[EnumMethodSpecs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Bir numaralandırıcı MethodSpec belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizi belirteci alır.|  
|[GetGenericParamConstraintProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Belirtilen kısıtlama belirtecin tarafından temsil edilen genel parametresini kısıtlaması ile ilişkili meta verileri alır.|  
|[GetGenericParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili meta verileri alır.|  
|[GetMethodSpecProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.|  
|[GetPEKind Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlı genellikle bir DLL veya EXE dosyası dosyasında,|  
|[GetVersionString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.PortableExecutableKinds>  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
