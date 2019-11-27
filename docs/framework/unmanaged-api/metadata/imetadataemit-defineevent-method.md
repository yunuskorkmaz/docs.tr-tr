---
title: IMetaDataEmit::DefineEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432558"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent Yöntemi
Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Hedef sınıf veya arabirim için belirteç. Bu bir `mdTypeDef` veya `mdTypeDefNil` belirtecidir.  
  
 `szEvent`  
 'ndaki Etkinliğin adı.  
  
 `dwEventFlags`  
 'ndaki Olay bayrakları.  
  
 `tkEventType`  
 'ndaki Olay sınıfı için belirteç. Bu bir `mdTypeDef`, bir `mdTypeRef`veya `mdTokenNil` belirteç.  
  
 `mdAddOn`  
 'ndaki Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.  
  
 `mdFire`  
 'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).  
  
 `rmdOtherMethods[]`  
 'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi. Dizi `mdMethodDefNil` belirteciyle sonlandırılır.  
  
 `pmdEvent`  
 dışı Olaya atanan meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
