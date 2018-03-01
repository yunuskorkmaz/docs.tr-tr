---
title: IMetaDataEmit Arabirimi
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856b4c42b018d6b1cefe6b61e21a15e7212f9541
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit Arabirimi
Oluşturmak, değiştirmek ve şu anda tanımlanmış kapsamda derleme hakkındaki meta verileri kaydetmek için yöntemler sağlar. Meta veriler bellekte veya diske kaydedilmiş.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyEditAndContinue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Belirtilen yapılan değişiklikler geçerli derleme kapsamı güncelleştirmelerle `pImport`.|  
|[DefineCustomAttribute Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Belirtilen nesneye bağlı olması için belirtilen metadata imzayla özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.|  
|[DefineEvent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Belirtilen meta veri imzayla bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.|  
|[DefineField Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Belirtilen meta veri imzayla bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.|  
|[DefineImportMember Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Geçerli kapsam dışında bir modüldeki tanımlanır ve bu başvuru tanımı için bir belirteç alır türünün bir üyesi için bir tanımı oluşturur.|  
|[DefineImportType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Geçerli kapsam dışında bir modülde tanımlanan ve bu başvuru tanımı için bir belirteç alan türüne bir başvuru için bir tanım oluşturur.|  
|[DefineMemberRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Geçerli kapsam dışında bir modülün bir üyeye başvuru için bir tanım oluşturur ve bu başvuru tanımına bir belirteci alır.|  
|[DefineMethod Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Bir yöntem için bir tanım belirtilen imzayla oluşturur ve bu yöntem tanımı için bir belirteç döndürür.|  
|[DefineMethodImpl Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Arabirimden devralınan bir yöntemin kullanımı için bir tanım oluşturur ve bu yöntemi uygulama tanımı için bir belirteç döndürür.|  
|[DefineModuleRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Belirtilen ada sahip bir modül için meta verileri imza oluşturur.|  
|[DefineNestedType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Meta veri imza tür tanımı oluşturur ve döndürür bir `mdTypeDef` token ayrıca tanımlanmış türü tarafından başvurulan türünün bir üyesi olduğunu belirten, bu tür için `tdEncloser`.|  
|[DefineParam Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzalı bir parametrenin tanımını oluşturur ve bu parametre tanımı için bir belirteç alır.|  
|[DefinePermissionSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Bir izin kümesi ile belirtilen metadata imza için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.|  
|[DefinePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan PInvoke imzası özelliklerini ayarlar.|  
|[DefineProperty Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Belirtilen türde bir özellik tanımı belirtilen oluşturur `get` ve `set` yöntemi erişimciler ve bu özellik tanımı için bir belirteç alır.|  
|[DefineSecurityAttributeSet Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Belirtilen belirteç tarafından başvurulan nesne eklemek için güvenlik izinleri kümesi oluşturur.|  
|[DefineTypeDef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.|  
|[DefineTypeRefByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Bir meta veri geçerli kapsamı dışında başka bir modülde tanımlanan bir tür için belirteç alır.|  
|[DefineUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Bir meta veri için belirtilen değişmez değer dize belirteci alır.|  
|[DeleteClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Belirtilen belirteç tarafından başvurulan türü için sınıf düzeni meta verileri imza yok eder.|  
|[DeleteFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan nesne için meta veri imzası hazırlama PInvoke bozar.|  
|[DeletePinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Belirtilen belirteç tarafından başvurulan nesne PInvoke eşleme meta verileri yok eder.|  
|[DeleteToken Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Belirtilen belirteç geçerli meta veri kapsamdan siler.|  
|[GetSaveSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Geçerli kapsamda derleme tahmini ikili boyutunu alır.|  
|[GetTokenFromSig Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Belirtilen meta veri imza için bir belirteç alır.|  
|[GetTokenFromTypeSpec Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Bir meta veri türü belirtilen metadata imzalı belirteç alır.|  
|[Merge Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Belirtilen alınan kapsam birleştirilecek kapsamları listesine ekler.|  
|[MergeEnd Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Birleştirmeler geçerli kapsam için bir veya daha fazla önceki çağrıları tarafından belirtilen tüm meta veri kapsamları `IMetaDataEmit::Merge`.|  
|[Save Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Belirtilen adresteki dosya için geçerli kapsamdaki tüm meta verilerini kaydeder.|  
|[SaveToMemory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Bellek belirtilen alan için geçerli kapsamdaki tüm meta verilerini kaydeder.|  
|[SaveToStream Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Belirtilen geçerli kapsamdaki tüm meta veriler kaydeder `IStream`.|  
|[SetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir türü sınıf düzeni imzası güncelleştirmeler `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan özel bir öznitelik değeri güncelleştirmeler `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliği güncelleştirmeler `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Belirtilen belirteç tarafından başvurulan alan, dönüş yöntemi veya yöntem parametresi için bilgi hazırlama PInvoke ayarlar.|  
|[SetFieldProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Belirtilen alan belirteci tarafından başvurulan bir alan için varsayılan değer güncelleştirir veya ayarlar.|  
|[SetFieldRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Göreli sanal adres alanının belirtilen belirtecin tarafından başvurulan genel bir değişken değerini ayarlar.|  
|[SetHandler Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Belirtilen tarafından başvurulan yöntemini ayarlar `IUnknown` işaretçi olarak belirteci yeniden harita oluşturma için bir bildirim geri çağırma.|  
|[SetMethodImplFlags Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Belirtilen belirteç tarafından başvurulan devralınan yöntemi uygulama meta verileri imzası güncelleştirir veya ayarlar.|  
|[SetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Belirtilen göreli sanal adresinde, önceki bir çağrı tarafından tanımlanan bir yöntemin depolanan özelliği, güncelleştirir veya ayarlar `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Güncelleştirmeler için önceki bir çağrı tarafından tanımlanan bir modül başvurular `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir yöntem parametresi özelliklerini değiştirir `IMetaDataEmit::DefineParam`.|  
|[SetParent Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Kurar belirtilen üye, önceki bir çağrı tarafından tanımlanan `IMetaDataEmit::DefineMemberRef`, önceki bir çağrı tarafından tanımlandığı gibi belirtilen türünün bir üyesi olan `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlanan bir izin kümesi meta verileri imzası özelliklerini güncelleştirir `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Ayarlar veya önceki bir çağrı tarafından tanımlandığı şekilde bir yöntemin PInvoke imzası özelliklerini değiştirir `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Önceki bir çağrı tarafından tanımlanmış bir özellik için meta verilerde depolanan özellikleri ayarlar `IMetaDataEmit::DefineProperty`.|  
|[SetRVA Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Belirtilen yöntem göreli sanal adresini ayarlar.|  
|[SetTypeDefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Önceki bir çağrı tarafından tanımlanan bir türü özelliklerini ayarlar `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Bir derlemeyi geçerli kapsam alır ve yeni bir meta veri imza için birleştirilmiş kapsamı alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
