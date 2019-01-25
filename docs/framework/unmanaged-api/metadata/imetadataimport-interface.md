---
title: IMetaDataImport Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4241f2057ce77713f91e969eda7765739613333
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732849"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport Arabirimi
İçeri aktarma ve taşınabilir yürütülebilir (PE) dosya veya bir tür kitaplığı veya tek başına, çalışma zamanı meta verileri ikili gibi başka bir kaynağı var olan meta verileri işlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Belirtilen tanıtıcısıyla Numaralandırıcı kapatır.|  
|[CountEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Öğe sayısı ile belirtilen tanıtıcı bir numaralandırıcı alır.|  
|[EnumCustomAttributes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Belirtilen tür veya üye ile ilişkili özel öznitelik tanımı belirteçleri listesini numaralandırır.|  
|[EnumEvents Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Olay tanımı belirteçleri TypeDef belirteç numaralandırır.|  
|[EnumFields Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|FieldDef simgesi belirteçleri için belirtilen TypeDef belirteci tarafından başvurulan türünü numaralandırır.|  
|[EnumFieldsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Belirtilen ada sahip belirtilen türün fieldDef simgesi belirteçleri numaralandırır.|  
|[EnumInterfaceImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Arabirim uygulamalarına temsil eden MethodDef belirteçleri numaralandırır.|  
|[EnumMemberRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Belirtilen türün üyelerini temsil eden MemberRef belirteçleri numaralandırır.|  
|[EnumMembers Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Belirtilen türün üyelerini temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumMembersWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Belirtilen ada sahip belirtilen türün üyelerini temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumMethodImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Belirtilen türün yöntemlerini temsil eden MethodBody ve MethodDeclaration belirteçleri numaralandırır.|  
|[EnumMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Belirtilen türün yöntemlerini temsil eden MethodDef belirteçleri numaralandırır.|  
|[EnumMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Özellikler ve belirtilen yöntem ilgili olduğu özellik değiştirme olayları numaralandırır.|  
|[EnumMethodsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Belirtilen ada sahip ve belirtilen TypeDef belirteci tarafından başvurulan tür tarafından tanımlanan yöntemlerini numaralandırır.|  
|[EnumModuleRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|İçeri aktarılan modülleri temsil eden ModuleRef belirteçleri numaralandırır.|  
|[EnumParams Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Belirtilen MethodDef belirteci tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.|  
|[EnumPermissionSets Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Belirtilen meta veri kapsamdaki nesneler için izinleri numaralandırır.|  
|[EnumProperties Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Belirtilen tür tanımı belirteci tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.|  
|[EnumSignatures Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Tek başına imzaları geçerli kapsamda temsil eden imzası belirteçlerinin numaralandırır.|  
|[EnumTypeDefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Geçerli kapsamdaki tüm türleri temsil eden TypeDef belirteçleri numaralandırır.|  
|[EnumTypeRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Geçerli meta veri kapsamda tanımlanan TypeRef belirteçleri numaralandırır.|  
|[EnumTypeSpecs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Geçerli meta veri kapsamda tanımlanan TypeSpec'te belirteçleri numaralandırır.|  
|[EnumUnresolvedMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Geçerli meta veri kapsamda çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumUserStrings Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Dize belirteçleri sabit kodlanmış dizeleri geçerli meta veri kapsamda temsil eden numaralandırır.|  
|[FindField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|FieldDef simgesi belirtilen tür üyesi olan ve belirtilen ada ve meta veri imzası olan bir alan için belirteç alır.|  
|[FindMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Bir işaretçi için MemberDef belirtilen ada ve meta verileri imza ile belirtilen tür tarafından tanımlanan üyesi için belirteç alır.|  
|[FindMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Bir işaretçi için MemberRef belirtilen ada ve meta verileri imza ile belirtilen tür tarafından tanımlanan üyesi için belirteç alır.|  
|[FindMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Bir işaretçi için MethodDef belirtilen ada ve meta verileri imza ile belirtilen türe göre tanımlanan yöntemi için belirteç alır.|  
|[FindTypeDefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Bir işaretçi için bir TypeDef meta veri türü için belirtilen ada sahip belirtecini alır.|  
|[FindTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Belirtilen ada sahip belirtilen arama kapsamda türe başvuran TypeRef meta veri belirteci için bir işaretçi alır.|  
|[GetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Belirtilen tür tanımı tarafından başvurulan sınıfın düzen bilgilerini belirtecini alır.|  
|[GetCustomAttributeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Adı verilen özel özniteliğinin değerini alır.|  
|[GetCustomAttributeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Kendi meta veri belirteci verilen özel özniteliğinin değerini alır.|  
|[GetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Belirtilen olay belirteci tarafından temsil edilen olay (bildirim türü, ekleme dahil olmak üzere ve Temsilciler, yöntemleri ve tüm bayraklar ve diğer ilişkili verileri kaldırma) meta veri bilgilerini alır.|  
|[GetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Belirtilen alan metaveri belirteci tarafından temsil edilen alan yerel, yönetilmeyen tür için bir işaretçi alır.|  
|[GetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Belirteç belirtilen fieldDef simgesi tarafından başvurulan alanı ile ilişkili meta verileri alır.|  
|[GetInterfaceImplProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Bir işaretçi, belirtilen yöntemini uygulayan bir tür için ve bu yöntem bir arabirim için meta veri belirteçlerini alır.|  
|[GetMemberProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Belirtilen meta veri belirteci tarafından başvurulan tür üyesi meta veri bilgilerini (adı, ikili imzası ve göreli sanal adres dahil) alır.|  
|[GetMemberRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.|  
|[GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Belirtilen MethodDef tarafından başvurulan yöntemi ile ilişkili meta veri belirteci alır.|  
|[GetMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Bir işaretçi belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan metot ve olay tarafından belirtilen EventProp başvurulan arasındaki ilişki için belirteç alır.|  
|[GetModuleFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Bir işaretçi için meta veriler geçerli meta veri kapsamda başvuru modülü için belirteç alır.|  
|[GetModuleRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Belirtilen meta veri belirteci tarafından başvurulan modül adını alır.|  
|[GetNameFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Belirtilen meta veri belirteci tarafından başvurulan nesne UTF-8 adını alır.|  
|[GetNativeCallConvFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Yerel bir belirtilen imza işaretçi tarafından temsil edilen yöntem için çağırma alır.|  
|[GetNestedClassProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|TypeDef, belirtilen iç içe türün kapsayan üst türü için belirteç alır.|  
|[GetParamForMethodIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Parametre belirtilen konumda sıralı sırada belirtilen MethodDef belirteci tarafından temsil edilen yönteme yöntemi parametrelerinin temsil eden belirteci için bir işaretçi alır.|  
|[GetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Meta veri değerleri tarafından belirtilen ParamDef başvurulan parametresi için belirteç alır.|  
|[GetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Belirtilen izin belirteci tarafından temsil edilen System.Security.PermissionSet ile ilişkili meta verileri alır.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Bir ModuleRef PInvoke çağrısına hedef derleme temsil etmek için belirteç alır.|  
|[GetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Belirtilen belirteç tarafından temsil edilen özelliği ilişkili meta verileri alır.|  
|[GetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Belirtilen belirteç tarafından temsil edilen kod nesnesinin göreli sanal adres uzaklığı alır.|  
|[GetScopeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Geçerli meta veri kapsamdaki ad ve isteğe bağlı olarak derlemesi veya modülü sürüm tanımlayıcısını alır.|  
|[GetSigFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Belirtilen belirteçle ilişkili ikili meta veri imzası alır.|  
|[GetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Belirtilen tür tanımı belirteci tarafından temsil edilen türü için meta veri bilgileri döndürür.|  
|[GetTypeRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Belirtilen TypeRef tarafından başvurulan türü ile ilişkili meta veri belirteci alır.|  
|[GetTypeSpecFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Belirtilen belirteç tarafından temsil edilen tür belirtimi ikili meta veri imzası alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Belirtilen meta veri belirteci tarafından temsil edilen sabit dizesini alır.|  
|[IsGlobal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Alan, yöntem veya belirtilen metaveri belirteci tarafından temsil edilen tür genel kapsamda sahip olup olmadığını gösteren bir değer alır.|  
|[IsValidToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Belirtilen belirteç kod nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.|  
|[ResetEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Belirtilen Numaralandırıcı belirtilen konuma sıfırlar.|  
|[ResolveTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Alır, belirtilen TypeRef belirteci tarafından başvurulan türü için bilgileri yazın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tasarımını `IMetaDataImport` arabirimi öncelikle araçları tarafından kullanılmak üzere tasarlanmıştır ve tür bilgilerini (örneğin, geliştirme araçları) alma veya yönetme Hizmetleri bileşenleri (örneğin, çözüm/Etkinleştirme Hizmetleri) dağıtılabilir. Yöntemlere `IMetaDataImport` aşağıdaki görev kategorilere ayrılır:  
  
-   Meta veri kapsamı içindeki öğe koleksiyonları olan numaralandırma.  
  
-   Belirli bir özellikler kümesi içeren bir öğe bulma.  
  
-   Belirtilen öğenin özellikleri alınıyor.  
  
-   Get yöntemleri, meta veri öğesi özelliklerini tek değerli döndürmek için özel olarak tasarlanmıştır. Özelliği başka bir öğeye bir başvuru olduğunda, o öğe için bir belirteç döndürülür. Herhangi bir işaretçi giriş türü, belirli bir değer değil başlatması gerektiğini belirtmek için boş olabilir. Temelde koleksiyon nesnelerini (örneğin, bir sınıfın uyguladığı arabirimlerin koleksiyonunu) özellikleri elde etmek için numaralandırma yöntemlerini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
