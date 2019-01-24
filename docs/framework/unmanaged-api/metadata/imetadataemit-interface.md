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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f28facc8acb430de4aa255208a62c5fc61f12cd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727670"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit Arabirimi
Oluşturabilir, değiştirebilir ve şu anda tanımlanmış kapsamda derleme hakkındaki meta verileri kaydetmek için yöntemler sağlar. Meta veriler, bellekte veya diske kaydedilmiş.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyEditAndContinue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Geçerli derleme kapsamı içinde belirtilen yapılan değişiklikleri güncelleştirir `pImport`.|  
|[DefineCustomAttribute Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Belirtilen nesneyi, eklenecek belirtilen meta veri imzası ile özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.|  
|[DefineEvent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Belirtilen meta verileri imza ile bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.|  
|[DefineField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Belirtilen meta verileri imza ile bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.|  
|[DefineImportMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Geçerli kapsamı dışında bir modülde tanımlandı ve bu başvuru tanımı için bir belirteç alır bir tür üyesi için bir tanım oluşturur.|  
|[DefineImportType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Geçerli kapsamı dışında bir modülde tanımlandı ve bu başvuru tanımına bir belirteç alır bir tür başvuru için bir tanım oluşturur.|  
|[DefineMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Geçerli kapsam dışında bir modülün bir üyesine bir başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteç alır.|  
|[DefineMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Belirtilen imzayla bir yöntem için bir tanım oluşturur ve bu yöntem tanımını bir belirteç döndürür.|  
|[DefineMethodImpl Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Bir arabirimden devralınan bir yöntemi uygulaması için bir tanım oluşturur ve bu yöntem uygulaması tanımı için bir belirteç döndürür.|  
|[DefineModuleRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Belirtilen ada sahip bir modül meta veri imzası oluşturur.|  
|[DefineNestedType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Meta veri imzası bir tür tanımı oluşturur ve döndürür bir `mdTypeDef` türüne ek olarak tanımlanan bir tür tarafından başvurulan tür üyesi olduğunu belirten, belirteç `tdEncloser`.|  
|[DefineParam Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzaya sahip bir parametre tanımında oluşturur ve bu parametre tanımı için bir belirteç alır.|  
|[DefinePermissionSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Bir izin kümesi ile belirtilen meta veri imzası için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.|  
|[DefinePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan PInvoke imzası özelliklerini ayarlar.|  
|[DefineProperty Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Belirtilen tür için bir özellik tanımı belirtilen oluşturur `get` ve `set` yöntemi erişimcileri ve bu özellik tanımı için bir belirteç alır.|  
|[DefineSecurityAttributeSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Belirtilen belirteç tarafından başvurulan nesne iliştirmek için güvenlik izinleri kümesi oluşturur.|  
|[DefineTypeDef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Ortak dil çalışma zamanı tür için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.|  
|[DefineTypeRefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Bir meta veri geçerli kapsamı dışında başka bir modül içinde tanımlanan bir tür için belirteç alır.|  
|[DefineUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Bir meta veri için belirtilen değişmez değer dize belirteci alır.|  
|[DeleteClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Belirtilen belirteç tarafından başvurulan türü için sınıf Düzen meta veri imzası yok eder.|  
|[DeleteFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan nesne için meta verileri imza hazırlama PInvoke yok eder.|  
|[DeletePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verileri yok eder.|  
|[DeleteToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Belirtilen belirteç geçerli bir meta veri kapsamından siler.|  
|[GetSaveSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Bütünleştirilmiş kodun ikili tahmini boyutu geçerli kapsamda alır.|  
|[GetTokenFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Belirtilen meta veri imzası bir belirteç alır.|  
|[GetTokenFromTypeSpec Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Bir meta veri türü belirtilen meta veri imzası belirtecini alır.|  
|[Merge Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Belirtilen içeri aktarılan kapsam birleştirilecek kapsamları listesine ekler.|  
|[MergeEnd Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Birleştirmeleri geçerli kapsam için bir veya daha fazla önceki çağrılar tarafından belirtilen tüm meta veri kapsamları `IMetaDataEmit::Merge`.|  
|[Save Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Belirtilen adresteki bir dosyaya geçerli kapsamdaki tüm meta verileri kaydeder.|  
|[SaveToMemory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Belirtilen bellek alanına geçerli kapsamdaki tüm meta verileri kaydeder.|  
|[SaveToStream Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Belirtilen geçerli kapsamdaki tüm meta verileri kaydeder `IStream`.|  
|[SetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir tür sınıfı Düzen imzası güncelleştirmeler `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan özel bir öznitelik değerini güncelleştirir `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerinin `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan alan, yöntem dönüş ya da yöntem parametresi için bilgi hazırlama PInvoke ayarlar.|  
|[SetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değer güncelleştirir veya ayarlar.|  
|[SetFieldRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Göreli sanal adres alanının belirtilen belirteci tarafından başvurulan bir genel değişken değerini ayarlar.|  
|[SetHandler Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Belirtilen tarafından başvurulan ayarlar `IUnknown` bir bildirim geri çağırması için belirteci yeniden eşleme olarak işaretçi.|  
|[SetMethodImplFlags Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Belirtilen belirteç tarafından başvurulan devralınan yöntem uygulaması meta veri imzası güncelleştirir veya ayarlar.|  
|[SetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Ayarlar veya belirtilen göreli sanal adres, bir yöntemin çağrıda tarafından tanımlanan depolandığı özellik güncelleştirmelerinin `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Güncelleştirmeler için önceki bir çağrı tarafından tanımlanan bir modül başvuruları `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir yöntem parametresi özelliklerini değiştirir `IMetaDataEmit::DefineParam`.|  
|[SetParent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Kurar, önceki bir çağrı tarafından tanımlandığı gibi belirtilen üye `IMetaDataEmit::DefineMemberRef`, önceki bir çağrı tarafından tanımlanan belirtilen türün bir üyesi olan `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir izin kümesi meta veri imzası özelliklerini güncelleştirir `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlandığı şekilde bir yöntemin PInvoke imzası, özelliklerini değiştirir `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Önceki bir çağrı tarafından tanımlanan bir özellik için meta verileri içinde depolanan özellikleri ayarlar `IMetaDataEmit::DefineProperty`.|  
|[SetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Belirtilen yöntemin göreli sanal adres ayarlar.|  
|[SetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Önceki bir çağrı tarafından tanımlanan bir tür özelliklerini ayarlar `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Bir derleme geçerli kapsam içeri aktarır ve yeni bir meta veri imzası birleştirilmiş kapsamını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
