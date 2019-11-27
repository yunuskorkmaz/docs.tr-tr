---
title: IMetaDataEmit::DefineImportMember Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431862"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember Yöntemi
Geçerli kapsamın dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAssemImport`  
 'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `pbHashValue`  
 'ndaki `pAssemImport`tarafından belirtilen derlemenin karmasını içeren bir dizi.  
  
 `cbHashValue`  
 'ndaki `pbHashValue` dizisindeki bayt sayısı.  
  
 `pImport`  
 'ndaki Hedef üyenin içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.  
  
 `mbMember`  
 'ndaki Hedef üyeyi belirten meta veri belirteci. Belirteç bir `mdMethodDef` (bir üye yöntemi için), `mdProperty` (üye özelliği için) veya `mdFieldDef` (bir üye alanı için) belirteci olabilir.  
  
 `pAssemEmit`  
 'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) arabirimi.  
  
 `tkParent`  
 'ndaki Hedef üyeye sahip olan, sırasıyla tür veya modül için `mdTypeRef` veya `mdModuleRef` belirteci.  
  
 `pmr`  
 dışı Üye başvurusunun geçerli kapsamında tanımlanan `mdMemberRef` belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineImportMember` yöntemi, `pImport`tarafından belirtilen başka bir kapsamda tanımlanan, `mbMember`tarafından belirtilen üyeyi arar ve özelliklerini alır. Bu bilgileri, üye başvurusunu oluşturmak için geçerli kapsamdaki [ımetadatayayma::D efineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metodunu çağırmak üzere kullanır.  
  
 Genellikle, `DefineImportMember` yöntemini kullanmadan önce, hedef üyenin üst sınıfı, arabirimi veya modülü için geçerli kapsamda, bir tür başvurusu veya modül başvurusu oluşturmanız gerekir. Bu başvurunun meta veri belirteci daha sonra `tkParent` bağımsız değişkenine geçirilir. Derleyici veya bağlayıcı tarafından daha sonra çözülebiliyorsa, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez. Özetlersek:  
  
- Hedef üye bir alan veya yöntem ise, üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için [ımetadatayayma::D efineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [ımetadatayayma::D Efineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodunu kullanın.  
  
- Hedef üye bir genel değişken veya genel işlevse (yani, bir sınıfın veya arabirimin üyesi değil), üyenin üst modülünün geçerli kapsamındaki bir modül başvurusu oluşturmak için [ımetadatayayma::D efineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodunu kullanın.  
  
- Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından çözülecektir, sonra `mdTokenNil` `tkParent`geçirin. Bu tek senaryo, genel bir işlev veya genel değişken, son olarak geçerli modüle ve birleştirilmiş meta veriler ile bağlantılandırılan bir. obj dosyasından içeri aktarılırken yapılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
