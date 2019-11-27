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
ms.openlocfilehash: 2d45a369def193b9c8d8f9a3aa954ede600a87dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434728"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport Arabirimi
Taşınabilir çalıştırılabilir (PE) dosyadan veya bir tür kitaplığı ya da tek başına, çalışma zamanı meta verileri ikilisi gibi başka bir kaynaktan varolan meta verileri içeri ve düzenleme için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Numaralandırıcısı belirtilen tanıtıcıyla kapatır.|  
|[CountEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Numaralandırıcı içindeki öğe sayısını Belirtilen tanıtıcıya göre alır.|  
|[EnumCustomAttributes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Belirtilen tür veya üyeyle ilişkili özel öznitelik tanım belirteçlerinin listesini sıralar.|  
|[EnumEvents Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Belirtilen TypeDef belirtecinin olay tanımı belirteçlerini numaralandırır.|  
|[EnumFields Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.|  
|[EnumFieldsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Belirtilen ada sahip belirtilen türdeki FieldDef belirteçlerini numaralandırır.|  
|[EnumInterfaceImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Arabirim uygulamalarını temsil eden MethodDef belirteçlerini numaralandırır.|  
|[EnumMemberRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Belirtilen türdeki üyeleri temsil eden MemberRef belirteçlerini numaralandırır.|  
|[EnumMembers Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumMembersWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Belirtilen ada sahip belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumMethodImpls Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini numaralandırır.|  
|[EnumMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçlerini numaralandırır.|  
|[EnumMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.|  
|[EnumMethodsWithName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Belirtilen ada sahip olan ve belirtilen TypeDef belirtecinin başvurduğu tür tarafından tanımlanan yöntemleri numaralandırır.|  
|[EnumModuleRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|İçeri aktarılan modülleri temsil eden ModuleRef belirteçlerini numaralandırır.|  
|[EnumParams Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Belirtilen MethodDef belirtecinin başvurduğu metodun parametrelerini temsil eden ParamDef belirteçlerini numaralandırır.|  
|[EnumPermissionSets Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Belirtilen meta veri kapsamındaki nesneler için izinleri numaralandırır.|  
|[EnumProperties Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Belirtilen TypeDef belirtecinin başvurduğu türün özelliklerini temsil eden PropertyDef belirteçlerini numaralandırır.|  
|[EnumSignatures Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Geçerli kapsamdaki tek başına imzaları temsil eden Imza belirteçlerini numaralandırır.|  
|[EnumTypeDefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Geçerli kapsam içindeki tüm türleri temsil eden TypeDef belirteçlerini numaralandırır.|  
|[EnumTypeRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini numaralandırır.|  
|[EnumTypeSpecs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Geçerli meta veri kapsamında tanımlanan TypeSpec belirteçlerini numaralandırır.|  
|[EnumUnresolvedMethods Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Geçerli meta veri kapsamındaki çözümlenmemiş yöntemleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumUserStrings Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Geçerli meta veri kapsamındaki sabit kodlanmış dizeleri temsil eden dize belirteçlerini numaralandırır.|  
|[FindField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Belirtilen türe üye olan alan için FieldDef belirtecini alır ve belirtilen ad ve meta veri imzasına sahiptir.|  
|[FindMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan üyenin MemberDef belirtecine yönelik bir işaretçi alır.|  
|[FindMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan üyenin MemberRef belirtecine yönelik bir işaretçi alır.|  
|[FindMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan metodun MethodDef belirtecine yönelik bir işaretçi alır.|  
|[FindTypeDefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Belirtilen ada sahip tür için TypeDef meta veri belirtecine yönelik bir işaretçi alır.|  
|[FindTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Belirtilen arama kapsamındaki türe belirtilen ada sahip olan TypeRef meta veri belirtecine yönelik bir işaretçi alır.|  
|[GetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Belirtilen TypeDef belirtecinin başvurduğu sınıfa ait düzen bilgisini alır.|  
|[GetCustomAttributeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Özel özniteliğin, adı verilen değerini alır.|  
|[GetCustomAttributeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Meta veri belirteci verilen özel özniteliğin değerini alır.|  
|[GetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini (bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler dahil) alır.|  
|[GetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.|  
|[GetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Belirtilen FieldDef belirtecinin başvurduğu alanla ilişkili meta verileri alır.|  
|[GetInterfaceImplProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Belirtilen yöntemi uygulayan tür için ve bu yöntemi bildiren arabirim için meta veri belirteçlerine bir işaretçi alır.|  
|[GetMemberProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Belirtilen meta veri belirtecinin başvurduğu tür üyesinin meta veri bilgilerini (ad, ikili imza ve göreli sanal adres dahil) alır.|  
|[GetMemberRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Belirtilen belirteç tarafından başvurulan üyeyle ilişkili meta verileri alır.|  
|[GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Belirtilen MethodDef belirtecinin başvurduğu metotla ilişkili meta verileri alır.|  
|[GetMethodSemantics Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Belirtilen MethodDef belirtecinin başvurduğu yöntem ile eşleştirilen özellik ve belirtilen EventProp belirteci tarafından başvurulan olay arasındaki ilişkiye yönelik bir işaretçi alır.|  
|[GetModuleFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Geçerli meta veri kapsamında başvurulan modülün meta veri belirtecine yönelik bir işaretçi alır.|  
|[GetModuleRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.|  
|[GetNameFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Belirtilen meta veri belirtecinin başvurduğu nesnenin UTF-8 adını alır.|  
|[GetNativeCallConvFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Belirtilen imza işaretçisi tarafından temsil edilen yöntem için yerel çağırma kuralını alır.|  
|[GetNestedClassProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Belirtilen iç içe türün kapsayan üst türü için TypeDef belirtecini alır.|  
|[GetParamForMethodIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Belirtilen MethodDef belirteci tarafından temsil edilen yöntem için yöntem parametrelerinin dizisinde belirtilen sıra konumundaki parametreyi temsil eden belirtece yönelik bir işaretçi alır.|  
|[GetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.|  
|[GetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Belirtilen Izin belirteciyle temsil edilen System. Security. PermissionSet ile ilişkili meta verileri alır.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.|  
|[GetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Belirtilen belirteçle temsil edilen özellik ile ilişkili meta verileri alır.|  
|[GetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Belirtilen belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresinin konumunu alır.|  
|[GetScopeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Geçerli meta veri kapsamındaki derleme ya da modülün adını ve isteğe bağlı olarak sürüm tanımlayıcısını alır.|  
|[GetSigFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Belirtilen belirteçle ilişkili ikili meta veri imzasını alır.|  
|[GetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Belirtilen TypeDef belirteci tarafından temsil edilen türe ait meta veri bilgilerini döndürür.|  
|[GetTypeRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Belirtilen TypeRef belirteci tarafından başvurulan türle ilişkili meta verileri alır.|  
|[GetTypeSpecFromToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Belirtilen belirteçle temsil edilen tür belirtiminin ikili meta veri imzasını alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Belirtilen meta veri belirteci tarafından temsil edilen sabit dizeyi alır.|  
|[IsGlobal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Belirtilen meta veri belirteci tarafından temsil edilen alanın, yöntemin veya türün genel kapsama sahip olup olmadığını gösteren bir değer alır.|  
|[IsValidToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Belirtilen belirtecin bir kod nesnesine geçerli bir başvuru içerip içermediğini gösteren bir değer alır.|  
|[ResetEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Belirtilen numaralandırıcısı belirtilen konuma sıfırlar.|  
|[ResolveTypeRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Belirtilen TypeRef belirteci tarafından başvurulan türe ilişkin tür bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IMetaDataImport` arabiriminin tasarımı, öncelikle tür bilgilerini (örneğin, geliştirme araçları) içeri aktaran veya dağıtılan bileşenleri (örneğin, çözümleme/etkinleştirme Hizmetleri) alacak olan araç ve hizmetler tarafından kullanılmak üzere tasarlanmıştır. `IMetaDataImport` yöntemleri aşağıdaki görev kategorilerine girer:  
  
- Meta veri kapsamındaki öğe koleksiyonları numaralandırılıyor.  
  
- Belirli bir özellik kümesine sahip bir öğe bulma.  
  
- Belirtilen öğenin özellikleri alınıyor.  
  
- Get yöntemleri, bir meta veri öğesinin tek değerli özelliklerini döndürmek için özel olarak tasarlanmıştır. Özelliği başka bir öğeye başvuru olduğunda, bu öğe için bir belirteç döndürülür. Herhangi bir işaretçi giriş türü, belirli bir değerin istenmediğini göstermek için NULL olabilir. Temel olarak koleksiyon nesneleri olan özellikleri almak için (örneğin, bir sınıfın uyguladığı arabirimlerin koleksiyonu), numaralandırma yöntemlerini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
