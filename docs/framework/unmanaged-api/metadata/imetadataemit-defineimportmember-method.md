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
ms.openlocfilehash: 2facc63023a20dd6aaac64d7d036324c31658bc8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501319"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember Yöntemi
Geçerli kapsamın dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.  
  
 `pbHashValue`  
 'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .  
  
 `cbHashValue`  
 'ndaki Dizideki bayt sayısı `pbHashValue` .  
  
 `pImport`  
 'ndaki Hedef üyenin içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.  
  
 `mbMember`  
 'ndaki Hedef üyeyi belirten meta veri belirteci. Belirteç bir `mdMethodDef` (üye yöntemi için), `mdProperty` (üye özelliği için) veya `mdFieldDef` (bir üye alanı için) belirteci olabilir.  
  
 `pAssemEmit`  
 'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.  
  
 `tkParent`  
 'ndaki `mdTypeRef` `mdModuleRef` Hedef üyeye sahip olan, sırasıyla tür veya modül için belirteç.  
  
 `pmr`  
 dışı `mdMemberRef`Üye başvurusu için geçerli kapsamda tanımlanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi tarafından belirtilen, tarafından belirtilen `DefineImportMember` `mbMember` başka bir kapsamda tanımlanan üyeyi arar `pImport` ve özelliklerini alır. Bu bilgileri, üye başvurusunu oluşturmak için geçerli kapsamdaki [ımetadatayayma::D efineMemberRef](imetadataemit-definememberref-method.md) metodunu çağırmak üzere kullanır.  
  
 Genellikle, yöntemini kullanmadan önce, `DefineImportMember` hedef üyenin üst sınıfı, arabirimi veya modülü için geçerli kapsamda, bir tür başvurusu veya modül başvurusu oluşturmanız gerekir. Bu başvurunun meta veri belirteci daha sonra `tkParent` bağımsız değişkenine geçirilir. Derleyici veya bağlayıcı tarafından daha sonra çözülebiliyorsa, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez. Özetlersek:  
  
- Hedef üye bir alan veya yöntem ise, üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için [ımetadatayayma::D efineTypeRefByName](imetadataemit-definetyperefbyname-method.md) veya [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md) metodunu kullanın.  
  
- Hedef üye bir genel değişken veya genel işlevse (yani, bir sınıfın veya arabirimin üyesi değil), üyenin üst modülünün geçerli kapsamındaki bir modül başvurusu oluşturmak için [ımetadatayayma::D efineModuleRef](imetadataemit-definemoduleref-method.md) metodunu kullanın.  
  
- Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından çözülecektir, sonra da geçiş yapın `mdTokenNil` `tkParent` . Bu tek senaryo, genel bir işlev veya genel değişken, son olarak geçerli modüle ve birleştirilmiş meta veriler ile bağlantılandırılan bir. obj dosyasından içeri aktarılırken yapılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
