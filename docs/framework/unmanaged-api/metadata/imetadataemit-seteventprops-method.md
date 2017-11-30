---
title: "IMetaDataEmit::SetEventProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
