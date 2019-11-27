---
title: IMetaDataEmit Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440891"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit Arabirimi
Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve kaydetme yöntemleri sağlar. Meta veriler bellekte depolanabilir veya diske kaydedilebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyEditAndContinue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Geçerli derleme kapsamını belirtilen `pImport`yapılan değişikliklerle güncelleştirir.|  
|[DefineCustomAttribute Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Belirtilen nesneye iliştirililmesi için belirtilen meta veri imzasına sahip özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.|  
|[DefineEvent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.|  
|[DefineField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.|  
|[DefineImportMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Geçerli kapsam dışındaki bir modülde tanımlanmış bir türün üyesi için bir tanım oluşturur ve bu başvuru tanımı için bir belirteç alır.|  
|[DefineImportType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Geçerli kapsamın dışındaki bir modülde tanımlanan bir türe başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteç alır.|  
|[DefineMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Geçerli kapsam dışındaki bir modülün üyesine başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteç alır.|  
|[DefineMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Belirtilen imzaya sahip bir yöntem için tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.|  
|[DefineMethodImpl Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Bir arabirimden devralınan yöntemin uygulanması için bir tanım oluşturur ve bu yöntem uygulama tanımına bir belirteç döndürür.|  
|[DefineModuleRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Belirtilen ada sahip bir modül için meta veri imzası oluşturur.|  
|[DefineNestedType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Bir tür tanımının meta veri imzasını oluşturur ve bu tür için bir `mdTypeDef` belirteci döndürür, ek olarak, tanımlı türün `tdEncloser`tarafından başvurulan türün bir üyesi olduğunu belirten.|  
|[DefineParam Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaya sahip bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.|  
|[DefinePermissionSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.|  
|[DefinePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.|  
|[DefineProperty Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Belirtilen `get` ve `set` yöntemi erişimcilerine sahip bir özellik tanımı oluşturur ve bu özellik tanımına bir belirteç alır.|  
|[DefineSecurityAttributeSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Belirtilen belirteç tarafından başvurulan nesneye iliştirilecek bir güvenlik izinleri kümesi oluşturur.|  
|[DefineTypeDef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımına bir meta veri belirteci alır.|  
|[DefineTypeRefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Geçerli kapsam dışında başka bir modülde tanımlanmış bir tür için meta veri belirteci alır.|  
|[DefineUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Belirtilen sabit dize için bir meta veri belirteci alır.|  
|[DeleteClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Belirtilen belirteç tarafından başvurulan tür için sınıf düzeni meta veri imzasını yok eder.|  
|[DeleteFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan nesne için PInvoke sıralama meta veri imzasını yok eder.|  
|[DeletePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verilerini yok eder.|  
|[DeleteToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Belirtilen belirteci geçerli meta veri kapsamından siler.|  
|[GetSaveSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Geçerli kapsamdaki derlemenin tahmini ikili boyutunu alır.|  
|[GetTokenFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Belirtilen meta veri imzası için bir belirteç alır.|  
|[GetTokenFromTypeSpec Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.|  
|[Merge Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.|  
|[MergeEnd Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|`IMetaDataEmit::Merge`için bir veya daha fazla çağrı tarafından belirtilen tüm meta veri kapsamlarını geçerli kapsama birleştirir.|  
|[Save Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen adresteki dosyaya kaydeder.|  
|[SaveToMemory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.|  
|[SaveToStream Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen `IStream`kaydeder.|  
|[SetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|`IMetaDataEmit::DefineTypeDef`önceki çağrısıyla tanımlanan bir türün sınıf düzeni imzasını ayarlar veya güncelleştirir.|  
|[SetCustomAttributeValue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|`IMetaDataEmit::DefineCustomAttribute`önceki bir çağrı tarafından tanımlanan özel bir özniteliğin değerini ayarlar veya güncelleştirir.|  
|[SetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|`IMetaDataEmit::DefineEvent`önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.|  
|[SetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan alan, yöntem döndürme veya yöntem parametresi için PInvoke sıralama bilgilerini ayarlar.|  
|[SetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.|  
|[SetFieldRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Belirtilen belirtecin başvurduğu alanın göreli sanal adresi için genel bir değişken değeri ayarlar.|  
|[SetHandler Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Belirtilen `IUnknown` işaretçisinin başvurduğu yöntemi, belirteç yeniden eşlemeleri için bir bildirim geri çağırması olarak ayarlar.|  
|[SetMethodImplFlags Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Belirtilen belirteç tarafından başvurulan devralınmış Yöntem uygulamasının meta veri imzasını ayarlar veya güncelleştirir.|  
|[SetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|`IMetaDataEmit::DefineMethod`için önceki bir çağrı tarafından tanımlanan yöntemin belirtilen göreli sanal adreste depolanan özelliği ayarlar veya güncelleştirir.|  
|[SetModuleProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|`IMetaDataEmit::DefineModuleRef`için önceki bir çağrı tarafından tanımlanan bir modüle başvuruları güncelleştirir.|  
|[SetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|`IMetaDataEmit::DefineParam`için önceki bir çağrı tarafından tanımlanan bir yöntem parametresinin özelliklerini ayarlar veya değiştirir.|  
|[SetParent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|`IMetaDataEmit::DefineMemberRef`önceki bir çağrı tarafından tanımlanan belirtilen üyenin, `IMetaDataEmit::DefineTypeDef`bir önceki çağrısıyla tanımlanan bir üyenin belirtilen bir üyesi olduğunu belirler.|  
|[SetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|`IMetaDataEmit::DefinePermissionSet`için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.|  
|[SetPinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Bir yöntemin PInvoke imzasının özelliklerini, `IMetaDataEmit::DefinePinvokeMap`önceki bir çağrısıyla tanımlanan şekilde ayarlar veya değiştirir.|  
|[SetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Önceki bir `IMetaDataEmit::DefineProperty`çağrısı tarafından tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.|  
|[SetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Belirtilen metodun göreli sanal adresini ayarlar.|  
|[SetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|`IMetaDataEmit::DefineTypeDef`önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.|  
|[TranslateSigWithScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
