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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7d42fe17af5b10d718d0e2b6a7ae33644fa4813
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730301"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent Yöntemi
Belirtilen meta verileri imza ile bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Hedef sınıf veya arabirim için belirteç. Bu bir `mdTypeDef` veya `mdTypeDefNil` belirteci.  
  
 `szEvent`  
 [in] Olayın adı.  
  
 `dwEventFlags`  
 [in] Olay bayrakları.  
  
 `tkEventType`  
 [in] Olay sınıfı için belirteci. Bu bir `mdTypeDef`, `mdTypeRef`, veya `mdTokenNil` belirteci.  
  
 `mdAddOn`  
 [in] Olay ya da null için abone olmak için kullanılan yöntem.  
  
 `mdRemoveOn`  
 [in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.  
  
 `mdFire`  
 [in] (Bir türetilmiş sınıf tarafından) olay oluşturmak için kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [in] Olay ile ilişkili diğer yöntemleri için belirteçleri dizisi. Dizi ile sonlandırılmış bir `mdMethodDefNil` belirteci.  
  
 `pmdEvent`  
 [out] Olaya atanan meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
