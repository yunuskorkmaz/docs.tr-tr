---
title: IMetaDataImport Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport
helpviewer_keywords: IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1067582b506d60092bef9639dc4a96ba41306437
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport-interface"></a>IMetaDataImport Arabirimi
İçeri aktarma ve taşınabilir yürütülebilir (PE) dosyasından ya da bir tür kitaplığı veya tek başına, çalışma zamanı meta veri ikili gibi diğer kaynak var olan meta veri düzenleme için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Belirtilen tanıtıcı ile Numaralandırıcı kapatır.|  
|[CountEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Öğe sayısını belirtilen tanıtıcı ile Numaralandırıcı alır.|  
|[EnumCustomAttributes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Belirtilen tür veya üye ile ilişkili özel öznitelik tanımı belirteçleri listesini numaralandırır.|  
|[EnumEvents Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Belirtilen TypeDef belirteci için olay tanımı belirteçleri numaralandırır.|  
|[EnumFields Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Belirtilen TypeDef belirteç tarafından başvurulan türü için fieldDef simgesi belirteçleri numaralandırır.|  
|[EnumFieldsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Belirtilen ada sahip belirtilen türde fieldDef simgesi belirteçleri numaralandırır.|  
|[EnumInterfaceImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Arabirim uygulamaları temsil eden MethodDef belirteçleri numaralandırır.|  
|[EnumMemberRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Belirtilen türün üyeleri temsil eden MemberRef belirteçleri numaralandırır.|  
|[EnumMembers Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Belirtilen türün üyeleri temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumMembersWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Belirtilen ada sahip belirtilen türün üyeleri temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumMethodImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçleri numaralandırır.|  
|[EnumMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçleri numaralandırır.|  
|[EnumMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Özellikleri ve belirtilen yöntem ilgili özellik değişikliği olayları numaralandırır.|  
|[EnumMethodsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Belirtilen ada sahip ve belirtilen TypeDef belirteç tarafından başvurulan türü tarafından tanımlanan yöntemlerini numaralandırır.|  
|[EnumModuleRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|İçeri aktarılan modülleri temsil ModuleRef belirteçleri numaralandırır.|  
|[EnumParams Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Belirtilen MethodDef belirteç tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.|  
|[EnumPermissionSets Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Belirtilen meta veri kapsamı içindeki nesneler için izinleri numaralandırır.|  
|[EnumProperties Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Belirtilen TypeDef belirteç tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.|  
|[EnumSignatures Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Geçerli kapsamdaki tek başına imzaları temsil eden imza belirteçleri numaralandırır.|  
|[EnumTypeDefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Geçerli kapsamdaki tüm türleri temsil eden TypeDef belirteçleri numaralandırır.|  
|[EnumTypeRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Geçerli meta veri kapsamda tanımlı TypeRef belirteçleri numaralandırır.|  
|[EnumTypeSpecs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Geçerli meta veri kapsamda tanımlı TypeSpec'te belirteçleri numaralandırır.|  
|[EnumUnresolvedMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Geçerli meta veri kapsamında çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.|  
|[EnumUserStrings Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Geçerli meta veri kapsamı sabit kodlanmış dizelerde temsil eden dize belirteçleri numaralandırır.|  
|[FindField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|FieldDef simgesi, belirtilen tür üyesi olduğunu ve belirtilen ad ve meta veri imza için alan belirteci alır.|  
|[FindMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Bir işaretçi MemberDef için belirtilen ad ve meta veri imza belirtilen türle tarafından tanımlanan üyesi için belirteç alır.|  
|[FindMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Bir işaretçi MemberRef için belirtilen ad ve meta veri imza belirtilen türle tarafından tanımlanan üyesi için belirteç alır.|  
|[FindMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Bir işaretçi MethodDef için belirtilen ad ve meta veri imza belirtilen türle tarafından tanımlanan yöntemi belirteci alır.|  
|[FindTypeDefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Bir işaretçi TypeDef meta verileri için türü için belirtilen adla belirteci alır.|  
|[FindTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Belirtilen ada sahip belirtilen arama kapsamdaki türüne başvuran TypeRef meta veri simgesi için bir işaretçi alır.|  
|[GetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Belirtilen TypeDef tarafından başvurulan sınıfı için düzen bilgilerini belirteci alır.|  
|[GetCustomAttributeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Adı verilen özel öznitelik değerini alır.|  
|[GetCustomAttributeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Meta veri simgesi verilen özel öznitelik değerini alır.|  
|[GetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Belirtilen olay belirtecin tarafından temsil edilen olayı için (ve Temsilciler, yöntemleri ve tüm bayraklar ve ilişkili diğer veri kaldırmak Ekle bildiri türü dahil) meta veri bilgilerini alır.|  
|[GetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Belirtilen alan meta veri simgesi tarafından temsil edilen alan yerel, yönetilmeyen türü için bir işaretçi alır.|  
|[GetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Belirtilen fieldDef simgesi tarafından başvurulan alanıyla ilişkili meta verileri belirtecini alır.|  
|[GetInterfaceImplProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Bir işaretçi ve bu yöntem bildirir arabirimi belirtilen yöntem uygulayan türü için meta veri belirteçlerini alır.|  
|[GetMemberProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Belirtilen meta veri simgesi tarafından başvurulan tür üye meta veri bilgilerini (adı, ikili imza ve göreli sanal adres dahil) alır.|  
|[GetMemberRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.|  
|[GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Belirtilen MethodDef tarafından başvurulan yöntemi ile ilişkili meta veri belirtecini alır.|  
|[GetMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Bir işaretçi belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan ve belirtilen EventProp tarafından başvurulan olay arasındaki ilişkiye belirtecini alır.|  
|[GetModuleFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Bir işaretçi meta veriler için geçerli meta veri kapsamda başvurulan modül için belirteç alır.|  
|[GetModuleRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Belirtilen meta veri simgesi tarafından başvurulan modül adını alır.|  
|[GetNameFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Belirtilen meta veri simgesi tarafından başvurulan nesne UTF-8 adını alır.|  
|[GetNativeCallConvFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Yerel bir belirtilen imza işaretçiyi tarafından temsil edilen yöntemi çağırma alır.|  
|[GetNestedClassProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|TypeDef belirtilen iç içe geçmiş tür kapsayan üst türü için belirteç alır.|  
|[GetParamForMethodIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Parametresinde belirtilen sıralı konumunu sırada belirtilen MethodDef belirteç tarafından temsil edilen yöntemi için Yöntem parametreleri temsil eden belirteci için bir işaretçi alır.|  
|[GetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Meta veri değerleri belirtilen ParamDef tarafından başvurulan parametresi için belirteç alır.|  
|[GetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Belirtilen izin belirteç tarafından temsil edilen System.Security.PermissionSet ilişkili meta verileri alır.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Bir ModuleRef PInvoke çağrısı hedef derlemenin temsil etmek için belirteç alır.|  
|[GetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Belirtilen belirteç tarafından temsil edilen özelliği ilişkili meta verileri alır.|  
|[GetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Belirtilen belirteç tarafından temsil edilen kod nesnesinin göreli sanal adres uzaklığını alır.|  
|[GetScopeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Ad ve isteğe bağlı olarak derleme veya modülü sürüm tanıtıcısı geçerli meta veri kapsamdaki alır.|  
|[GetSigFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Belirtilen belirteçle ilişkili ikili meta verileri imza alır.|  
|[GetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Belirtilen TypeDef belirteç tarafından temsil edilen türü için meta veri bilgileri döndürür.|  
|[GetTypeRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Belirtilen TypeRef tarafından başvurulan türüyle ilişkili meta veri belirtecini alır.|  
|[GetTypeSpecFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Belirtilen belirteç tarafından temsil edilen tür belirtimi ikili meta verileri imzasını alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Belirtilen meta veri simgesi tarafından temsil edilen sabit değerli bir dize alır.|  
|[IsGlobal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Alan, yöntemi veya türü tarafından belirtilen meta veri simgesi gösterilir genel kapsama sahip olup olmadığını belirten bir değer alır.|  
|[IsValidToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Belirtilen belirteç kodu nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.|  
|[ResetEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Belirtilen Numaralandırıcı belirtilen konuma sıfırlar.|  
|[ResolveTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Alır belirtilen TypeRef belirteç tarafından başvurulan türünün bilgilerini girin.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tasarımını `IMetaDataImport` arabirimi öncelikle araçları tarafından kullanılmak üzere tasarlanmıştır ve türü bilgileri (örneğin, geliştirme araçları) alma veya yönetme hizmetler dağıtılabilir bileşenleri (örneğin, çözümleme/Etkinleştirme Hizmetleri). Yöntemlere `IMetaDataImport` aşağıdaki görev kategorilere ayrılır:  
  
-   Meta veri kapsamında öğelerinin koleksiyonları numaralandırma.  
  
-   Belirli bir özellikler kümesi içeren bir öğe bulma.  
  
-   Belirtilen öğenin özelliklerini alınıyor.  
  
-   Get yöntemleri bir meta veri öğesi tek değerli özelliklerini döndürmek için özel olarak tasarlanmıştır. Özelliği bir başvuru başka bir öğe olduğunda, o öğe için bir belirteç döndürdü. Herhangi bir işaretçi giriş türü belirli değeri değil istenen olduğunu belirtmek için NULL olabilir. Temelde koleksiyon nesnelerine (örneğin, bir sınıf uygular arabirimleri toplama) özellikleri almak için numaralandırma yöntemlerini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
