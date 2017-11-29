---
title: "IMetaDataEmit::DefineImportMember Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d06bf7649f09b2111bf9a6840968743ad77bdca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember Yöntemi
Bir tür ya da geçerli kapsamı dışında tanımlanır ve bu başvurusu için bir belirteç tanımlayan modülü belirtilen üyesine bir başvuru oluşturur.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pAssemImport`  
 [in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) içinden hedef üye alındığından derleme temsil eden arabirim.  
  
 `pbHashValue`  
 [in] Belirtilen derleme için karma içeren bir dizi `pAssemImport`.  
  
 `cbHashValue`  
 [in] Bayt sayısı `pbHashValue` dizi.  
  
 `pImport`  
 [in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) içinden hedef üye alındığından meta veri kapsamı temsil eden arabirim.  
  
 `mbMember`  
 [in] Hedef üye belirtir meta veri simgesi. Belirteç olabilir bir `mdMethodDef` (için üye yöntemi) `mdProperty` (bir üye özelliği için) veya `mdFieldDef` (için üye alanı) belirteci.  
  
 `pAssemEmit`  
 [in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) içine hedef üye alındığından derleme temsil eden arabirim.  
  
 `tkParent`  
 [in] `mdTypeRef` Veya `mdModuleRef` belirteç türü ya da modülü, sırasıyla, hedef üye sahip.  
  
 `pmr`  
 [out] `mdMemberRef` Üye başvurusunun geçerli kapsamda tanımlı belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineImportMember` Yöntemi tarafından belirtilen üye arayan `mbMember`, yani tarafından belirtilen başka bir kapsamda tanımlanan `pImport`ve özelliklerini alır. Çağırmak için bu bilgiyi kullanır [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) üye başvuru oluşturmak için geçerli kapsamdaki yöntemi.  
  
 Genellikle, önce kullandığınız `DefineImportMember` yöntemi, oluşturmanız gerekir, geçerli kapsam, bir tür referansı veya hedef üyenin üst sınıf, arabirim veya modül için modülü başvurusu. Bu başvuru için meta veri simgesi ardından geçirilen `tkParent` bağımsız değişkeni. Derleyici veya bağlayıcı tarafından daha sonra çözümlenir, hedef üyenin üst başvuru oluşturmak gerekmez. Özetlersek:  
  
-   Hedef alan veya yöntem üyesiyse, kullanın ya da [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [Imetadataemit::defineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) bir türü başvurusu geçerli kapsam için oluşturmak üzere yöntemi Üyenin üst sınıf veya üst arabirim.  
  
-   Hedef üye bir genel değişkeni ya da genel işlevi (diğer bir deyişle, değil üyesi sınıfta veya arabirimde) ise, kullanın [Imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) bir modül başvurusu geçerli kapsamın üyenin üst oluşturulacağı yöntemi Modül.  
  
-   Hedef üyenin üst daha sonra derleyici veya bağlayıcı tarafından çözümlenir, daha sonra geçirin `mdTokenNil` içinde `tkParent`. İçinde bu uygulandığı tek senaryo genel işlevi, veya genel değişkeni geçerli modüle bağlı sonuçta bir .obj dosyasından içeri aktarılmakta olan ve meta verileri birleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
