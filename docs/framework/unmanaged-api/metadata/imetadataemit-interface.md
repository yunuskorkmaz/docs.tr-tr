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
ms.openlocfilehash: a2c2512abc28f0140fc261c5136c7e1255db96de
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009222"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit Arabirimi
Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve kaydetme yöntemleri sağlar. Meta veriler bellekte depolanabilir veya diske kaydedilebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyEditAndContinue Yöntemi](imetadataemit-applyeditandcontinue-method.md)|Geçerli derleme kapsamını belirtilen değişikliklerle güncelleştirir `pImport` .|  
|[DefineCustomAttribute Yöntemi](imetadataemit-definecustomattribute-method.md)|Belirtilen nesneye iliştirililmesi için belirtilen meta veri imzasına sahip özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.|  
|[DefineEvent Yöntemi](imetadataemit-defineevent-method.md)|Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.|  
|[DefineField Yöntemi](imetadataemit-definefield-method.md)|Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.|  
|[DefineImportMember Yöntemi](imetadataemit-defineimportmember-method.md)|Geçerli kapsam dışındaki bir modülde tanımlanmış bir türün üyesi için bir tanım oluşturur ve bu başvuru tanımı için bir belirteç alır.|  
|[DefineImportType Yöntemi](imetadataemit-defineimporttype-method.md)|Geçerli kapsamın dışındaki bir modülde tanımlanan bir türe başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteç alır.|  
|[DefineMemberRef Yöntemi](imetadataemit-definememberref-method.md)|Geçerli kapsam dışındaki bir modülün üyesine başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteç alır.|  
|[DefineMethod Yöntemi](imetadataemit-definemethod-method.md)|Belirtilen imzaya sahip bir yöntem için tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.|  
|[DefineMethodImpl Yöntemi](imetadataemit-definemethodimpl-method.md)|Bir arabirimden devralınan yöntemin uygulanması için bir tanım oluşturur ve bu yöntem uygulama tanımına bir belirteç döndürür.|  
|[DefineModuleRef Yöntemi](imetadataemit-definemoduleref-method.md)|Belirtilen ada sahip bir modül için meta veri imzası oluşturur.|  
|[DefineNestedType Yöntemi](imetadataemit-definenestedtype-method.md)|Bir tür tanımının meta veri imzasını oluşturur ve `mdTypeDef` Bu tür için bir belirteç döndürür, ek olarak, tanımlı türün tarafından başvurulan türün bir üyesi olduğunu belirten `tdEncloser` .|  
|[DefineParam Yöntemi](imetadataemit-defineparam-method.md)|Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaya sahip bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.|  
|[DefinePermissionSet Yöntemi](imetadataemit-definepermissionset-method.md)|Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.|  
|[DefinePinvokeMap Yöntemi](imetadataemit-definepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.|  
|[DefineProperty Yöntemi](imetadataemit-defineproperty-method.md)|Belirtilen ve Yöntem erişimcilerine sahip olan belirtilen tür için bir özellik tanımı oluşturur `get` `set` ve bu özellik tanımına bir belirteç alır.|  
|[DefineSecurityAttributeSet Yöntemi](imetadataemit-definesecurityattributeset-method.md)|Belirtilen belirteç tarafından başvurulan nesneye iliştirilecek bir güvenlik izinleri kümesi oluşturur.|  
|[DefineTypeDef Yöntemi](imetadataemit-definetypedef-method.md)|Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımına bir meta veri belirteci alır.|  
|[DefineTypeRefByName Yöntemi](imetadataemit-definetyperefbyname-method.md)|Geçerli kapsam dışında başka bir modülde tanımlanmış bir tür için meta veri belirteci alır.|  
|[DefineUserString Yöntemi](imetadataemit-defineuserstring-method.md)|Belirtilen sabit dize için bir meta veri belirteci alır.|  
|[DeleteClassLayout Yöntemi](imetadataemit-deleteclasslayout-method.md)|Belirtilen belirteç tarafından başvurulan tür için sınıf düzeni meta veri imzasını yok eder.|  
|[DeleteFieldMarshal Yöntemi](imetadataemit-deletefieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan nesne için PInvoke sıralama meta veri imzasını yok eder.|  
|[DeletePinvokeMap Yöntemi](imetadataemit-deletepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verilerini yok eder.|  
|[DeleteToken Yöntemi](imetadataemit-deletetoken-method.md)|Belirtilen belirteci geçerli meta veri kapsamından siler.|  
|[GetSaveSize Yöntemi](imetadataemit-getsavesize-method.md)|Geçerli kapsamdaki derlemenin tahmini ikili boyutunu alır.|  
|[GetTokenFromSig Yöntemi](imetadataemit-gettokenfromsig-method.md)|Belirtilen meta veri imzası için bir belirteç alır.|  
|[GetTokenFromTypeSpec Yöntemi](imetadataemit-gettokenfromtypespec-method.md)|Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.|  
|[Merge Metodu](imetadataemit-merge-method.md)|Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.|  
|[MergeEnd Yöntemi](imetadataemit-mergeend-method.md)|' A bir veya daha fazla çağrı tarafından belirtilen tüm meta veri kapsamlarını geçerli kapsama birleştirir `IMetaDataEmit::Merge` .|  
|[Save Yöntemi](imetadataemit-save-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen adresteki dosyaya kaydeder.|  
|[SaveToMemory Yöntemi](imetadataemit-savetomemory-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.|  
|[SaveToStream Yöntemi](imetadataemit-savetostream-method.md)|Geçerli kapsamdaki tüm meta verileri belirtilen öğesine kaydeder `IStream` .|  
|[SetClassLayout Yöntemi](imetadataemit-setclasslayout-method.md)|Önceki çağrısıyla tanımlanan bir türün sınıf düzeni imzasını ayarlar veya güncelleştirir `IMetaDataEmit::DefineTypeDef` .|  
|[SetCustomAttributeValue Yöntemi](imetadataemit-setcustomattributevalue-method.md)|Önceki bir çağrı tarafından tanımlanan özel bir özniteliğin değerini ayarlar veya güncelleştirir `IMetaDataEmit::DefineCustomAttribute` .|  
|[SetEventProps Yöntemi](imetadataemit-seteventprops-method.md)|Önceki çağrısıyla tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir `IMetaDataEmit::DefineEvent` .|  
|[SetFieldMarshal Yöntemi](imetadataemit-setfieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan alan, yöntem döndürme veya yöntem parametresi için PInvoke sıralama bilgilerini ayarlar.|  
|[SetFieldProps Yöntemi](imetadataemit-setfieldprops-method.md)|Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.|  
|[SetFieldRVA Yöntemi](imetadataemit-setfieldrva-method.md)|Belirtilen belirtecin başvurduğu alanın göreli sanal adresi için genel bir değişken değeri ayarlar.|  
|[SetHandler Yöntemi](imetadataemit-sethandler-method.md)|Belirtilen işaretçinin başvurduğu yöntemi, `IUnknown` belirteç yeniden eşlemeleri için bir bildirim geri çağırması olarak ayarlar.|  
|[SetMethodImplFlags Yöntemi](imetadataemit-setmethodimplflags-method.md)|Belirtilen belirteç tarafından başvurulan devralınmış Yöntem uygulamasının meta veri imzasını ayarlar veya güncelleştirir.|  
|[SetMethodProps Yöntemi](imetadataemit-setmethodprops-method.md)|Önceki bir çağrı tarafından tanımlanan bir yöntemin belirtilen göreli sanal adreste depolanan özelliği ayarlar veya güncelleştirir `IMetaDataEmit::DefineMethod` .|  
|[SetModuleProps Yöntemi](imetadataemit-setmoduleprops-method.md)|, Bir önceki çağrısıyla tanımlanan bir modüle başvuruları güncelleştirir `IMetaDataEmit::DefineModuleRef` .|  
|[SetParamProps Yöntemi](imetadataemit-setparamprops-method.md)|Önceki çağrısıyla tanımlanmış bir yöntem parametresinin özelliklerini ayarlar veya değiştirir `IMetaDataEmit::DefineParam` .|  
|[SetParent Yöntemi](imetadataemit-setparent-method.md)|Önceki bir çağrı tarafından tanımlanan belirtilen üyenin `IMetaDataEmit::DefineMemberRef` , bir önceki çağrısıyla tanımlanan, belirtilen türün bir üyesi olduğunu belirler `IMetaDataEmit::DefineTypeDef` .|  
|[SetPermissionSetProps Yöntemi](imetadataemit-setpermissionsetprops-method.md)|Önceki çağrısıyla tanımlanan bir izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir `IMetaDataEmit::DefinePermissionSet` .|  
|[SetPinvokeMap Yöntemi](imetadataemit-setpinvokemap-method.md)|Bir yöntemin PInvoke imzasının, bir önceki çağrısıyla tanımlandığı şekilde özelliklerini ayarlar veya değiştirir `IMetaDataEmit::DefinePinvokeMap` .|  
|[SetPropertyProps Yöntemi](imetadataemit-setpropertyprops-method.md)|Önceki çağrısıyla tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar `IMetaDataEmit::DefineProperty` .|  
|[SetRVA Yöntemi](imetadataemit-setrva-method.md)|Belirtilen metodun göreli sanal adresini ayarlar.|  
|[SetTypeDefProps Yöntemi](imetadataemit-settypedefprops-method.md)|Önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar `IMetaDataEmit::DefineTypeDef` .|  
|[TranslateSigWithScope Yöntemi](imetadataemit-translatesigwithscope-method.md)|Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
