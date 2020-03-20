---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177524"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps Yöntemi
[IMetaDataEmit::DefineEvent'e](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)yapılan bir önceki çağrıyla tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ev`  
 [içinde] Olay belirteci.  
  
 `dwEventFlags`  
 [içinde] Olay bayrakları. Bu `CorEventAttr` değerlerin bir bitmask olduğunu.  
  
 `tkEventType`  
 [içinde] Olay sınıfının belirteci. Bu ya `mdTypeDef` bir `mdTypeRef` ya da bir belirteç.  
  
 `mdAddOn`  
 [içinde] Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 [içinde] Olaya aboneliğini iptal etmek veya geçersiz kılmak için kullanılan yöntem.  
  
 `mdFire`  
 [içinde] Olayı yükseltmek için (türetilmiş bir sınıf tarafından) kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [içinde] Olayla ilişkili diğer yöntemler için bir dizi belirteç. Dizinin son öğesi `mdMethodDefNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
