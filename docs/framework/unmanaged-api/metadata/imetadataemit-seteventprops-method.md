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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42dc78ff3c58b67801cd99512781d8c8509dd272
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps Yöntemi
Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerini [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `ev`  
 [in] Olay belirteci.  
  
 `dwEventFlags`  
 [in] Olay bayraklar. Bu, bir bit maskesi olan `CorEventAttr` değerleri.  
  
 `tkEventType`  
 [in] Event sınıfı için belirteci. Bu olan bir `mdTypeDef` veya `mdTypeRef` belirteci.  
  
 `mdAddOn`  
 [in] Olay ya da null için abone olmak için kullanılan yöntem.  
  
 `mdRemoveOn`  
 [in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.  
  
 `mdFire`  
 [in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi. Dizinin son öğesi olmalı `mdMethodDefNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
