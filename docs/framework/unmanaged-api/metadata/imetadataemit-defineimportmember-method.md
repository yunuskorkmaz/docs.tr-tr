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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ac44d29dd99e0205c515905f9846263033babf3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479304"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember Yöntemi
Bir türün veya geçerli kapsam dışında tanımlanan ve bu başvuru için bir belirteç tanımlar modülü belirtilen üyesine bir başvuru oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) hedef üye içe derleme temsil eden arabirim.  
  
 `pbHashValue`  
 [in] Tarafından belirtilen derleme için karma içeren bir dizi `pAssemImport`.  
  
 `cbHashValue`  
 [in] Bayt sayısı `pbHashValue` dizisi.  
  
 `pImport`  
 [in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) hedef üye içe meta veri kapsamı temsil eden arabirim.  
  
 `mbMember`  
 [in] Hedef üye belirleyen meta veri belirteci. Belirteç olabilir bir `mdMethodDef` (için üye yöntemi) `mdProperty` (bir üye özelliği için) veya `mdFieldDef` (için bir üye alan) belirteci.  
  
 `pAssemEmit`  
 [in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) hedef üye içe içine derleme temsil eden arabirim.  
  
 `tkParent`  
 [in] `mdTypeRef` Veya `mdModuleRef` typ nebo modul belirteci, sırasıyla, hedef üye sahip.  
  
 `pmr`  
 [out] `mdMemberRef` Üye başvurusu için geçerli kapsamda tanımlı belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineImportMember` Yöntemi tarafından belirtilen üye, şuna `mbMember`, yani tarafından belirtilen başka bir kapsamda tanımlı `pImport`ve özelliklerini alır. Çağırmak için bu bilgileri kullanır [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) üyesi başvuru oluşturmak için geçerli kapsamda yöntemi.  
  
 Genellikle, önce kullanırsınız `DefineImportMember` yöntemi oluşturmanız gerekir, geçerli kapsam, bir tür başvurusu veya hedef üyenin üst sınıf, arabirim veya modül için modülü başvurusu. Bu başvuru için meta veri belirteci sonra geçirilen `tkParent` bağımsız değişken. Derleyici veya bağlayıcı tarafından daha çözümlenir, hedef üyenin üst başvuru oluşturmak gerekmez. Özetlersek:  
  
-   Hedef alan veya yöntem üyesiyse, kullanın [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [Imetadataemit::defineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) geçerli kapsamda bir tür başvurusu için oluşturmak üzere yöntemi Üyenin üst sınıfta veya üst arabirimi.  
  
-   Genel bir değişken veya genel işlev (diğer bir deyişle, bir üyesi değil bir sınıf veya arabirim) hedef üye ise kullanın [Imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) geçerli kapsamda üyenin üst için bir modül başvurusu oluşturmak için yöntemi Modül.  
  
-   Hedef üyenin üst daha sonra derleyici veya bağlayıcı tarafından çözümlenir, ardından geçirin `mdTokenNil` içinde `tkParent`. Tek senaryo, bu geçerlidir genel bir işlev olduğunda veya genel değişkeni geçerli bir modüle sonuçta bağlanacak bir .obj dosyasından içeri aktarılan ve meta veriler birleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
