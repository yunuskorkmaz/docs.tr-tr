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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175869"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember Yöntemi
Geçerli kapsam dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.  
  
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
 [içinde] Hedef üyenin içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `pbHashValue`  
 [içinde] Tarafından belirtilen derleme için karma içeren `pAssemImport`bir dizi.  
  
 `cbHashValue`  
 [içinde] Dizideki `pbHashValue` bayt sayısı.  
  
 `pImport`  
 [içinde] Hedef üyenin içe aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.  
  
 `mbMember`  
 [içinde] Hedef üyeyi belirten meta veri belirteci. Belirteç bir `mdMethodDef` (üye yöntemi için), `mdProperty` (üye özellik `mdFieldDef` için) veya (üye alan için) belirteç olabilir.  
  
 `pAssemEmit`  
 [içinde] Hedef üyenin içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) arabirimi.  
  
 `tkParent`  
 [içinde] Hedef `mdTypeRef` `mdModuleRef` üyenin sahibi olan tür veya modülün belirteci.  
  
 `pmr`  
 [çıkış] `mdMemberRef` Üye başvurusu için geçerli kapsamda tanımlanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem, `DefineImportMember` başka bir kapsamda `mbMember`tanımlanan, belirtilen `pImport`üyeyi arar ve özelliklerini alır. Bu bilgileri, üye başvurusu oluşturmak için geçerli kapsamdaki [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemini aramak için kullanır.  
  
 Genellikle, `DefineImportMember` yöntemi kullanmadan önce, geçerli kapsamda, hedef üyenin ana sınıfı, arabirimi veya modülü için bir tür başvurusu veya modül başvurusu oluşturmanız gerekir. Bu başvuru için meta veri belirteci `tkParent` sonra bağımsız değişkengeçirilir. Derleyici veya bağlayıcı tarafından daha sonra çözülecekse, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez. Özetlersek:  
  
- Hedef üye bir alan veya yöntemse, [iMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [iMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) yöntemini kullanarak, geçerli kapsamda, üyenin üst sınıfı veya üst arabirimi için bir tür başvurusu oluşturun.  
  
- Hedef üye küresel bir değişken veya global bir işlevse (yani bir sınıfın veya arabirimin üyesi değilse), üyenin ana modülü için geçerli kapsamda bir modül başvurusu oluşturmak için [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) yöntemini kullanın.  
  
- Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından `mdTokenNil` çözülecekse, 'yi `tkParent`geçin. Bunun geçerli olduğu tek senaryo, küresel bir işlev in veya global değişkenin sonunda geçerli modüle bağlanacak ve meta veriler birleştirilecek bir .obj dosyasından içe aktarıldığı zamandır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
