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
ms.openlocfilehash: 02d1ea1ef12fa158ce7ec94aeca4356ac54d4e5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503490"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport Arabirimi
Taşınabilir çalıştırılabilir (PE) dosyadan veya bir tür kitaplığı ya da tek başına, çalışma zamanı meta verileri ikilisi gibi başka bir kaynaktan varolan meta verileri içeri ve düzenleme için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[CloseEnum Yöntemi](imetadataimport-closeenum-method.md)|Numaralandırıcısı belirtilen tanıtıcıyla kapatır.|  
|[CountEnum Yöntemi](imetadataimport-countenum-method.md)|Numaralandırıcı içindeki öğe sayısını Belirtilen tanıtıcıya göre alır.|  
|[EnumCustomAttributes Yöntemi](imetadataimport-enumcustomattributes-method.md)|Belirtilen tür veya üyeyle ilişkili özel öznitelik tanım belirteçlerinin listesini sıralar.|  
|[EnumEvents Yöntemi](imetadataimport-enumevents-method.md)|Belirtilen TypeDef belirtecinin olay tanımı belirteçlerini numaralandırır.|  
|[EnumFields Yöntemi](imetadataimport-enumfields-method.md)|Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.|  
|[EnumFieldsWithName Yöntemi](imetadataimport-enumfieldswithname-method.md)|Belirtilen ada sahip belirtilen türdeki FieldDef belirteçlerini numaralandırır.|  
|[EnumInterfaceImpls Yöntemi](imetadataimport-enuminterfaceimpls-method.md)|Arabirim uygulamalarını temsil eden MethodDef belirteçlerini numaralandırır.|  
|[EnumMemberRefs Yöntemi](imetadataimport-enummemberrefs-method.md)|Belirtilen türdeki üyeleri temsil eden MemberRef belirteçlerini numaralandırır.|  
|[EnumMembers Yöntemi](imetadataimport-enummembers-method.md)|Belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumMembersWithName Yöntemi](imetadataimport-enummemberswithname-method.md)|Belirtilen ada sahip belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumMethodImpls Yöntemi](imetadataimport-enummethodimpls-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini numaralandırır.|  
|[EnumMethods Yöntemi](imetadataimport-enummethods-method.md)|Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçlerini numaralandırır.|  
|[EnumMethodSemantics Yöntemi](imetadataimport-enummethodsemantics-method.md)|Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.|  
|[EnumMethodsWithName Yöntemi](imetadataimport-enummethodswithname-method.md)|Belirtilen ada sahip olan ve belirtilen TypeDef belirtecinin başvurduğu tür tarafından tanımlanan yöntemleri numaralandırır.|  
|[EnumModuleRefs Yöntemi](imetadataimport-enummodulerefs-method.md)|İçeri aktarılan modülleri temsil eden ModuleRef belirteçlerini numaralandırır.|  
|[EnumParams Yöntemi](imetadataimport-enumparams-method.md)|Belirtilen MethodDef belirtecinin başvurduğu metodun parametrelerini temsil eden ParamDef belirteçlerini numaralandırır.|  
|[EnumPermissionSets Yöntemi](imetadataimport-enumpermissionsets-method.md)|Belirtilen meta veri kapsamındaki nesneler için izinleri numaralandırır.|  
|[EnumProperties Yöntemi](imetadataimport-enumproperties-method.md)|Belirtilen TypeDef belirtecinin başvurduğu türün özelliklerini temsil eden PropertyDef belirteçlerini numaralandırır.|  
|[EnumSignatures Yöntemi](imetadataimport-enumsignatures-method.md)|Geçerli kapsamdaki tek başına imzaları temsil eden Imza belirteçlerini numaralandırır.|  
|[EnumTypeDefs Yöntemi](imetadataimport-enumtypedefs-method.md)|Geçerli kapsam içindeki tüm türleri temsil eden TypeDef belirteçlerini numaralandırır.|  
|[EnumTypeRefs Yöntemi](imetadataimport-enumtyperefs-method.md)|Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini numaralandırır.|  
|[EnumTypeSpecs Yöntemi](imetadataimport-enumtypespecs-method.md)|Geçerli meta veri kapsamında tanımlanan TypeSpec belirteçlerini numaralandırır.|  
|[EnumUnresolvedMethods Yöntemi](imetadataimport-enumunresolvedmethods-method.md)|Geçerli meta veri kapsamındaki çözümlenmemiş yöntemleri temsil eden MemberDef belirteçlerini numaralandırır.|  
|[EnumUserStrings Yöntemi](imetadataimport-enumuserstrings-method.md)|Geçerli meta veri kapsamındaki sabit kodlanmış dizeleri temsil eden dize belirteçlerini numaralandırır.|  
|[FindField Yöntemi](imetadataimport-findfield-method.md)|Belirtilen türe üye olan alan için FieldDef belirtecini alır ve belirtilen ad ve meta veri imzasına sahiptir.|  
|[FindMember Yöntemi](imetadataimport-findmember-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan üyenin MemberDef belirtecine yönelik bir işaretçi alır.|  
|[FindMemberRef Yöntemi](imetadataimport-findmemberref-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan üyenin MemberRef belirtecine yönelik bir işaretçi alır.|  
|[FindMethod Yöntemi](imetadataimport-findmethod-method.md)|Belirtilen ad ve meta veri imzasıyla belirtilen tür tarafından tanımlanan metodun MethodDef belirtecine yönelik bir işaretçi alır.|  
|[FindTypeDefByName Yöntemi](imetadataimport-findtypedefbyname-method.md)|Belirtilen ada sahip tür için TypeDef meta veri belirtecine yönelik bir işaretçi alır.|  
|[FindTypeRef Yöntemi](imetadataimport-findtyperef-method.md)|Belirtilen arama kapsamındaki türe belirtilen ada sahip olan TypeRef meta veri belirtecine yönelik bir işaretçi alır.|  
|[GetClassLayout Yöntemi](imetadataimport-getclasslayout-method.md)|Belirtilen TypeDef belirtecinin başvurduğu sınıfa ait düzen bilgisini alır.|  
|[GetCustomAttributeByName Yöntemi](imetadataimport-getcustomattributebyname-method.md)|Özel özniteliğin, adı verilen değerini alır.|  
|[GetCustomAttributeProps Metodu](imetadataimport-getcustomattributeprops-method.md)|Meta veri belirteci verilen özel özniteliğin değerini alır.|  
|[GetEventProps Yöntemi](imetadataimport-geteventprops-method.md)|Belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini (bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler dahil) alır.|  
|[GetFieldMarshal Yöntemi](imetadataimport-getfieldmarshal-method.md)|Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.|  
|[GetFieldProps Yöntemi](imetadataimport-getfieldprops-method.md)|Belirtilen FieldDef belirtecinin başvurduğu alanla ilişkili meta verileri alır.|  
|[GetInterfaceImplProps Metodu](imetadataimport-getinterfaceimplprops-method.md)|Belirtilen yöntemi uygulayan tür için ve bu yöntemi bildiren arabirim için meta veri belirteçlerine bir işaretçi alır.|  
|[GetMemberProps Yöntemi](imetadataimport-getmemberprops-method.md)|Belirtilen meta veri belirtecinin başvurduğu tür üyesinin meta veri bilgilerini (ad, ikili imza ve göreli sanal adres dahil) alır.|  
|[GetMemberRefProps Yöntemi](imetadataimport-getmemberrefprops-method.md)|Belirtilen belirteç tarafından başvurulan üyeyle ilişkili meta verileri alır.|  
|[GetMethodProps Yöntemi](imetadataimport-getmethodprops-method.md)|Belirtilen MethodDef belirtecinin başvurduğu metotla ilişkili meta verileri alır.|  
|[GetMethodSemantics Metodu](imetadataimport-getmethodsemantics-method.md)|Belirtilen MethodDef belirtecinin başvurduğu yöntem ile eşleştirilen özellik ve belirtilen EventProp belirteci tarafından başvurulan olay arasındaki ilişkiye yönelik bir işaretçi alır.|  
|[GetModuleFromScope Yöntemi](imetadataimport-getmodulefromscope-method.md)|Geçerli meta veri kapsamında başvurulan modülün meta veri belirtecine yönelik bir işaretçi alır.|  
|[GetModuleRefProps Yöntemi](imetadataimport-getmodulerefprops-method.md)|Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.|  
|[GetNameFromToken Yöntemi](imetadataimport-getnamefromtoken-method.md)|Belirtilen meta veri belirtecinin başvurduğu nesnenin UTF-8 adını alır.|  
|[GetNativeCallConvFromSig Yöntemi](imetadataimport-getnativecallconvfromsig-method.md)|Belirtilen imza işaretçisi tarafından temsil edilen yöntem için yerel çağırma kuralını alır.|  
|[GetNestedClassProps Metodu](imetadataimport-getnestedclassprops-method.md)|Belirtilen iç içe türün kapsayan üst türü için TypeDef belirtecini alır.|  
|[GetParamForMethodIndex Yöntemi](imetadataimport-getparamformethodindex-method.md)|Belirtilen MethodDef belirteci tarafından temsil edilen yöntem için yöntem parametrelerinin dizisinde belirtilen sıra konumundaki parametreyi temsil eden belirtece yönelik bir işaretçi alır.|  
|[GetParamProps Yöntemi](imetadataimport-getparamprops-method.md)|Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.|  
|[GetPermissionSetProps Metodu](imetadataimport-getpermissionsetprops-method.md)|Belirtilen Izin belirteciyle temsil edilen System. Security. PermissionSet ile ilişkili meta verileri alır.|  
|[GetPinvokeMap](imetadataimport-getpinvokemap-method.md)|Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.|  
|[GetPropertyProps Yöntemi](imetadataimport-getpropertyprops-method.md)|Belirtilen belirteçle temsil edilen özellik ile ilişkili meta verileri alır.|  
|[GetRVA Yöntemi](imetadataimport-getrva-method.md)|Belirtilen belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresinin konumunu alır.|  
|[GetScopeProps Metodu](imetadataimport-getscopeprops-method.md)|Geçerli meta veri kapsamındaki derleme ya da modülün adını ve isteğe bağlı olarak sürüm tanımlayıcısını alır.|  
|[GetSigFromToken Yöntemi](imetadataimport-getsigfromtoken-method.md)|Belirtilen belirteçle ilişkili ikili meta veri imzasını alır.|  
|[GetTypeDefProps Yöntemi](imetadataimport-gettypedefprops-method.md)|Belirtilen TypeDef belirteci tarafından temsil edilen türe ait meta veri bilgilerini döndürür.|  
|[GetTypeRefProps Yöntemi](imetadataimport-gettyperefprops-method.md)|Belirtilen TypeRef belirteci tarafından başvurulan türle ilişkili meta verileri alır.|  
|[GetTypeSpecFromToken Yöntemi](imetadataimport-gettypespecfromtoken-method.md)|Belirtilen belirteçle temsil edilen tür belirtiminin ikili meta veri imzasını alır.|  
|[GetUserString Yöntemi](imetadataimport-getuserstring-method.md)|Belirtilen meta veri belirteci tarafından temsil edilen sabit dizeyi alır.|  
|[IsGlobal Yöntemi](imetadataimport-isglobal-method.md)|Belirtilen meta veri belirteci tarafından temsil edilen alanın, yöntemin veya türün genel kapsama sahip olup olmadığını gösteren bir değer alır.|  
|[IsValidToken Yöntemi](imetadataimport-isvalidtoken-method.md)|Belirtilen belirtecin bir kod nesnesine geçerli bir başvuru içerip içermediğini gösteren bir değer alır.|  
|[ResetEnum Yöntemi](imetadataimport-resetenum-method.md)|Belirtilen numaralandırıcısı belirtilen konuma sıfırlar.|  
|[ResolveTypeRef Yöntemi](imetadataimport-resolvetyperef-method.md)|Belirtilen TypeRef belirteci tarafından başvurulan türe ilişkin tür bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IMetaDataImport`Arabirimin tasarımı öncelikle tür bilgilerini (örneğin, geliştirme araçları) içeri aktaran veya dağıtılan bileşenleri (örneğin, çözümleme/etkinleştirme Hizmetleri) alacak araçlar ve hizmetler tarafından kullanılmak üzere tasarlanmıştır. İçindeki Yöntemler `IMetaDataImport` Aşağıdaki görev kategorilerine girer:  
  
- Meta veri kapsamındaki öğe koleksiyonları numaralandırılıyor.  
  
- Belirli bir özellik kümesine sahip bir öğe bulma.  
  
- Belirtilen öğenin özellikleri alınıyor.  
  
- Get yöntemleri, bir meta veri öğesinin tek değerli özelliklerini döndürmek için özel olarak tasarlanmıştır. Özelliği başka bir öğeye başvuru olduğunda, bu öğe için bir belirteç döndürülür. Herhangi bir işaretçi giriş türü, belirli bir değerin istenmediğini göstermek için NULL olabilir. Temel olarak koleksiyon nesneleri olan özellikleri almak için (örneğin, bir sınıfın uyguladığı arabirimlerin koleksiyonu), numaralandırma yöntemlerini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
